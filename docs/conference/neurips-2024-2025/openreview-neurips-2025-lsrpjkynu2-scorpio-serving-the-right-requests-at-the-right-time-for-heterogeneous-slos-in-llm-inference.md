---
title: "Scorpio: Serving the Right Requests at the Right Time for Heterogeneous SLOs in LLM Inference"
title_zh: Scorpio：面向异构服务等级目标的LLM推理请求适时服务系统
authors: "Yinghao Tang, Tingfeng Lan, Xiuqi Huang, Hui Lu, Wei Chen"
date: 2025-05-09
pdf: "https://openreview.net/pdf?id=LSrpJkynU2"
tags: ["query:edge-llm"]
score: 8.0
evidence: 面向服务等级目标的LLM服务系统
tldr: 针对现有LLM服务系统忽略异构SLO导致目标达成率低的问题，Scorpio提出利用SLO异构性进行自适应调度，包括TTFT保护器采用最晚截止时间优先重排序和拒绝不可达请求，TPOT保护器采用基于VBS的准入控制和信用机制。实验表明，Scorpio在保持高吞吐的同时显著提升了SLO达成率。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1425, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1153, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1427, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 795, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1500, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 712, \"height\": 952, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 997, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 694, \"height\": 940, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1400, \"height\": 840, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-lsrpjkynu2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 962, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lsrpjkynu2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1455, \"height\": 289, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lsrpjkynu2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 587, \"height\": 331, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lsrpjkynu2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 381, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lsrpjkynu2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1448, \"height\": 1019, \"label\": \"Table\"}]"
motivation: 现有LLM服务系统以最大吞吐为目标，忽视异构SLO导致次优。
method: 设计TTFT保护和TPOT保护机制，通过自适应调度、排队和批处理优化SLO达成。
result: 在多种工作负载下，Scorpio提高了系统好吞吐和SLO达成率。
conclusion: Scorpio通过SLO感知调度有效平衡吞吐和服务质量，适用于多SLO场景。
---

## Abstract
Existing Large Language Model (LLM) serving systems prioritize maximum throughput. They often neglect Service Level Objectives (SLOs) such as Time to First Token (TTFT) and Time Per Output Token (TPOT), which leads to suboptimal SLO attainment. This paper introduces SCORPIO, an SLO-oriented LLM serving system designed to maximize system goodput and SLO attainment for workloads with heterogeneous SLOs. Our core insight is to exploit SLO heterogeneity for adaptive scheduling across admission control, queue management, and batch selection. SCORPIO features a TTFT Guard, which employs least-deadline-first reordering and rejects unattainable requests, and a TPOT Guard, which utilizes a VBS-based admission control and a novel credit-based batching mechanism. Both guards are supported by a predictive module. Evaluations demonstrate that SCORPIO improves system goodput by up to 14.4X and SLO adherence by up to 46.5% compared to state-of-the-art baselines.

---

## 论文详细总结（自动生成）

# SCORPIO 论文详细总结

## 1. 核心问题与整体含义（研究动机与背景）

- **现状**：当前主流 LLM 服务系统（如 vLLM、SGLang）以最大化吞吐量为首要目标，普遍忽略服务等级目标（SLO），例如首 token 到达时间（TTFT）和每输出 token 时间（TPOT）。
- **问题**：不同应用对 SLO 的需求存在固有异构性（例如编程助手要求低延迟，聊天机器人可容忍稍高延迟），但现有系统对所有请求无差异化处理，导致 SLO 达标率低下，尤其在突发流量下容易引发大规模 SLO 违规。
- **目标**：设计一个面向异构 SLO 的 LLM 服务系统，最大化系统好吞吐（goodput）和 SLO 达标率（SLO adherence），在保证服务质量的同时提高资源效率。

## 2. 方法论：核心思想、技术细节与算法流程

### 2.1 核心思想
- **利用 SLO 异构性进行自适应调度**：在准入控制、队列管理、批处理选择等所有阶段动态调度“合适的请求”，使具有宽松 SLO 的请求容忍稍晚服务或跳过部分迭代，优先满足紧 SLO 请求。

### 2.2 系统架构（三部分）

#### a) 预测模块（Predictor）
1. **输出长度预测器**：微调 OPT-125M 模型，将输出长度分为 100 个等宽桶（bin），进行多分类预测；相比之前粗粒度分桶（10 桶），提升了预测分辨率与准确率。
2. **TPOT 估计器**：基于实测数据拟合 ITL（token 间延迟）的线性模型：
   - `ITL = α|R|·Lavg + β|R| + γLavg + δ`
   - 给定新请求加入后，估计未来 P(r) 步的平均 TPOT。
3. **TTFT 估计器**：根据预填充时间公式（针对短/长输入分段线性）和等待队列中所有请求的预填充时间之和，估计最小 TTFT。

#### b) TTFT 保护器（TTFT Guard）
1. **最晚截止时间优先（LDF）重排序**：根据请求剩余 TTFT 截止期限重新排序等待队列，越紧急的请求越靠前。
2. **不可达 SLO 拒绝**：若预测 TTFT 将超过截止期限，则直接拒绝（标记为不可达），避免浪费资源。

#### c) TPOT 保护器（TPOT Guard）
1. **TPOT 相对比例（TRP）定义**：`TRP(r) = min_{r'∈R} S_TP(r') / S_TP(r)`，衡量请求 r 相对于当前最紧 TPOT 请求的紧急程度。
2. **基于信用的批处理机制（Credit-based Batching）**：每个请求按 TRP 速率累积信用（Credit），当信用 ≥1.0 时才有资格参与下一轮批处理，之后扣除 1.0。这使得宽松 SLO 的请求被跳过迭代的次数更多。
3. **基于虚拟批大小（VBS）的准入控制**：将系统实际负载视为所有请求 TRP 之和（`VBS = Σ TRP(r)`），若加入新请求后预估 TPOT 不超过当前运行请求中的最小 TPOT SLO，则准入；否则拒绝。
4. **算法流程（Algorithm 1）**：
   - 循环：对等待队列中的每个请求，尝试加入运行队列，用 VBS 和 TPOT 估计器判断是否准入；
   - 对运行队列中每个请求，每步累积信用，信用满的请求加入本轮批处理，并扣减信用。

## 3. 实验设计

- **数据集**：ShareGPT、LMSYS-Chat-1M（真实对话数据）。
- **模型**：Meta Llama-3.1 8B（单 GPU 运行）、Google Gemma-2 27B（4 GPU 张量并行）。
- **SLO 设置**：6 类 SLO 场景，涵盖紧/松 TTFT 与 TPOT 组合。
- **对比基线**：
  - vLLM（吞吐优先）
  - S3（基于输出长度排序的最短任务优先，复现在 vLLM 上）
  - Mooncake（基于早期拒绝的准入控制）
- **评估指标**：goodput（单位时间成功满足 SLO 的请求数）、SLO adherence（满足 SLO 的请求比例）。
- **实验场景**：
  - **QPS 缩放**：在不同 QPS（5~20）下对比 goodput 和 SLO adherence（4 组图，各数据集×模型）。
  - **真实轨迹服务**：使用 Azure 20 分钟轨迹（含突发负载），统计累计 SLO 达标请求数（4 组图）。
  - **消融实验**：逐步增加 TTFT Guard 和 TPOT Guard，观察 TTFT 违规数、TPOT 违规数、goodput（在 QPS=14 下，4 组图）。
  - **额外观测**：预测器干扰对比（部署在同一 GPU vs 单独 GPU）、桶策略分析（不同桶数下的精度、Kendall τ、RMSE）、分析模型精度（R²、RMSE、MAPE）。

## 4. 资源与算力

- **硬件**：1 台服务器，含 4×NVIDIA A100 GPU（80GB），NVLink 成对互联，GPU0-GPU1 和 GPU2-GPU3 之间为 NVLink，跨对通过 PCIe + NUMA 通信。
- **模型部署**：Llama-3.1 8B 单 GPU，Gemma-2 27B 4 GPU 张量并行。预测器 OPT-125M 与 LLM 在同一 GPU 上运行（附录 A.5 分析干扰）。
- **训练**：序列长度预测器用 20K 样本（6:2:2 划分），学习率 2e-5，batch size 64，训练 8 epochs。未明确说明训练耗时，但预测器推理开销可忽略（附录已声明）。
- **备注**：低 QPS 下性能退化部分归因于预测器与 LLM 的资源争用；若将预测器部署在独立 GTX 3090（24GB）上可缓解。

## 5. 实验数量与充分性

- **实验总量**：约 12 组主要实验（QPS 缩放 4 组、真实轨迹 4 组、消融 4 组），外加附录中桶策略分析（2 模型×2 数据集×多桶数）、分析模型精度（多个指标）、干扰分析（2 模型×2 数据集×多 QPS）。
- **充分性**：多角度评估，覆盖不同模型规模、多种 SLO 组合、实际突发轨迹、组件贡献分析、预测器影响、阈值敏感性等。对比基线均来自 SOTA 文献且复现公平。结论具有统计意义（误差棒在分析模型中已报告 R² 等）。
- **公平性**：所有基线均基于 vLLM 重新实现核心策略，确保公平比较。消融实验采用逐步添加的方式验证各组件必要性。

## 6. 主要结论与发现

- SCORPIO 在高 QPS（如 15 QPS）下 goodput 提升高达 **14.4 倍**，SLO adherence 提升高达 **46.5%**，远超所有基线。
- 在真实轨迹服务中，累计 SLO 达标请求数是 Mooncake 的 1.25 倍、vLLM 的 2.01 倍、S3 的 2.11 倍。
- 消融实验表明：TTFT Guard 和 TPOT Guard 相互依赖，缺少任一个都会导致另一类违规急剧上升。
- SCORPIO 的调度开销小于 **1%**，几乎不增加推理延迟。
- 预测器干扰在高负载下影响约 5%~20%，在低负载下更明显；可考虑独立部署来缓解。
- 100 桶等宽分桶策略在预测精度、排序一致性（Kendall τ）、RMSE 上达到最佳平衡。

## 7. 优点

- **创新性**：首次系统性地利用 SLO 异构性进行全链路自适应调度，提出信用批处理与虚拟批大小准入控制等新颖机制。
- **系统-算法协同设计**：预测器、两个保护器紧密配合，形成闭环反馈。
- **实验全面**：覆盖多种负载、模型、基线、消融、干扰分析，结论扎实。
- **可复现性**：附详细超参数、训练细节，计划开源代码。
- **部署友好**：调度开销极低，适合在线服务。

## 8. 不足与局限

- **低 QPS 性能退化**：在轻负载下，SCORPIO 的复杂性反而导致小幅度性能下降（goodput 降为 0.92~0.98 倍，SLO adherence 降低 1%~2%），作者归因于预测器资源争用，建议轻负载切换简单调度策略（未实现）。
- **与最新技术集成不足**：未考虑预填充-解码分离（如 DistServe）等更优架构；仅处理了拒绝场景，未探索降级（如降低精度、迁移请求）等柔性策略。
- **预测器依赖**：对输出长度预测的准确性敏感，虽然实验表明预测模型效果较好，但在极端分布或长尾场景下可能引入误差。
- **实验局限**：只在两个模型上测试，未覆盖更大规模模型（如 70B+）或多节点分布式场景。实验时间未明确标注，部分附录中的桶策略分析可能缺乏统计检验（如多次重复平均）。
- **应用限制**：假定所有请求的 SLO 已知且固定，实际中可能动态变化；未考虑请求优先级、公平性等其他服务质量维度。

（完）
