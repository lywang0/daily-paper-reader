---
title: "Star Attention: Efficient LLM Inference over Long Sequences"
title_zh: Star注意力：长序列上高效的大语言模型推理
authors: "Shantanu Acharya, Fei Jia, Boris Ginsburg"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=QY7Au9nZwp"
tags: ["query:edge-llm"]
score: 6.0
evidence: 块稀疏注意力实现高效长序列推理
tldr: "长序列LLM推理因自注意力二次复杂度而昂贵。本文提出Star Attention，两阶段块稀疏近似：第一阶段跨主机并行块局部注意力，第二阶段全局注意力。该方法与多数Transformer集成，减少内存和推理时间11倍，保留97-100%准确率。"
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-qy7au9nzwp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 682, \"height\": 766, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qy7au9nzwp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 968, \"height\": 612, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qy7au9nzwp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 371, \"height\": 293, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qy7au9nzwp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1769, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qy7au9nzwp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1698, \"height\": 751, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qy7au9nzwp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1763, \"height\": 530, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qy7au9nzwp/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 800, \"height\": 520, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qy7au9nzwp/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 806, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qy7au9nzwp/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1773, \"height\": 486, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-qy7au9nzwp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1353, \"height\": 471, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qy7au9nzwp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 958, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qy7au9nzwp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1771, \"height\": 348, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qy7au9nzwp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1334, \"height\": 740, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qy7au9nzwp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1450, \"height\": 428, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qy7au9nzwp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 605, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qy7au9nzwp/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 812, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qy7au9nzwp/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1310, \"height\": 807, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qy7au9nzwp/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 756, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qy7au9nzwp/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1209, \"height\": 666, \"label\": \"Table\"}]"
motivation: 长序列推理成本高、速度慢，注意力计算复杂。
method: 两阶段块稀疏注意力：第一阶段并行局部注意力，第二阶段全局注意力。
result: 推理时间和内存减少11倍，准确率几乎无损。
conclusion: Star Attention为长序列LLM推理提供了高效且兼容的解决方案。
---

## Abstract
Inference with Transformer-based Large Language Models (LLMs) on long sequences is both costly and slow due to the quadratic complexity of the self-attention mechanism. We introduce Star Attention, a two-phase block-sparse approximation that improves computational efficiency by sharding attention across multiple hosts while minimizing communication overhead. In the first phase, the context is processed using blockwise-local attention across hosts, in parallel. In the second phase, query and response tokens attend to all prior cached tokens through sequence-global attention. Star Attention integrates seamlessly with most Transformer-based LLMs trained with global attention, reducing memory requirements and inference time by up to 11x while preserving 97-100% of accuracy.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与研究动机
- **问题**：基于Transformer的大语言模型（LLM）在长序列推理时，自注意力机制的计算复杂度为二次方，导致计算成本高、推理速度慢。
- **背景**：长上下文（百万级token）在代码分析、多文档摘要、大规模检索等场景中至关重要，但现有方法（如Ring Attention、FlashAttention）在推理阶段仍需全局注意力，开销随上下文长度线性增长；而稀疏注意力方法（如StreamingLLM、MInference）虽降低复杂度，但常需微调或牺牲精度。
- **目标**：在不牺牲准确率的前提下，大幅降低长序列推理的计算和存储开销，且无需额外训练。

## 2. 方法论：Star Attention
### 核心思想
- 两阶段块稀疏注意力：利用“长上下文+短查询”任务的局部性，将上下文编码和查询/生成解耦。
  - **Phase 1（上下文编码）**：将长上下文切分为连续块，每块（除第一块外）前缀一个锚块（anchor block，即第一块），跨主机并行计算块内局部注意力，不进行主机间通信。只保留当前块的KV缓存，丢弃锚块的KV。
  - **Phase 2（查询编码与令牌生成）**：查询广播到所有主机，各主机利用本地KV缓存计算局部注意力及softmax分母之和；指定查询主机收集所有局部注意力输出和softmax分母，通过在线softmax方法聚合为全局注意力，然后生成下一个token并更新查询主机的KV缓存。
- **关键技术细节**：
  - 锚块机制：避免每个块独立处理时产生多个注意力峰（attention sinks），使得局部注意力分布近似全局注意力。
  - 分布式softmax：仅需传输每个token的一个标量（局部softmax分母和）和一个向量（局部注意力输出），通信量极小。
- **与现有模型兼容**：可直接应用于任何基于全局注意力训练的Transformer模型，无需微调或修改架构。

## 3. 实验设计
### 数据集与基准（Benchmark）
- **RULER**：合成基准，含13个任务，覆盖检索（Needle-in-a-Haystack）、多跳追踪、聚合、问答等类别。
- **BABILong**：5个需要多事实推理的任务。
- **InfiniteBench**：10个真实/合成任务，包括摘要、多语言问答、代码调试、检索等。

### 对比方法
- **主基线**：Ring Attention（分布式全局注意力）。
- **稀疏注意力基线**：StreamingLLM（全局sink+滑动窗口）、MInference（动态稀疏模式）。
- **消融实验**：调查锚块位置、锚块内容、锚块大小的影响。

### 模型
- Llama-3.1-8B-Instruct、Llama-3.1-70B-Instruct（支持128K上下文）。
- gradientai-Llama-3-8B-Instruct-262K/1048K（扩展至256K/1M上下文）。
- 使用HuggingFace Transformers和NVIDIA TRT-LLM框架实现。

## 4. 资源与算力
- 所有实验使用 **NVIDIA A100 GPU**，bfloat16精度。
- 具体配置（见表7）：
  - 8B模型：16K-128K用8张GPU；256K-512K用16张；1M用32张。
  - 70B模型：16K-32K用8张GPU；64K用16张；128K用32张。
- 实验中使用 Flash Attention 优化，确保与Ring Attention对比公平。
- 论文未提及训练时间或预训练成本（该方法无需训练）。

## 5. 实验数量与充分性
- **大量实验**：
  - 在RULER上对128K序列（表1）及128K-1M（表5）进行了速度与精度对比。
  - 在BABILong上覆盖16K-128K（图4）。
  - 在InfiniteBench上与StreamingLLM、MInference对比（表3）。
  - 消融实验：锚块位置与内容（表4）、锚块大小（图5b）、块大小对精度的影响（图5a）。
  - 任务类别分析（图7、图8）：分析Single-NIAH、Multi-NIAH、Multi-Hop、Aggregation、QA。
- **充分性评价**：实验设计较为充分，覆盖不同序列长度、模型规模、任务类型；消融实验深入探究了锚块机制的各要素；对比了分布式（Ring Attention）和非分布式（StreamingLLM、MInference）方法。但所有实验均基于Llama系列，未在其他架构（如Qwen、Gemma）上验证，通用性有一定局限。

## 6. 主要结论与发现
- Star Attention在保持 **97-100%** 全局注意力精度的同时，实现 **最高11倍（128K）到16.9倍（1M）** 的推理加速。
- 锚块机制至关重要：锚块的内容（使用第一块真实token）比位置ID更关键；锚块大小需与上下文块大小相当才能达到最佳精度。
- 较大块大小提高精度，但较小块提供更高吞吐；在128K时，块大小设为序列1/4是较好的折中。
- 在聚合任务（如频率统计、总结）上甚至优于全局注意力；多跳追踪任务挑战较大，因跨块信息传递受限。

## 7. 优点
- **高效性与精度兼顾**：通过稀疏近似实现了接近全局注意力的精度，且加速比随序列长度增加而显著提升。
- **无需微调或训练**：即插即用，兼容大部分预训练Transformer LLM。
- **通信开销极小**：分布式softmax仅需传输标量和向量，远低于Ring Attention的KV缓存通信。
- **设计洞察深刻**：锚块机制巧妙地解决了局部注意力带来的多注意力峰问题，分析严谨（位置vs内容消融）。
- **实验全面**：覆盖3个基准、多个模型、不同序列长度，并包含详细的消融和任务级分析。

## 8. 不足与局限
- **模型通用性不足**：仅测试Llama系列，未在Qwen、Gemma等架构上验证。
- **多跳追踪任务性能下降**：跨块信息通信完全依赖第二阶段，对需要多次跨块推理的任务精度有所损失。
- **锚块大小约束**：需与上下文块大小一致，增加内存开销；为何如此要求的理论原因未完全解释。
- **极端长序列小块精度退化**：当块大小相对于序列长度过小时（如1M序列块大小为32K），精度下降较明显（-5.32%）。
- **分布式部署假设**：方法假设多主机环境，单GPU场景下效率可能不如FlashAttention。
- **未提及训练阶段**：该方法仅针对推理，与KV缓存压缩等技术正交，但文中未讨论与这些方法联合使用时的效果。

（完）
