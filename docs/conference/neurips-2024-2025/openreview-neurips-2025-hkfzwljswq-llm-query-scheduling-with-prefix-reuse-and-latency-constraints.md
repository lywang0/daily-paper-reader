---
title: LLM Query Scheduling with Prefix Reuse and Latency Constraints
title_zh: 带有前缀重用和延迟约束的大语言模型查询调度
authors: "Gregory Dexter, Shao Tang, Ata Fatahibaarzi, Qingquan Song, Tejas Dharamsi, Aman Gupta"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=HKfZwLjSwQ"
tags: ["query:edge-llm"]
score: 7.0
evidence: 基于前缀重用的LLM推理查询调度
tldr: 针对在线LLM推理中前缀重用查询调度面临延迟约束的问题，本文首先揭示了现有FCFS和最长前缀匹配策略的局限性，然后提出了一个基于RadixAttention的正式理论框架，用于在满足TTFT和TPOT约束的同时优化调度。理论分析和模拟实验表明，该框架能够显著提高延迟约束下的服务质量。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-hkfzwljswq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1123, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-hkfzwljswq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 662, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-hkfzwljswq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1440, \"height\": 1126, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-hkfzwljswq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 813, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hkfzwljswq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 811, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-hkfzwljswq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 809, \"height\": 217, \"label\": \"Table\"}]"
motivation: 现有前缀重用调度策略无法有效满足延迟约束。
method: 构建基于RadixAttention的查询调度理论框架，支持优先满足TTFT和TPOT约束。
result: 理论分析和模拟证明新框架在满足延迟约束方面优于现有方法。
conclusion: 该工作为前缀重用场景下的LLM查询调度提供了理论基础和实用指导。
---

## Abstract
The efficient deployment of large language models (LLMs) in online settings requires optimizing inference performance under stringent latency constraints, particularly the time-to-first-token (TTFT) and time-per-output-token (TPOT). This paper focuses on the query scheduling problem for LLM inference with prefix reuse, a technique that leverages shared prefixes across queries to reduce computational overhead. Our work reveals previously unknown limitations of the existing first-come-first-serve (FCFS) and longest-prefix-match (LPM) scheduling strategies with respect to satisfying latency constraints. We present a formal theoretical framework for LLM query scheduling under RadixAttention, a prefix reuse mechanism that stores and reuses intermediate representations in a radix tree structure. Our analysis establishes the NP-hardness of the scheduling problem with prefix reuse under TTFT constraints and proposes a novel scheduling algorithm, $k$-LPM, which generalizes existing methods by balancing prefix reuse and fairness in query processing. Theoretical guarantees demonstrate that $k$-LPM achieves improved TTFT performance under realistic traffic patterns captured by a data generative model. Empirical evaluations in a realistic serving setting validates our findings, showing significant reductions in P99 TTFT compared to baseline methods.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在大语言模型（LLM）在线推理场景中，查询调度需要在满足严格延迟约束（尤其是首token生成时间 TTFT 和每个输出token时间 TPOT）的同时，最大化系统“好吞吐量”（goodput）。现有调度策略（如先来先服务 FCFS 和最长前缀匹配 LPM）在引入前缀重用（RadixAttention）后，未能有效兼顾延迟约束与缓存复用效率，导致高负载下TTFT急剧上升。
- **背景与意义**：前缀重用是提升LLM推理效率的关键技术，通过缓存和复用KV缓存中共享前缀的计算结果，减少冗余计算。然而，其性能严重依赖于查询处理顺序（即调度策略）。本文首次系统分析了RadixAttention下的调度问题，揭示了FCFS和LPM的固有缺陷，并提出了新的调度算法k-LPM，为前缀重用场景下的延迟优化提供了理论基础和实用方法。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：在保证前缀重用效率（类似LPM）的同时，避免某些查询因始终无高重叠前缀而被无限期推迟（FCFS的公平性）。通过交替执行k次LPM贪婪匹配和1次FCFS（处理最老查询），平衡缓存复用与等待时间。
- **关键技术细节**：
  - 建立形式化计算模型（Definition 2）：定义查询流 $(x_i, t_i)$，处理时间公式 $R(j_k) = \max\{R(j_{k-1}), t_{j_k}\} + (1 + c_{\text{attn}} \cdot |x_{j_k}|)(|x_{j_k}| - \text{Overlap}(x_{j_k}, x_{j_{k-1}}))$，其中 $c_{\text{attn}}$ 表示自注意力相对于前馈网络的计算开销比例。
  - 提出 **k-LPM 算法**（Algorithm 1）：
    ```
    1. 输入：查询队列 Q = {(x_i, t_i)}
    2. while true:
        3. 处理最老查询（最早到达）
        4. for i = 1 to k-1:
            5. 选择当前前缀缓存命中率最高的查询处理
    ```
    当 k=1 时退化为 FCFS，k→∞ 时退化为 LPM。
  - 数据生成模型（Definition 4）：定义“规则到达混洗队列”，捕捉实际应用中查询前缀呈树状结构、用户重复、文档唯一的特点。该模型使理论分析可进行。
  - **理论结果**：
    - **Theorem 1**：证明在TTFT约束下，判断是否存在可行调度是NP-hard问题（归约于3-PARTITION）。
    - **Theorem 2 & Corollary 3**：证明在数据生成模型下（c_attn=0），k-LPM的最大TTFT上界优于FCFS和LPM，且当 $0 < s < u$ 且 $k>1$ 时，k-LPM同时优于两者。
    - **Theorem 4**（附录）：存在算法可在 $O(n \cdot \exp(\frac{1}{p}\log\frac{1}{p}))$ 时间内返回 (1-p) 百分位TTFT满足约束或证明无解。

### 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **数据集/场景**：
  - **真实数据**：从Team [2025] 提供的8k上下文长度提示中采样，每条提示包含 (Instruction, Member Profile, Past Interactions, Question) 四部分，前三个为共享前缀，仅Question变化。共2100条提示，其中100条用于预热，2000条用于测试。
  - **合成数据**：使用“规则到达混洗队列”（Definition 4），控制用户前缀重复数k、前缀长度u、文档长度d、到达间隔s。
- **Benchmark**：SGLang v0.4.1 的 serving benchmark 工具，采用泊松到达过程。
- **对比方法**：
  - FCFS（先来先服务）
  - LPM（最长前缀匹配，SGLang默认）
  - k-LPM（k=2, 3, 1000等）
- **评价指标**：主要报告P99 TTFT，同时附录包含P50, P90, P95。

### 4. 资源与算力

- **主要实验**（Section 5）：
  - 模型：Llama-3.1-8B-Instruct
  - GPU：8× NVIDIA A100 (tensor parallelism)
  - 框架：SGLang v0.4.1
  - 未明确说明每次实验的运行时长或总GPU小时数。
- **附录C.2实验**：
  - 模型：Meta-Llama-3.2-1B-Instruct
  - GPU：单张 H100
  - 同样未说明运行时长。

### 5. 实验数量与充分性

- **实验组数**：
  - 主要实验（Figure 2）：5种k值（1,2,3,1000,∞）在不同请求率下测量P99 TTFT，共约5×（多个请求率点）组数据。
  - 附录Figure 3：同样设置下绘制P50、P90、P95、P99。
  - 附录Table 1（表1）：在80 req/s下，变化重复前缀与文档长度比例（1000/5000, 3000/3000, 5000/1000），比较FCFS、k-LPM(k=4)、LPM的Median/P90/P95。
- **充分性与客观性**：
  - 实验覆盖了不同负载强度（请求率从低到高）和不同前缀重用程度（前缀占比变化）。
  - 使用真实提示数据集，并采用实际LLM和服务框架，贴合生产环境。
  - **不足之处**：
    - 未提供误差条或多次重复的统计分析（作者声明因计算成本限制）。
    - 仅测试了单一模型（8B和1B两种参数规模），缺乏对更大模型或不同架构的评估。
    - 未与最新调度策略（如FastSwitch、Orca等）进行直接对比。
    - 超参数k的选择依赖于经验（实验中测试了固定k值），未展示自适应或调优过程。

### 6. 论文的主要结论与发现

- 现有FCFS和LPM在高负载、前缀重用的场景下均无法同时满足延迟约束，存在显著P99 TTFT尖峰。
- 证明了带前缀重用的TTFT约束调度问题是NP-hard，说明不存在高效最优解。
- 提出的k-LPM算法理论上在数据生成模型下能同时优于FCFS和LPM，且在实际实验中验证了：k=2时在多数请求率下P99 TTFT最低；LPM在极低负载下较好，FCFS在极低负载下也好，但在中等至高负载下k-LPM显著占优。
- 实验结果与理论分析一致，验证了模型的预测能力。

### 7. 优点：方法或实验设计上的亮点

- **理论贡献**：首次为RadixAttention下的查询调度建立严格形式化模型，并证明NP-hardness，奠定了该问题的理论基础。
- **算法设计巧妙**：k-LPM简单而有效，通过一个参数k就统一了FCFS和LPM，并提供了可证明的改进（Theorem 2），同时在实际中易于实现。
- **实验设计全面**：同时使用了真实工业数据（LinkedIn的360Brew提示集）和可控合成数据，覆盖多种负载和前缀结构，增强了结论的可信度。
- **附录提供了百分位约束的近似算法**（Theorem 4），展示了即使NP-hard问题也有实用近似方案。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **实验覆盖有限**：
  - 仅测试Llama-3.1-8B和1B模型，未涉及更大规模模型（如70B或175B）或其他架构（如MoE），这些模型的注意力计算和缓存行为可能不同。
  - 未与最新调度方法（如FastSwitch、DistServe等）进行定量比较，仅与FCFS和LPM对比。
- **实验可重复性**：作者未提供代码或公开数据集（因LinkedIn内部数据限制），且未报告误差棒，降低了统计显著性。
- **理论假设的局限性**：
  - 计算模型假设批量大小为1，并以最近一次查询的缓存状态简化，实际RadixAttention使用LRU缓存和管理多个前缀，可能带来偏差（作者承认此简化）。
  - 数据生成模型假设树高为2、前缀重复均匀，现实场景可能更复杂（如多级共享、非均匀重复）。
  - 理论分析中假设c_attn=0，虽然通过Corollary 3说明可推广，但未严格证明对任意c_attn均成立。
- **应用限制**：k-LPM需要设置超参数k，默认值可能依赖于具体工作负载，未提供自适应调整机制。
- **仅关注TTFT**：论文主要优化首token延迟，未考虑TPOT或整体吞吐，对于decode阶段主导的场景可能不适用。

（完）
