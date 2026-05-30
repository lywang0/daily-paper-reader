---
title: Transcending Cost-Quality Tradeoff in Agent Serving via Session-Awareness
title_zh: 通过会话感知超越代理服务中的成本-质量权衡
authors: "Yanyu Ren, Li Chen, Dan Li, Xizheng Wang, Zhiyuan Wu, Yukai Miao, Yu Bai"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=RmqWt1btxQ"
tags: ["query:edge-llm"]
score: 6.0
evidence: 面向LLM代理的会话感知服务框架
tldr: LLM代理服务具有可预测请求模式、递增质量需求等特点，但现有系统缺乏会话感知。本文提出会话感知服务系统，通过有效KV缓存管理和最佳模型选择，超越了传统服务中的成本-质量权衡。该工作扩展了LLM服务框架的概念，虽聚焦agent场景，但其会话感知思想可应用于边缘端的多轮交互场景。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1297, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 720, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 435, \"height\": 278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1293, \"height\": 313, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 668, \"height\": 249, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 665, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1428, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1423, \"height\": 241, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1418, \"height\": 287, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 692, \"height\": 224, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1429, \"height\": 240, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 697, \"height\": 223, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 761, \"height\": 1025, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 730, \"height\": 250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 660, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1180, \"height\": 159, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1175, \"height\": 179, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 919, \"height\": 148, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 810, \"height\": 149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1297, \"height\": 806, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1430, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 987, \"height\": 115, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1180, \"height\": 147, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 959, \"height\": 211, \"label\": \"Table\"}]"
motivation: LLM代理服务中缺乏会话感知导致KV缓存管理低效，需要专门的优化。
method: 提出会话感知的服务框架，动态管理KV缓存和选择模型。
result: 在代理场景下超越成本-质量权衡，提升效率和质量。
conclusion: 会话感知是优化LLM服务的重要方向，对边缘交互式应用有价值。
---

## Abstract
Large Language Model (LLM) agents are capable of task execution across various domains by autonomously interacting with environments and refining LLM responses based on feedback.
However, existing model serving systems are not optimized for the unique demands of serving agents. Compared to classic model serving, agent serving has different characteristics:
predictable request pattern, increasing quality requirement, and unique prompt formatting. We identify a key problem for agent serving: LLM serving systems lack session-awareness. They neither perform effective KV cache management nor precisely select the cheapest yet competent model in each round.
This leads to a cost-quality tradeoff, and we identify an opportunity to surpass it in an agent serving system.

To this end, we introduce AgServe for AGile AGent SERVing.
AgServe features a session-aware server that boosts KV cache reuse via Estimated-Time-of-Arrival-based eviction and in-place positional embedding calibration, a quality-aware client that performs session-aware model cascading through real-time quality assessment, and a dynamic resource scheduler that maximizes GPU utilization. 
With AgServe, we allow agents to select and upgrade models during the session lifetime, and to achieve similar quality at much lower costs, effectively transcending the tradeoff. Extensive experiments on real testbeds demonstrate that AgServe (1) achieves comparable response quality to GPT-4o at a 16.5\% cost. (2) delivers 1.8$\times$ improvement in quality relative to the tradeoff curve.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）代理（Agent）在执行任务时，需要通过多轮与环境交互并基于反馈优化响应。与传统的 LLM 服务相比，代理服务具有三个显著特点：**可预测且高频的请求模式**（每轮间隔毫秒级、输出短）、**上下文不断增长且难度递增**（多轮会话中上下文长度和任务复杂度均增加）、**独特的提示格式**（采用中间截断而非前缀截断）。现有 LLM 服务系统严重缺乏**会话感知（Session-Awareness）**，既无法有效管理 KV 缓存（前缀匹配策略不适用、LRU 驱逐不感知会话语义），也无法精准选择最便宜且胜任的模型（路由和级联方法忽略会话生命周期并导致频繁迁移），从而陷入**成本-质量权衡**（使用更大模型获得高质量但成本高，反之亦然）。
- **整体含义**：论文旨在设计一个专为 LLM 代理服务的系统，通过利用会话的可预测性、增长特征和独特结构，在降低推理成本的同时维持或提升响应质量，**超越成本-质量权衡**。

### 2. 论文提出的方法论：核心思想、关键技术细节

论文提出 **AGSERVE**（AGile AGent SERVing）系统，由三个核心组件构成：

- **会话感知服务器（Session-Aware Server, SAS）**：负责管理会话 KV 缓存并执行推理。
  - **ETA 驱动的缓存驱逐（ECE）**：基于预估到达时间（Estimated Time of Arrival）进行缓存驱逐，替代传统的 LRU 策略。通过考虑每个会话的下一请求到达时间和缓存大小，使用动态规划选择最小化总 TTFT（首 Token 生成时间）的驱逐集合。
  - **原地位置嵌入校准（In-place Positional Embedding Calibration）**：针对中间截断（Middle Truncation）场景，通过旋转矩阵的数学变换直接调整已缓存 Key 的位置编码，避免重新计算 KV 缓存，保持前缀匹配能力。
  - **会话 ID-序列表（SIST）**：维护每个会话的块 ID，支持会话级的缓存索引和复用。

- **质量感知客户端（Session Guard Client, SGC）**：负责实时监控会话质量并选择模型。
  - **Q-Judge**：在会话开始时评估任务难度，选择初始模型（小/中/大）。训练时采用定制损失函数，倾向于低估难度（underkill）而非高估（overkill），避免不必要的高成本。
  - **R-Judge**：在会话过程中定期（频率可调）评估每轮响应的推理质量，识别服务失败、规则违反、无效动作或低质量推理。若质量低于阈值，触发**重试**或**服务升级迁移**（切换到更大模型），并支持回滚到之前检查点。
  - **模型级联**：采用三层模型层级（如 Llama-8B → Llama-70B → GPT-4o），初始选择小模型，随会话推进和难度增加动态升级。

- **资源调度器（Resource Scheduler, RS）**：动态分配 GPU 资源以最大化利用率。
  - 根据模型需求/供给比例（需求 = 调用频率，供给 = 可用 KV 缓存容量），自动调整各模型实例的 GPU 数量。优先为高需求/低供给比的模型扩容。
  - 将可调模型限制在单节点内以减少通信开销。

**核心创新**：将会话感知引入 KV 缓存管理（ETA 驱逐 + 原地校准）和模型选择（实时质量监控 + 动态级联），联合优化推理效率、服务质量和资源利用率。

### 3. 实验设计：数据集/场景、Benchmark、对比方法

- **评估基准**：基于 **AgentBench**（Liu et al., 2023）中的四个代理任务：
  - **AlfWorld (AW)**：家庭助手代理，多轮交互。
  - **Card Game (CG)**：双人策略游戏（AquaWar），支持多代理协作。
  - **Knowledge Graph (KG)**：查询知识图谱回答事实性问题，支持回滚。
  - **Mind2Web (M2W)**：网页导航和操作，通常仅需少数几轮。
- **评估指标**：
  - **质量评分**（0-100）：综合正常行为（25%）、任务完成度（50%）、回合效率（25%），具体各任务有调整（如 CG 按胜率，KG 按 F1 等）。
  - **成本**：开源模型按云服务器零售价折算（如 $10/小时），商业 API（GPT-4o）按官方定价。
  - **端到端延迟**（秒）、缓存命中率、TTFT 等微基准。
- **对比方法**：
  - **vLLM+**：单模型服务（Llama-8B/70B/GPT-4o 各单独运行）+ 前缀缓存 + 重试。
  - **Cascade**：三层级联但无 R-Judge 和 Q-Judge，始终从小模型开始。
  - **RouteLLM**：基于 BERT 路由器的模型选择（训练集同 AGSERVE）。
  - **Llumnix++**：扩展 SoTA LLM 服务系统 Llumnix，支持多实例分配（仅 Llumnix++ 基线）。
- **实验设置**：
  - **A6000 测试床**：2 节点 × 4 块 A6000（48GB/块），用于级联实验。
  - **A800 测试床**：2 节点 × 8 块 A800（80GB/块），用于多代理负载实验。
  - **模型**：Llama-3 8B/70B（开源） + GPT-4o（API）。

### 4. 资源与算力

- **训练**：
  - Q-Judge：基于 BERT，训练 10 个 epoch，batch size 16，warm-up 500 步，使用单块 A6000 GPU，耗时 2.9 小时。
  - R-Judge：基于 DistilBERT，训练 10 个 epoch，weight decay 1e-2，warm-up 500 步，耗时 17 分钟。
- **推理**：
  - 级联实验：A6000 测试床（共 8 块 A6000，每节点 4 块）。Llama-8B 占用 1/4 节点（即 1 块 GPU？但实际运行两个实例，每实例需多 GPU？原文说“两个实例，一个运行 Llama-8B，另一个运行 Llama-70B”，并提及“AGSERVE 需要 5/4 节点”），推测资源占用按模型比例。
  - 多代理实验：A800 测试床（共 2 节点 × 8 块 A800，即 16 块 A800），TP 大小 ≤ 4。
- **未明确说明**：训练 R-Judge 和 Q-Judge 的具体 GPU 数量（文中只说“利用单块 A6000”）；总训练时长约 3 小时；推理运行多组实验的总 GPU 小时数未报告。

### 5. 实验数量与充分性

- **端到端级联实验**（§7.2）：在 4 个代理任务（AW, CG, KG, M2W）上对比 AGSERVE 与 vLLM+、Cascade、RouteLLM，每个任务给出平均成本-质量曲线。
- **多代理负载实验**（§7.3）：在 4 种发送分布（Uniform, Gamma, Poisson, Burst）下对比 AGSERVE 与 Llumnix++、RouteLLM，每个分布跑 100 个 agent。
- **消融实验与微基准**（§7.4）：
  - SAS 缓存性能：在不同 batch size（5-8）下测缓存命中率、TTFT 分布；对比 vLLM 的正确性和延迟（4 个 agent）。
  - SGC 质量监控：R-Judge 和 Q-Judge 的准确率/召回率（人类标注数据），以及 QMM 对 TTFT 的影响。
  - RS 动态分配：对比静态分配（FS1, FS2）的端到端延迟（平均、P90、P50）。
  - 额外分析：人类评委对比（附录 E.8）、大规模仿真（附录 F）。
- **充分性评价**：实验覆盖了不同代理类型、不同负载模型、不同资源分配策略，并进行了消融，总体较充分。但不足在于：
  - 仅使用 Llama-3 系列和 GPT-4o，模型多样性有限。
  - 仿真实验（大规模）基于理想化假设，未在真实集群上验证。
  - 成本计算依赖云定价模型，可能无法完全代表真实部署成本。

### 6. 论文的主要结论与发现

- **主要结论**：AGSERVE 在代理服务中**超越了成本-质量权衡**。
- **定量结果**：
  - 在保持与 GPT-4o 相当服务质量（质量≈90）的同时，成本仅为 GPT-4o 的 **16.5%**（AW 任务，零售价）。
  - 在同一成本水平下，AGSERVE 相对于成本-质量权衡曲线获得 **1.8× 质量提升**。
  - 多代理负载下，相比 Llumnix++ 减少 64% 成本，同时质量提升 **1.6×**。
  - 缓存命中率相比 LRU 政策提高 **2.86×**。
  - 原地校准和 ETA 驱逐结合使回合延迟降低 **50%**。
  - 动态资源分配使端到端延迟加速 **1.2×**。

### 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - 首次系统性地将**会话感知**引入代理服务，覆盖缓存管理、模型选择和资源调度三大环节。
  - 提出 ETA 驱逐策略，利用代理请求的可预测性实现近似最优缓存效用。
  - 创新性地采用**原地位置嵌入校准**处理中间截断，避免额外存储和重计算。
  - **实时质量监控（R-Judge）** 结合重试与动态迁移，实现细粒度服务质量保障。
- **实验亮点**：
  - 采用真实代理基准 AgentBench 的 4 种不同难度和交互模式的代理任务。
  - 对比了多种基线，包括传统单模型、级联、路由和 SoTA 多实例系统（Llumnix++）。
  - 同时评估延迟、成本、质量，并给出成本-质量曲线，直观展示超越权衡。
  - 包含消融实验（缓存策略、质量判断、动态分配）及人类评委对比，支撑方法有效性。

### 8. 不足与局限

- **实验覆盖有限**：
  - 仅使用两个开源模型系列（Llama-3 8B/70B）和一个商业 API（GPT-4o），不同模型族（如 Qwen、Mistral）未验证；级联层数固定为三层，灵活性未充分展示。
  - 多代理实验中的轨迹（agent 启动分布）为合成数据，非真实用户日志。
  - 大规模实验仅通过仿真（附录 F），未在真实分布式集群上运行。
- **依赖与偏差风险**：
  - R-Judge 的准确性依赖训练数据（Chatbot-Arena 修改版），可能无法泛化到新代理领域；阈值 θ 需人工设定，可能带来主观偏差。
  - Q-Judge 存在低估/高估偏差，尽管损失函数倾向低估，但仍可能错误分配初始模型。
  - 成本模型采用零售云定价，实际自建数据中心可能改变成本比例。
- **应用限制**：
  - 系统假设代理请求模式可预测，但现实中的代理可能因网络延迟或外部事件导致模式突变，此时 ETA 预测可能失效。
  - 原地位置嵌入校准仅适用于 RoPE 位置编码的模型（如 Llama），对于其他位置编码（如 AliBi）不直接适用。
  - 节点路由当前采用静态绑定（第一轮调度到最空闲实例），不支持在会话进行中迁移，负载均衡能力有限。

（完）
