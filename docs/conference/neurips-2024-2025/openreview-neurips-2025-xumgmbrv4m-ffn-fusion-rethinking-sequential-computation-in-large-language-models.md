---
title: "FFN Fusion: Rethinking Sequential Computation in Large Language Models"
title_zh: FFN Fusion：重新思考大语言模型中的顺序计算
authors: "Akhiad Bercovich, Mohammed Dabbah, Omri Puny, Ido Galil, Amnon Geifman, Yonatan Geifman, Izhak Golan, Ehud Dov Karpas, Itay Levy, Zach Moshe, Najeeb Nabwani, Tomer Ronen, Itamar Schen, Ido Shahaf, Oren Tropp, Ran Zilberstein, Ran El-Yaniv"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=XUmGMBRv4M"
tags: ["query:edge-llm"]
score: 5.0
evidence: 通过并行化FFN层减少推理延迟的架构优化
tldr: 大语言模型中的FFN层序列通常被视为顺序计算。FFN Fusion发现其中存在可并行化的机会，提出识别并融合这些序列的方法，将它们转化为并行操作，在不影响模型行为的情况下显著降低推理延迟。在Llama-3.1-405B上应用后，模型大小从405B减至253B，同时保持性能。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 740, \"height\": 894, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 868, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 476, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1167, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 872, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1063, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1164, \"height\": 1035, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1276, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1348, \"height\": 1013, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 745, \"height\": 778, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1141, \"height\": 1109, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1374, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 660, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 598, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 728, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 588, \"height\": 467, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 586, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 590, \"height\": 284, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 840, \"height\": 364, \"label\": \"Table\"}]"
motivation: LLM中FFN层序列的顺序计算限制了推理速度。
method: 识别可并行化的FFN层序列并将其融合为并行操作。
result: 在Llama-3.1-405B上创建253B模型，推理延迟显著降低。
conclusion: FFN Fusion通过并行化顺序计算实现了高效的LLM推理。
---

## Abstract
We introduce \textit{FFN Fusion}, an architectural optimization technique that reduces sequential computation in large language models by identifying and exploiting natural opportunities for parallelization. Our key insight is that sequences of Feed-Forward Network (FFN) layers, particularly those remaining after the removal of specific attention layers, can often be parallelized with minimal accuracy impact. We develop a principled methodology for identifying and fusing such sequences, transforming them into parallel operations that significantly reduce inference latency while preserving model behavior. Applying these techniques to Llama-3.1-405B-Instruct, we create a 253B model (253B-Base), an efficient and soon-to-be publicly available model that achieves a 1.71$\times$ speedup in inference latency and 35$\times$ lower per-token cost while maintaining strong performance across benchmarks. Most intriguingly, we find that even full transformer blocks containing both attention and FFN layers can sometimes be parallelized, suggesting new directions for neural architecture design.

---

## 论文详细总结（自动生成）

# 论文总结：FFN Fusion: Rethinking Sequential Computation in Large Language Models

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）中广泛采用顺序计算架构，尤其是前馈网络（FFN）层按顺序依次执行，导致推理延迟高、计算效率低。传统的优化方法（如量化、剪枝、混合专家模型 MoE）各有局限，例如量化存在精度-速度权衡，剪枝难以在不损失精度的情况下进一步压缩，MoE 在小批量情况下 GPU 利用率差。
- **整体含义**：论文挑战了“FFN 层必须顺序执行”的传统观点，发现多个连续 FFN 层（尤其是在移除部分注意力层后）之间依赖度很低，可以并行化。通过融合这些 FFN 层，可以显著降低推理延迟、减少同步开销，同时保持甚至提升模型能力。这项工作为 LLM 效率优化提供了一个互补的、可落地的架构优化方向。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

### 核心思想
- 识别出经过注意力层删除后留下的长序列 FFN 层，这些层之间具有低依赖性，可以并行执行。
- 将多个连续的 FFN 层融合成单个更宽的 FFN 层，使得所有子层共享同一输入，从而消除层间依赖，支持并行计算。

### 关键技术细节
- **FFN Fusion 公式**：
  - 对于注意力已移除的连续 FFN 块 $\hat{f}_i, \ldots, \hat{f}_{i+c}$，定义并行版本：
    $$\hat{f}_{[i,i+c]}(X) = X + \sum_{j=0}^{c} \text{FFN}_{i+j}(\eta_2(X))$$
    其中所有 FFN 共享同一归一化后的输入 $\eta_2(X)$，因此可以独立并行计算。
- **定理 3.1**：多个 SwiGLU FFN 的和等价于一个具有拼接权重的单一 FFN 层，即：
  $$W_1^* = \begin{bmatrix} W_1^1 \\ \vdots \\ W_1^n \end{bmatrix}^\top,\quad W_2^* = \begin{bmatrix} W_2^1 \\ \vdots \\ W_2^n \end{bmatrix}^\top,\quad W_3^* = [W_3^1, \ldots, W_3^n]$$
  这保证了融合后的层可以以标准方式实现，无需特殊算子。
- **依赖度分析**：定义块 $j$ 对块 $i$ 的依赖为余弦距离 $M_{ij} = \text{CosDist}(h_j(X), \tilde{h}_j^i(X))$，其中 $h_j(X)=f_j(X)-X$，$\tilde{h}_j^i$ 表示移除块 $i$ 后的输出。低余弦距离（蓝色区域）表示弱依赖，适合融合。
- **融合流程**（图 1）：
  1. 使用 Puzzle 框架移除部分注意力层和剪枝 FFN 层，留下连续 FFN 序列。
  2. 根据依赖度分析（或经验规则）将连续 FFN 层分组。
  3. 将每组内的 FFN 层融合为一个宽 FFN 层（最后一个 FFN 通常保留不融合）。
  4. 对融合后的模型进行知识蒸馏（KD）和/或连续预训练（CPT）以恢复性能。

### 算法流程（文字描述）
1. **Step 1 (Puzzle)**：对预训练模型进行神经架构搜索，移除不必要的注意力层，剪枝部分 FFN 通道，得到减少深度的中间模型。
2. **Step 2 (FFN Fusion)**：识别注意力移除后留下的长 FFN 序列，按 GPU 内存限制分组，每组内的多个 FFN 权重按定理 3.1 拼接成单个宽 FFN。
3. **Step 3 (训练恢复)**：进行多阶段知识蒸馏（KD）或更长周期的连续预训练（CPT）以补偿融合带来的微小性能损失，必要时进行对齐（如 RLHF）。

## 3. 实验设计：数据集、基准、对比方法

### 数据集
- **蒸馏/训练数据**：Distillation Mix（FineWeb、Dolma、Buzz-V1.2 共 224B tokens），以及 Llama-405B 合成的数据（用于对齐）。
- **评估基准**：
  - MMLU / MMLU-Instruct / MMLU-Pro
  - Arena Hard
  - HumanEval
  - MT-Bench
  - RULER (128K)（长上下文）
  - MATH-500

### 对比方法
- **基线**：原始 Llama-3.1-405B-Instruct、Llama-3.3-70B-Instruct
- **消融对比**：
  - 不同融合程度（Step 1~4，逐步减少 FFN 层数）
  - 直接移除 FFN vs. FFN Fusion（图6）
  - 包含最后一个 FFN vs. 排除最后一个 FFN（表4）
  - 反转 FFN 顺序（表6）

### 实验场景
- 主要实验在 **253B 模型**（从 Llama-405B 经 Puzzle + FFN Fusion 得到）上进行。
- 补充实验在 **49B 模型**（从 Llama-70B 衍生）、**Mistral Large 2**（未公开细节）和 **Llama-3.1-8B-Instruct** 上验证通用性。

## 4. 资源与算力

- **推理硬件**：单节点 8×H100 (640GB) 或单块 B100 (192GB)；Tensor Parallel (TP) 8。
- **训练硬件**：未明确指定训练使用的 GPU 型号和数量，仅提到多阶段蒸馏使用了 54B tokens 等数据规模。论文未公开训练计算成本（如 GPU 小时数）。
- **说明**：论文在算力资源方面披露不充分，仅给出了推理效率对比（tokens/second），未报告训练耗时。

## 5. 实验数量与充分性

- **实验数量**：相当丰富。包括：
  - 253B 模型全套基准测试（表1、图4）
  - 49B 模型消融（表3、图6、表4、表6）
  - 8B 和 Mistral Large 2 验证（表5）
  - 依赖度热力图（图3、图8、图10）
  - 全块并行化初步探索（附录B、表7）
- **充分性评估**：
  - **优点**：覆盖多种规模（8B、49B、70B、253B、405B）、多种模型族（Llama、Mistral），消融实验系统（融合程度、最后层敏感性、移除 vs 融合），分析工具（依赖度量）提供了可解释性。
  - **不足**：
    - 未在 MoE 模型上测试。
    - 全块并行化仅初步探索，缺少深入消融。
    - 缺少与 MoE 模型的直接推理效率对比（仅附录定性讨论）。
    - 部分实验结果（如表5的 Mistral Large 2 和 8B）仅报告 MMLU 和 MT-Bench，覆盖不够全面。
  - **公平性**：对比基线为原模型（同一硬件、同一框架），消融设计合理，整体客观。

## 6. 论文的主要结论与发现

1. **FFN 融合显著提升推理效率**：在 Ultra-253B-Base 上实现 1.71× 用户延迟加速，35× 更低每个 token 成本（batch size=32），同时参数量从 405B 降至 253B。
2. **性能保持或超越原模型**：在 MMLU、HumanEval、MT-Bench 等多项基准上匹配甚至超过 Llama-405B。
3. **最后 FFN 层更敏感**：应避免对每个 FFN 序列的最后一个 FFN 进行融合，否则精度下降更明显。
4. **低依赖区域的存在**：通过依赖度热力图找到了注意力移除后的大块低依赖区域，这些区域最适合融合。
5. **全块并行化可行但挑战更大**：初步实验显示并行化 2 组 4 块基本无损，但更多组并行时性能显著下降。
6. **解释性支持**：融合区域中 $h(X)$ 与 $X$ 的比值较小，表明这些层对输入方向改变有限，因此共享输入近似有效。

## 7. 优点

- **创新性**：首次系统性地挑战 FFN 顺序执行的必要性，提出可验证的并行化方案。
- **理论支撑**：定理 3.1 严格证明了多个 SwiGLU FFN 的可合并性。
- **依赖分析工具**：余弦距离度量块间依赖，为融合选择提供了可解释依据，可推广到其他架构分析。
- **多规模验证**：从 8B 到 253B 跨度大，展示了方法的可扩展性。
- **实用性强**：最终模型将公开发布，且融合过程无需新算子，可直接在现有推理框架中实现。
- **消融完备**：对融合位置、层序、移除 vs 融合等进行了详细对比，验证了设计选择。

## 8. 不足与局限

- **前提条件限制**：FFN Fusion 需要先通过 Puzzle 移除注意力层才能产生长 FFN 序列，并非所有模型都自然存在此类序列。
- **融合后需要额外训练**：虽然融合后精度下降不大，但恢复到原始水平仍需大量蒸馏数据（数十 B tokens），增加了部署成本。
- **全块并行化不成熟**：包含注意力的完整块并行化仅初步探索，实际加速未在优化框架中实现，适用性有限。
- **未覆盖 MoE 模型**：论文仅定性讨论 MoE 在中等批量下的效率问题，未试验 MoE 中 FFN 的融合，可能难以直接迁移。
- **算力信息披露不足**：训练具体 GPU 数量和时长未公开，降低了可重复性。
- **实验偏差风险**：部分实验（如 Mistral Large 2）仅在一个模型种子下测试，可能不足以完全排除随机性；长上下文测试仅用 RULER 一项指标。
- **应用限制**：方法假设依赖度低区域自然存在，但并非所有模型（尤其小模型或未预训练模型）都具备此特性。

（完）
