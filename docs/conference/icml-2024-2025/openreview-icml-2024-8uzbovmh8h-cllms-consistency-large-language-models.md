---
title: "CLLMs: Consistency Large Language Models"
title_zh: "CLLMs: 一致性大语言模型"
authors: "Siqi Kou, Lanxiang Hu, Zhezhi He, Zhijie Deng, Hao Zhang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=8uzBOVmh8H"
tags: ["query:edge-llm"]
score: 8.0
evidence: 通过一致性模型和Jacobi解码实现高效LLM推理
tldr: CLLMs提出了一种新方法，通过微调目标LLM使其在Jacobi轨迹中从任意状态一致地预测固定点，从而加速收敛。该方法将Jacobi解码的速度提升从微不足道提升至2.4到3.4倍，使并行化解码成为实用方案，显著提高了LLM推理效率。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-8uzbovmh8h/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 866, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-8uzbovmh8h/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1768, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-8uzbovmh8h/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 811, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-8uzbovmh8h/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1329, \"height\": 743, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-8uzbovmh8h/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1324, \"height\": 746, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-8uzbovmh8h/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 859, \"height\": 625, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-8uzbovmh8h/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 871, \"height\": 401, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-8uzbovmh8h/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 885, \"height\": 1213, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-8uzbovmh8h/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 886, \"height\": 1207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-8uzbovmh8h/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1726, \"height\": 585, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-8uzbovmh8h/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1305, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-8uzbovmh8h/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 794, \"height\": 846, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-8uzbovmh8h/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 672, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-8uzbovmh8h/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1776, \"height\": 516, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-8uzbovmh8h/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1693, \"height\": 284, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-8uzbovmh8h/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1345, \"height\": 279, \"label\": \"Table\"}]"
motivation: Jacobi解码理论上可并行化，但实践中速度提升极小，因为很少能一步预测多个token。
method: 微调LLM使其在Jacobi迭代中从任意状态一致地输出固定点，加速收敛。
result: 在多种任务上实现了2.4倍到3.4倍的生成速度提升。
conclusion: 通过训练一致性模型，使Jacobi解码真正实用，加速LLM推理。
---

## Abstract
Jacobi decoding shows promise for more efficient LLM inference as it breaks the sequential nature of the LLM decoding process and transforms it into more parallelizable computation. However, in practice, it achieves little speedup compared to traditional autoregressive (AR) decoding, primarily because Jacobi decoding seldom accurately predicts more than one token in a single fixed-point iteration step. To address this, we develop a new approach aimed at realizing fast convergence from any state to the fixed point in a Jacobi trajectory. This is accomplished by refining the target LLM to consistently predict the fixed point given any state as input. Extensive experiments demonstrate the effectiveness of our method, showing 2.4$\times$ to 3.4$\times$ improvements in generation speed while preserving generation quality across both domain-specific and open-domain benchmarks.

---

## 论文详细总结（自动生成）

# CLLMs: Consistency Large Language Models 论文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：大语言模型（LLM）推理采用自回归（AR）解码，顺序生成token，导致高延迟。并行解码方法如Jacobi解码理论上可打破顺序依赖，但实践中速度提升极小（仅约1.05×），因为Jacobi迭代很少能一步正确预测多个token。
- **背景**：现有加速方法如推测解码（需额外小型草稿模型）、Medusa（需添加多个解码头，增加参数量）都存在额外开销或复杂度。本文旨在通过微调目标LLM本身，使其在Jacobi解码中快速收敛，实现无附加组件的高效推理。

## 2. 方法论：核心思想、关键技术细节、算法流程
### 2.1 核心思想
- 将Jacobi解码的迭代过程类比于扩散模型的概率流ODE轨迹，借鉴**一致性模型（Consistency Models）** 的思想：训练模型将Jacobi轨迹上的任意中间状态直接映射到固定点（即AR解码结果）。
- 通过**一致性损失**迫使模型从任意输入状态直接输出与固定点一致的分布，同时加上**自回归损失**维持生成质量。

### 2.2 关键技术细节
- **Jacobi解码回顾**：将AR解码转化为求解非线性方程组，通过并行迭代更新n-token序列（n个连续token），直至收敛到固定点。
- **全局一致性损失（L_GC）**：对于Jacobi轨迹上的随机状态y和固定点y*，最小化qθ(y|y_<i, x)与qθ⁻(y*|y*_<i, x)之间的前向KL散度。
- **局部一致性损失（L_LC）**：仅要求相邻状态y^(j)和y^(j+1)的输出一致，效果弱于全局损失。
- **自回归损失（L_AR）**：标准下一个token预测的负对数似然，防止偏离目标LLM分布。
- **总损失**：L = L_consistency + ω L_AR （ω为权重系数）。
- **数据准备**：用目标LLM在领域数据上运行Jacobi解码收集轨迹，进行数据增强（随机纠正错误token）和清洗（去除重复/低质量样本）。
- **推理**：采用带KV缓存的Jacobi解码，逐步缩短迭代状态长度，减少计算量。

### 2.3 算法流程（文字说明）
1. **数据集生成**（Algorithm 1）：对提示集合中的每条提示，用目标LLM执行Jacobi解码，记录每条轨迹（从随机初始化到固定点）。可进行数据增强与过滤。
2. **训练**（Algorithm 2）：从数据集中采样（提示、轨迹、完整响应），计算自回归损失；从轨迹中随机采样一个状态，计算一致性损失；联合优化。
3. **推理**（Algorithm 3）：对当前提示，用LLM预填充第一token；维护n-token序列，每次并行前向传播后检测正确token（与上一轮相等的），保留固定token及其KV缓存，截断错误部分继续迭代，直到达到生成长度。

## 3. 实验设计
### 3.1 数据集与场景
- **领域特定任务**：Text-to-SQL（Spider）、Python代码生成（CodeSearchNet Python）、数学推理（GSM8K）。
- **开放域任务**：ShareGPT对话数据，评估用MT-bench。
- **语言建模**：raw-WikiText2和PTB。

### 3.2 Benchmark与对比方法
- **基线方法**：
  - Fine-tuned baseline（直接在目标LLM上监督微调）。
  - Medusa-2（添加多个解码头）。
  - 推测解码（用小蒸馏模型作为草稿模型）。
  - 不同解码算法：标准AR解码、Jacobi解码、Lookahead解码。
- **评估指标**：速度（tokens/s）、加速比（相对于AR解码）、任务指标（GSM8K solve rate、MT-bench score、Spider执行准确率、HumanEval pass@1、困惑度PPL）。

## 4. 资源与算力
- **硬件**：8× NVIDIA A100 40GB GPU + 128 AMD EPYC 7742 64核CPU。
- **训练成本**（附录D）：
  - 数据集生成：耗时约5 GPU·小时（Spider，200万token）到120 GPU·小时（ShareGPT，2亿token），可加速为<1至10小时（使用vLLM批量推理）。
  - 一致性训练：Spider约2小时（<0.01%预训练成本），GSM8K约12小时，CodeSearchNet Python约22小时（~0.1%），ShareGPT约30小时（~0.2%）。均使用8× A100 40GB GPU。

## 5. 实验数量与充分性
- **实验组数**：主实验在3个领域任务+1个开放域任务上进行，与3种基线（fine-tuned、Medusa、推测解码）在3种解码模式（AR、Jacobi、Lookahead）下对比，共约4×3×3=36组结果（含表和附录）。
- **消融实验**：
  - 数据集大小（20K/100K/500K轨迹）对加速比和MT-bench分数的影响（表4）。
  - n-token序列长度（16/32/64/128/256）对速度和准确率的影响（图3）。
  - 损失设计（全局vs局部损失，AR损失权重ω=1 vs 10，表6）。
  - 语言建模任务（表5）验证通用性。
- **充分性判断**：
  - 实验覆盖了领域特定、开放域、语言建模等多种场景。
  - 对每个关键超参数（数据量、序列长度、损失系数）均进行了系统探究。
  - 与SOTA方法的对比公平（相同骨干模型、相同硬件环境）。
  - 局限性讨论（数据质量依赖、未探索on-policy GKD等）。
- **总体评价**：实验设计较全面，充分支持方法有效性。但缺乏在更大模型（如13B/70B）上的验证，且MT-bench开放域加速比略低于Medusa（2.5× vs 2.7×），但参数量更少。

## 6. 主要结论与发现
- CLLMs在Jacobi解码下实现2.4×~3.4×加速（领域任务），MT-bench上2.4×，同时几乎不损失生成质量。
- **加速机制**：发现了**快速前传（fast forwarding）** 现象（一次迭代正确预测多个连续token）和**固定token（stationary tokens）** 现象（即使前面有错误token，正确token也能保持）。CLLMs的这两类token计数比原始LLM提升2.0×~6.8×。
- 一致性训练使CLLM学会**搭配结构（collocations）**，如编程语言中的关键词搭配、自然语言中的常见短语。
- 可与Lookahead解码进一步结合，获得额外加速。

## 7. 优点
- **方法创新**：将扩散模型的一致性训练思想引入LLM加速领域，思路新颖，理论有据。
- **无附加组件**：无需改动模型架构或添加草稿模型，内存友好，易于部署。
- **训练成本低**：只需少量领域数据（如1M token）就能取得显著加速。
- **兼容性**：可与KV缓存、FlashAttention、Lookahead解码等其他加速技术结合。
- **实验充分性**：多数据集、多基线、多消融，验证了方法的鲁棒性。

## 8. 不足与局限
- **依赖数据质量**：Jacobi轨迹中若包含低质量/重复样本，会导致CLLM生成退化，需严格清洗。
- **开放域泛化有限**：MT-bench加速比（2.4×）低于领域任务（3.0~3.4×），可能需要更多数据或更好的搭配学习。
- **未与更大规模模型对比**：仅实验7B模型，未验证13B/70B等更大规模下的效果和训练开销。
- **仅限贪心解码**：论文明确只考虑greedy sampling，未探索采样策略。
- **Overshoot风险**：训练中可能过度强调一致性导致分布偏移，需平衡AR损失权重（实验显示AR损失权重10时精度更高但加速略降）。
- **未讨论on-policy GKD**：附录中提及可以使用学生自生成样本替代教师数据以减少额外开销，但未实验验证。
- **预处理开销**：需要先运行Jacobi解码生成训练数据（一次性），对于大规模数据集仍有成本。

（完）
