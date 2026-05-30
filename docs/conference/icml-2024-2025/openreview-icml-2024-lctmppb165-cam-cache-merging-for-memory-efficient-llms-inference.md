---
title: "CaM: Cache Merging for Memory-efficient LLMs Inference"
title_zh: CaM：面向内存高效LLM推理的缓存合并
authors: "Yuxin Zhang, Yuxuan Du, Gen Luo, Yunshan Zhong, Zhenyu Zhang, Shiwei Liu, Rongrong Ji"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=LCTmppB165"
tags: ["query:edge-llm"]
score: 7.0
evidence: 内存高效的KV缓存合并减少推理内存占用
tldr: CaM（缓存合并）通过一种显著度引导的采样策略，将待驱逐的KV缓存自适应地合并到剩余缓存中，在减少LLM推理内存占用的同时保持输出质量。该方法避免了传统缓存驱逐带来的性能下降，为资源受限设备上的高效LLM推理提供了新思路。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-lctmppb165/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1733, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lctmppb165/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 867, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-lctmppb165/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1767, \"height\": 1188, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-lctmppb165/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 855, \"height\": 517, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lctmppb165/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1701, \"height\": 712, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lctmppb165/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 861, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lctmppb165/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 834, \"height\": 300, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-lctmppb165/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 747, \"height\": 225, \"label\": \"Table\"}]"
motivation: LLM推理中KV缓存占用大量内存，缓存驱逐会导致输出扰动。
method: 提出CaM，自适应地合并待驱逐缓存到剩余缓存，采用显著度引导的采样策略。
result: CaM在压缩缓存的同时保持了模型输出质量，优于传统驱逐方法。
conclusion: CaM为LLM推理提供了一种内存高效的缓存压缩方案，适用于资源受限场景。
---

## Abstract
Despite the exceptional performance of Large Language Models (LLMs), the substantial volume of key-value (KV) pairs cached during inference presents a barrier to their efficient deployment. To ameliorate this, recent works have aimed to selectively eliminate these caches, informed by the attention scores of associated tokens. However, such cache eviction invariably leads to output perturbation, regardless of the token choice. This perturbation escalates with the compression ratio, which can precipitate a marked deterioration in LLM inference performance. This paper introduces Cache Merging (CaM) as a solution to mitigate this challenge. CaM adaptively merges to-be-evicted caches into the remaining ones, employing a novel sampling strategy governed by the prominence of attention scores within discarded locations. In this manner, CaM enables memory-efficient LLMs to preserve critical token information, even obviating the need to maintain their corresponding caches. Extensive experiments utilizing LLaMA, OPT, and GPT-NeoX across various benchmarks corroborate CaM's proficiency in bolstering the performance of memory-efficient LLMs. Code is released at https://github.com/zyxxmu/cam.

---

## 论文详细总结（自动生成）

# CaM：面向内存高效LLM推理的缓存合并

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大语言模型（LLM）在推理时需要存储大量的键值（KV）缓存，消耗巨大GPU内存。例如，LLaMA-65B在batch size=128、序列长度=2048时，KV缓存约需365GB，是模型参数（约130GB）的近3倍。
- **现有方法局限**：当前主流做法是**缓存驱逐**（如StreamingLLM、H2O、Scissorhands），根据注意力得分选择性丢弃部分token的KV缓存。然而，无论选择标准如何，驱逐必然导致输出扰动（output perturbation），且压缩比越高性能下降越严重。
- **本文目标**：提出一种**缓存合并**（Cache Merging, CaM）策略，通过将待驱逐的KV缓存合并到保留的缓存中，而非直接丢弃，从而在减少内存占用的同时保持输出质量。

## 2. 方法论：核心思想、技术细节与算法流程

- **核心思想**：受视觉Transformer中Token Merge（ToMe）启发，将待驱逐的value缓存按比例合并到相邻的连续token的value缓存中，理论上可在特定条件下实现零输出扰动（Theorem 3.2）。
- **关键公式与推理**：
  - 直接驱逐导致输出扰动：$\Delta_t = -A_{ti}V_i$。
  - 若将$V_i$按比例$r$合并到$V_j$：$\bar{V}_j = V_j + rV_i$，则当前步扰动可消除，但未来步扰动$\Theta_{t+1}$取决于$r$与未来注意力的匹配程度（式7）。
  - 为降低未来步扰动，CaM将$V_i$**均匀合并**到连续的一段局部token（$j$到$j+m$）中，使合并后扰动变为$(avg(A_{j:j+m}) - A_i)V_i$（式10）。
  - **Theorem 3.3**：若$avg(A_{j:j+m}) < 2A_i$，则合并引起的扰动小于直接驱逐。此条件在实际中通过概率采样满足。
- **采样策略（Merge Mask）**：使用累积注意力分数$\bar{A}$（历史步总和），通过伯努利采样决定是否合并：$M \sim \text{Bernoulli}(\text{clamp}(\bar{A}_i / avg(\bar{A}_{j:j+m}), 0, 1))$（式14）。当$2\bar{A}_i > avg(\bar{A}_{j:j+m})$时，合并概率高；否则低，避免引入更大误差。
- **算法流程（Algorithm 1）**：
  1. 输入：当前步注意力权重$A$、V-Cache $V$、待驱逐索引$i$、局部起始索引$j$、局部窗口大小$m$。
  2. 计算累积注意力$\bar{A} = \sum_{k=1}^t A_k$。
  3. 采样合并掩码$M$。
  4. 若$M=1$，则将$V_i$均匀加到$V_j$至$V_{j+m}$上：$\bar{V}_k = V_k + M V_i / m$。
- **优势**：CaM不改变驱逐策略本身，而是作为插件增强现有方法（如StreamingLLM、H2O、Scissorhands），无需矩阵乘法，计算开销极低。

## 3. 实验设计

- **数据集/场景**：
  - 问答（QA）：COPA, MathQA, OpenBookQA, PiQA, RTE, Winogrande（使用lm-eval-harness框架）。
  - 文本摘要：XSUM, CNN/DailyMail（使用HELM框架）。
  - 语言建模：Wikitext-2, PG-19（困惑度Perplexity）。
- **Benchmark**：与全缓存（Full Cache）对比，基线方法包括StreamingLLM、H2O、Scissorhands。模型涵盖LLaMA (7B/30B/65B)、OPT-13B、GPT-NeoX-20B。
- **对比方法**：
  - StreamingLLM（保留前4个token和最近窗口）。
  - H2O（保留累积注意力高的token）。
  - Scissorhands（基于重要性假设）。
- **实验设置**：零样本评估（zero-shot），KV缓存压缩率从10%到90%不等；每个实验使用5个不同随机种子报告均值和方差。

## 4. 资源与算力

- 论文中**未明确说明**训练所需的GPU数量或总时长。
- 仅提及实验在**NVIDIA Tesla A800 GPU**上完成，每个实验使用5个随机种子。
- 推理阶段CaM额外开销极小：在PG-19第一个样本上，CaM相比StreamingLLM仅增加约1.2 ms/token（26.1→27.3 ms/token），GPU内存增加0.2GB（19.1→19.3GB）。

## 5. 实验数量与充分性

- **实验数量**：覆盖3种模型系列（LLaMA、OPT、GPT-NeoX）、4种KV缓存预算（10%~90%）、7个QA任务、2个摘要任务、2个语言建模任务，以及3种基线方法的对比（StreamingLLM、H2O、Scissorhands）。
- **消融实验**（Table 2）：分别移除“平均合并”（w/o Avg Merge）、“合并掩码”（w/o Merge Mask）、“累积注意力”（w/o Acc. Attention）来验证各组件有效性。
- **合并掩码区间分析**（Table 3）：探索不同clamp区间对性能的影响。
- **充分性评价**：
  - 实验覆盖了多种模型规模（7B~65B）、多种任务类型（QA、摘要、语言建模）、多种压缩比，较为全面。
  - 使用了5个随机种子报告均值和方差，统计严谨。
  - 对比方法均为当时最先进（StreamingLLM、H2O、Scissorhands），公平性好。
- **客观性**：结果展示CaM在所有任务上一致优于基线，且在多数场景下提升显著。消融实验证明了每个组件的重要性。

## 6. 主要结论与发现

- CaM能**显著提升**现有缓存压缩方法的推理性能，尤其在高压缩比下（如20%缓存预算）效果明显。
- 例如，在LLaMA-7B上，CaM使StreamingLLM在RTE上的零样本准确率从49.5%提升至54.6%（提升5.1%）；在OpenBookQA上从30.0%提升至31.8%。
- CaM作为插件方法，可与任意驱逐策略结合（如H2O、Scissorhands），且不会带来显著计算或内存开销。
- 合并掩码的采样策略是关键：直接合并所有待驱逐缓存会导致性能下降，甚至低于基线。

## 7. 优点

- **创新性**：首次将“缓存合并”概念引入LLM推理领域，不同于传统的驱逐范式，为解决KV缓存内存瓶颈提供了新思路。
- **理论支撑**：通过定理证明在特定条件下合并可减少甚至消除输出扰动，给出可操作的充分条件。
- **实用性**：作为即插即用组件，兼容现有所有主流驱逐方法，无需额外训练或模型修改。
- **高效率**：无矩阵乘法，推理吞吐量仅下降约5%，内存几乎无增加。
- **实验全面**：覆盖多种模型、任务、压缩比，消融实验设计合理，统计可靠。

## 8. 不足与局限

- **注意力分布稳定性假设**：CaM依赖“局部连续token的平均注意力在未来步保持稳定”的实证观察，但在长序列或注意力突变场景下可能失效。
- **合并掩码仅依赖累积注意力**：可能并非最优，不同层、不同头部注意力分布差异较大，未探索逐层自适应合并策略。
- **实验覆盖不足**：
  - 未在更大模型（如LLaMA-70B以上）或更多样化任务（如代码生成、数学推理）上验证。
  - 未与量化方法（如KIVI、FlexGen）结合测试。
- **潜在偏差**：所有实验均基于英文数据集，未见多语言或领域特定场景。
- **应用限制**：CaM设计用于解码阶段预填充（prefill）后的生成步骤，对长上下文推理（如多轮对话）的鲁棒性需进一步验证。

（完）
