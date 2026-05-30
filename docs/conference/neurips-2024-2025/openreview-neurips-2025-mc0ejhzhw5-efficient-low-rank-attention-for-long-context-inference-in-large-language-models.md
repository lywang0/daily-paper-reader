---
title: Efficient Low Rank Attention for Long-Context Inference in Large Language Models
title_zh: 面向长上下文大语言模型推理的高效低秩注意力机制
authors: "Li Tenghui, Guoxu Zhou, Xuyang ZHAO, Yuning Qiu, Qibin Zhao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Mc0eJHZhW5"
tags: ["query:edge-llm"]
score: 8.0
evidence: 低秩注意力减少长上下文推理中的KV缓存，适用于资源受限设备
tldr: 针对长上下文推理中KV缓存占用大量GPU内存、限制在资源受限设备上部署的问题，本文提出LRQK方法，在预填充阶段将全精度查询和键矩阵分解为紧凑低秩因子，在解码阶段使用低维投影计算代理注意力分数，仅选择前k个token。实验表明，该方法在显著降低内存消耗的同时，在多种长上下文任务上保持了与全精度注意力相媲美的性能，为边缘设备上的长上下文LLM推理提供了高效解决方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-mc0ejhzhw5/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1133, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mc0ejhzhw5/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 871, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mc0ejhzhw5/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1050, \"height\": 690, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mc0ejhzhw5/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1050, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mc0ejhzhw5/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 882, \"height\": 339, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-mc0ejhzhw5/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1391, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mc0ejhzhw5/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 642, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mc0ejhzhw5/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1225, \"height\": 167, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mc0ejhzhw5/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 654, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mc0ejhzhw5/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1511, \"height\": 513, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mc0ejhzhw5/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1218, \"height\": 463, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mc0ejhzhw5/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1096, \"height\": 490, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mc0ejhzhw5/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1209, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mc0ejhzhw5/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1028, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mc0ejhzhw5/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1109, \"height\": 529, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mc0ejhzhw5/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1395, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mc0ejhzhw5/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1425, \"height\": 416, \"label\": \"Table\"}]"
motivation: 长上下文推理中KV缓存内存开销大，限制了在资源受限设备上的应用。
method: 提出低秩查询键注意力（LRQK），将查询和键矩阵分解为低秩因子，并基于低维投影选择关键token。
result: 在多个长上下文基准上减少内存使用，同时保持推理质量。
conclusion: LRQK通过低秩分解有效缓解长上下文推理的内存瓶颈，适合资源受限场景。
---

## Abstract
As the length of input text increases, the key-value (KV) cache in LLMs imposes prohibitive GPU memory costs and limits long-context inference on resource constrained devices.
  Existing approaches, such as KV quantization and pruning, reduce memory usage but suffer from numerical precision loss or suboptimal retention of key-value pairs.
  In this work, Low Rank Query and Key attention (LRQK) is introduced, a two-stage framework that jointly decomposes full-precision query and key matrices into compact rank-\(r\) factors during the prefill stage, and then employs these low-dimensional projections to compute proxy attention scores in \(\mathcal{O}(lr)\) time at each decode step.
  By selecting only the top-\(k\) tokens and a small fixed set of recent tokens, LRQK employs a mixed GPU-CPU cache with a hit-and-miss mechanism where only missing full-precision KV pairs are transferred, thereby preserving exact attention outputs while reducing CPU-GPU data movement.
  Extensive experiments on the RULER and LongBench benchmarks with LLaMA-3-8B and Qwen2.5-7B demonstrate that LRQK matches or surpasses leading sparse-attention methods in long context settings, while delivering significant memory savings with minimal accuracy loss. Our code is available at \url{https://github.com/tenghuilee/LRQK}.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

随着大语言模型（LLMs）处理长上下文文本的需求日益增长，**KV缓存（Key-Value cache）** 在推理过程中会随着序列长度线性增长，导致GPU显存开销剧增，严重限制了在资源受限设备（如消费级GPU）上进行长上下文推理的能力。现有方法（如KV量化、剪枝、卸载）虽能缓解内存压力，但都存在固有缺陷：量化损失数值精度；剪枝可能错误丢弃重要token；卸载策略因PCIe数据传输引入高延迟。因此，需要一种在内存效率、数值精度和计算延迟之间取得平衡的方案。

论文的研究动机正是解决这一矛盾：利用注意力机制中固有的**稀疏性**和**低秩性**，提出一种两阶段推理框架，既保留全精度注意力输出，又大幅减少GPU内存占用和数据传输开销。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- **低秩性**：在解码器-only Transformer中，Query和Key矩阵的交互（QKᵀ）呈现出显著的低秩结构（如图3所示）。因此可以将其分解为紧凑的秩-r因子，用于高效计算代理注意力分数。
- **稀疏性**：每一解码步仅少数token贡献主要注意力权重（如图4所示当前token邻居具有高注意力分数）。因此只需选择top-k活跃token和少量最近token进行全精度注意力计算。

### 关键技术细节
- **两阶段框架**：
  - **预填充阶段（Prefill）**：对整段输入，联合优化Query和Key矩阵的低秩分解，得到左因子 \(A_Q, A_K \in \mathbb{R}^{l \times r}\) 和右因子 \(B_Q, B_K \in \mathbb{R}^{r \times d}\)（\(r \ll d\)，l为序列长度，d为头维度）。优化目标为最小化重构误差（式(5)），采用块坐标下降法迭代求解（Algorithm 1）。
  - **解码阶段（Decode）**：每生成一个新token，先利用前一时刻的低秩因子更新当前token的低秩近似 \(\mathbf{bq}_t, \mathbf{bk}_t \in \mathbb{R}^{1 \times r}\)（通过求解带约束的拉格朗日问题，式(8)），然后使用 \(A_K\) 和 \(\mathbf{bq}_t\) 计算代理注意力分数，选出top-k索引；再结合一个固定大小的**lite token**集（最近token），构成GPU缓存；仅缺失的KV对从CPU传输到GPU，实现精确注意力计算（Algorithm 2）。

- **混合缓存管理**：采用“命中-未命中”机制，GPU仅缓存活跃token（top-k）和lite token（最近固定数），其余存储在CPU。解码时只传输缺失的KV对，减少数据搬运。

- **公式流程**：
  - 预填充：求解 \(Q \approx A_Q B_Q, K \approx A_K B_K\)，同时近似 \(QK^\top \approx A_Q A_K^\top\)。
  - 解码：迭代更新 \(\mathbf{bq}_t, \mathbf{bk}_t\)，并梯度更新 \(B_Q, B_K\)，最后用 \(A_K \mathbf{bq}_t^\top\) 选top-k。

## 3. 实验设计

### 数据集与基准
- **RULER**：长上下文基准，测试序列长度128K（主要实验），也包含4K、8K、16K、32K子集。任务包括S1/S2（单/多键检索）、MK1/MK2（多键值）、MQ/MV、QA-1/QA-2（SQuAD/HotpotQA）、VT（可变追踪）等。
- **LongBench**：长文档理解任务（FWE、NQA、MQA、GRep、SAM、PRetr、LCC等）。
- **WikiText-2-v1**：用于分析注意力的分布和miss rate统计。

### 对比方法
- **全精度基线**：原始LLaMA-3-8B-1M, Qwen2.5-7B等。
- **稀疏注意力方法**：Loki, InfiniGen, Quest, ShadowKV (均为动态稀疏注意力)。
- 额外对比：StreamingLLM、H₂O、SnapKV等方法已在相关工作讨论，未直接对比但属于同一范畴。

### 实验配置
- backbone模型：LLaMA-3-8B-1M（1M上下文），Qwen2.5-7B-Instruct，LLaMA-3.1-8B，Mistral-7B，Phi-3-mini-128k，Qwen2.5-14B/32B。
- 默认超参数：rank r=32, top-k=2048, lite tokens=64, 迭代2次, 容差1e-2。
- 消融实验：改变rank (8,16,24,32), top-k (256,512,1024), lite tokens数量。

## 4. 资源与算力

论文明确说明了硬件配置：
- 主要实验：NVIDIA A100 GPU（40GB/80GB显存），单卡运行。
- 部分额外实验：NVIDIA GeForce RTX 3090 (24GB), RTX A6000 (48GB)。
- 未明确说明训练时长（论文关注推理阶段，不涉及训练），但给出了吞吐量数据（如表11：在A100上4K→64K的Prefill/Decode速度）。
- 实验环境：PyTorch bfloat16精度，float32用于逆矩阵计算；CPU为AMD EPYC 7742。

## 5. 实验数量与充分性

- **大量实验**：覆盖RULER的多种子任务（10+个指标）、LongBench的8个任务；涉及多个模型（LLaMA-3-8B, Qwen2.5-7B, LLaMA-3.1-8B, Mistral, Phi-3, Qwen2.5-14B/32B）。
- **消融实验充分**：对rank、top-k进行独立变化分析（表3、表4）；对lite tokens、初始化策略、结合KVQuant、不同缓存策略（有/无hit/miss）均进行了对比。
- **客观性**：与多个SOTA基线公平比较，在相同GPU和数据集下运行。
- **不足**：未对所有超参数组合进行全面网格搜索，但提供了实用指导（附录D）。统计显著性（误差棒）未明确报告，但实验重复性可保证。

总体而言，实验设计较为全面，覆盖了多种模型、任务尺度和消融维度，充分验证了方法有效性。

## 6. 论文的主要结论与发现

- **LRQK在长上下文推理中显著减少GPU内存消耗**，在128K上下文下，仅需存储top-2048+64个KV对，内存占用仅为全量的约1.6% + 少量额外开销。
- **在RULER 128K上**，LRQK在多个任务上匹配甚至超越ShadowKV等基线，尤其在MQ、MV、QA-1、PRetr等任务上表现突出。
- **解码吞吐量稳定**：在上下文从4K扩展到64K时，LRQK的decode速度几乎不变（约5-7 tokens/s），而CPU卸载方法性能急剧下降（64K时仅0.5 tokens/s）。
- **低秩因子初始化鲁棒**：随机初始化与基于重要性的初始化性能相差无几（表10）。
- **与KV量化兼容**：LRQK结合KVQuant后仍保持竞争力，无灾难性损失。

## 7. 优点

- **创新性**：联合低秩分解Query和Key，同时约束QKᵀ近似，避免单独对K做SVD的高昂代价（如ShadowKV）。
- **精度保留**：代理注意力仅用于筛选token，最终注意力计算使用原始全精度值，保证数值精度无损失。
- **高效数据传输**：hit/miss机制和lite token缓冲区减少CPU-GPU数据传输约60%（miss rate约0.4）。
- **轻量级**：矩阵逆运算规模为r×r（r很小），计算负担小。
- **通用性强**：在多个模型（从7B到32B）和多个上下文长度（4K~128K）上均有效。

## 8. 不足与局限

- **计算瓶颈**：CPU端索引操作成为主要性能瓶颈（而非PCIe带宽），导致解码吞吐量仍低于全GPU推理（约5-7 tokens/s vs 35+ tokens/s）。
- **超参数依赖任务**：rank和top-k的最佳值需要针对具体模型和任务进行微调，虽然提供了默认值，但非最优配置可能需要额外验证。
- **长上下文检索任务波动**：在RULER的MK2（多键2）等任务上，LRQK表现低于ShadowKV，说明某些场景下低秩近似可能导致信息丢失。
- **实验覆盖局限**：未测试更大模型（如70B）或更长上下文（>128K），也未涉及混合精度训练等场景。
- **统计显著性未报告**：部分核心结果未提供误差范围或多次运行标准偏差。

（完）
