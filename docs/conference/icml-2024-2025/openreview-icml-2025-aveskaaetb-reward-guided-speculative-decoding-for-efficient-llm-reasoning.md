---
title: Reward-Guided Speculative Decoding for Efficient LLM Reasoning
title_zh: 奖励引导的推测解码：高效大语言模型推理
authors: "Baohao Liao, Yuhui Xu, Hanze Dong, Junnan Li, Christof Monz, Silvio Savarese, Doyen Sahoo, Caiming Xiong"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=AVeskAAETB"
tags: ["query:edge-llm"]
score: 5.0
evidence: 推测解码加速LLM推理
tldr: 针对LLM推理效率问题，本文提出奖励引导的推测解码（RSD），结合轻量草稿模型和强大目标模型，引入过程奖励模型评估中间步骤，动态决定是否调用目标模型。理论证明阈值混合策略最优，实验表明在推理速度与输出质量间取得更好平衡。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1526, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 730, \"height\": 255, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1652, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 806, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 811, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 681, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1736, \"height\": 740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-aveskaaetb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1568, \"height\": 420, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 854, \"height\": 638, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 806, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1700, \"height\": 1363, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 862, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 793, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1758, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 865, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1326, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1532, \"height\": 1583, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-aveskaaetb/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1664, \"height\": 359, \"label\": \"Table\"}]"
motivation: 现有推测解码方法严格无偏，限制了效率与质量的权衡。
method: 使用过程奖励模型指导草稿模型解码，阈值策略动态调用目标模型。
result: 相比标准推测解码，在相同质量下推理速度更快。
conclusion: RSD为LLM推理提供了灵活高效的加速方案。
---

## Abstract
We introduce Reward-Guided Speculative Decoding (RSD), a novel framework aimed at improving the efficiency of inference in large language models (LLMs). RSD synergistically combines a lightweight draft model with a more powerful target model, incorporating a controlled bias to prioritize high-reward outputs, in contrast to existing speculative decoding methods that enforce strict unbiasedness.
RSD employs a process reward model to evaluate intermediate decoding steps and dynamically decide whether to invoke the target model, optimizing the trade-off between computational cost and output quality. We theoretically demonstrate that a threshold-based mixture strategy achieves an optimal balance between resource utilization and performance. Extensive evaluations on challenging reasoning benchmarks, including Olympiad-level tasks, show that RSD delivers significant efficiency gains against decoding with the target model only (up to 4.4X fewer FLOPs), while achieving significant better accuracy than parallel decoding method on average (up to +3.5). These results highlight RSD as a robust and cost-effective approach for deploying LLMs in resource-intensive scenarios.

---

## 论文详细总结（自动生成）

# Reward-Guided Speculative Decoding for Efficient LLM Reasoning 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在推理任务中逐步生成 token 的计算成本极高，特别是对于长链推理（如数学、代码）。现有的推测解码（Speculative Decoding, SD）虽能加速推理，但严格保持无偏性（unbiasedness），导致当草稿模型与目标模型分布差异较大时，高质量 token 可能被错误拒绝，造成计算浪费，且无法在效率与质量间灵活权衡。
- **研究动机**：在保证推理质量的前提下，进一步降低推理计算开销，使 LLM 在资源受限场景下（如实时应用、高吞吐量服务）更易部署。
- **整体含义**：通过引入过程奖励模型（Process Reward Model, PRM）指导解码过程，有控制地引入偏差（controlled bias），优先接受高奖励输出，从而在提高推理效率的同时，甚至可能超越目标模型本身的性能。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
- **奖励引导的推测解码（RSD）**：动态混合轻量草稿模型（draft model, \(P_m\)）与强大目标模型（target model, \(P_M\)），通过过程奖励模型评估每个推理步骤的质量，决定是否接受草稿模型的输出，而非强制精确匹配。
- **混合分布**：每一步的最终分布 \(P_{RSD}(y_i|z_i) = \omega(r(y_i|z_i)) P_m(y_i|z_i) + \nu P_M(y_i|z_i)\)，其中 \(\omega(\cdot)\) 是奖励的非递减权重函数（接受概率），\(\nu\) 是归一化常数（目标模型始终参与）。
- **阈值策略**：理论上证明，在有限计算预算下，最优策略是二进制阶跃函数：\(\omega(r) = 1\) 当 \(r \ge \delta\)，否则为 0，即只接受高奖励步骤。

### 关键技术细节
1. **过程奖励模型（PRM）**：评估每个推理步骤的奖励分数 \(r(y_i|z_i)\)，范围 [0,1]。
2. **自适应调用**：若草稿步骤的奖励 \(\ge \delta\)，则接受并继续；否则调用目标模型重新生成该步骤。
3. **算法流程（Algorithm 1 & 2）**：
   - 草稿模型生成候选步骤 \(\hat{y}_i\)。
   - PRM 计算奖励 \(r_i\)。
   - 根据接受准则 \(A_\omega(r_i)\)（若 \(\omega(r)=0\) 或 1 则确定性拒绝/接受，否则概率接受）决定是否接受。
   - 直到遇到 EOS 或达到最大长度。
4. **权重函数变体**：常数、二进制阶跃、裁剪、Sigmoid、Logistic 等，实验表明二进制阶跃表现最佳。

### 理论贡献
- **Proposition 2.1**：混合分布公式。
- **Proposition 2.2**：在 \(\omega\) 非递减且目标模型期望奖励不低于草稿模型时，RSD 期望奖励 \(\ge\) 草稿模型。
- **Proposition 2.3**：最优策略为阈值二进制函数。

## 3. 实验设计：数据集、基准与对比方法

### 数据集
- **推理基准**：GSM8K（数学）、MATH500（数学，含 5 级复杂度）、Olympiad Bench（奥赛级）、GPQA（研究生级）、MMLU STEM（科学）、GaoKao-2023-En（高考英文数学）。
- **通用任务**：AlpacaEval（指令跟随，805 条 prompt）。
- **额外**：CN Middle School 24、College Math、Minerva Math。

### 基准方法
- **目标模型单独解码**（Target only）。
- **草稿模型+测试时扩展**：多数投票（Majority Voting）、Best-of-N（BoN）、Beam Search、Process Best-of-N。
- **标准推测解码（SD）**：无偏加速。
- **RSD**：多种配置（不同 PRM 大小、不同 \(\delta\)）。

### 模型配置
- **草稿模型**：Qwen2.5-Math-1.5B-Instruct、Llama-3.2-1B-Instruct。
- **目标模型**：Qwen2.5-Math-7B/72B-Instruct、Qwen2.5-7B-Instruct、Llama-3.1-8B-Instruct。
- **PRM**：Skywork-o1-Open-PRM-1.5B/7B、Qwen2.5-Math-PRM-7B/72B。
- **ORM（通用任务）**：Skywork-Reward-Llama-3.1-8B。

### 评价指标
- **准确率**（数学推理）。
- **胜率**（AlpacaEval 2.0 vs GPT-4 Turbo）。
- **计算量**：FLOPs（基于 2N 每 token 估算，含 PRM 开销）。

## 4. 资源与算力

- **文中未明确说明训练时长或 GPU 数量**，仅提到：
  - 所有实验在 NVIDIA A100 GPU 上运行。
  - 使用 vLLM 作为推理后端。
  - 默认温度 = 0 (贪婪解码) 或 0.7 (采样)。
- **推理计算量度量**：FLOPs（包含目标模型、草稿模型、PRM 的推理开销），未涉及训练开销。

## 5. 实验数量与充分性

- **大量多维度实验**：
  - 主表（Table 2）覆盖 8 种任务，对比 4 类基线（Target only、Majority Voting、BoN、SD），并测试不同模型规模（1.5B/7B/72B）和不同 PRM（1.5B/7B）。
  - 每种 RSD 配置包括固定 \(\delta=0.7\) 和最优 \(\delta^*\) 两种设定。
  - 消融实验：阈值 \(\delta\) 扫描（Fig.5, Table B.2）、权重函数比较（Fig.6）、PRM 鲁棒性（Table 5）、模型合并（Table 4, B.3）、复杂度分层分析（Fig. B.1）。
  - 泛化性验证：通用模型（Llama-3.1, Qwen2.5-Instruct）、通用领域任务（AlpacaEval, Table 6）。
- **充分性评价**：
  - **充分**：覆盖数学推理所有主流数据集，模型配置多样，消融全面。
  - **客观公平**：与 SD 公平对比（相同草稿/目标模型），计算量及 FLOPs 严格对齐；BoN 采用较大采样数以体现其收敛性能；但未与最新其它推理加速方法（如 Medusa、Eagle 等）对比，存在一定局限性。

## 6. 论文的主要结论与发现

1. **RSD 显著优于标准 SD**：在 7 out of 8 设置中，固定 \(\delta=0.7\) 即超越目标模型；优化 \(\delta\) 后平均准确率提升 +1.0~+1.2。
2. **计算效率巨大提升**：相比仅用目标模型，最多减少 4.4× FLOPs（72B 目标 vs 7B+72B 混合）。
3. **阈值自适应分配计算**：简单问题（低奖励）直接接受草稿模型（节省计算），困难问题（低奖励）触发目标模型，实现自动计算分配。
4. **过程奖励模型是关键**：二进制阶跃权重函数效果最佳；PRM 大小越大效果越好（7B 优于 1.5B）。
5. **RSD 可融合 SD**：可无缝结合，进一步优化拒绝步骤的效率。
6. **通用领域可行**：即使使用 ORM 替代 PRM，胜率仍远超草稿模型，表明 RSD 框架通用。

## 7. 优点：方法或实验设计上的亮点

- **理论支撑**：严格证明最优策略为阈值函数，并与约束优化（KKT 条件）关联，提供了坚实理论基础。
- **动态计算分配**：首创将 PRM 引入决策式解码，自动区分简单/困难步骤，是首个将测试时计算扩展与推测解码结合的工作。
- **全面消融**：深入分析了阈值、权重函数、PRM 类型、模型合并、复杂度分层等维度，结论可信。
- **代码开源**：提供 GitHub 仓库，易于复现和扩展。
- **工程实用性**：通过模型合并减少需部署的模型数量，降低落地成本。

## 8. 不足与局限

- **依赖过程奖励模型**：高质量 PRM 的获取本身有成本，且 PRM 的可靠性直接影响 RSD 效果；目前缺乏通用领域 PRM，限制了应用范围。
- **实验覆盖局限**：
  - 未与更多推测解码变体（如 Eagle、Medusa、Self-Speculative Decoding）对比加速比。
  - 仅测试了数学和指令跟随任务，未涉及代码、长文本生成等更多场景。
  - 未报告实际推理延迟（如 tokens/s），仅用 FLOPs 近似，实际硬件加速效果可能不同。
- **未讨论训练开销**：PRM 的训练成本未纳入考量，论文假设已有训练好的 PRM。
- **偏差风险**：引入偏差可能在高安全场景带来不可预测错误，论文未深入讨论偏差对最终答案正确性的影响边界。
- **超参数敏感性**：阈值 \(\delta\) 在不同任务上需手动调整才能达到最优（Table B.2），缺乏自适应方案。

（完）
