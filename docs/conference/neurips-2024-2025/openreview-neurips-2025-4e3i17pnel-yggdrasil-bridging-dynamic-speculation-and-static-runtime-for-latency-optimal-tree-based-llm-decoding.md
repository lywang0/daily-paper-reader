---
title: "Yggdrasil: Bridging Dynamic Speculation and Static Runtime  for Latency-Optimal Tree-Based LLM Decoding"
title_zh: Yggdrasil：桥接动态推测与静态运行时的延迟最优树型LLM解码
authors: "Yue Guan, Changming Yu, Shihan Fang, Weiming Hu, Zaifeng Pan, Zheng Wang, Zihan Liu, Yangjie Zhou, Yufei Ding, Minyi Guo, Jingwen Leng"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=4E3I17pNEl"
tags: ["query:edge-llm"]
score: 6.0
evidence: 跨硬件协同设计的延迟最优推测解码系统
tldr: 现有推测解码系统因动态推测与静态运行时假设不匹配导致性能次优。Yggdrasil提出协同设计方法，通过等增长树结构兼容静态图、延迟感知优化目标选择草稿以及阶段调度降低开销。实验表明，Yggdrasil在多种硬件上实现了高达3.98倍加速，且无需修改原始模型。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 664, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 724, \"height\": 314, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 726, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 382, \"height\": 257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 345, \"height\": 251, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 601, \"height\": 263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 751, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 511, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1453, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1421, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 707, \"height\": 216, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 739, \"height\": 215, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 706, \"height\": 220, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 611, \"height\": 232, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 649, \"height\": 186, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4e3i17pnel/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 676, \"height\": 192, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-4e3i17pnel/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 655, \"height\": 268, \"label\": \"Table\"}]"
motivation: 推测解码性能受限于动态推测与静态运行时之间的不匹配。
method: 提出等增长树结构、延迟感知目标优化和阶段调度，实现协同设计的推测解码系统。
result: 在多种硬件配置上实现了高达3.98倍的加速比。
conclusion: Yggdrasil通过软硬协同设计实现了延迟最优的推测解码。
---

## Abstract
Speculative decoding improves LLM inference by generating and verifying multiple tokens in parallel, but existing systems suffer from suboptimal performance due to a mismatch between dynamic speculation and static runtime assumptions. We present Yggdrasil, a co-designed system that enables latency-optimal speculative decoding through context-aware tree drafting and compiler-friendly execution. Yggdrasil introduces an equal-growth tree structure for static graph compatibility, a latency-aware optimization objective for draft selection, and stage-based scheduling to reduce overhead. Yggdrasil supports unmodified LLMs and achieves up to $3.98\times$ speedup over state-of-the-art baselines across multiple hardware setups.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：大语言模型（LLM）在自回归解码时逐 token 生成，导致严重的顺序依赖和硬件利用率低下。推测解码（Speculative Decoding）通过并行生成和验证多个候选 token 来加速推理，但现有系统因**动态推测算法**（如根据上下文调整树结构）与**静态运行时编译假设**（如固定计算图、固定算子形状）之间的根本性不匹配，导致性能次优。
- **核心问题**：动态树结构破坏编译优化（如 CUDA Graph、算子自动调优）；高平均接受长度（AAL）不等同于高端到端加速，因为验证开销随 token 数非线性增长；运行时 CPU 逻辑开销（条件分支、调度）造成 GPU 空闲气泡。
- **整体含义**：需要一种**协同设计**的系统，既能保留上下文感知的动态推测带来的高 AAL，又能兼容静态编译优化，使端到端延迟最小化。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- **延迟感知优化目标**：用实际的系统加速比（考虑草稿和验证的延迟特性）代替 AAL 作为优化目标，平衡推测质量与执行开销。
- **等增长树（Equal-Growth Tree, EGT）**：一种新颖的树结构，确保每层草稿宽度固定，从而维持静态算子形状，兼容编译优化；同时通过深度预测、宽度选择和验证剪枝实现上下文自适应。
- **阶段调度运行时**：通过提前执行草稿阶段（Ahead-of-Time Execution）和基于 profiling 的搜索最优执行计划，减少 CPU-GPU 协调开销。

### 关键技术细节
1. **延迟感知优化目标（公式文字说明）**：
   - 加速比 = (AAL × T_verifier(1)) / (Num_draft × T_drafter + T_verifier(W_verify))，其中 T_verifier(W) 是验证 W 个 token 的延迟。树结构涉及参数 ⟨W_draft, D_draft, W_verify⟩（草稿宽度、深度、验证数）。
   - 该目标更精确地反映实际 wall time 收益，克服了 AAL 忽略硬件特性的问题。

2. **等增长树算法**：
   - **深度预测**：训练一个轻量级多头 MLP 深度预测器，输入目标模型最后 token 嵌入，输出预期接受长度。离线训练，在线一次性生成所有草稿图。
   - **宽度选择**：在给定预测深度下，贪心选择草稿宽度 W_draft 以最大化加速比目标。
   - **验证剪枝**：草稿完成后，通过动态规划求解最大收益子树，确定实际验证的 token 数 W_verify，避免过度验证。

3. **阶段调度**：
   - **提前尾草稿（Ahead-of-Time Tail Draft）**：不再条件性草稿最后一个 token，而是预先草稿整个候选序列，接受时直接复用结果，消除条件分支。
   - **提前头草稿（Ahead-of-Time Head Draft）**：将下一轮的头草稿与当前轮的接收阶段重叠执行。
   - **基于 profiling 的计划搜索**：离线枚举不同执行计划（各阶段先后/并行组合），用 profiling 测得的各阶段延迟评估，选择最优静态执行计划。

## 3. 实验设计：数据集、场景、Benchmark 与对比方法

- **数据集**：C4、Wikipedia（Wikitext）、CNNDaily Mail。用于语言建模任务的端到端延迟评估。
- **基准场景**：单请求交互式设定（latency-oriented），假设独占 GPU。
- **对比方法**：
  - **SpecInfer**（动态树，算法导向）
  - **Sequoia**（静态树，数据集自适应）
  - **vLLM-Spec**（基于 vLLM 的序列推测）
  - 以及消融实验中的变体（eager 执行、无编译等）
- **评估指标**：每 token 生成延迟（TPOT）、加速比（相对于 SpecInfer 的归一化延迟）。

## 4. 资源与算力

- **GPU 型号**：NVIDIA A100 (80G) 和 A40。CPU 为 Intel Xeon E5-2620 v3 @ 2.40GHz。
- **环境**：CUDA 11.7，TorchInductor（PyTorch 2.0 编译器）。
- **未明确说明**：文中未提及 GPU 数量、训练深度预测器所需的具体算力（小时数）、每实验运行次数等。但实验涉及多个模型组合（Llama-2-7B、13B 作为 target，68M、160M 作为 drafter）和三个数据集，应在单卡或双卡上完成。

## 5. 实验数量与充分性

- **实验组数**：包括端到端延迟比较（Fig.10，3 数据集 × 4 模型组合 × 2 GPU 类型 = 24 组结果），树结构对比（Fig.11），优化分解（Fig.12，5 种逐步优化），参数敏感性分析（Fig.13），目标函数对比（Fig.14），温度影响（Fig.15）等。总计约 20 余组实验。
- **充分性评价**：
  - **优点**：覆盖了多种目标/草稿模型组合（7B/13B target，68M/160M drafter）、两种主流 GPU（A100、A40）、多个数据集；进行了全面的消融实验，逐项量化每种优化的贡献。
  - **客观性**：对比了三种 SOTA 基线系统（SpecInfer、Sequoia、vLLM-Spec），实验设置透明。使用标准基准和公开模型。
  - **不足**：仅在单请求延迟场景下评估，未涉及吞吐导向的批处理场景；不同基线可能使用了不同优化程度（如 Sequoia 也用了 TorchInductor），但 Yggdrasil 仍大幅领先，说明公平性可控。

## 6. 论文的主要结论与发现

1. Yggdrasil 实现了 **2.76×–3.98×** 的端到端加速（相对于 SpecInfer），在 A100 上更优。
2. **EGT 结构**在相同验证预算下比 Sequoia 的静态树实现更高的 AAL，并且通过与编译优化的结合获得同时高 AAL 和低延迟。
3. **延迟感知目标**相比于直接优化 AAL 额外提升约 8% 的性能。
4. **阶段调度**（提前执行 + 计划搜索）贡献约 1.21× 的额外加速，证明运行时优化在推测解码中的重要性。
5. 优化分解表明，**图形编译（O2）** 是最大的单点加速（2.775×），其次是阶段调度（O4）、验证剪枝（O3）和深度预测（O5）。
6. 在低采样温度下（temperature=0）性能更高，且 Yggdrasil 在所有温度下始终优于 Sequoia。

## 7. 优点

- **算法-系统协同设计**：首次同时解决动态推测与静态编译的矛盾，具有创新性。
- **实用性强**：无需修改模型架构，支持现有 LLM；基于开源编译器 TorchInductor，易于部署。
- **优化粒度细**：从目标函数、树结构、运行时调度等多层次优化，且每个模块有消融验证。
- **实验全面**：涵盖不同模型规模、硬件、数据集和基线，结果可信度高。

## 8. 不足与局限

- **场景局限**：仅针对**单请求延迟最优**场景，未考虑吞吐导向的批处理（continuous batching）或在线服务场景。在批量推理中，Yggdrasil 的调度策略可能与批次调度器产生冲突。
- **预测器泛化性**：深度预测器需针对每个数据集和模型组合离线训练（一次），虽然轻量，但仍然增加部署成本。
- **硬件依赖**：实验仅覆盖 NVIDIA GPU（A100、A40），未在 AMD、Intel 或边缘设备上验证。
- **未开放代码**：论文声明“一旦被接收将开源”，但当前无法复现（NeurIPS 政策允许）。
- **潜在偏差**：对比基线可能未完全适配 Yggdrasil 的编译优化（如 SpecInfer 基于 eager 模式），但作者已尽力公平对比（Sequoia、vLLM-Spec 也用了 TorchInductor）。
- **缺少统计误差**：未报告误差条（error bars）或多次运行标准差，结果的稳定性不明确。

（完）
