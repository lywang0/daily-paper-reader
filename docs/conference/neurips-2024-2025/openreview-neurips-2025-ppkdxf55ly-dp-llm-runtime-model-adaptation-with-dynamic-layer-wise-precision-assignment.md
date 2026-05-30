---
title: "DP-LLM: Runtime Model Adaptation with Dynamic Layer-wise Precision Assignment"
title_zh: DP-LLM：基于动态层精度分配的运行时模型适应
authors: "Sangwoo Kwon, Seong Hoon Seo, Jae W. Lee, Yeonhong Park"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ppKDXf55lY"
tags: ["query:edge-llm"]
score: 8.0
evidence: 运行时动态精度分配，适配设备端LLM
tldr: 本文针对设备端LLM运行时延迟和精度约束多变的问题，观察到每层敏感度在解码步骤中动态变化，提出DP-LLM机制动态分配每层精度，结合多尺度量化实现内存高效的运行时模型适应，平衡性能与准确性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ppkdxf55ly/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 571, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ppkdxf55ly/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 821, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ppkdxf55ly/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 732, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ppkdxf55ly/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 563, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ppkdxf55ly/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1388, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ppkdxf55ly/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 668, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ppkdxf55ly/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1423, \"height\": 282, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ppkdxf55ly/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1363, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ppkdxf55ly/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1364, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ppkdxf55ly/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1365, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ppkdxf55ly/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1365, \"height\": 484, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1397, \"height\": 1058, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1410, \"height\": 484, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 622, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1328, \"height\": 852, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1140, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1325, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1171, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 662, \"height\": 139, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 990, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1251, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1201, \"height\": 526, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1131, \"height\": 526, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1442, \"height\": 483, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 848, \"height\": 578, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ppkdxf55ly/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1302, \"height\": 284, \"label\": \"Table\"}]"
motivation: 设备端LLM需应对运行时约束变化，现有混合精度方案未考虑层敏感度动态性。
method: 根据解码步骤中每层敏感度动态调整精度分配。
result: 在保持准确性的同时有效匹配目标延迟或精度。
conclusion: DP-LLM实现了高效的设备端LLM运行时适应。
---

## Abstract
How can we effectively handle queries for on-device large language models (LLMs) with varying runtime constraints, such as latency and accuracy? Multi-scale quantization addresses this challenge by enabling memory-efficient runtime model adaptation of LLMs through the overlaying of multiple model variants quantized to different bitwidths. Meanwhile, an important question still remains open-ended: how can models be properly configured to match a target precision or latency? While mixed-precision offers a promising solution, we take this further by leveraging the key observation that the sensitivity of each layer dynamically changes across decoding steps. Building on this insight, we introduce DP-LLM, a novel mechanism that dynamically assigns precision to each layer based on input values. Experimental results across multiple models and benchmarks demonstrate that DP-LLM achieves a superior performance-latency trade-off, outperforming prior approaches.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：设备端（on‑device）大型语言模型（LLM）推理面临运行时约束（如延迟和精度）的动态变化。需要一种机制，能在内存受限的环境下，根据查询的不同需求（如 QoS 预算波动、系统负载变化）灵活调整模型精度，以平衡性能与准确性。
- **背景挑战**：传统多尺度量化（multi‑scale quantization）虽能高效部署多个不同位宽的模型，但配置模型时通常采用均匀位宽分配，无法支持非整数精度，且忽略了层间敏感度差异。混合精度方案虽能解决部分问题，但现有静态混合精度方法假设每层敏感度是固定的，而作者发现**每层对量化的敏感度在解码步骤（token by token）中动态变化**，这一机会尚未被利用。
- **论文贡献**：提出 DP‑LLM，一种动态层精度分配机制，根据每层输入值在运行时决定是否使用高/低位宽，实现更优的性能‑延迟权衡。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：利用每层敏感度在解码过程中的动态性，为每层定义候选精度集（通常为两个相邻位宽，如 3‑bit 和 4‑bit），并在运行时根据输入特征选择合适精度。选择依据是“相对误差”（relative error），即使用高低位宽权重时 GEMV 输出向量差的范数 \(\lVert \Delta W x \rVert\)。若相对误差大则用高位宽，否则用低位宽。
- **关键技术步骤**（分为三个阶段）：
  1. **层最大精度选择**：基于二阶泰勒展开（Fisher 信息矩阵近似 Hessian），在给定内存预算下通过整数规划为每层确定允许的最大精度（列表 B）。
  2. **层平均精度分配**：为每层学习一个平均精度 \(p_i\)（取值在 [最小精度, 最大精度] 之间），并正则化使整体平均精度接近目标精度。训练时用混合线性层 \(y = r W_l x + (1-r) W_h x\)（其中 \(l=\lfloor p \rfloor, h=\lceil p \rceil, r=1-(p-l)\)），只更新 \(p_i\) 参数，在少量校准数据上微调。
  3. **平均精度转阈值**：利用校准集计算各层的相对误差分布，取 \(r_i = 1-(p_i - l)\) 分位数作为阈值 \(T_i\)。运行时若 \(\lVert \Delta W x \rVert > T_i\) 则选用高位宽，否则低位宽。
- **相对误差估计**（混合方法）：
  - **线性回归法**：对输入向量范数与相对误差强线性相关的层（\(R^2 \ge 0.9\)），用线性函数 \(\alpha \lVert x \rVert + \beta\) 近似，开销极低。
  - **随机投影法**：其余层利用 Johnson‑Lindenstrauss 引理，预计算低维投影矩阵 \(G = A \Delta W\)（\(k=64\)），运行时通过 \(Gx\) 估计范数。
  - **异步估计**：对残差连接直接相连的层（QKV、Up Proj），使用上一解码步骤的输出来估算相对误差，与当前层计算重叠以减少延迟。

## 3. 实验设计：数据集、场景、基准与对比方法

- **模型**：Llama‑3‑8B 和 Phi‑3‑Medium（14B），另在附录中补充 Qwen2.5‑3B/32B。
- **数据集**：
  - **困惑度**：WikiText2、C4（教师强制解码评估）。
  - **下游任务**：GSM8K（数学推理）、MBPP（代码生成）、BBH（推理）、MATH（数学）。
- **基准方法**：基于 Any‑Precision LLM 多尺度量化框架，对比静态混合精度方法：
  - **LLM‑MQ**：使用梯度的一阶信息进行敏感度估计。
  - **HAWQ‑V2**：使用二阶 Hessian 信息（Fisher 近似）进行敏感度估计。
- **实验配置**：支持 3‑bit 到 6‑bit 精度，以 0.25‑bit 步长递增目标精度（3.25~4.75），在 5‑bit 内存预算下为主实验，另在附录中给出 4‑bit、6‑bit 预算结果。

## 4. 资源与算力

- 文中明确说明：
  - 微调使用 **单张 RTX 3090（24GB VRAM）** 或 **A100 80GB**。
  - Llama‑3‑8B 微调约 **1 小时**（RTX 3090）/ **30 分钟**（A100），使用 **14GB VRAM**。
  - Phi‑3‑Medium 微调约 **2 小时**（RTX 3090）/ **1 小时**（A100），使用 **21GB VRAM**。
- 延迟评估硬件：NVIDIA Jetson Orin AGX 64GB（边缘设备）和 NVIDIA RTX 4060 Ti 16GB（消费级 GPU）。

## 5. 实验数量与充分性

- **实验数量**：覆盖两个主要模型（8B & 14B）、两个困惑度数据集、四个下游任务、7 个目标精度（3.25~4.75 步长 0.25），即每个模型约 \(2 \times 4 \times 7 = 56\) 个主要组合；附录中还包含不同内存预算（4‑bit, 6‑bit）、不同规模模型（3B, 32B）、不同校准集、不同 \(h/l\) 组合的消融。
- **充分性与公平性**：
  - 对比两个强基线（LLM‑MQ、HAWQ‑V2），均基于相同多尺度量化框架，控制变量。
  - 进行了精度/延迟权衡分析，并测量了运行时开销（相对延迟增加 <5%）。
  - 评估了近似估计的误差（表 3，与精确估计对比），证明近似损失很小。
  - 评估了每查询 QoS 波动（表 7，99% 分位位宽偏差 <3%）。
  - 进行了消融实验（表 6）：逐个去除线性回归、异步估计，验证各组件贡献。
  - 仅评估解码阶段（教师强制或自回归生成），对仅依赖对数似然的静态任务（如句子分类）未覆盖（在局限性中说明）。
- **总体评价**：实验设计较为全面，覆盖多种模型、数据集、精度配置和消融，对比公平，结论可信。

## 6. 主要结论与发现

- **动态层精度分配**相比静态混合精度在几乎所有目标精度和数据集上取得更低的困惑度和更高的下游任务准确率（表 1、表 2）。
- **运行时开销极低**：几何平均延迟增加仅 0.68%~3.12%（表 4），主要得益于线性回归 + 异步估计的混合方案。
- **每查询 QoS 影响小**：即使 99% 分位，有效位宽偏差平均 <3%（表 7）。
- **近似估计有效**：用线性回归和随机投影替代精确计算，性能损失可忽略（表 3）。

## 7. 优点（亮点）

- **新颖洞察**：首次系统论证 LLM 解码过程中层敏感度的动态性，并据此设计运行时动态精度选择。
- **轻量高效**：采用混合误差估计（线性回归为主、随机投影为辅）和异步估计，几乎不增加推理延迟。
- **内存友好**：基于多尺度量化，只需额外存储少量低维投影矩阵（约 2.4% 额外 GPU 内存，表 9）。
- **泛化能力强**：在多种模型（8B~32B）、多种任务上一致优于静态基线。
- **实用性强**：针对设备端场景，支持细粒度精度控制（0.25‑bit 步长），且实时适应可有效匹配 QoS 约束。

## 8. 不足与局限

- **仅适用于解码阶段**：不影响预填充阶段（prefill），且不适用于仅基于对数似然的评估任务（如分类）。
- **最佳努力 QoS**：动态精度分配以最佳努力方式匹配目标精度，不提供严格的 QoS 保证（未来工作）。
- **校准集依赖性**：阈值和线性回归系数由校准集统计得到，可能对校准数据分布敏感；作者实验表明使用不同校准集（C4 vs. WikiText2）结果仍稳健（表 14）。
- **随机投影误差**：虽然理论上保证概率下界（论文声称 91% 置信度误差 <15%），但极端输入下可能偏差较大。
- **实验模型数量有限**：主要基于 Llama‑3‑8B 和 Phi‑3‑Medium（14B），更大模型（如 70B）未见评估（附录有 32B，但未全面覆盖）。
- **未与最新单模型量化方法（如 AWQ、SqueezeLLM）直接对比**：因为它们不支持动态精度调整，但作为端到端精度‑延迟权衡的参照可能仍有价值。

（完）
