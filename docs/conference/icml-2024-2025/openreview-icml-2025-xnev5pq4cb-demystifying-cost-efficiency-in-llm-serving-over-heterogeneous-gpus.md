---
title: Demystifying Cost-Efficiency in LLM Serving over Heterogeneous GPUs
title_zh: 揭示异构GPU上LLM服务的成本效率
authors: "YOUHE JIANG, Fangcheng Fu, Xiaozhe Yao, Guoliang HE, Xupeng Miao, Ana Klimovic, Bin CUI, Binhang Yuan, Eiko Yoneki"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=xnEv5pq4cB"
tags: ["query:edge-llm"]
score: 9.0
evidence: 异构GPU上的LLM服务成本效率研究
tldr: 本文系统研究了在异构GPU资源上服务LLM的成本效率问题。通过全面基准测试，发现不同GPU类型具有不同的计算和内存特性，可以与多样化请求的资源需求相匹配。通过精心确定请求与GPU的分配，可以大幅优化LLM服务的成本效率，为云平台上利用异构GPU提供了实践指导。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 816, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 825, \"height\": 316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1764, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1750, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 844, \"height\": 676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 846, \"height\": 295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 841, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 847, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 830, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 824, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1764, \"height\": 585, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1750, \"height\": 1200, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1745, \"height\": 1200, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 875, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 865, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 840, \"height\": 378, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 853, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 832, \"height\": 671, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 769, \"height\": 159, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 960, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 916, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 953, \"height\": 384, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 883, \"height\": 204, \"label\": \"Table\"}]"
motivation: 现有LLM服务主要依赖同构GPU，导致成本效率低下，因为不同请求的资源需求各异。
method: 通过全面基准测试，分析异构GPU的特性，提出按请求资源需求匹配GPU类型的优化策略。
result: 实验表明，异构GPU分配可显著提升LLM服务的成本效率。
conclusion: 利用异构GPU能够更好地满足多样化请求的需求，优化服务成本。
---

## Abstract
Recent advancements in Large Language Models (LLMs) have led to increasingly diverse requests, accompanied with varying resource (compute and memory) demands to serve them. However, this in turn degrades the cost-efficiency of LLM serving as common practices primarily rely on homogeneous GPU resources. In response to this problem, this work conducts a thorough study about serving LLMs over heterogeneous GPU resources on cloud platforms. The rationale is that different GPU types exhibit distinct compute and memory characteristics, aligning well with the divergent resource demands of diverse requests. Particularly, through comprehensive benchmarking, we discover that the cost-efficiency of LLM serving can be substantially optimized by meticulously determining GPU composition, deployment configurations, and workload assignments. Subsequently, we design a scheduling algorithm via mixed-integer linear programming, aiming at deducing the most cost-efficient serving plan under the constraints of price budget and real-time GPU availability. Remarkably, our approach effectively outperforms homogeneous and heterogeneous baselines under a wide array of scenarios, covering diverse workload traces, varying GPU availablilities, and multi-model serving. This casts new light on more accessible and efficient LLM serving over heterogeneous cloud resources.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **背景**：大语言模型（LLM）服务日益多样化，不同请求在输入/输出长度上差异显著（例如短输入长输出、长输入短输出），导致计算和内存需求高度异质。然而，当前主流实践仍依赖同构GPU集群（如全部使用A100或H100），难以匹配这种资源需求差异，造成资源浪费和成本效率低下。
- **核心问题**：是否可以利用异构GPU资源（不同GPU类型具有不同的算力、显存带宽和容量）来提升LLM服务的成本效率？如果可以，如何系统性地优化GPU组成、部署配置和工作负载分配？
- **意义**：为云平台上更经济、高效地部署LLM服务提供新思路，推动LLM服务的可及性和可持续性。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：通过**协同优化三个关键因素**来最大化成本效率：
  1. **GPU组成**：选择何种类型、多少数量的GPU组成集群。
  2. **部署配置**：每个模型副本采用何种并行策略（数据并行DP、张量并行TP、流水线并行PP及其组合）。
  3. **工作负载分配**：将不同请求按资源需求分发到最合适的GPU副本上。
- **关键技术细节**：
  - **全面基准测试**：在6种GPU（A6000, A40, L40, A100, H100, 4090）上，对Llama3-8B和Llama3-70B模型，测试9种不同输入/输出长度组合的工作负载，测量每美元吞吐量和各百分位延迟的总成本。发现：数据中心GPU（H100/A100）擅长计算密集型任务；工作站GPU（A40/A6000/L40）在内存密集型任务上性价比高；消费级GPU（4090）适合小模型。
  - **调度算法**：基于**混合整数线性规划（MILP）**，在给定预算和实时GPU可用性约束下，联合优化GPU组成、部署配置和工作负载分配，最小化整体完成时间（makespan）。MILP变量包括：每种配置的副本数（整数）、工作负载分配比例（连续）。约束包括：预算、GPU可用性、内存限制、连通性等。
  - **加速优化**：引入二分搜索、剪枝、近似可行性检查（背包近似）等方法，将搜索时间降低约4倍，且性能损失小于1%。
  - **多模型扩展**：支持同时服务多个LLM（如Llama3-8B和Llama3-70B），通过引入模型维度统一优化。

## 3. 实验设计
- **数据集/场景**：
  - 三个真实工作负载跟踪：瑞士AI中心（1个月数据）、Azure-Trace（生产日志）、WildGPT数据集。
  - 每个跟踪包含9种工作负载类型，按输入/输出长度长短组合划分。
- **基准线**：
  - **同构基线**：仅租用H100、A6000或4090一种GPU，并在同构集群上优化部署配置和工作负载分配。
  - **异构基线**：与HexGen（最优异构框架）和Helix（基于最大流的调度）对比。
- **评估指标**：系统吞吐量（req/s）、各百分位延迟（P10-P100）。
- **对比方式**：在4种随机实时GPU可用性（表4）和3种预算水平（15/30/60 $/h）下进行端到端实验。

## 4. 资源与算力
- 论文未明确给出总GPU数量或训练时长。实验在云平台（Vast.ai）上租赁GPU进行推理服务，使用了6种GPU类型（A6000, A40, L40, A100, H100, 4090），每种类型数量随预算和可用性变化（最大可达32块）。
- 模型为Llama3-8B和Llama3-70B，推理服务使用vLLM框架。未说明单独训练或预训练过程。

## 5. 实验数量与充分性
- **组实验数量**：覆盖9种工作负载×2种模型×6种GPU×多种配置，生成大量基准数据；端到端实验在3个跟踪×4种可用性×3个预算下进行，共约36组主实验；还包括消融实验（图8）、与HexGen/Helix对比（图7、表3）、算法效率实验（图9）、多模型实验（图10）、预算敏感性分析（图16）、在线重规划实验（表7）等。
- **充分性与公平性**：
  - 实验设计较为全面，覆盖了同构/异构、不同预算、不同可用性、单模型/多模型场景。
  - 对同构基线也使用调度算法优化了配置，保证了对比公平。
  - 消融实验分别关闭GPU组成、部署配置、工作负载分配优化，验证了各部分贡献。
  - 与HexGen对比时，考虑了其均匀组成和最优组成两种设置，确保公正。
  - 不足：在线重规划仅做演示性实验，未深入讨论动态调度开销；所有实验基于离线模拟和一次性基准测试，未在真实在线服务系统中长期运行验证。

## 6. 主要结论与发现
- **异构GPU可显著提升成本效率**：在相同预算下，相比最优同构基线，吞吐量最高提升41%，平均提升20%；延迟最高降低54%，平均降低20%。
- **三个优化因素均不可或缺**：消融实验显示，关闭任一优化会导致吞吐量下降15%~34%，证明GPU组成、部署配置、工作负载分配需协同优化。
- **算法高效可扩展**：二分搜索+剪枝将MILP求解时间降低约4倍，且性能损失小于1%，适用于中等规模集群（最多48块GPU）。
- **多模型场景同样有效**：在同时服务Llama3-8B和Llama3-70B时，性能提升达35%。
- **竞争性超越现有方法**：优于HexGen（14%~18%）和Helix（25%~35%）。

## 7. 优点
- **系统性**：首次将GPU组成、部署配置、工作负载分配三个维度联合优化，形成完整解决方案。
- **实用性**：考虑真实云环境中的预算限制和实时GPU可用性，贴合实际部署需求。
- **可扩展性**：通过二分搜索、剪枝等启发式方法，将MILP求解时间控制在可接受范围（约15秒内），便于在线重规划。
- **实验设计严谨**：多数据集、多基线、消融实验、敏感性分析，验证充分。
- **贡献清晰**：提供基准测试洞察、可复现的MILP公式、开源潜力（未明确承诺但可推断）。

## 8. 不足与局限
- **静态假设**：主要面向离线批量处理场景，假设工作负载可预知且同时到达。在线动态调度仅作初步讨论，未实现完整自适应系统。
- **MILP可扩展性瓶颈**：当GPU总数超过100或模型类型超过5种时，求解时间可能变得不可接受（论文未测试更大规模）。
- **基准测试覆盖**：仅测试了Llama3系列，未覆盖其他架构（如Mixtral、DeepSeek）或量化/稀疏化模型。
- **未考虑KV cache管理**：工作负载分配未显式考虑KV cache的内存占用和复用（如PagedAttention），可能低估实际内存压力。
- **忽略网络异构性**：仅简单限制TP必须在单机内，未深入优化跨机网络瓶颈（如PP阶段的通信）。
- **公平性局限**：与HexGen/Helix对比时，未在完全相同硬件环境下运行（论文为模拟，但声称基于真实测量），可能存在微小偏差。
- **在线重规划风险**：重规划可能导致服务中断或请求迁移成本，论文未量化。

（完）
