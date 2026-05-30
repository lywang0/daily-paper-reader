---
title: Inference-Time Hyper-Scaling with KV Cache Compression
title_zh: 基于KV缓存压缩的推理时超缩放
authors: "Adrian Łańcucki, Konrad Staniszewski, Piotr Nawrot, Edoardo Ponti"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=8ZiElzQxf1"
tags: ["query:edge-llm"]
score: 4.0
evidence: 通过KV缓存压缩在相同计算预算内生成更多令牌，资源高效
tldr: 推理时间扩展通过生成更长序列提升推理准确性，但受限于KV缓存大小。本文提出动态内存稀疏化（DMS）方法，仅需1000步训练即可实现8倍压缩，在不显著降低准确性的前提下增加有效推理计算量，从而提升扩展推理的准确性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-8zielzqxf1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 634, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8zielzqxf1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 598, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8zielzqxf1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1412, \"height\": 1872, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8zielzqxf1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1432, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8zielzqxf1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1323, \"height\": 739, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8zielzqxf1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1419, \"height\": 285, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8zielzqxf1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1415, \"height\": 1855, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8zielzqxf1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1355, \"height\": 557, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8zielzqxf1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1331, \"height\": 1507, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 309, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 642, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1320, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 971, \"height\": 1010, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 981, \"height\": 535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 918, \"height\": 848, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1365, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1370, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1371, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1296, \"height\": 635, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1295, \"height\": 636, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1081, \"height\": 634, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 970, \"height\": 300, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8zielzqxf1/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 865, \"height\": 119, \"label\": \"Table\"}]"
motivation: 推理时间扩展受KV缓存大小瓶颈，而非生成令牌数。
method: 提出动态内存稀疏化（DMS）方法，稀疏化KV缓存以实现高压缩比。
result: 仅需1K训练步骤即可实现8倍压缩，提升推理准确性。
conclusion: 通过KV缓存压缩实现了推理时超缩放，有效提升推理准确性。
---

## Abstract
Inference-time scaling trades efficiency for increased reasoning accuracy by generating longer or more parallel sequences. However, in Transformer LLMs, generation cost is bottlenecked by the size of the key–value (KV) cache, rather than the number of generated tokens. Hence, we explore inference-time hyper-scaling: by compressing the KV cache, we can generate more tokens within the same compute budget and further improve the accuracy of scaled inference. The success of this approach, however, hinges on the ability of compression methods to preserve accuracy even at high compression ratios. To make hyper-scaling practical, we introduce Dynamic Memory Sparsification (DMS), a novel method for sparsifying KV caches that only requires 1K training steps to achieve 8× compression, while maintaining better accuracy than training-free sparse attention. Instead of prematurely discarding cached tokens, DMS delays token eviction, implicitly merging representations and preserving critical information. We demonstrate the effectiveness of inference-time hyper-scaling with DMS on multiple families of LLMs, showing that it boosts accuracy for comparable inference latency and memory load. For instance, we enhance Qwen-R1 32B by 9.1 points on AIME 24, 7.6 on GPQA, and 9.6 on LiveCodeBench on average for an equivalent number of memory reads.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：在 Transformer 大语言模型（LLM）中，推理时扩展（inference-time scaling）通过生成更长的推理链或更多并行序列来提升推理准确率，但生成成本主要受限于键值（KV）缓存的大小，而非生成的 token 数量。KV 缓存随序列长度和批量大小线性增长，导致内存瓶颈和延迟增加。
- **核心问题**：能否通过压缩 KV 缓存，在相同计算预算（延迟、内存）下生成更多 token，从而进一步提高扩展推理的准确率？但前提是压缩方法必须能在高压缩比下保持模型精度。
- **整体含义**：本文提出“推理时超缩放”（inference-time hyper-scaling）概念，即利用 KV 缓存压缩来打破 token 预算与计算预算之间的等价关系，使更长的推理序列或更多并行序列成为可能，从而提升推理能力。

### 2. 方法论：核心思想、关键技术细节

- **核心思想**：提出动态内存稀疏化（Dynamic Memory Sparsification, DMS）方法，是一种可训练的 KV 缓存压缩方法，通过稀疏化（即选择性丢弃）KV 条目来减小缓存大小，同时通过延迟淘汰机制保留关键信息。
- **关键技术细节**：
  - **淘汰决策**：每个时间步，DMS 使用一个线性层（权重 w、偏置 b）结合 Gumbel-sigmoid 分布预测二元淘汰决策 α（0 表示保留，1 表示淘汰）。训练时 α 通过随机重参数化保持可微。
  - **延迟淘汰**：被标记为淘汰的 token 不会立即删除，而是保留一个滑动窗口（默认大小 256 token），直到该 token 移出窗口后才真正淘汰。这避免了过早丢弃有用上下文。
  - **训练目标**：使用 logit 蒸馏损失（教师为原始 LLM）和辅助损失（强制平均压缩比匹配目标 α⋆）。目标压缩比从 0 逐步退火到 1−1/CR（CR 为压缩比），每 100 训练步增加 1 个单位 CR。
  - **实现**：不增加额外参数（借用每个查询组的第一个查询头的第一个维度来预测 α），支持 PagedAttention 等现有高效内核。
  - **推理时**：将 α 取整为 0/1，被淘汰的 token 在滑动窗口外被覆盖，无额外读写开销。

### 3. 实验设计

- **数据集和场景**：
  - 推理时超缩放评估：AIME 2024（数学）、MATH-500（数学）、GPQA Diamond（硬科学）、LiveCodeBench（编程）。采用 exact match 或 pass@all 准确率。
  - 通用 LLM 评估：GSM8K、MMLU、HellaSwag、Needle in a Haystack（NIAH）、Variable Tracking（VT）等长上下文任务。
  - 吞吐量和延迟测量：在 NVIDIA H100 SXM GPU 上使用 HuggingFace Transformers + FlashAttention 实现。
- **基准（Baselines）**：
  - 训练无关方法：TOVA、H2O、Quest。
  - 训练型方法：动态内存压缩（DMC）。
  - 原始未压缩模型（Vanilla）。
- **模型**：Qwen 2.5 1.5B/7B/32B（蒸馏自 DeepSeek R1）、Qwen3-8B（蒸馏自 Qwen3-235B-A22B）、Llama 3.2 1B Instruct（消融实验）。

### 4. 资源与算力

- 文中提供了训练成本表（附录 Table 3）：
  - Llama 3.2 1B：CR i → CR i+1 需约 10 GPU 小时（batch size 1024, 上下文 4096, 步数 100）。
  - Qwen-R1 1.5B：约 30 GPU 小时。
  - Qwen-R1 7B：约 75 GPU 小时。
  - Qwen-R1 32B：约 345 GPU 小时。
  - Qwen3-8B：约 270 GPU 小时（batch size 256, 上下文 32768）。
- 所有训练在 NVIDIA H100 GPU 上使用 Megatron-LM，bfloat16 精度，FP32 优化器状态。
- 总训练步数：DMS 达到 CR 8× 仅需 700 步（CR 4× 约 300 步），相比 DMC 的 44K 步大幅减少。

### 5. 实验数量与充分性

- **实验数量**：涵盖 4 个推理数据集 ×3 种模型大小 × 多种配置（W-L-CR，其中 W 为并行链数，L 为序列长度，CR 为压缩比），共数十个实验点。同时提供了消融实验（延迟淘汰 vs 即时淘汰、不同滑动窗口大小、数据效率等）、通用任务评估（多任务表 Table 1 & Table 2）、长上下文评估（NIAH、VT）、吞吐量对比等。
- **充分性与公平性**：
  - 与多种基线（TOVA、H2O、Quest、DMC）对比，覆盖训练无关和训练型方法。
  - 报告了 Pareto 前沿、平均值改进（附录 Table 8-9），部分结果附带标准误差（附录 Table 6）。
  - 超参数公开（滑动窗口 256、训练步数、学习率等），使用 logit 蒸馏以保证数据可重复性。
  - 局限性：未包含更大模型（>32B）和更长上下文（>32K），未与其他量化/分解方法正交组合，未在异质架构（如 Multi-head Latent Attention）上测试。

### 6. 主要结论与发现

- **推理时超缩放有效**：DMS 在所有测试模型和数据集上显著优于原始模型和基线，在 KV 缓存内存读取和峰值内存两个指标下取得了更好的 Pareto 前沿。例如，Qwen-R1 32B 在 AIME 24 上平均提升 12.0 分，GPQA 提升 8.6 分，LiveCodeBench 提升 9.7 分（图 1、表 8）。
- **DMS 相比训练无关方法的优势**：在高压缩比（8×）下仍保持接近原始模型的准确率，而 TOVA、H2O 等性能严重下降。Quest 虽准确率较好，但内存不减反增。
- **DMS 相比 DMC 的数据效率优势**：仅需 DMC 约 1/60 的训练 token 即可达到可比甚至更好的准确率（图 5 右）。
- **延迟淘汰策略关键**：即时淘汰会导致准确率快速下降，而延迟淘汰（滑动窗口）稳定模型性能（图 5 左）。
- **通用能力保持**：在非推理场景（如 MMLU、HellaSwag）中 DMS 几乎无损，甚至长上下文任务（NIAH、VT）超越原始模型（表 1）。

### 7. 优点

- **方法创新**：首次将 KV 缓存压缩与推理时扩展结合，定义“超缩放”概念，并设计出数据高效的压缩方法。
- **高效实用**：仅需 1K 训练步实现 8× 压缩，无额外参数，兼容现有推理系统（如 PagedAttention）。
- **评估全面**：涵盖多种模型族、规模和任务类型，并报告实际吞吐量/延迟测量，结果具有工程指导意义。
- **消融深入**：通过消融实验验证了延迟淘汰、滑动窗口大小、训练数据效率等设计选择的有效性。

### 8. 不足与局限

- **模型与上下文范围有限**：实验限于 1B–32B 参数、上下文 ≤32K、压缩比 ≤8×，更大规模/更长上下文的推广性未知。
- **未与正交方法结合**：未探索与 KV 缓存量化（如 KIVI、KVQuant）或低秩分解（如 LoRC）的组合效果。
- **架构依赖**：仅在标准多头注意力（GQA）上验证，未在 Multi-head Latent Attention 等变体上测试。
- **验证器扩展未探索**：论文仅使用无验证器的扩展策略（如多数投票），未涉及过程奖励模型（PRM）场景，后者需额外加速。
- **训练数据细节不足**：部分训练数据为内部结构（如 Llama 3.2 1B 的训练数据来源于合成数据和代码数据集），虽公开核心数据（如 OpenR1-Math-220k），但完全复现需额外说明。
- **潜在偏差风险**：未讨论压缩可能引入的推理偏差或公平性问题（作者在附录中提及放大现有风险，但未具体分析）。

（完）
