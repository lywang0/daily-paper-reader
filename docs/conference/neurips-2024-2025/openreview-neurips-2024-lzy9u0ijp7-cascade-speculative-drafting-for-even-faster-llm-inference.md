---
title: Cascade Speculative Drafting for Even Faster LLM Inference
title_zh: 级联推测草拟：实现更快的LLM推理
authors: "Ziyi Chen, Xiaocong Yang, Jiacheng Lin, Chenkai Sun, Kevin Chang, Jie Huang"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=lZY9u0ijP7"
tags: ["query:edge-llm"]
score: 5.0
evidence: 改进的推测解码算法加速LLM推理
tldr: 推测解码中草稿生成存在自回归慢和等时分配问题。级联推测草拟（CS Drafting）引入级联执行算法，优化草稿生成过程，减少目标模型运行次数，从而加速推理。实验表明该方法在多种模型上实现了显著的加速效果。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-lzy9u0ijp7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-lzy9u0ijp7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1308, \"height\": 488, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-lzy9u0ijp7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 1487, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lzy9u0ijp7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 790, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lzy9u0ijp7/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1292, \"height\": 595, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lzy9u0ijp7/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1402, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lzy9u0ijp7/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 458, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-lzy9u0ijp7/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1383, \"height\": 1159, \"label\": \"Table\"}]"
motivation: 推测解码中草稿生成过程效率低下，包括自回归慢和等时分配。
method: 提出级联推测执行算法，优化草稿生成以减少目标模型运行次数。
result: 在多种模型上实现了显著的加速效果。
conclusion: CS Drafting通过级联草拟优化进一步加速了LLM推理。
---

## Abstract
Introduced to enhance the efficiency of large language model (LLM) inference, speculative decoding operates by having a smaller model generate a draft. A larger target model then reviews this draft to align with its output, and any acceptance by the target model results in a reduction of the number of the target model runs, ultimately improving efficiency. However, the drafting process in speculative decoding includes slow autoregressive generation and allocates equal time to generating tokens, irrespective of their importance. These inefficiencies collectively contribute to the suboptimal performance of speculative decoding. To further improve LLM inference, we introduce Cascade Speculative Drafting (CS Drafting), a speculative execution algorithm that incorporates two types of cascades. The *Vertical Cascade* eliminates autoregressive generation from neural models, while the *Horizontal Cascade* optimizes time allocation in drafting for improved efficiency. Combining both cascades, CS Drafting achieves greater speedup compared to the baselines in our experiments, while preserving the same output distribution as the target model. Our code is publicly available at https://github.com/lfsszd/CS-Drafting.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义

大型语言模型（LLM）的推理延迟是实际部署中的关键瓶颈。现有的**推测解码**（Speculative Decoding）方法通过一个小型草稿模型快速生成草稿，再由大型目标模型并行验证，从而减少目标模型的运行次数，加速推理。然而，推测解码的草稿生成过程存在两个主要低效问题：
- **自回归生成缓慢**：草稿模型仍需逐 token 自回归生成，尽管其规模较小，但多次运行的成本依然显著。
- **等时分配**：所有草稿 token 被赋予相同的生成时间，但实际中，早期 token 被接受的概率远高于后期 token（呈指数衰减），导致后期低价值 token 浪费了大量计算资源。

为解决上述问题，论文提出了**级联推测草拟（Cascade Speculative Drafting, CS Drafting）**，通过两种级联机制进一步加速 LLM 推理，同时保持输出分布与目标模型一致。

## 2. 论文提出的方法论

### 核心思想
CS Drafting 包含两种正交的级联策略：
- **垂直级联**：用更小的模型（甚至统计语言模型）为草稿模型生成草稿，从而消除神经模型的自回归生成。每个神经草稿模型负责验证更小模型的输出，递归进行直到成本可忽略的统计语言模型（如 Max-Gram）。
- **水平级联**：根据 token 位置分配不同的草稿模型——早期高接受概率的 token 用较大模型生成，后期低概率 token 用更小模型生成，最终由统计语言模型完成最后少量 token，从而优化时间分配。

### 关键技术细节
- **统计语言模型 Max-Gram**：一种基于最大匹配的算法，从输入或已有生成中贪婪匹配最长子串，若无匹配则回退到 Wikipedia 的二元模型。它成本极低，适合作为级联的最底层。
- **宽松性（Lenience）**：在草稿模型之间的验证过程中可引入超参数 \\(l \geq 1\\)，允许更宽松的接受条件以加速，但目标模型验证时 \\(l=1\\) 以保证输出分布不变。
- **算法流程**（Algorithm 1）：
  - 输入：目标模型 \\(M_t\\)，草稿模型列表 \\(\{M_{d1},...,M_{dn}\}\\)，上三角超参数矩阵 \\(K_{nn}\\)（每层停止条件），宽松性 \\(l\\)。
  - 水平级联通过 for 循环实现：依次用不同草稿模型生成指定数量的 token。
  - 垂直级联通过递归实现：每个草稿模型调用更小模型进行草拟，自身进行验证。
  - 递归基例：最小模型（如 MaG）直接生成 token 和 logits。
  - 最终由目标模型验证所有草稿，并额外生成一个 token。

### 理论分析
- **垂直级联的期望加速比**（Theorem 4.3）：当统计模型成本 \\(c_{d2} \ll 1\\) 时，垂直级联几乎总能提高效率。
- **水平级联的期望加速比**（Theorem 4.5）：通过分析不同位置 token 的接受概率与模型成本，证明水平级联优于等时分配。

## 3. 实验设计

### 数据集
- **GSM8K**：小学数学应用题，零样本链式思维设置。
- **MMLU**：57个学科的大规模多任务语言理解基准，零样本设置。

### 对比方法
- **自回归生成**（基准）。
- **标准推测解码**（Speculative Decoding）使用单一草稿模型（FLAN-T5-SMALL 或 FLAN-T5-BASE）。
- **CS Drafting** 不同变体：单神经模型+MaG，以及双神经模型+MaG（BASE+SMALL+MAG）。
- 在 decoder-only 模型上还对比了 **Medusa**（一种带树注意力的加速方法）以及 **CS Drafting + Tree Attention**。

### 模型选择
- **Encoder-decoder**：目标模型为 FLAN-T5-XXL，草稿模型为 FLAN-T5-BASE 和 FLAN-T5-SMALL。
- **Decoder-only**：目标模型为 Vicuna-7B，草稿模型为 68M 参数的模型（使用同一 tokenizer）。

### 评价指标
- **标准化墙钟时间改善（SWI）**：假设每轮运行时间与模型参数量成正比，或采用前人报告的延迟数据，保证可复现性。
- **实际墙钟时间**：在 NVIDIA A40 上测量的 tokens/s。

## 4. 资源与算力

论文明确提及所有涉及墙钟时间的实验均在**单张 NVIDIA A40 GPU** 上执行。未说明训练时长或具体 GPU 数量（因为实验均为推理阶段，无需训练）。对于 SWI 指标则仅基于假设模型参数规模，不涉及实际硬件。

## 5. 实验数量与充分性

### 实验组数
- **Encoder-decoder**（Table 2）：在 GSM8K 和 MMLU 上各测试了 3 种 CS Drafting 配置（BASE+MAG, SMALL+MAG, BASE+SMALL+MAG）以及 2 种标准推测解码配置，共约 10 组主要实验。
- **Decoder-only**（Table 3）：对比了自回归、推测解码、CS Drafting、Medusa、CS Drafting+Tree Attention，共 5 组。
- **消融实验**（Table 4）：对超参数 \\(K_{00}\\) 进行了不同取值的测试（1,2,3）并报告 tokens/s。
- **水平级联消融**：在 Vicuna-7B 上移除水平级联后性能从 56.16 降至 53.55 tokens/s。

### 充分性与公平性
- 实验覆盖两种架构（encoder-decoder 和 decoder-only）、两个数据集、多种草稿模型组合。
- 使用了 **标准化 SWI** 消除硬件差异，同时报告实际墙钟时间，客观全面。
- 对比方法（标准推测解码、Medusa）均是领域内强基线，实验设置（零样本、贪心解码）一致。
- 但未提供多次运行的标准差或置信区间，且未在更多模型（如 GPT-系列）上验证。

## 6. 论文的主要结论与发现

1. CS Drafting 在 GSM8K 上最高获得 **44% 额外加速**（相较于最快标准推测解码），在 MMLU 上最高获得 **81% 额外加速**。
2. 仅使用一个神经草稿模型 + MaG 即可获得显著加速（MMLU 上额外 70%，GSM8K 上额外 32%），且无需额外部署成本。
3. 在垂直级联中，较大的草稿模型（如 BASE）在 MaG 辅助下优于较小的草稿模型（SMALL），打破了标准推测解码中“越小越好”的结论。
4. CS Drafting 可与树注意力（Tree Attention）结合，进一步超越 Medusa，表明其兼容性良好。
5. 理论分析支持垂直级联和水平级联的加速有效性，并与实验结果一致。

## 7. 优点

- **创新的双重级联设计**：垂直消除自回归，水平优化时间分配，两者正交且互补。
- **理论与实验紧密结合**：提供概率生成函数推导的期望加速比公式，并给出非平凡证明。
- **高效且无损**：目标模型验证时不使用宽松性，保证输出分布不变；MaG 模型参数仅等于 tokenizer 大小，内存开销可忽略。
- **实验可复现性强**：提供标准化 SWI 指标，公开代码，并给出超参数细节。
- **兼容性强**：可直接与现有加速方法（如树注意力）结合，进一步提升性能。

## 8. 不足与局限

- **硬件依赖性问题**：虽然报告了 SWI 和实际墙钟时间，但不同硬件配置下的实际加速可能有所差异。论文在限制一节已承认该点。
- **超参数调优**：超参数矩阵 \\(K_{nn}\\) 和宽松性 \\(l\\) 需要手动选择，作者虽展示 K00 不敏感，但整体调优可能复杂。
- **实验覆盖有限**：仅使用 FLAN-T5 和 Vicuna 两个模型系列，未在更大模型（如 LLaMA-70B）或更多任务（如翻译、对话）上验证。
- **缺乏统计显著性报告**：未给出多次运行的标准差或置信区间，无法评估结果稳定性。
- **MaG 算法的通用性**：MaG 基于最大匹配和 Wikipedia 二元模型，可能对特定领域（如代码、医学文本）效果不佳，需进一步研究领域适应方法。

（完）
