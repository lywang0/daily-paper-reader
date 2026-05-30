---
title: "EE-LLM: Large-Scale Training and Inference of Early-Exit Large Language Models with 3D Parallelism"
title_zh: EE-LLM：基于3D并行的早期退出大语言模型大规模训练与推理
authors: "Yanxi Chen, Xuchen Pan, Yaliang Li, Bolin Ding, Jingren Zhou"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=xFk0w9zoV3"
tags: ["query:edge-llm"]
score: 5.0
evidence: 早期退出机制加速LLM推理
tldr: 本文提出EE-LLM框架，支持大规模早期退出LLM的训练和推理，采用3D并行技术。早期退出可加速推理，但此前难以扩展。EE-LLM实现了算法创新和性能优化，包括轻量级反向传播方法和流水线并行中空闲资源利用。实验表明在大规模集群上训练和推理高效。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-xfk0w9zov3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 754, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xfk0w9zov3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 775, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xfk0w9zov3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1631, \"height\": 769, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xfk0w9zov3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 851, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xfk0w9zov3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 843, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xfk0w9zov3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 812, \"height\": 883, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xfk0w9zov3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 806, \"height\": 1221, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xfk0w9zov3/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 867, \"height\": 877, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xfk0w9zov3/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1768, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xfk0w9zov3/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 896, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xfk0w9zov3/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1610, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xfk0w9zov3/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 875, \"height\": 538, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-xfk0w9zov3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1516, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-xfk0w9zov3/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1242, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-xfk0w9zov3/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1695, \"height\": 591, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-xfk0w9zov3/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1549, \"height\": 746, \"label\": \"Table\"}]"
motivation: 早期退出能加速LLM推理，但缺乏大规模训练和推理的支持。
method: 构建EE-LLM框架，基于Megatron-LM实现3D并行，优化早期退出训练的反向传播和流水线调度。
result: 成功扩展到大规模模型，推理加速显著。
conclusion: EE-LLM使早期退出LLM在大规模场景下实用，提升推理效率。
---

## Abstract
We present EE-LLM, a framework for large-scale training and inference of early-exit large language models (LLMs). While recent works have shown preliminary evidence for the efficacy of early exiting in accelerating LLM inference, EE-LLM makes a foundational step towards scaling up early-exit LLMs by supporting their training and inference with massive 3D parallelism. Built upon Megatron-LM, EE-LLM implements a variety of algorithmic innovations and performance optimizations tailored to early exiting, including a lightweight method that facilitates backpropagation for the early-exit training objective with pipeline parallelism, techniques of leveraging idle resources in the original pipeline schedule for computation related to early-exit layers, and two approaches of early-exit inference that are compatible with KV caching for autoregressive generation. Our analytical and empirical study shows that EE-LLM achieves great training efficiency with negligible computational overhead compared to standard LLM training, as well as outstanding inference speedup without compromising output quality. To facilitate further research and adoption, we release EE-LLM at https://github.com/pan-x-c/EE-LLM.

---

## 论文详细总结（自动生成）

# EE-LLM: 基于3D并行的早期退出大语言模型大规模训练与推理

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：早期退出（Early Exit）可以加速大语言模型（LLM）推理，但此前工作受限于模型规模较小（最大13B参数），缺乏支持大规模训练和推理的系统基础设施。
- **背景**：标准LLM（如GPT-3 175B）已广泛部署，而早期退出LLM因其自适应计算能力有望进一步降低推理成本，但面临三大挑战：1) 训练需支持3D并行（数据、张量/序列、流水线并行）；2) 早期退出层会带来额外计算开销；3) 与KV缓存冲突。
- **整体含义**：本文提出EE-LLM框架，首次实现大规模早期退出LLM的端到端支持（训练+推理），使早期退出能实用化扩展到百亿参数级别。

## 2. 方法论
- **核心思想**：在Megatron-LM框架基础上扩展，通过算法创新和性能优化支持早期退出LLM的3D并行训练与推理。
- **关键技术细节**：
  - **训练反向传播**：提出轻量级辅助损失（auxiliary loss）方法，每个流水线阶段定义局部损失 \( L_i \)，并通过线性项 \(\langle g_i, x_i \rangle\) 传播后续梯度的信息，实现跨阶段梯度计算，无需额外通信。
  - **资源利用优化**：
    - 利用流水线1F1B调度中的“显式气泡”（空闲时间）和“隐式气泡”（负载不均）来放置早期退出层的计算。
    - 将早期退出层的前向计算延迟到对应微批的**反向步骤**中执行，减少激活内存占用（从 \(O(P \cdot s \cdot b \cdot V)\) 降至 \(O(s \cdot b \cdot V)\)）。
  - **推理兼容KV缓存**：
    - **KV重计算方法**：维护缺失KV缓存的token列表，在每次前向时重计算它们的KV，利用GPU批处理加速。
    - **流水线并行方法**：当在某阶段提前退出时，退出token立即返回第一阶段生成下一个token，同时继续在原设备上完成后续阶段的前向以补全KV缓存（与后续token的前向并行），理论加速与选择退出层的计算时间匹配。

## 3. 实验设计
- **数据集**：使用Data-Juicer提供的预训练数据子集。
- **Benchmark任务**（来自HELM）：
  - BoolQ、TruthfulQA（问答，评估指标EM）
  - NaturalQuestions（封闭/开放问答，F1）
  - XSUM、CNN/DailyMail（摘要，ROUGE-L）
- **对比方法**：
  - 训练：对比标准LLM（无早期退出）的损失收敛和训练效率。
  - 推理：对比KV重计算方法（TP=1和TP=4）与流水线并行方法（PP=4）。
- **设置**：采用贪心解码和基于置信度的退出条件（阈值可调），比较加速比与生成质量。

## 4. 资源与算力
- **训练**：
  - 集群：8节点，每节点8块Nvidia A100-80GB GPU，共64块GPU。
  - 模型规模：1.3B、7B、13B、30B参数。
  - 并行配置：数据并行度固定4，张量并行（TP）和流水线并行（PP）取值（如PP=4,TP=1等）。
  - 全局batch size=2048，序列长度=2048。
- **推理**：
  - 4块Nvidia A100-40GB GPU，用于流水线并行推理。
- **未明确训练时长**：仅给出每迭代时间（如30B模型约100秒/迭代），但未说明总训练步数。

## 5. 实验数量与充分性
- **训练实验**：
  - 损失收敛曲线（1.3B和7B模型，含不同配置的消融）。
  - 训练效率对比（时间、峰值内存 vs 早期退出数量、并行策略）涵盖1.3B/7B/13B/30B。
  - 附加实验：不同早期退出结构（加MLP、不同层位置）的损失收敛。
- **推理实验**：
  - 六个任务上比较不同阈值下的加速比和评价指标。
  - 对比两种推理方法（KV重计算 vs 流水线并行）的延迟。
- **消融实验**：性能优化（推迟前向、移动退出层位置）的影响（表1）。
- **充分性**：实验覆盖不同模型规模、并行配置、任务类型、阈值设置，结果具有代表性。比较公平（相同数据、超参数）。但未与其他动态网络方法（如层跳过、投机性解码）直接对比。

## 6. 主要结论与发现
- **训练**：EE-LLM训练早期退出LLM的额外开销极小，峰值内存不变（在合理配置下），时间仅增加少量（每个早期退出约 \(f_{EE}+b_{EE}\)）。
- **推理**：流水线并行方法在多个任务上达到2倍以上加速，且输出质量与全模型推理相当或略优（如BoolQ、TruthfulQA）。KV重计算方法在高带宽硬件下更快，但流水线并行更实用。
- **收敛性**：早期退出损失略高于最终损失，但最终损失接近甚至低于标准LLM，表明多任务训练未损害全模型性能。
- **适用性**：早期退出对“简单”token（高置信度）有效，可在不牺牲整体质量的前提下大幅加快生成速度。

## 7. 优点
- **方法创新**：提出的辅助损失反向传播方法简洁有效，无需修改通信模式；利用流水线气泡和延迟前向计算实现高效训练。
- **系统实现**：基于Megatron-LM构建，开源代码，支持灵活配置（退出位置、结构、损失权重等）。
- **实验覆盖**：训练效率分析包含理论公式与实测，验证了资源利用优化；推理实验覆盖多种任务和阈值，对比了两种方法。
- **兼容性**：推理方法兼容KV缓存，不依赖硬件批处理效应（流水线并行方法理论加速明确）。
- **规模突破**：首次将早期退出LLM训练扩展到30B参数（受限于可用硬件），展示了可扩展性。

## 8. 不足与局限
- **实验局限**：最大规模仅30B（受64块A100限制），未在更大模型（如175B）上进行验证。推理仅测试1.3B和7B模型，更大模型下的加速比仅为推测。
- **对比不足**：未与其他加速方法（如投机性解码、层跳过、混合专家）进行对比，缺乏Relative Improvement分析。
- **推理方法限制**：流水线并行方法需要多设备；KV重计算在高理论复杂度下依赖GPU批处理，在CPU或低带宽设备上可能无效。
- **阈值依赖**：退出条件基于置信度阈值，可能不鲁棒（如长尾分布、对抗性输入）。论文未讨论更高级的退出决策机制。
- **模型架构**：仅基于纯解码器GPT架构，未验证编码器-解码器或MoE架构。
- **训练数据**：使用数据子集，未给出具体大小；训练收敛曲线显示部分尖峰，可能受不稳定因素影响。

（完）
