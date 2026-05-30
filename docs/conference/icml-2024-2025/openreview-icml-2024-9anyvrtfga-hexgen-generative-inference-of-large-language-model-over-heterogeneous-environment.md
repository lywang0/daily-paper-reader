---
title: "HexGen: Generative Inference of Large Language Model over Heterogeneous Environment"
title_zh: HexGen：异构环境下的大规模语言模型生成推理
authors: "YOUHE JIANG, Ran Yan, Xiaozhe Yao, Yang Zhou, Beidi Chen, Binhang Yuan"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=9ANyvRtFGa"
tags: ["query:edge-llm"]
score: 9.0
evidence: 异构分布式LLM推理引擎
tldr: 针对大规模语言模型在异构环境下的生成推理开销问题，提出HexGen分布式推理引擎。通过支持张量并行和流水线并行的不对称分区，使模型可灵活部署于多种GPU构成的异构网络。结合基于约束优化的调度算法，有效降低单数据中心集中推理的成本。实验验证了其在不同异构集群上的性能优势。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-9anyvrtfga/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 816, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9anyvrtfga/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1731, \"height\": 796, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9anyvrtfga/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 833, \"height\": 529, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9anyvrtfga/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 829, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9anyvrtfga/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 833, \"height\": 529, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9anyvrtfga/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 586, \"height\": 276, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-9anyvrtfga/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 828, \"height\": 306, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-9anyvrtfga/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1777, \"height\": 389, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9anyvrtfga/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1365, \"height\": 1078, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9anyvrtfga/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-9anyvrtfga/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 786, \"height\": 588, \"label\": \"Table\"}]"
motivation: 单个数据中心推理成本高，异构和跨数据中心部署可降低成本。
method: 提出HexGen引擎，支持不对称张量并行和流水线并行分区，并采用约束优化调度算法。
result: 在异构网络和多样GPU上实现高效推理，降低成本。
conclusion: HexGen有效利用异构资源，提升LLM推理的经济性。
---

## Abstract
Serving generative inference of the large language model is a crucial component of contemporary AI applications. In this paper, our focus lies in deploying such services in a heterogeneous and cross-datacenter setting to mitigate the substantial inference costs typically associated with a single centralized datacenter. Towards this end, we propose HexGen, a flexible distributed inference engine that uniquely supports the asymmetric partition of generative inference computations over both tensor model parallelism and pipeline parallelism, which allows for effective deployment across diverse GPUs interconnected by a fully heterogeneous network. We further propose a sophisticated scheduling algorithm grounded in constrained optimization that can adaptively assign asymmetric inference computation across the GPUs to fulfill inference requests while maintaining acceptable latency levels. We conduct an extensive empirical study to evaluate the efficiency of HexGen by serving the state-of-the-art Llama-2 (70B) model. The experimental results suggest that HexGen can choose to achieve up to $2.3\times$ lower latency deadlines or tolerate up to $4\times$ more traffic request rates compared with the homogeneous baseline given the same budget.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：大规模语言模型（LLM）的生成推理服务通常部署在单一同质化的数据中心，使用昂贵的高性能GPU，导致推理成本极高，限制了技术的普及。论文探索在**异构、跨数据中心**的环境下部署LLM推理，以降低成本并利用更经济的计算资源（如竞价实例、服务器计算、志愿者GPU等）。
- **研究动机**：异构环境带来两大挑战：① GPU算力异构性（不同型号的峰值FLOPS、显存带宽、显存容量差异），现有推理框架要求对称并行配置，无法充分利用异构GPU能力；② GPU连接异构性（NVLink/PCIe/RDMA到跨地域慢速网络），导致延迟和带宽差异巨大，需要更灵活的调度策略。
- **整体含义**：提出HexGen系统，通过支持**非对称的张量模型并行（TP）和流水线并行（PP）**，以及基于约束优化的调度算法，在异构GPU集群上实现经济高效的LLM推理服务，验证了相同预算下性能可超越同质化数据中心方案。

## 2. 方法论：核心思想、关键技术细节
### （1）核心思想
- 允许**每个流水线阶段分配不同数量的Transformer层和不同的张量并行度**，以适配GPU算力异构性；同时调度算法优化跨GPU的分配，在通信开销和计算负载间取得平衡。

### （2）关键技术细节

#### a. 非对称并行实现
- 初始化时为每个流水线阶段配置独立的TP度数和层数；每个阶段选举一个“leader GPU”，负责与前/后阶段通信；leader接收激活后广播给组内其他GPU执行TP计算。
- 修改FlashAttention框架，集成新的流水线并行设计。

#### b. 形式化调度问题
- 定义设备集 \( D \)，通信矩阵 \( A \)（延迟）和 \( B \)（带宽），模型总层数 \( L \)；目标是找到最优分配 \( \sigma \)，最大化服务等级目标（SLO）达标率，同时满足每个GPU的显存约束。
- 代价函数包括计算代价（考虑参数扫描和矩阵乘）、TP通信代价（使用BSP模型）、PP通信代价（使用最快连接），以及显存约束（参数、KV cache、激活缓存）。

#### c. 两阶段优化算法
- **阶段1 – 流水线内布局优化**：给定一个GPU子集（一个流水线组），使用动态规划（DP）找到最优的阶段划分和TP度数分配。DP递归枚举每阶段使用的GPU类型数量，时间复杂度 \( O(S_i \cdot \prod_{k=1}^{N_T} \#_k) \)（假定同类型GPU在同一机器上），比暴力枚举 \( 2^{|d|} \) 高效。
- **阶段2 – 全局遗传算法**：在全局GPU集上搜索最优划分（多个独立流水线组）。初始化用K-means聚类，定义三种变异操作（合并、分裂、交换），并加入早期剪枝（显存不足直接淘汰）。每个变异生成的子代通过阶段1的DP确定最优布局，并用模拟器（AlpaServe）估计SLO达标率。

#### d. 公式摘要（文字说明）
- 计算代价：每层TP群组中，扫描参数的时间 = \( 12H^2 B_{type} s_{out}^t / (|d_{i,j}| m_d) \)，矩阵乘时间 = \( 24 b_t (s_{in}^t + s_{out}^t) H^2 / (|d_{i,j}| c_d) \)。
- TP通信代价：每层两个AllReduce，按ReduceScatter和AllGather两个超步骤建模。
- PP通信代价：阶段间点对点通信，使用最小延迟和带宽的链路。
- 显存约束：参数、KV cache、激活缓存之和 ≤ GPU显存。

## 3. 实验设计
- **模型**：Llama-2 70B（70亿参数），使用真实世界提示集（Lmsys Chatbot Arena Conversations）。
- **场景与设置**：
  - 同质化基线：2台AWS p4d.24xlarge（每台8×A100-40G，$65.54/h），运行FlashAttention（标准同质化推理）。
  - 异构全预算：从FluidStack租赁多个GPU组合（2×3090Ti×8（冰岛）、2×3090Ti×3（挪威）、1×A5000×8（内华达）、2×A6000×8（伊利诺伊）、1×A5000×8（伊利诺伊）、1×A40×4（伊利诺伊），总预算$65.04/h）。
  - 异构半预算：仅用2×3090Ti×8（冰岛）、2×3090Ti×3（挪威）、1×A5000×8（内华达），预算$29.6/h。
- **对比方法**：
  - 同质化基线：FlashAttention（同质数据中心）。
  - 异构基线：Petals（当前最先进的去中心化推理系统）；HuggingFace-TGI（同质化下的先进推理服务）。
  - 消融：HexGen去掉非对称并行（symmetric版本）、随机变异调度算法、仅初始化的分配。
- **评价指标**：SLO达标率（请求在给定延迟阈值内完成的比例），测量不同SLO尺度（相对于A100执行延迟的倍数）和不同请求率（0.125-10 req/s）下的表现。
- **工作负载生成**：采用泊松过程模拟请求到达，输入长度32/64/128 tokens，输出长度32/64/128 tokens。

## 4. 资源与算力
- **同质化基线**：2台AWS p4d.24xlarge，每台8×NVIDIA A100-40G，共16块A100。
- **异构全预算**：约58块GPU（型号包括3090Ti、A5000、A6000、A40），分布于冰岛、挪威、内华达、伊利诺伊等多个数据中心。
- **异构半预算**：约22块GPU（3090Ti×16 + A5000×8）。
- **训练/推理时长**：论文未明确说明具体运行小时数，仅提及每次调度搜索耗时2.1分钟（全预算）和1.5分钟（半预算）。

## 5. 实验数量与充分性
- **实验数量**：大量实验覆盖多种输出长度（32/64/128）、多种请求率（0.125-10 req/s）、多个SLO尺度（8-90倍基准延迟）。共生成约30+个子图（如图2、3、4、5、7），每个子图显示不同参数组合下的SLO达标率曲线。
- **消融实验**：比较HexGen vs. 无对称并行版本（symmetric）、半预算版本、随机初始化版本、随机变异版本。
- **动态实验**：模拟4个GPU离线，测试HexGen重新调度后的性能（图4）。
- **成本模型验证**：微基准测试对比估计值与实际执行时间（表3），误差在可接受范围内。
- **充分性**：实验设计较为全面，覆盖了同质/异构、全预算/半预算、不同并行策略、静态/动态场景，且与两种最先进基线（Petals、TGI）对比，结论有说服力。但缺少对更大模型（如Falcon-180B）或多模型并发推理的验证。

## 6. 主要结论与发现
- **成本效益**：相同预算下，HexGen（异构全预算）相比同质化FlashAttention可降低延迟上限**最高2.3倍**（平均1.5倍），或承受**最高4倍**的请求率（平均2倍）。即使预算减半，HexGen仍能达到与同质化基线相近的性能。
- **非对称并行效果**：相比对称并行版本，HexGen可降低延迟上限**最高1.8倍**，承受**最高2倍**的请求率。
- **与Petals对比**：HexGen（半预算）比Petals降低延迟上限**最高3.5倍**，承受请求率**最高10倍**。
- **与TGI对比**：HexGen（全预算）与TGI（同质数据中心）性能基本持平，甚至略优（延迟低1.25倍）。
- **调度算法有效性**：所提遗传算法收敛快（2-1.5分钟），相比随机变异提高SLO达标率约26%；估计的SLO达标率与实际值接近（92% vs 94%）。
- **动态适应性**：部分GPU离线后重调度，性能下降很小，仍远优于Petals。

## 7. 优点
- **系统设计**：首个支持**完全非对称TP+PP**的生成推理引擎，能灵活适配异构GPU计算能力和网络带宽。
- **调度算法**：将复杂调度问题分解为两阶段（DP+遗传算法），有效降低搜索复杂度，且提供可证明的显存约束。
- **成本效益突出**：利用异构低价GPU可获得甚至超过同质化高性能GPU集群的推理性能，显著降低部署成本。
- **端到端实现**：基于FlashAttention修改并集成libP2P通信，具备实际部署能力。
- **实验全面**：对比多种基线，包含消融、动态场景、成本模型验证，结论可靠。

## 8. 不足与局限
- **未集成高级批处理策略**：当前版本不支持动态批处理（如连续批处理），而同质化系统（如TGI）已具备此功能，限制了HexGen在同等条件下发挥全部潜力。
- **静态调度假设**：调度算法只在部署时运行一次；虽然支持重调度，但对于高频动态加入/退出GPU的场景，反复重搜索可能带来额外开销（论文中仅测试了4 GPU离线，未测试大规模动态变化）。
- **成本模型简化**：计算代价模型忽略了一些非矩阵操作（如激活函数、LayerNorm），通信模型采用BSP，可能低估实际延迟（尤其对于超慢速跨洲连接）。
- **实验规模有限**：仅测试Llama-2 70B一个模型，未验证更大模型（如Falcon-180B）或多模型并发场景；异构GPU类型数有限（4种），未真正覆盖极多类型。
- **公平性**：同质化基线使用FlashAttention，但未使用其可能集成的批处理优化（如PagedAttention），可能略微低估同质化系统的性能。此外，异构环境中的网络条件（UDP打洞实现的VPN）可能与实际生产环境有差异。
- **应用限制**：要求所有GPU服从统一调度（需有协调器），完全去中心化场景下（如志愿者GPU）的信任和安全性问题未讨论。

（完）
