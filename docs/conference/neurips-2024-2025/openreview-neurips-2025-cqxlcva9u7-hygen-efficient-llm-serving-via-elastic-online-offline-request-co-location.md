---
title: "HyGen: Efficient LLM Serving via Elastic Online-Offline Request Co-location"
title_zh: HyGen：通过弹性在线-离线请求共置实现高效LLM服务
authors: "Ting Sun, Penghan Wang, Fan Lai"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=cQxLCVa9u7"
tags: ["query:edge-llm"]
score: 6.0
evidence: 干扰感知的LLM服务系统，协调在线和离线负载
tldr: HyGen针对LLM服务中在线和离线负载单独部署导致资源利用率低的问题，提出干扰感知服务系统，通过延迟预测器和SLO感知分析器估计执行时间和干扰，在保护在线服务SLO的同时混合部署两种负载。实验证明该系统可大幅提升资源效率，为LLM服务框架提供优化范例。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 517, \"height\": 766, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 692, \"height\": 791, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1427, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1430, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 649, \"height\": 286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 630, \"height\": 306, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 366, \"height\": 286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 780, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1375, \"height\": 326, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 671, \"height\": 282, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 743, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 674, \"height\": 306, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 687, \"height\": 320, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 687, \"height\": 317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 728, \"height\": 262, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-cqxlcva9u7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 1127, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cqxlcva9u7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1432, \"height\": 1324, \"label\": \"Table\"}]"
motivation: LLM在线和离线负载单独部署导致资源浪费。
method: 干扰感知的共置策略，结合延迟预测和SLO分析。
result: 提高资源利用率，满足SLO。
conclusion: 混合部署可提升LLM服务效率。
---

## Abstract
Large language models (LLMs) have facilitated a wide range of applications with distinct service-level objectives (SLOs), from latency-sensitive online tasks like interactive chatbots to throughput-oriented offline workloads like data synthesis. The existing deployment model, which dedicates machines to each workload, simplifies SLO management but often leads to poor resource utilization. This paper introduces HyGen, an interference-aware LLM serving system that enables efficient co-location of online and offline workloads while preserving SLOs. HyGen incorporates two key innovations: (1) performance control mechanisms, including a latency predictor to estimate batch execution time and an SLO-aware profiler to quantify latency interference, and (2) SLO-aware offline scheduling policies that maximize serving throughput and prevent starvation. Our evaluation on production workloads shows that HyGen achieves up to 3.9-5.8× throughput gains over online and hybrid serving baselines, while ensuring latency SLOs. The code of HyGen is publicly available at https://github.com/UIUC-MLSys/HyGen.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：大型语言模型（LLM）服务面临在线任务（如聊天机器人，对延迟敏感）和离线任务（如数据合成，对吞吐量敏感）的差异化服务水平目标（SLO）。现有部署模式将两类负载分配到独立集群，简化了SLO管理，但导致资源利用率低下。
- **背景**：在线请求负载具有显著的日内波动和突发性（如Azure LLM服务显示请求率在几分钟内变化高达3倍）。为满足峰值需求，服务提供商需过度配置GPU资源，导致非高峰时段大量资源闲置。
- **动机**：通过在同一推理引擎上弹性共置在线和离线工作负载，可利用空闲资源提升效率，同时保证在线请求的延迟SLO。
- **整体含义**：HyGen是一个干扰感知的LLM服务系统，通过精确的延迟控制和智能调度实现高效的负载共置，在不牺牲SLO的前提下大幅提升吞吐量。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：基于干扰感知的在线-离线请求共置策略，通过两阶段调度（先在线、后离线）和精细化的性能控制机制，在满足在线SLO的同时最大化离线吞吐量。
- **关键组件**：
  - **双队列架构**：分离在线和离线请求队列，各自采用现有调度策略（如FCFS、公平调度）。在线阶段优先处理在线请求；离线阶段利用剩余容量。
  - **延迟预测器（Latency Predictor）**：采用线性回归模型估计批处理执行时间，输入特征包括：预填充总token数（$S_p$）、解码总token数（$S_d$）、$S_p^2$（捕捉二次注意力复杂度）、预填充请求数（$N_p$）、解码请求数（$N_d$）。模型训练仅需~15ms（CPU上80000样本），推理时延~18μs。
  - **SLO感知分析器（SLO-aware Profiler）**：将延迟SLO转化为可操作的延迟预算。通过离线测试和二分搜索确定满足SLO的批次延迟上限，并在线动态调整。
  - **SLO感知离线调度策略**：基于前缀共享最大化（PSM）策略，将离线请求组织成前缀树，按深度优先搜索（DFS）顺序选择共享前缀最多的请求，提升KV缓存复用。为防饥饿，扩展版本结合公平性（通过效用比率平衡前缀共享与请求新鲜度）。
- **算法流程**（两阶段调度）：
  1. 在线阶段：基于在线请求队列和运行中请求，利用延迟预测器和预算确定可调度的在线请求，形成初始批次。
  2. 离线阶段：使用剩余延迟预算、内存预算和块大小，以PSM顺序尝试添加离线请求。若内存或延迟不足，则进行抢占（优先保留在线请求）。
  3. 异步消息队列实现主进程与调度器解耦，降低开销。

## 3. 实验设计
- **数据集与场景**：
  - 在线工作负载：Azure LLM推理轨迹2023（真实生产trace），Mooncake轨迹（附加实验）。
  - 离线工作负载：arXiv摘要数据集（长文档摘要）、CNN/DailyMail摘要、MMLU（用于前缀共享模拟）。
- **基准方法**：
  - **Sarathi**：纯在线服务基线。
  - **Sarathi-offline**：纯离线服务（调优块大小以最大化吞吐量）。
  - **Sarathi++**：在Sarathi上实现混合服务，但无SLO感知（简单在线优先+抢占）。
  - **HyGen\***：在Sarathi++基础上增加离线QPS控制（经profile保证SLO边界），用于评估HyGen完整设计的吞吐量增益。
- **测量指标**：
  - 延迟：Time to First Token (TTFT)、Time Between Tokens (TBT) 的均值和P99。
  - 吞吐量：tokens per second (TPS) 或 queries per second (QPS)。
  - 干扰容忍度：参数化（以百分比表示允许的SLO松弛）。

## 4. 资源与算力
- **硬件**：实验在三种GPU平台上进行：
  - 4×NVIDIA A100 (40GB VRAM)
  - 4×NVIDIA A40 (48GB VRAM)
  - 1×NVIDIA A5000 (24GB VRAM)
- **模型规模**：Llama2-7B, Qwen-14B, Mistral-7B, Sheared-LLaMA-2.7B, Yi-34B（使用TP=2, PP=2分布式推理）。
- **训练成本**：延迟预测器的线性回归模型在CPU上训练约15ms（80,000样本），运行时推理约18μs，开销极低。
- **未明确说明**：完整的训练/部署集群规模、每次实验的具体GPU小时数等。

## 5. 实验数量与充分性
- **实验组数**：大量实验覆盖多个维度：
  - **端到端性能**（图3-4）：在Llama2-7B和Qwen-14B上，针对四个SLO指标（均值/P99 TBT/TTFT）和不同容忍度（0.05-0.25s等），展示HyGen相比Sarathi和HyGen\*的SLO遵守和吞吐量。
  - **性能分解**（图5-8）：延迟预测器精度（~1-2% MAPE）、PSM对吞吐量的影响（高达4×增益）、SLO分析器的作用、时序吞吐量动态调整。
  - **消融研究**（图9-17）：
    - 模型并行度（Yi-34B TP=2, PP=2）
    - 不同SLO要求（多指标同时满足）
    - 不同在线QPS水平（0.5-2.5 QPS）
    - 不同模型和数据集（Mistral + Mooncake, CNN/DailyMail等）
    - 不同硬件（A5000+Sheared-LLaMA-2.7B）
    - 预测器精度对吞吐量的鲁棒性（MAPE高达20%仍有良好表现）
    - 在线到达率对离线吞吐量的影响
- **充分性与公平性**：实验充分，对比了有/无SLO感知的混合服务基线（Sarathi++和HyGen\*），并包含纯在线和纯离线上限。消融覆盖关键设计选择。结果客观展示了HyGen的优势和局限性。

## 6. 主要结论与发现
- **吞吐量提升**：HyGen在保证SLO的前提下，相较于纯在线服务（Sarathi）实现3.87×吞吐量提升，相较于混合基线（HyGen\*）最高达5.84×吞吐量提升，达到纯离线服务（Sarathi-offline）84.3%的吞吐量。
- **SLO遵守**：在所有测试的设置中（不同SLO指标、容忍度、在线QPS），HyGen均能严格控制延迟，满足目标SLO。
- **延迟预测器**：平均绝对百分比误差（MAPE）仅1.78%（Llama2-7B）和1.07%（Qwen-14B），满足实时调度需求。
- **前缀共享最大化（PSM）**：通过智能重排离线请求顺序，实现高达4×离线吞吐量增益。
- **系统鲁棒性**：即使预测器误差高达20%，系统仍能有效控制SLO并维持高吞吐量。
- **动态适应性**：HyGen根据在线负载波动自动调整离线吞吐量，在低负载时积极填充，高负载时减少干扰。

## 7. 优点
- **创新性**：首次系统研究LLM在线-离线负载共置问题，提出干扰感知的控制机制和调度策略。
- **实用性**：延迟预测器轻量（线性回归）且准确；SLO分析器将抽象SLO转化为可操作预算；双队列架构兼容现有调度策略。
- **性能优异**：显著提升吞吐量（3.9-5.8×）同时保证严格SLO，证明共置的可行性和收益。
- **全面评估**：覆盖多种硬件、模型、数据集、SLO条件，并包含详细消融，验证各组件贡献。
- **开源**：代码公开，便于复现和应用。

## 8. 不足与局限
- **预测器假设**：假设性能预测稳定，但在高度动态或对抗性输入下可能退化（未深入测试极端波动场景）。
- **单模型共置**：HyGen专注于单个模型场景；扩展到异构模型或多租户环境可能引入新的干扰模式，当前未验证。
- **评估局限性**：主要基于Azure和Mooncake等特定生产trace，泛化到其他服务架构或框架可能需要额外适配。
- **抢占机制**：目前仅支持状态保留的抢占，未探索更复杂的抢占策略（如状态丢弃、交换），可能影响极端情况下的效率。
- **公平性**：扩展PSM虽缓解饥饿，但效用比率的选择基于启发式，缺乏理论最优保证。
- **硬件限制**：仅在有限GPU型号上测试，未包含最新架构（如H100）或大规模分布式集群。

（完）
