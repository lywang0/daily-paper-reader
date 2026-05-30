---
title: "DynaPipe: Dynamic Layer Redistribution for Efficient Serving of LLMs with Pipeline Parallelism"
title_zh: DynaPipe：通过动态层重分配实现LLM流水线并行高效服务
authors: "HongXin Xu, Tianyu Guo, Xianwei Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=D6w7wIN360"
tags: ["query:edge-llm"]
score: 8.0
evidence: 用于流水线并行服务的动态层重分配
tldr: 针对LLM服务中流水线并行导致的负载不均和气泡问题，提出DynaPipe动态层重分配方法，通过重新分配各阶段层数以平衡计算负载，显著减少流水线空闲时间，提升整体服务吞吐量，为高效大模型服务提供新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有流水线并行服务中，尾部阶段因额外处理导致负载不均，造成上游阶段空闲，性能下降。
method: 动态监测各阶段计算负载，实时调整层分配，平衡各阶段计算时间。
result: 实验表明，DynaPipe有效消除流水线气泡，显著提升吞吐量。
conclusion: 动态层重分配是提升流水线并行服务效率的有效手段。
---

## Abstract
To accelerate large language model (LLM) inference, pipeline parallelism partitions model layers into sequential stages, each assigned to a different device for concurrent execution. However, this method often suffers from pipeline bubbles caused by imbalanced computation in the tail stage. While upstream stages focus solely on layer-forward operations, the final stage must also handle post-processing tasks like sampling, introducing significant latency. This uneven workload leads to pipeline misalignment, forcing upstream stages to idle and degrading overall performance. Existing frameworks typically distribute layers evenly across stages without accounting for computational load differences. To address this, we propose DynaPipe, a dynamic layer redistribution scheme that adaptively balances computation by predicting execution latency in real time. Moreover, we introduce an asynchronous key-value (KV) cache migration coordinator to enable
non-blocking layer redistribution during inference. Experiments on representative LLMs demonstrate that DynaPipe reduces average end-to-end request latency by 8% to 49% across diverse workloads, outperforming state-of-the-art pipeline parallelism systems.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在LLM推理中，流水线并行（Pipeline Parallelism, PP）将模型层划分为多个阶段，每个阶段分配到不同设备。然而，尾部阶段除了前向计算外，还需处理采样（sampling）等额外后处理任务（如logits计算和token采样），导致计算负载不均衡。这产生“流水线气泡”（pipeline bubbles），上游阶段因等待尾部阶段而空闲，显著降低GPU利用率和端到端性能。
- **现有方法局限**：现有框架（如vLLM、gLLM）通常采用静态均匀层分配，未考虑采样带来的负载差异；部分静态重分配策略无法适应动态变化的采样开销与层前向时间比率。
- **研究动机**：提出一种运行时动态层重分配方案，实时监测各阶段计算负载并调整层-阶段映射，以平衡前向与采样负载，消除气泡。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过动态重分配尾部阶段的层到上游阶段，使采样与前向计算重叠，从而平衡各阶段执行时间，减少流水线气泡。
- **三大核心组件**：
  - **执行时间预测器（Execution Time Predictor）**：
    - 分别预测单层前向时间 \( T_{layer} \) 和采样时间 \( T_{sample} \)。
    - 公式：\( T_{layer} = \sum_{i=1}^{N} (\phi_1 n_i + \phi_2 n_i L_i + \epsilon) \)（基于token数n和序列长度L），\( T_{sample} = \alpha N_{decode} + \beta \)（基于解码请求数）。
    - 参数通过离线profile拟合，预测误差低（层前向平均4.95%，采样仅0.31%）。
  - **气泡感知调度器（Bubble-Aware Scheduler）**：
    - 使用预测值计算重分配后各阶段时间差 \(\Delta = T_{sample} - k \cdot T_{layer} - \frac{k}{m} \cdot T_{layer}\)，其中k为从尾部移除的层数，m为接收层的前序阶段数。
    - 引入**滑动窗口阈值机制**：仅当同一配置在连续窗口内稳定出现时才触发重分配，避免频繁调整。
  - **迁移协调器（Migration Coordinator）**：
    - 支持**异步KV缓存迁移**：源阶段完成迁移层的计算后立即异步传输KV缓存，目标阶段仅在需要新层时才等待，实现计算与通信重叠，避免流水线停顿。

## 3. 实验设计

- **数据集**：
  - **ShareGPT**：真实用户-ChatGPT对话数据，平均输入/输出长度：221/157（P50），627/382（P90）。
  - **Azure-Conv**：Azure生产环境对话数据，平均输入/输出长度：514/192（P50），1008/412（P90）。
- **模型**：
  - 主实验：Qwen2.5-14B、Qwen2.5-32B。
  - 附加实验：Qwen3-30B-A3B（MoE）、Meta-Llama-3-8B-Instruct（dense）。
- **Baseline对比方法**：
  - **vLLM (v0.8.5 V1)**：pipeline并行+固定chunk。
  - **SGLang (v0.4.3.post2)**：tensor并行。
  - **gLLM**：基于pipeline并行的自适应调度（论文基础框架）。
- **评价指标**：
  - **平均端到端延迟（E2EL）**：请求发出到完成的时间。
  - **SLO达标率**：TTFT和TPOT均低于设定阈值（ShareGPT 14B: TTFT 1s, TPOT 100ms; 32B: TTFT 4s, TPOT 250ms; Azure-Conv相应调整）的请求占比。
- **实验场景**：不同请求率（6-36 reqs/s）、不同输出输入长度比（0~0.5）、不同窗口阈值（0-50）、单节点与多节点（模拟跨节点）、多种模型架构。

## 4. 资源与算力

- **硬件平台**：4块NVIDIA A100-PCIe-40GB GPU，通过PCIe连接。
- **多节点模拟**：通过禁用NCCL的共享内存、P2P和IB，强制使用TCP模拟跨节点环境（同样4块A100）。
- **未明确说明**：总推理实验时长或训练时长（论文为推理优化，无训练阶段）；但提及单次实验耗时较长，难以重复运行。

## 5. 实验数量与充分性

- **实验数量**：包含多种场景，总计约8个主要图表，涵盖：
  - 主性能对比（图4）：两种数据集×两种模型×多个请求率 = 约20+子图。
  - 输出输入比影响（图5）：固定输入512，输出变化，对比4种静态策略 + DynaPipe。
  - 窗口阈值影响（图6）：展示E2EL和调整次数随阈值变化。
  - 多节点实验（图7）：两种数据集×多个请求率。
  - 预测器准确性（图8）：散点图验证层时间与采样时间预测。
  - 其他模型泛化（附录图9）：MoE和dense模型。
  - 开销分析（附录B）：迁移开销、内存开销。
- **充分性与公平性**：
  - 对比了最先进的SOTA框架，使用统一chunk prefill配置。
  - 消融实验：静态策略对比、窗口阈值影响，验证各组件贡献。
  - 覆盖不同负载强度、不同架构、单节点和多节点，较为全面。
  - 但未报告误差棒，作者因实验时间过长而无法多次重复。

## 6. 论文的主要结论与发现

- **性能提升显著**：与gLLM等相比，DynaPipe在ShareGPT上降低E2EL最多40%，在Azure-Conv上降低34%；平均降低8%-49%。SLO达标率在高负载下提升明显，可支撑高出19%的请求率。
- **动态调整优于静态**：固定层重分配策略在不同输出输入长度比下表现不一，而DynaPipe始终最优。
- **预测器高效**：预测开销仅0.5μs，层时间误差<5%，采样误差<0.5%。
- **迁移开销可被掩盖**：通过异步迁移和滑动窗口，实际迁移次数少（窗口25时仅4次调整），对性能影响小。
- **跨模型泛化**：在MoE和dense模型上同样有效。

## 7. 优点：方法或实验设计上的亮点

- **问题发现新颖**：首次系统化指出采样操作是流水线并行中的关键瓶颈，并量化其影响（采样时间可达单层前向的3.09倍）。
- **方案完整**：预测-调度-迁移三者闭环设计，实现运行时自适应。
- **异步KV缓存迁移**：非阻塞设计，避免流水线停顿，实用性强。
- **稳定性设计**：滑动窗口阈值过滤噪声，减少不必要的重分配。
- **实验覆盖全面**：多种模型尺寸、架构、数据集、负载强度、跨节点设置，并附带开销分析，可信度高。
- **代码开源**：提供复现基础。

## 8. 不足与局限

- **额外内存开销**：预加载可能重分配的层权重，导致GPU内存增加约7.5%（以32B为例），论文承认可通过异步卸载优化。
- **迁移延迟仍存在**：在跨节点场景下（TCP模拟），通信开销略大，性能增益略低于单节点；且未在更高带宽互联（如NVLINK）下测试。
- **仅针对流水线并行**：未结合tensor并行、序列并行等多维并行进行联合优化。
- **实验重复性不足**：未提供误差棒，统计显著性未充分证明。
- **窗口阈值手动设定**：论文固定窗口大小为25，未提供自适应调优方法。
- **预测模型依赖离线profile**：参数需针对每个模型预先拟合，可能增加部署成本。

（完）
