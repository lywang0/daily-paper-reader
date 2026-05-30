---
title: "MuxServe: Flexible Spatial-Temporal Multiplexing for Multiple LLM Serving"
title_zh: "MuxServe: 灵活的多LLM服务时空复用"
authors: "Jiangfei Duan, Runyu Lu, Haojie Duanmu, Xiuhong Li, Xingcheng ZHANG, Dahua Lin, Ion Stoica, Hao Zhang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=R0SoZvqXyQ"
tags: ["query:edge-llm"]
score: 10.0
evidence: 多LLM服务框架，使用时空复用技术
tldr: MuxServe提出了一种灵活的时空复用系统用于高效的多LLM服务。其核心思想是根据LLM的流行度进行共置以复用内存资源，并利用预填充和解码阶段的特性来分离和灵活共置计算资源。系统形式化定义了复用问题，并提出了新颖的调度方法，显著提升了多LLM服务的吞吐量和效率。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-r0sozvqxyq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 873, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-r0sozvqxyq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 863, \"height\": 347, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-r0sozvqxyq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 850, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-r0sozvqxyq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 865, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-r0sozvqxyq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1784, \"height\": 596, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-r0sozvqxyq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 361, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-r0sozvqxyq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 675, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-r0sozvqxyq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 671, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-r0sozvqxyq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 886, \"height\": 733, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-r0sozvqxyq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 866, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-r0sozvqxyq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1784, \"height\": 593, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-r0sozvqxyq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 907, \"height\": 249, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-r0sozvqxyq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 831, \"height\": 1061, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-r0sozvqxyq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 850, \"height\": 762, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-r0sozvqxyq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 851, \"height\": 930, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-r0sozvqxyq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 822, \"height\": 116, \"label\": \"Table\"}]"
motivation: 现有方法难以高效服务多个LLM，因为不同LLM的流行度变化导致资源利用不均。
method: 提出MuxServe系统，通过时空复用思想，将LLM共置以复用内存，并分离预填充和解码阶段以复用计算资源。
result: 实验表明，MuxServe显著提升了多LLM服务的吞吐量和资源利用率。
conclusion: MuxServe通过灵活的复用策略有效解决了多LLM服务中的资源竞争问题。
---

## Abstract
Large language models (LLMs) have demonstrated remarkable performance, and organizations are racing to serve LLMs of varying sizes as endpoints for use-cases like chat, programming and search. However, efficiently serving multiple LLMs poses significant challenges for existing approaches due to varying popularity of LLMs. In the paper, we present MuxServe, a flexible spatial-temporal multiplexing system for efficient multiple LLM serving. The key insight behind is to colocate LLMs considering their popularity to multiplex memory resources, and leverage the characteristics of prefill and decoding phases to separate and flexibly colocate them to multiplex computation resources. MuxServe formally formulates the multiplexing problem, and proposes a novel placement algorithm and adaptive batch scheduling strategy to identify optimal colocations and maximize utilization. MuxServe designs a unified resource manager to enable flexible and efficient multiplexing. Evaluation results show that MuxServe can achieves up to $1.8\times$ higher throughput or processes $2.9\times$ more requests within $99\%$ SLO attainment. The code is available at: https://github.com/hao-ai-lab/MuxServe.

---

## 论文详细总结（自动生成）

好的，以下是对给定论文《MuxServe: Flexible Spatial-Temporal Multiplexing for Multiple LLM Serving》的详细中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

*   **核心问题**：随着大语言模型（LLM）在多种应用场景（如聊天、编程、搜索）中的普及，服务提供商需要同时部署和运行多个不同规模和版本的LLM。然而，不同LLM的流行度和请求负载存在显著差异，导致传统的**空间分区**（为每个LLM分配固定GPU组）或**时间复用**（模型在GPU上分时调度）方法效率低下。
    *   空间分区会导致热门LLM资源紧张，冷门LLM GPU闲置，造成资源浪费。
    *   时间复用忽略了LLM推理中预填充（Prefill）和增量解码（Decoding）阶段对计算资源的不同需求，导致GPU利用率不稳定，多数时间处于低谷。
*   **研究动机**：目标是设计一种更灵活、高效的LLM服务系统，以最大化集群资源利用率，提升整体吞吐量，并满足服务质量（SLO）要求。
*   **整体含义**：论文通过引入**时空复用**（Spatial-Temporal Multiplexing）的概念，将计算和内存资源的复用提升到新的维度，为多LLM服务问题提供了一种有效的解决方案。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

*   **核心思想**：
    1.  **内存复用**：根据LLM的流行度进行共置（Colocate），将低负载的LLM与高负载的LLM放在一起，从而共享GPU内存资源。
    2.  **计算复用**：利用LLM推理中“预填充”阶段计算密集型和“增量解码”阶段计算稀疏的特性，将这两个阶段的执行单元分离，并灵活地共置在同一GPU上同时执行，以填满计算资源。

*   **关键技术细节**：
    1.  **问题形式化**：将多LLM服务问题形式化为一个组合优化问题。目标是找到一个最优的**LLM单元（LLM Unit）** 分组，即一组共置在一起的LLM及其分配的GPU，以最大化整个集群的吞吐量。
    2.  **基于枚举的贪婪放置算法（Algorithm 1 & 2）**：
        *   首先，为每个LLM生成所有可能的并行配置候选（如SM数量、流水线并行度），这些配置能满足其工作负载需求。
        *   然后，枚举所有可能的设备网格组（Device Mesh Groups）。
        *   接下来，采用贪婪策略，优先将计算需求大的LLM（考虑模型规模和流行度）放置在能带来最大吞吐量提升的设备网格上。
    3.  **自适应批调度算法 - ADBS（Algorithm 3）**：
        *   在一个LLM单元内部，通过**Token块配额（Token Block Quota）** 公平地分配KV缓存资源给不同LLM，确保公平性。
        *   调度策略优先处理“预填充”任务，因为它们能更好地利用GPU计算资源。当没有“预填充”任务时，再调度“增量解码”任务，通过轮询（Round-Robin）方式执行，最大化共置机会。
        *   算法会定期调整“Token块配额”，将低利用率LLM的缓存重新分配给高需求LLM，以适应动态变化的工作负载。
    4.  **统一资源管理器**：
        *   利用NVIDIA MPS在SM粒度上动态分配计算资源给不同的“预填充”和“解码”作业，实现灵活的计算复用。
        *   将LLM权重、激活值和KV缓存分别存储在三个分区中。其中，**统一的KV缓存空间（Unified KV Cache）** 采用“头式缓存”（Head-wise Cache）设计，将KV缓存划分为细粒度的块，使得不同规模的LLM可以共享同一片物理内存，减少了内存浪费。

*   **算法流程（文字说明）**：
    1.  **离线阶段**：对于给定的LLM集合和预估工作负载，使用**枚举-贪婪放置算法**确定最优的LLM单元分组。
    2.  **在线阶段**：在每个LLM单元内，**ADBS算法**根据实时请求到达情况，动态地、公平地调度不同LLM的“预填充”和“解码”作业。统一资源管理器则负责执行这些调度决策，在GPU上灵活分配计算和内存资源。

### 3. 实验设计

*   **使用的数据集/场景**：
    *   **合成工作负载**：请求速率遵循**幂律分布**（由指数α控制流行度差异），请求内容从**ShareGPT**数据集采样。
    *   **真实工作负载**：从**ChatLMSYS**跟踪日志中采样LLM和请求，模拟实际服务场景。
*   **Benchmark**：
    *   **模型**：基于**LLaMA**架构的多种尺寸模型，涵盖4B到70B参数。
    *   **LLM数量**：在合成负载测试中，共服务19个不同尺寸的LLM（12个4B-8B, 4个8B-21B, 2个21B-41B, 1个41B-70B）。在真实负载测试中，服务16个LLM。
*   **对比方法**：
    1.  **空间分区（Spatial Partitioning）**：每个LLM使用独立的vLLM实例在固定GPU组上服务。
    2.  **时间复用（Temporal Multiplexing）**：类似AlpaServe，将多个LLM共置，但按照先来先服务（FCFS）的时间片方式调度。

### 4. 资源与算力

*   **GPU**：4节点集群，每个节点配备**8块NVIDIA A100 (80GB) GPU**，总共**32块GPU**。
*   **网络**：节点内通过600GB/s NVLink连接，节点间通过200Gbps InfiniBand连接。
*   **训练时长**：论文未明确说明训练或预计算（如配置枚举）所需的时长。

### 5. 实验数量与充分性

*   **实验数量**：论文进行了多组实验，包括：
    *   **端到端吞吐量和SLO达成率实验**：在5种不同流行度（α值）和多个负载速率下，对比了三种方法（空间、时间、MuxServe）。
    *   **真实负载实验**：在不同平均请求速率下，对比了三种方法。
    *   **三个消融实验**：
        1.  放置算法（与“按内存大小贪婪放置”对比）。
        2.  ADBS调度算法（与FCFS和Round-Robin对比）。
        3.  统一资源管理器（分步启用计算和内存管理进行对比）。
*   **充分性与公平性**：
    *   实验设计较为全面，覆盖了合成和真实场景，并进行了详尽的消融分析，验证了每个核心组件的有效性。
    *   对比基线（空间分区和时间复用）是当前主流或相关的代表性工作，对比公平。
    *   使用了不同的流行度分布和负载强度，考察了系统的鲁棒性和适用范围。
    *   结论明确，实验结果与论文提出的核心思想一致，充分支持了其论点。

### 6. 论文的主要结论与发现

*   MuxServe在吞吐量和SLO达成率上显著优于空间分区和时间复用基线。
    *   **吞吐量**：最高可提升**1.8倍**。
    *   **SLO达成率**：在99% SLO约束下，可处理多达**2.9倍**的请求。
*   当LLM之间的**流行度差异越大**（即α值越大），MuxServe相对于其他方法的优势越明显，因为它能更有效地将热门与冷门LLM共置以复用内存。
*   **自适应批调度算法（ADBS）** 能更公平地分配KV缓存资源，其token块使用分布与请求负载分布更吻合，从而获得比FCFS和Round-Robin更高的吞吐量。
*   **统一资源管理器**的各个组成部分（计算复用和统一内存管理）都对最终性能有积极贡献，其中“解耦预填充与解码”带来的性能提升最为显著。

### 7. 优点

*   **问题新颖性**：首次系统性地探索并形式化了多LLM服务中的时空复用问题，提出了一种有效的解决方案框架。
*   **方法有效性**：基于预填充和解码阶段特性的核心洞察，设计了高效的放置和调度算法，直击现有方法（时间复用）的痛点。
*   **系统完整性**：将问题形式化、算法设计、系统实现（统一资源管理器）紧密结合起来，形成了完整、可落地的系统。
*   **实验充分性**：通过合成和真实负载的全面实验，并辅以细致的消融研究，有力证明了方法的有效性和各个组件的贡献。
*   **工程贡献**：提出的头式缓存（Head-wise Cache）和自适应配额调整机制，巧妙地解决了多LLM共享内存时的高效和公平性问题。

### 8. 不足与局限

*   **实验覆盖**：
    *   所有实验均在特定硬件（32x A100 80GB）和网络（200Gbps IB）上进行，结果的可推广性可能受限于此。在不同GPU（如H100）或更慢网络环境下的性能有待验证。
    *   主要评估了LLaMA模型，对其他架构（如GPT、PaLM）的适用性未明确讨论。
    *   假设工作负载可知或可从历史数据预估。对于突发性极强的、完全不可预测的负载，其表现可能不及预期。
*   **潜在偏差风险**：论文中吞吐量SLO达成率（图5）在低负载或SLO宽松时，MuxServe并未表现出压倒性优势，甚至在某些点略低于空间分区。这表明其优势主要体现在高负载或严格SLO场景下，对于追求极致低延迟的场景，可能存在权衡。
*   **应用限制**：
    *   MuxServe依赖于NVIDIA MPS技术，这限制了其在非NVIDIA硬件上的部署。
    *   系统的复杂性（全局调度器、多个进程、CUDA IPC通信）可能引入额外的性能开销和部署运维难度，论文未详细分析这些开销。
    *   系统优化目标是最大化总吞吐量和SLO，对于请求间的公平性（如防止某个LLM的某次长请求被频繁抢占）的讨论相对有限。
    *   论文未讨论如何优雅地处理新LLM的加入或现有LLM的在线更新，这对在线服务系统是重要的实际考量。

（完）
