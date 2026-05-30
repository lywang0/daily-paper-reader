---
title: Efficient LLM Scheduling by Learning to Rank
title_zh: 通过学习排序实现高效LLM调度
authors: "Yichao Fu, Siqi Zhu, Runlong Su, Aurick Qiao, Ion Stoica, Hao Zhang"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=wlLjYl0Gi6"
tags: ["query:edge-llm"]
score: 8.0
evidence: 利用学习排序优化LLM服务系统的调度
tldr: LLM服务中输出长度未知导致FCFS调度效率低，本文发现可通过学习排序预测请求相对长度，从而近似短作业优先调度。作者开发的新型调度器显著减少了队头阻塞，提升吞吐量和服务质量。该工作直接针对LLM服务框架的核心调度问题，对边缘端的LLM serving有指导意义。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-wlljyl0gi6/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1394, \"height\": 211, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wlljyl0gi6/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1453, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wlljyl0gi6/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1458, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wlljyl0gi6/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1319, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wlljyl0gi6/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1317, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wlljyl0gi6/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 891, \"height\": 693, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-wlljyl0gi6/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 1235, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-wlljyl0gi6/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-wlljyl0gi6/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1420, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-wlljyl0gi6/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1414, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-wlljyl0gi6/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1234, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-wlljyl0gi6/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 688, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-wlljyl0gi6/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 393, \"height\": 487, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-wlljyl0gi6/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 539, \"height\": 173, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-wlljyl0gi6/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 565, \"height\": 148, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-wlljyl0gi6/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 532, \"height\": 146, \"label\": \"Table\"}]"
motivation: LLM推理中输出长度未知导致FCFS调度效率低下，需要更智能的调度策略。
method: 提出基于学习排序的调度器，利用排名信息近似最短作业优先。
result: 减少队头阻塞，显著提升系统吞吐量。
conclusion: 学习排序为LLM服务调度提供了一种高效且实用的方法。
---

## Abstract
In Large Language Model (LLM) inference, the output length of an LLM request is typically regarded as not known a priori. Consequently, most LLM serving systems employ a simple First-come-first-serve (FCFS) scheduling strategy, leading to Head-Of-Line (HOL) blocking and reduced throughput and service quality. 
In this paper, we reexamine this assumption -- we show that, although predicting the exact generation length of each request is infeasible, it is possible to predict the relative ranks of output lengths in a batch of requests, using learning to rank. The ranking information offers valuable guidance for scheduling requests. Building on this insight, we develop a novel scheduler for LLM inference and serving that can approximate the shortest-job-first (SJF) schedule better than existing approaches. We integrate this scheduler with the state-of-the-art LLM serving system and show significant performance improvement in several important applications: 2.8x lower latency in chatbot serving and 6.5x higher throughput in synthetic data generation. Our code is available at https://github.com/hao-ai-lab/vllm-ltr.git

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）推理服务中，请求的输出长度通常被认为在生成前无法获知。现有的LLM服务系统大多采用先来先服务（FCFS）调度策略，这导致了严重的队头阻塞（Head-Of-Line blocking, HOL），即长请求会阻塞后续短请求，从而增加平均用户延迟，降低系统吞吐量和服务质量。
- **研究动机**：理论上，最短作业优先（SJF）及其抢占式变体最短剩余时间优先（SRTF）可以最小化平均延迟，但这些策略需要预先知道请求的生成长度，而这在传统LLM服务中被认为是不可能或极难做到的。作者试图重新审视这一假设，探索是否可以在不精确预测每个请求长度的情况下，仍然实现近似SJF/SRTF的调度效果。
- **整体含义**：本文提出通过“学习排序”（Learning to Rank）来预测一批请求中输出长度的相对顺序（而非精确数值），并利用这一排名信息指导调度，从而在无需精确长度预测的前提下，显著缓解HOL阻塞，提升服务性能。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：
  - 虽然精确预测单个请求的生成长度困难，但预测一批请求中长度的相对顺序是可行的，且这种相对顺序信息足以近似SJF/SRTF调度。
  - 使用肯德尔秩相关系数（Kendall's Tau）来衡量预测的排序与真实生成长度排序（即Oracle SJF/SRTF排序）之间的相似度。实验表明，Kendall's Tau越高的调度策略，在实际系统中往往带来更低的平均延迟。
  - 优化目标是训练一个轻量级辅助模型（如OPT-125M），使其能够对输入提示（prompt）按期望的生成长度进行排序，从而得到长度排名预测。

- **关键技术细节**：
  - **排名预测器（Predictor）**：采用小型OPT模型作为骨干，在最后一层隐藏状态后添加一个线性层，输出一个标量作为排名分数。训练数据来自真实LLM（如Llama-3-70B）在标准采样（温度=1.0）下生成的输出长度。训练标签通过将生成长度按10个token为间隔分桶后得到相对排名，以增加鲁棒性。
  - **损失函数**：采用列表式排名损失——ListMLE（式2）。ListMLE直接优化整个列表的似然，鼓励模型输出排序接近真实排序。选择ListMLE的原因是它与Kendall's Tau的优化目标一致（最大化排序一致性），且比逐点、逐对损失更适合本任务。
  - **调度算法（Algorithm 1）**：
    1. 将新到达的一组请求送入预测器，批量得到每个请求的分数（预测的生成长度排序依据）。
    2. 将所有请求（包括尚未完成的请求）按（优先级，分数）进行排序，优先级用于处理饥饿问题。
    3. 从排序后的序列中依次选取请求形成当前运行批次（受内存或批次大小限制）。
    4. 执行该批次的生成（迭代级调度，与连续批处理和PagedAttention兼容）。
    5. 更新每个请求的饥饿计数器（未被执行则计数增加）；当饥饿计数超过阈值时，提升该请求的优先级并赋予执行量子（PriorityQuantum），以防止长请求被无限推迟。
  - **饥饿预防机制**：定义`max_waiting_time = max(TTFT, max(TPOT))`作为用户等待感知的公平性度量。通过提升已饥饿请求的优先级，并限制其高优先级状态的有效时间，在保障整体延迟的同时防止长请求永久无法获得服务。

## 3. 实验设计：使用了哪些数据集/场景，它的benchmark是什么，对比了哪些方法

- **数据集与场景**：
  - **数据集**：ShareGPT（真实对话记录）和 LMSYS-Chat-1M（大规模真实LLM对话数据集）。每个数据集-模型对采样10k个非重叠提示用于服务，另10k用于训练排序预测器。
  - **场景**：1) 在线聊天机器人服务（chatbot serving），测量平均延迟和P90延迟（每token延迟）。2) 离线合成数据生成（synthetic data generation），测量生成固定数量样本的时间或固定时间内生成的样本数量。

- **Benchmark**：基于vLLM v0.4.1框架，测试了Llama-3-8B（单GPU）和Llama-3-70B（8GPU，张量并行）两种模型。评估指标包括：平均每token延迟、P90延迟、吞吐量（请求/秒）、饥饿度量（max_waiting_time）。

- **对比方法**：
  1. **FCFS**：先来先服务。
  2. **MLFQ**：多级反馈队列（参考FastServe实现，约1.2k行Python代码）。
  3. **Perception Only (PO)**：让LLM自己预测生成长度（生成15个token后预测剩余长度），然后基于预测长度调度。
  4. **Classification**：训练一个基于OPT模型的分类器（类似S3方法），将长度分类到10个桶中。
  5. **Ranking (Ours)**：本文提出的基于学习排序的调度方法。

## 4. 资源与算力

- 论文中明确了测试平台：一台DGX服务器，配备8块NVIDIA A100 40GB GPU，256 vCPU，1TB主机内存，GPU间通过NVLink互联。
- 训练预测器（OPT-125M或OPT-350M）在10k样本上，批大小32，训练5个epoch。未给出具体训练时间或GPU型号，但提到预测器开销极低（对服务时间的影响<2%）。
- 主要端到端实验在A100 40GB GPU集群上完成，未说明总GPU时数。

## 5. 实验数量与充分性

- **实验数量**：论文进行了多组实验，涵盖：
  - 聊天服务场景：在Llama-3-8B和70B上，对ShareGPT和LMSYS-Chat-1M两个数据集，测试不同请求到达率下的平均延迟（图3，包含多个速率点）。
  - 突发请求实验（表1）：用2000个请求的突发模式测试平均延迟和P90延迟。
  - 合成数据生成实验（表2）：两种设置（生成1k样本所需时间，以及5分钟内生成样本数）。
  - 排名预测能力比较（表3）：不同方法的Kendall's Tau、分类准确率、端到端延迟和时间。
  - 饥饿预防效果分析（图4、图5）。
  - 预测器开销分析（表4）。
  - 消融与敏感性分析（附录中）：不同批大小对Kendall's Tau的影响，不同模型大小的影响，重新预测的影响等。
- **充分性与客观性**：
  - 实验覆盖了两种具有代表性的真实数据集，两种模型规模（8B和70B），多个竞争基线和多种负载模式，较为全面。
  - 对比方法包括了当前主流（FCFS）、专用方法（MLFQ、PO）和基于分类的预测方法（Classification），且都基于同一框架vLLM实现，确保了比较公平。
  - 进行了饥饿预防分析，展示了权衡。
  - 不足之处：未在更多模型（如GPT类）上验证；未与更先进的调度方法（如Andes等）直接比较；部分实验仅报告单次结果，未给出误差棒或统计显著性（作者已说明因算力限制）。

## 6. 论文的主要结论与发现

- 预测请求长度的相对排名是可行的，且远比精确预测长度简单有效。
- Kendall's Tau是衡量调度策略接近SJF/SRTF程度的良好指标，高Tau往往对应低延迟。
- 提出的Ranking调度器在聊天服务场景下，相比FCFS最高可降低平均延迟6.9倍，相比PO降低1.5-1.9倍；在突发请求下P90延迟降低最多2.8倍。
- 在合成数据生成任务中，Ranking调度器可将生成1k样本所需时间减少2.4-6.5倍，或将5分钟内生成样本数提升最多3.2倍。
- 饥饿预防机制能有效降低max_waiting_time（高达3.4倍），且对延迟影响很小（<30%），整体可接受。
- 预测器开销极低（不到总服务时间的2%），适用于生产环境。

## 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - 创新性地将“学习排序”引入LLM调度，利用排名代替精确预测，大幅降低预测难度和模型要求（小型OPT即可）。
  - 提出使用Kendall's Tau作为调度质量度量，并验证其与实际性能的强相关性，为优化提供明确目标。
  - 设计了实用的饥饿预防机制，平衡延迟优化与公平性，且算法简洁，只需约500行代码即可集成到vLLM。
- **实验设计亮点**：
  - 在多个真实数据集和两种规模模型上评估，覆盖在线和离线两种典型场景。
  - 对比方法全面，包括朴素FCFS、专用预测方法（PO）、分类方法（S3变体）和传统多级反馈队列（MLFQ），公平比较。
  - 提供了充分的消融实验和敏感性分析（附录），深入分析预测器大小、批次大小、重预测等影响因素。

## 8. 不足与局限

- **局限性明确列出（见第6节）**：
  - Kendall's Tau虽然整体与延迟相关，但在某些局部乱序情况下（如短请求内部混淆）可能不能完全反映实际性能。
  - 调度器尚未与较新的优化技术（如chunk-prefill、prefill-decode disaggregation）结合测试，效果未知。
  - 论文仅测试了Llama-3系列模型，在其他架构（如GPT、OPT）上的一般性有待验证。
- **其他潜在不足**：
  - 预测器需要针对特定目标LLM的训练数据（通过运行该LLM获得输出长度），这增加了部署成本；虽然论文展示了跨数据集迁移能力，但仍有性能下降。
  - 饥饿预防中的阈值（StarvationThreshold、PriorityQuantum）需要调参，论文未给出通用指导。
  - 实验未包含统计误差棒或显著性检验，可能影响结论的稳健性。
  - 对比方法MLFQ的实现细节较多，可能引入额外开销，影响公平性（但附录A验证了其行为正确性）。

（完）
