---
title: "Confident or Seek Stronger: Exploring Uncertainty-Based Small LM Routing From Benchmarking to Generalization"
title_zh: 自信还是寻求更强：从基准测试到泛化的不确定性小语言模型路由探索
authors: "Yu-Neng Chuang, Leisheng Yu, Guanchu Wang, Lizhe Zhang, Zirui Liu, Xuanting Cai, Yang Sui, Vladimir Braverman, Xia Hu"
date: 2025-05-10
pdf: "https://openreview.net/pdf?id=smdbra3VEi"
tags: ["query:edge-llm"]
score: 7.0
evidence: 小语言模型在边缘设备上的部署及效率权衡
tldr: 边缘设备上小语言模型（SLM）因能效优势被广泛部署，但处理复杂查询时准确率不足。本文研究基于不确定性的SLM路由策略，将高置信度查询本地处理，低置信度查询卸载至大模型，在保证可靠性的同时控制调用成本。实验证明了路由机制在边缘场景下的有效性。该工作直接针对边缘设备LLM推理的资源效率优化。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-smdbra3vei/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-smdbra3vei/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1406, \"height\": 780, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-smdbra3vei/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1393, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-smdbra3vei/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1347, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-smdbra3vei/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1452, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-smdbra3vei/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1453, \"height\": 342, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-smdbra3vei/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 384, \"label\": \"Table\"}]"
motivation: 边缘设备部署SLM面临复杂查询准确率低的问题，需要高效路由机制来平衡效率和可靠性。
method: 提出不确定性驱动的SLM路由方法，根据小模型置信度决定是否调用大模型。
result: 在多种基准上验证了路由策略在边缘场景下对效率和准确率的平衡效果。
conclusion: 不确定性路由为边缘设备上的高效LLM推理提供了有价值的优化方向。
---

## Abstract
Small language models (SLMs) are increasingly deployed on edge devices for personalized applications, offering efficient decoding latency and reduced energy consumption. However, these SLMs often generate inaccurate responses when handling complex queries. One promising solution is uncertainty-based SLM routing, offloading high-stakes queries to stronger large language models (LLMs) when resulting in low-confidence responses on SLM. This follows the principle of If you lack confidence, seek stronger support to enhance reliability. Relying on more powerful LLMs is yet effective but increases invocation costs. Therefore, striking a routing balance between efficiency and efficacy remains a critical challenge. Additionally, efficiently generalizing the routing strategy to new datasets remains under-explored. In this paper, we conduct a comprehensive investigation into benchmarking and generalization of uncertainty-driven routing strategies from SLMs to LLMs over 5000+ settings. Our findings highlight: First, uncertainty-correctness alignment in different uncertainty quantification (UQ) methods significantly impacts routing performance. Second, uncertainty distributions depend more on both the specific SLM and the chosen UQ method, rather than on downstream data. Building on the insight, we propose a proxy routing data construction pipeline and open-source a hold-out set to enhance the generalization on predicting the routing curve for new downstream data. Experimental results indicate that proxy routing data effectively bootstraps routing performance without any new data.

---

## 论文详细总结（自动生成）

好的，基于您提供的论文文本，以下是对该论文的详细中文总结，按照要求的八点展开。

---

## 1. 核心问题与整体含义

**研究动机与背景：** 小型语言模型（SLM）因低延迟和低能耗被广泛部署在手机、可穿戴设备等边缘设备上，但在处理复杂查询时准确率往往不足。一个主流解决方案是**基于不确定性的路由**：当 SLM 对自己生成的回答缺乏信心（低置信度）时，将查询转发给更强的大型语言模型（LLM），遵循“不自信就求助更强模型”的原则。然而，频繁调用 LLM 会显著增加部署成本。因此，**如何在保证系统整体可靠性的同时，最小化对 LLM 的调用次数（即平衡效率与效果）** 成为一个关键挑战。此外，现有的路由方法通常需要在新数据集上重新收集数据和分析，缺乏对未见数据集的泛化能力，制约了实际部署。

**论文整体含义：** 本文系统性基准测试了基于不确定性的 SLM 路由策略（5000+ 配置），并提出了一个**代理路由数据构建流水线**，使得路由策略能够在无需任何新下游数据的情况下，准确预测在新数据集上的路由曲线，从而高效初始化路由系统。

## 2. 提出的方法论

**核心思想：** 通过 SLM 自身的不确定性量化（UQ）分数来判断是否将查询路由给 LLM。关键在于找到 UQ 分数与预测正确性之间良好的对齐关系，从而做出高效的路由决策。论文还基于“不确定性分布主要取决于 SLM 和 UQ 方法，而非下游数据”这一发现，构建一个领域泛化的代理路由数据集来模拟任意新数据集的路由行为。

**关键技术细节：**
- **不确定性量化方法**：评估了 4 大类共 8 种 UQ 方法：
  - **词元/序列概率类**：平均 Token 概率、困惑度（Perplexity，取其倒数作为置信度）、p(True)
  - **口头化不确定性**：单步口头化（1s）、两步口头化（2s）
  - **输出一致性类**：Jaccard 度（对 5 个样本计算相似度）
  - **训练探针类**：训练探针（Trained Probe，用有监督数据训练 MLP 从隐层状态预测正确性）、OOD 探针（OOD Probe，用其他所有域的数据训练）
- **路由决策**：设定一个置信度阈值，SLM 对查询的置信度低于该阈值时路由给 LLM。通过调整阈值可控制路由比例（被转发查询的比例），从而得到路由曲线（不同路由比例下的系统准确率）。

**代理路由数据构建流水线（Algorithm 1 文字说明）：**
1. 收集多个不同领域的数据集集合 D（如常识推理、数学推理等）。
2. 使用选定的 UQ 方法处理 D 中的每个样本，得到全局不确定性分布，并将其离散化为 M 个分箱。
3. 从每个分箱中按比例加权采样一定数量的样本，形成最终代理路由数据集 X。这样 X 就拥有了与原始分布相似的不确定性覆盖范围。
- **关键思想**：由于不确定性分布与数据域无关，这个代理数据集可以用于预测任意新下游数据集的路由曲线，无需访问新数据本身。

## 3. 实验设计

- **数据集**：共 15 个，覆盖 4 个领域：
  - 数学推理：AQuA、GSM8K、MultiArith、SVAMP、MATH-500
  - 常识推理：CommonsenseQA、HellaSwag、OpenBookQA、PIQA、TruthfulQA、Winogrande、BoolQ、Social IQa
  - 对话与上下文理解：CoQA
  - 问题解决：MMLU
- **模型**：
  - SLM（12 个）：非推理型（Llama-3.2-1B/3B-Instruct、Phi-3.5-mini、Mistral-7B、Qwen2.5-7B、Llama-3.1-8B、Granite-3.1-8B）、推理型（Qwen3 系列 0.6B/1.7B/4B、Phi-4-mini-reasoning）、RNN 型（RWKV-7-2.9B）
  - LLM（4 个）：开源的 Llama-3.1-70B-Instruct、Qwen3-32B、DeepSeek-R1，以及 API 模型 GPT-4.1 mini
- **对比方法**：8 种 UQ 方法作为路由评分函数相互对比；同时对比不同 SLM 与 LLM 组合。
- **Benchmark 指标**：
  - **不确定性-正确性对齐**：使用 ROC AUC 分数衡量 UQ 分数与预测正确性的相关性。
  - **路由性能**：绘制“系统准确率 vs 路由比例”的曲线，直观展示效率-效果权衡。
  - **代理数据泛化**：将代理路由数据预测的路由曲线与基于完整新数据集计算的真实曲线进行比较。

## 4. 资源与算力

论文明确提到：**所有实验均在 4 张 80 GB NVIDIA A100 GPU 上完成**。训练探针（Trained Probe）设置 20 个 epochs，学习率 5e-4；OOD 探针也是 20 个 epochs，学习率 1e-4。但未给出总的训练或推理耗时，也未给出单个实验的平均运行时间。

## 5. 实验数量与充分性

- **实验规模**：超过 **5000+ 种设置**（12 个 SLM × 4 个 LLM × 8 个 UQ 方法 × 15 个数据集，部分组合有额外变体）。
- **充分性**：覆盖了不同架构（Transformer、RNN）、不同规模（0.6B–8B）、不同训练风格（推理 vs 非推理）的 SLM，以及开源和闭源 LLM；数据集覆盖多种任务类型（选择题、自由生成、是非题）。路由性能评估在两个泛化设定（完全域外、部分域内）下进行。此外，报告了平均三次运行的结果以确保可靠性。
- **公平性**：代码已匿名开源（https://anonymous.4open.science/r/quodlibeta），便于复现；设置了固定种子和温度（0），控制随机性。GPT-4.1 mini 用于评估自由生成答案的正确性，避免了人工偏差。

## 6. 主要结论与发现

1. **不确定性-正确性对齐是路由性能的关键**：对齐好的 UQ 方法（如 Trained Probe、OOD Probe、Perplexity）能显著提升路由效果；而口头化方法（Verbalization-1s/2s）对齐很差，不适合 SLM 路由。
2. **SLM 在高置信度查询上可以媲美 LLM**：当保留 SLM 最自信的查询（如最高 20%）时，其准确率接近甚至等于 LLM 的水平。
3. **不确定性分布主要由 SLM 和 UQ 方法决定，而非下游数据集**：不同数据集上同一 SLM+UQ 组合的置信度分布几乎重合（图 4）。这一现象是代理路由数据可行性的理论基础。
4. **代理路由数据能准确预测新数据集的路由曲线，无需任何新数据**：在完全域外和部分域内设定下，由代理数据计算的路由曲线与真实曲线高度吻合（图 5、图 6），证明其强大的泛化能力，可用于早期部署阶段的路由策略初始化。

## 7. 优点

- **全面而系统的基准测试**：5000+ 配置覆盖了主流 SLM/LLM/UQ/数据集，结果详实，为后续研究提供了可靠参考。
- **发现具有推广价值**：不确定性分布的数据无关性是一个重要洞见，简化了路由策略在新场景下的部署。
- **提出实用解决方案**：代理路由数据构建流水线无需任何新数据即可预测路由曲线，显著降低了早期部署成本和时间，适合高可靠性场景。
- **开源代码和数据**：促进可复现性和社区进一步研究。
- **分析细致深入**：包含多维度可视化（ROC AUC、路由曲线、相对准确率等），对方法优劣给出了清晰解释。

## 8. 不足与局限

- **未覆盖所有 SLM 类型**：实验只用了预训练 SLM，不含通过剪枝、量化等压缩得到的模型，其不确定性特性可能不同。
- **未涉及多模态模型**：仅处理纯文本，未来需扩展到视觉-语言模型（如 LLaVa、InternVL）。
- **代理路由数据域覆盖有限**：虽然采用了 14 个数据集，但若新数据集属于非常极端的域（如代码生成），泛化效果可能下降。
- **口头化方法表现差**：可能因为 SLM 本身太小、训练指令不足，但对更大 LLM 可能有效，论文未深入探讨原因。
- **实际部署挑战**：未考虑设备间差异（如 iOS vs Android）、数据隐私、持续学习等问题，仅为离线基准测试。
- **语言限制**：所有数据集为英文，未检测对中文等其他语言的泛化性。
- **未比较其他非不确定性的路由方法**：如基于分类器训练的路由器，仅聚焦于不确定性驱动。

---

（完）
