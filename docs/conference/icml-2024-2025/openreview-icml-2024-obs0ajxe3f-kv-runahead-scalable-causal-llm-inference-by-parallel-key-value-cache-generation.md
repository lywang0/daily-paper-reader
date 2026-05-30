---
title: "KV-Runahead: Scalable Causal LLM Inference by Parallel Key-Value Cache Generation"
title_zh: KV-Runahead：通过并行键值缓存生成实现可扩展的因果LLM推理
authors: "Minsik Cho, Mohammad Rastegari, Devang Naik"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=OBs0AjXE3F"
tags: ["query:edge-llm"]
score: 6.0
evidence: 并行KV缓存生成加速预填充阶段
tldr: KV-Runahead通过多进程并行生成KV缓存来加速LLM推理的预填充阶段，显著缩短首Token生成时间。该方法利用因果注意力的特性，最小化计算和通信开销，为高效LLM推理提供了一种可扩展的并行化方案。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 896, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 795, \"height\": 281, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 872, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 843, \"height\": 285, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 842, \"height\": 285, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1624, \"height\": 922, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1620, \"height\": 926, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 880, \"height\": 282, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 802, \"height\": 735, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1790, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1795, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1789, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1208, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 575, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-obs0ajxe3f/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1799, \"height\": 402, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-obs0ajxe3f/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1347, \"height\": 1117, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-obs0ajxe3f/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1328, \"height\": 679, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-obs0ajxe3f/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 889, \"height\": 333, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-obs0ajxe3f/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 835, \"height\": 419, \"label\": \"Table\"}]"
motivation: LLM推理的预填充阶段因顺序计算成为瓶颈，而解码阶段因KV缓存更快。
method: 提出KV-Runahead，通过多进程并行填充KV缓存来加速预填充阶段，并利用因果注意力减少冗余计算。
result: 实验表明KV-Runahead有效缩短了首Token生成时间，提升了推理吞吐量。
conclusion: KV-Runahead为LLM推理提供了一种高效的并行化方法，可集成到推理框架中。
---

## Abstract
Large Language Model or LLM inference has two phases, the prompt (or prefill) phase to output the first token and the extension (or decoding) phase to the generate subsequent tokens. In this work, we propose an efficient parallelization scheme, KV-Runahead to accelerate the prompt phase. The key observation is that the extension phase generates tokens faster than the prompt phase because of key-value cache (KV-cache). Hence, KV-Runahead parallelizes the prompt phase by orchestrating multiple processes to populate the KV-cache and minimizes the time-to-first-token (TTFT). Dual-purposing the KV-cache scheme has two main benefits. First, since KV-cache is designed to leverage the causal attention map, we minimize computation and computation automatically. Second, since it already exists for the extension phase, KV-Runahead is easy to implement. We further propose context-level load-balancing to handle uneven KV-cache generation (due to the causal attention) and to optimize TTFT. Compared with an existing parallelization scheme such as tensor or sequential parallelization where keys and values are locally generated and exchanged via all-gather collectives, our experimental results demonstrate that KV-Runahead can offer over 1.4× and 1.6× speedups for Llama 7B and Falcon 7B respectively.

---

## 论文详细总结（自动生成）

# KV-Runahead 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）推理过程中，**预填充阶段（Prompt Phase）** 生成第一个Token的时间（Time-to-First-Token, TTFT）过长，成为用户交互体验的瓶颈。预填充阶段需处理长用户上下文，计算密集型（复杂度为O(C²)，C为上下文长度），而解码阶段因键值缓存（KV-cache）加速而更快。
- **研究背景**：现有并行化方案（如张量并行、序列并行）未充分利用因果注意力的特性，导致计算和通信存在冗余（例如全规约All-gather操作产生额外开销，且强制全局同步）。作者旨在设计一种专门针对LLM因果解码器的高效并行化方法，以降低TTFT。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：**KV-Runahead** 将解码阶段已有的KV-cache机制“双用途”化——在预填充阶段利用多进程并行生成KV-cache，为最后一个进程提供完整的KV-cache，从而加速首Token生成。由于KV-cache天然遵循因果掩码（只计算下三角），因此自动避免了上三角的过度计算。
- **关键技术细节**：
  - **上下文级负载均衡（Context-Level Load-Balancing）**：由于因果依赖，早期进程需等待前序进程的KV-cache，后期进程计算量大。因此采用**非均匀划分**上下文（partition）以平衡各进程等待时间与计算时间，最小化TTFT。划分通过**离线分层网格搜索**（Hierarchical Grid Search）获得，并构建查找表；推理时对未知长度进行线性插值预测。
  - **异步点对点通信**：KV-Runahead使用点对点异步send/recv操作传递KV-cache，替代TSP中的全局同步All-gather，减少了通信量（总通信量仅为TSP的一半左右）且对网络波动更鲁棒。
  - **实现简单**：只需在现有LLM注意力模块中插入recv/send及KV-cache拼接操作，无需修改模型架构。
- **公式与算法流程**：
  - 理论下界：TTFT*(p) = α [C²/2 (1/p + 1/p²)]，表明对于很长的上下文存在超线性可扩展性（例如2进程超过2倍加速）。
  - 通信量对比：TSP总通信量 Net_tsp = (p-1)C；KV-Runahead总通信量 Net_kvr = (p-1)C/2。
  - 执行流程示例：给定p个进程，每个进程计算自己分片内的(Q, K, V)；进程i从i-1接收KV-cache并拼接；进程i将更新后的KV-cache发送给i+1；最后各进程计算注意力并输出。

## 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **数据集/场景**：未指定特定数据集，而是采用**合成长上下文**（长度为1k至16k tokens）进行基准测试，聚焦TTFT指标。同时也测试了多种模型（Llama 7B/13B/30B, Falcon 1B/7B）以及不同GPU数量（2/4/8）和网络带宽环境（高带宽300GB/s，低带宽10GB/s，以及噪声网络）。
- **Benchmark**：主要衡量**Time-to-First-Token (TTFT)**，同时比较了可扩展性（与理论下界对比）和鲁棒性（噪声网络下的TTFT退化）。
- **对比方法**：
  - **Tensor/Sequence Parallelization (TSP)**：代表现有SOTA并行化方案（张量并行或序列并行），使用均匀划分上下文和All-gather通信。
  - **KV-Runahead变体**：
    - **KVR-E**：均匀上下文划分（无负载均衡）；
    - **KVR-S**：通过分层网格搜索得到最优划分；
    - **KVR-P**：从查找表线性插值预测划分。

## 4. 资源与算力

- 所有实验在**单节点**上进行，配备 **8× NVIDIA A100 GPU**。
- 使用 **FP16** 精度，**PyTorch 2.0** 和 **NCCL 2.14**。
- 高低带宽环境：高带宽为300GB/s（默认NVLink）；低带宽通过关闭高速CUDA-direct链路模拟为10GB/s。
- **未明确说明训练时长**，但提到离线查找表生成耗时约33小时（针对8 GPU、16k上下文的情况），且可并行化加速。

## 5. 实验数量与充分性

- **实验组数**：较为充分。包括：
  - 两种模型（Llama 7B, Falcon 7B）在不同上下文长度（1k~16k）和GPU数量（2/4/8）下的TTFT对比（图8、图9）。
  - 额外扩展实验：Llama 13B、Llama 30B、Falcon 1B及Llama 7B的MQA/GQA变体（附录表1、表2）。
  - 低带宽10GB/s和噪声网络场景（图11）。
  - 负载均衡验证（图10，插值预测与搜索最优的偏差<1.3%）。
  - 并行推理效益分析（附录表3，不同带宽和上下文下的适用性）。
- **充分性与公平性**：
  - 对比方法TSP是现有公开并行方案，KV-Runahead与其公平比较。
  - 消融实验区分了均匀划分（KVR-E）和最优划分（KVR-S），以及预测划分（KVR-P）。
  - 实验覆盖了不同模型规模、上下文长度、GPU数量、网络带宽，结论较稳健。
  - 但未提及在真实应用场景（如RAG、摘要等）中的端到端延迟测试，也**未包含与流水线并行等方法对比**。

## 6. 论文的主要结论与发现

- KV-Runahead（KVR-S）在所有测试场景中**一致优于TSP**：在Llama 7B上最高加速1.42×（4 GPU/12k上下文，300GB/s），在Falcon 7B上最高加速1.63×（8 GPU/8k上下文）。
- 在低带宽（10GB/s）环境下加速更显著（如1.79×），因为减少了通信量。
- 负载均衡对TTFT改善重要：均匀划分（KVR-E）在某些短上下文时反而可能不如TSP，而KVR-S始终优于TSP。
- 点对点异步通信使KV-Runahead对非均匀带宽更鲁棒（噪声下TSP最多退化11.8%，KVR仅退化2.7%）。
- 通过插值预测的划分（KVR-P）与搜索最优的偏差<1.3%，证明查找表方法实用。
- 理论上，对于长上下文存在超线性可扩展性，KV-Runahead更接近理论下界。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：巧妙复用KV-cache机制实现并行预填充，思路新颖且易于实现。
- **效率高**：消除冗余计算和通信，降低TTFT；异步通信避免全局同步。
- **鲁棒性**：点对点通信对网络波动容忍度高，适合异构或云环境。
- **负载均衡方法**：离线分层网格搜索+在线插值预测，工程实用性强。
- **实验全面**：覆盖多种模型、上下文长度、GPU数量、网络条件，并包含消融和鲁棒性分析。

## 8. 不足与局限

- **实验覆盖的局限性**：
  - 未在真实长上下文应用（如对话、RAG）中测试端到端延迟或吞吐量。
  - 仅与TSP对比，未与流水线并行、环注意力等其他并行方案对比。
  - 仅测试了单节点多GPU，未涉及跨节点分布式场景。
- **实现依赖**：需要KV-cache在物理连续内存中管理（如vLLM支持），否则需要额外拷贝。
- **查找表生成开销**：离线搜索（尤其对于多GPU和大上下文）耗时较高（约33小时/配置），且需目标硬件实测。
- **短上下文劣势**：当上下文很短（<4k）且GPU数多时，并行化收益被通信开销抵消，KVR-S仍可提升但幅度较小。
- **未讨论对解码阶段的影响**：仅聚焦预填充阶段，未分析KV-Runahead对整体推理流水线（包括解码阶段TPOT）的潜在影响。

（完）
