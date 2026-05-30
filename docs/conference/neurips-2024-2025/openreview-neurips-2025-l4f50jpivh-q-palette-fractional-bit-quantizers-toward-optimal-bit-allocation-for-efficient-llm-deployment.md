---
title: "Q-Palette: Fractional-Bit Quantizers Toward Optimal Bit Allocation for Efficient LLM Deployment"
title_zh: Q-Palette：面向最优比特分配的高效LLM部署分数比特量化器
authors: "Deokjae Lee, Hyun Oh Song"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=l4F50jpiVH"
tags: ["query:edge-llm"]
score: 9.0
evidence: 面向边缘设备高效部署的权重量化方法
tldr: 大语言模型在边缘设备上的部署受限于内存和延迟，权重量化是关键。Q-Palette从信息论角度推导最优比特分配，提出分数比特量化器，有效处理重尾异常值。实验表明，该方法在保持精度的同时显著减少内存占用，特别适用于边缘设备的小批量推理场景。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-l4f50jpivh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1463, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l4f50jpivh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 621, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l4f50jpivh/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 619, \"height\": 530, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l4f50jpivh/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1431, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l4f50jpivh/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1435, \"height\": 641, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-l4f50jpivh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1304, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l4f50jpivh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1399, \"height\": 684, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l4f50jpivh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1402, \"height\": 707, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l4f50jpivh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1389, \"height\": 331, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l4f50jpivh/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 808, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l4f50jpivh/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l4f50jpivh/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1399, \"height\": 685, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l4f50jpivh/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1275, \"height\": 668, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l4f50jpivh/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1297, \"height\": 530, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l4f50jpivh/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1212, \"height\": 359, \"label\": \"Table\"}]"
motivation: 边缘设备部署LLM受限于内存和延迟，权重量化至关重要。
method: 从信息论推导最优比特分配，设计分数比特量化器处理重尾分布。
result: 在保持精度的同时显著减少内存占用，适用于边缘设备。
conclusion: Q-Palette通过最优比特分配实现了高效的LLM边缘部署。
---

## Abstract
We study weight-only post-training quantization (PTQ), which quantizes the weights of a large language model (LLM) without retraining, using little or no calibration data. Weight-only PTQ is crucial for reducing the memory footprint and latency of LLM inference, especially in memory-bound, small-batch inference scenarios, such as personalized inference on edge devices. Despite its importance, irregular weight distributions with heavy-tailed outliers in LLMs complicate quantization, recently motivating rotation-based methods that transform weights into near-Gaussian distributions, which are more regular with fewer outliers, thereby reducing quantization error. In this work, we first derive the information-theoretically optimal bit allocation for Gaussianized weights under given bit budgets, revealing that fine-grained fractional-bit quantizers approaching the Gaussian distortion-rate bound are essential to achieve near-optimal quantization performance. To bridge this theoretical insight and practical implementation, we introduce Q-Palette, a versatile collection of fractional-bit quantizers that range from trellis-coded quantizers offering near-optimal distortion to simpler vector and scalar quantizers optimized for faster inference, all efficiently implemented with optimized CUDA kernels across various bitwidths. Furthermore, leveraging Q-Palette as a foundational component, we propose a novel mixed-scheme quantization framework, jointly optimizing quantizer choices and layer fusion decisions given resource constraints. The code is available at https://github.com/snu-mllab/Q-Palette.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义
- **背景**：大语言模型（LLM）在边缘设备（如笔记本、手机）部署时面临内存和延迟瓶颈，尤其是小批量推理场景。权重量化（weight-only PTQ）能显著压缩模型并加速推理，但LLM权重存在重尾异常值分布，使量化困难。最近旋转方法（如随机Hadamard变换）可将权重高斯化，减少异常值。
- **核心问题**：如何在高斯化后的权重上实现信息论最优的比特分配？现有量化器（如TCQ）仅支持整数位宽且批量支持有限，无法利用分数比特优势。同时，量化器选择与层融合需要联合优化以实现更好的精度-延迟权衡。

### 2. 方法论
- **核心思想**：从信息论出发，推导理想高斯量化器下的最优比特分配公式（Theorem 3.1），揭示分数比特量化器逼近高斯率失真界是实现近最优性能的关键。基于此设计Q-Palette：一套分数比特量化器集合，并进一步提出融合感知混合方案量化（fusion-aware MSQ）框架。
- **关键技术细节**：
  - **最优比特分配推导**：假设权重经高斯化处理后，量化误差满足率失真下界 \(E[err] \ge 2^{-2b}\)。在记忆约束下，将问题建模为连续优化，得到闭式解 \(b_l^* = \max\left(\eta, \frac{1}{2\ln 2}\left(\ln \frac{a_l}{d_{\text{in}}^l d_{\text{out}}^l} + C\right)\right)\)，其中 \(a_l\) 为灵敏度系数，\(C\) 由总预算决定。
  - **Q-Palette量化器**：
    - **非均匀标量量化（NUQ）**：通过k-means构建非均匀码本，支持2.0~8.0位宽。
    - **向量量化（VQ）**：2D VQ，码本大小为2的幂，支持1.5~6.0位宽（步长0.5）。
    - **网格编码量化（TCQ）**：基于bitshift变体，支持1.5~5.0位宽（步长0.5），及半TCQ（混合两种位宽实现中间位宽如2.75）。
  - **CUDA核实现**：Tensor Core核（支持所有量化器，批量≤8）和CUDA Core核（NUQ/VQ，批量灵活），优化了旋转开销（共享旋转矩阵、仅沿输入维度旋转）。
  - **融合感知MSQ**：将线性层融合（如QKV投影）作为额外决策变量，与量化器选择联合优化，建模为整数线性规划（ILP），使用OR-Tools求解。

### 3. 实验设计
- **数据集与场景**：
  - 语言建模：WikiText2困惑度（序列长度4096或8192）。
  - 零样本准确率：ARC-easy/challenge、HellaSwag、PiQA、WinoGrande（使用lm_eval）。
  - 推理延迟：RTX4090/RTX3090 GPU，批量大小1和8，测量解码吞吐量（tokens/sec）。
- **Benchmark与对比方法**：
  - 单方案基线：HQQ（均匀量化）、NormalFloat（NUQ，FLUTE核）、HIGGS-Single（VQ）、QTIP（TCQ，数据无关/数据感知）。
  - 混合方案基线：HIGGS-MSQ。
  - 消融：无融合MSQ、不同损失项（linearity vs actual）、无高斯化处理等。
- **模型**：LLaMA 3.1-8B/70B、LLaMA 3.2-1B/3B、LLaMA 2-7B/13B、Qwen 2.5-7B。

### 4. 资源与算力
- **GPU**：RTX4090、RTX3090（本地或云环境）。
- **训练/计算成本**：
  - 敏感性系数 \(a_l\) 需一次性计算16×L次KL散度损失（可并行），具体时间未报告。
  - ILP求解使用OR-Tools的SCIP求解器，时间限制60秒。
  - 整体训练时长未明确提及（属于PTQ，无需重训练）。

### 5. 实验数量与充分性
- **实验数量**：丰富。
  - 主表（Table 3, 4）覆盖三个LLaMA 3模型+三个位宽；Table 2覆盖延迟加速比。
  - 附录包含：Qwen 2.5-7B和LLaMA 3.1-70B的MSQ结果（图5）；消融实验（Table 8-10）；不同硬件（RTX3090）附加延迟数据（附录D表7）。
  - 数据无关与数据感知两种设置均评估。
- **充分性**：实验设计较周全，对比了多种主流基线，涵盖不同模型规模、位宽、批量大小。结果具有统计稳健性（低方差验证见附录A表5）。
- **公平性**：基线配置按照官方文档/论文设定，对于未公开实现的HIGGS直接引用其论文结果。消融实验控制变量清晰。整体公平性较好。

### 6. 主要结论与发现
- 理论最优比特分配需要分数比特量化器：Q-Palette提供的TCQ等量化器在接近率失真界的同时支持精细位宽，显著优于整数位宽方案。
- 融合感知MSQ在精度-延迟Pareto前沿上全面超越现有方法：例如在LLaMA 3.1-8B上，相比NormalFloat@3.25位，融合感知MSQ提速36%且困惑度更低（6.39 vs 7.70）。
- 高效CUDA核实现使TCQ在批量大小≤8时实际可用（之前被视为计算昂贵），RTX4090上批量1时TCQ-2比QTIP-2提速22%（3.57× vs 2.91×）。

### 7. 优点
- **理论指导实践**：从信息论推导最优比特分配，明确分数比特量化器的必要性，为设计提供依据。
- **量化器多样性**：同时支持NUQ、VQ、TCQ及半TCQ，覆盖精度-速度全频谱，适应不同部署需求。
- **工程优化**：优化旋转开销（共享矩阵、仅单侧旋转）；Tensor Core和CUDA Core双核实现，支持更宽批量。
- **融合感知系统优化**：首次将层融合纳入MSQ联合优化，开辟新优化维度，获得明显收益。
- **实验全面**：多种模型、多种位宽、数据无关/数据感知、延迟/记忆约束，消融充分，结果可信。

### 8. 不足与局限
- **计算成本**：敏感性系数 \(a_l\) 计算仍需16×L次KL散度损失，虽可并行且可复用，但仍是线性开销。
- **范围限制**：仅针对权重PTQ，未扩展到权重激活联合量化或重训练场景。
- **硬件依赖**：CUDA核针对NVIDIA GPU优化，对其他加速器（如NPU）的适用性未验证。
- **评估集有限**：仅使用WikiText2和5个零样本任务，长序列或高精度场景的泛化能力未充分测试。
- **未探讨的失败模式**：当预算极端紧张或模型异常值非常严重时，高斯化假设可能不成立，论文未提供鲁棒性分析。

（完）
