---
title: Compute or Load KV Cache? Why Not Both?
title_zh: 计算还是加载KV缓存？为何不两者兼顾？
authors: "Shuowei Jin, Xueshen Liu, Qingzhao Zhang, Zhuoqing Mao"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=WOyOtaO6lQ"
tags: ["query:edge-llm"]
score: 6.0
evidence: 计算和I/O双向调度以加载KV缓存
tldr: Cake提出了一种新型KV缓存加载系统，通过双向调度策略并行利用计算和I/O资源，动态平衡KV缓存的计算与加载过程，有效解决了前缀缓存因存储I/O带宽限制导致的高延迟问题，为长上下文LLM推理提供了高效的预填充加速方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-woyotao6lq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 684, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-woyotao6lq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 836, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-woyotao6lq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 852, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-woyotao6lq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 834, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-woyotao6lq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 837, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-woyotao6lq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 837, \"height\": 281, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-woyotao6lq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 806, \"height\": 153, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-woyotao6lq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 881, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-woyotao6lq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 668, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-woyotao6lq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 870, \"height\": 420, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-woyotao6lq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 613, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-woyotao6lq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 845, \"height\": 572, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-woyotao6lq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 868, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-woyotao6lq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 607, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-woyotao6lq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1125, \"height\": 620, \"label\": \"Table\"}]"
motivation: 前缀缓存因I/O带宽瓶颈导致高延迟。
method: 设计Cake系统，双向调度计算和I/O资源，并行执行KV缓存计算和加载。
result: Cake显著降低了预填充阶段延迟，提升了长上下文推理效率。
conclusion: Cake通过计算-I/O并行化克服了存储带宽限制，优化了LLM推理性能。
---

## Abstract
Large Language Models (LLMs) are increasingly deployed in large-scale online services, enabling sophisticated applications. However, the computational overhead of generating key-value (KV) caches in the prefill stage presents a major bottleneck, particularly for long-context inputs. Prefix caching mitigates this issue by storing KV caches for reuse, reducing redundant computation. Despite its advantages, prefix caching suffers from high latency due to the limited I/O bandwidth of storage devices, constraining inference efficiency. To address this challenge, we introduce Cake, a novel KV cache loading system that optimally utilizes both computational and I/O resources in parallel. Cake employs a bidirectional scheduling strategy that dynamically balances KV cache computation and loading, ensuring efficient resource utilization. Additionally, Cake incorporates an adaptive scheduling mechanism that seamlessly integrates with non-prefix caching requests, improving system throughput and adapting to fluctuating resource availabilty. Through extensive evaluations across various hardware configurations, datasets, and storage conditions, Cake achieves on average 2.6× reduction in Time to First Token (TTFT) compared to compute-only and I/O-only methods. Our findings highlight Cake as an effective and practical solution for optimizing long-context LLM inference, bridging the gap between computation and I/O efficiency in large-scale AI deployments.

---

## 论文详细总结（自动生成）

## 论文核心问题与整体含义

- **研究动机**：大语言模型（LLM）在长上下文推理时，预填充阶段生成键值（KV）缓存的计算开销巨大。前缀缓存通过复用已缓存的KV缓存来减少冗余计算，但受限于存储设备（如磁盘、网络）的低I/O带宽，导致加载延迟高，影响首次令牌时间（TTFT）。现有方法要么完全依赖计算，要么完全依赖I/O加载，未能充分利用两种资源的并行性。
- **整体含义**：本文提出Cake系统，通过双向并行调度计算和I/O资源，显著降低长上下文前缀缓存场景下的TTFT，提升推理效率。

## 论文提出的方法论

### 核心思想
- 利用计算和I/O资源的并行性：在典型推理服务器上，GPU计算KV缓存的等效吞吐量与从SSD加载相当（约2–4 GB/s），因此并行执行二者可有效降低延迟。
- 关键洞察：计算成本随令牌位置递增（后部令牌需关注更多前序令牌），而I/O加载成本与令牌位置无关。因此，从序列头部开始计算KV缓存（计算成本低），从尾部开始加载已缓存的KV缓存（I/O成本恒定），双向进行直至相遇，可最小化总延迟。

### 关键技术细节
- **双向调度策略**：将输入序列切分为固定大小的块（chunk）。初始化两个指针：compute_ptr从序列首部正向移动，io_ptr从序列尾部反向移动。GPU计算线程从compute_ptr开始正向计算KV缓存；I/O线程从io_ptr开始反向加载已缓存的KV缓存。当两指针相遇或交叉时，整个序列的KV缓存就绪。
- **自适应调度机制**：与vLLM的chunk prefill调度集成。优先级顺序：解码请求 > 非前缀缓存分块预填充 > 前缀缓存分块预填充。空闲计算资源优先分配给非缓存请求，剩余资源用于Cake的计算部分，确保系统吞吐量。
- **动态适应资源波动**：双向并行设计天然适应计算和I/O带宽的波动——当一方资源变化时，相遇点自动调整，始终保证最低延迟。

### 算法流程（文字说明）
1. 输入请求，将序列按固定块大小分块。
2. 计算所有块的哈希，查找存储后端中已缓存的最新前缀，确定总令牌数。
3. 初始化两个指针：compute_ptr = 0，io_ptr = total_tokens - 1。
4. 并行启动两个线程：
   - GPU计算线程：从compute_ptr开始正向计算KV缓存，每次计算后增加compute_ptr，直至compute_ptr >= io_ptr或遇到CPU内存中已缓存的块。
   - I/O加载线程：从io_ptr开始反向加载已缓存的KV缓存，每次加载后减少io_ptr，直至io_ptr <= compute_ptr。
5. 两线程完成后，整个序列的KV缓存准备就绪，开始解码。

## 实验设计

### 数据集
- LongChat（多轮对话）
- TriviaQA（长文档问答）
- NarrativeQA（长文档问答）
- 由于性能评估与具体令牌内容无关，主要依赖令牌长度，因此使用均匀采样生成4k–16k令牌的合成提示（间隔2k）。

### Benchmark
- TTFT（Time-to-First-Token）作为主要评估指标。

### 对比方法
- **计算-only**：vLLM（v0.6.2）的chunk prefill模式（默认块大小512令牌）。
- **I/O加载-only**：LMCache（v0.1.4），从本地/远程磁盘加载已缓存的KV缓存。

### 实验场景
- 不同硬件（A100、H100、2×A100）
- 不同GPU利用率（12.5%–100%）
- 不同I/O带宽（7 Gbps到100 Gbps）
- 不同序列长度（4k–16k令牌）
- 不同模型架构（LongAlpaca-7B/13B、LLaMA3.1-8B/70B）
- 不同块大小（64–2048令牌）
- KV缓存压缩方法（8-bit、3-bit量化）
- 资源波动（随机计算预算和I/O带宽轨迹）
- 自适应调度（突发非缓存请求场景）

## 资源与算力

- 论文明确提及的硬件配置：
  - 服务器1：2×NVIDIA A100 80GB GPU（NVLink连接）、64核AMD EPYC 7763 CPU、2.0TB内存。
  - 服务器2：单NVIDIA H100 GPU、26核vCPU、200GB内存。
- 训练时长未说明，因为该工作聚焦推理优化而非模型训练。实验为推理阶段性能测量。

## 实验数量与充分性

- **实验组数**：覆盖7个主要维度（硬件、利用率、带宽、序列长度、模型、块大小、压缩），每个维度下多个配置，总计超过30个不同条件组合。此外还有资源波动、自适应调度、系统开销等专项实验。
- **充分性评估**：实验设计全面，覆盖了影响Cake性能的主要变量，包括极端情况（如极低带宽、极高计算资源）。对比基准（计算-only、I/O-only）合理，且对极端数据点进行了标记和排除处理，避免误导。实验客观公平，符合学术规范。

## 论文的主要结论与发现

- Cake在大多数配置下平均TTFT减少2.6×（相对于计算-only和I/O-only的较大者）。具体平均加速比：相对于I/O-only为2.23×，相对于计算-only为3.76×（排除极端不平衡场景后）。
- 计算和I/O资源平衡时（加速比接近2×），Cake效益最显著；当一方严重瓶颈时，加速比受限于较优资源。
- 序列越长，Cake相对于计算-only的加速比越大，因为后部令牌计算成本高。
- GQA和KV缓存压缩（量化）可提升I/O效率，进一步增强Cake效果。
- 自适应调度在突发非缓存请求场景下，系统吞吐量提升26%。
- Cake引入的开销极小（仅轻量级检查）。

## 优点

- **创新性**：首个系统性地并行利用计算和I/O资源进行KV缓存加载的工作，填补了该领域空白。
- **实用性**：与现有推理引擎（vLLM、LMCache）无缝集成，无需修改模型结构；自适应调度机制保障实际部署时的吞吐量。
- **理论指导**：基于计算成本随序列位置递增、I/O成本恒定的洞察，设计双向调度策略，具有理论依据。
- **实验全面**：涵盖多种硬件、模型、带宽、压缩方法、动态环境，充分验证了方法的鲁棒性和通用性。

## 不足与局限

- **实验覆盖**：仅评估了TTFT，未深入分析对端到端解码延迟或服务吞吐量的整体影响（除自适应调度实验外）。
- **偏差风险**：部分极端不平衡场景（如短序列+高计算资源+低带宽）下，Cake不如计算-only方法，但论文承认了这一点，并提出可通过回退机制改进，但未实现。
- **应用限制**：仅针对前缀缓存命中场景，对于完全未命中的计算请求，Cake不提供增益（但也不会引入额外开销）。此外，分布式环境下的兼容性仅理论讨论，未给出实证。
- **资源说明不够详细**：虽然给出了GPU型号，但未披露每次实验运行的具体耗时或训练成本（非训练任务可理解）。
- **消融实验不足**：虽然进行了多维度参数变化实验，但未系统分析双向调度策略中不同块大小、不同并行粒度对性能的具体影响（仅对比了不同块大小下的加速比，未深入解释）。

（完）
