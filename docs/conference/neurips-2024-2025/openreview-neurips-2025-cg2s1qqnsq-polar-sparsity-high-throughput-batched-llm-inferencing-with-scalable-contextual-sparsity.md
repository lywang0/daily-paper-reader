---
title: "Polar Sparsity: High Throughput Batched LLM Inferencing with Scalable Contextual Sparsity"
title_zh: Polar Sparsity：具有可扩展上下文稀疏性的高吞吐批量LLM推理
authors: "Susav Shrestha, Bradley Settlemyer, Nikoli Dryden, A. L. Narasimha Reddy"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=cg2S1qqNSq"
tags: ["query:edge-llm"]
score: 4.0
evidence: 面向硬件感知的稀疏化技术加速批量推理
tldr: 上下文稀疏性在批量推理中因活跃神经元联合趋近稠密计算而难以扩展。Polar Sparsity发现注意力头稀疏性在批量大小变化时保持稳定，据此开发可扩展的上下文稀疏方法，在保持精度的同时实现高吞吐推理。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1444, \"height\": 603, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 611, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1441, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1435, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1443, \"height\": 606, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1443, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1438, \"height\": 603, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1433, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1447, \"height\": 616, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1430, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1442, \"height\": 606, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1442, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1442, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cg2s1qqnsq/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1445, \"height\": 603, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-cg2s1qqnsq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 702, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cg2s1qqnsq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1044, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cg2s1qqnsq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1457, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cg2s1qqnsq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1450, \"height\": 439, \"label\": \"Table\"}]"
motivation: 现有上下文稀疏性在批量推理时因神经元联合导致计算密集，无法有效扩展。
method: 发现注意力头稀疏性在批量变化时保持稳定，并基于此开发可扩展的稀疏化方法。
result: 在批量推理中实现了高吞吐和低延迟，同时保持模型精度。
conclusion: Polar Sparsity通过利用注意力头稀疏性的批不变性实现了可扩展的稀疏推理。
---

## Abstract
Accelerating large language model (LLM) inference is critical for real-world deployments requiring high throughput and low latency. Contextual sparsity, where each token dynamically activates only a small subset of the model parameters, shows promise but does not scale to large batch sizes due to union of active neurons quickly approaching dense computation. We introduce Polar Sparsity, highlighting a key shift in sparsity importance from MLP to Attention layers as we scale batch size and sequence length. While MLP layers become more compute-efficient under batching, their sparsity vanishes. In contrast, attention becomes increasingly more expensive at scale, while their head sparsity remains stable and batch-invariant. We develop Selective Head Attention with hardware-efficient, sparsity-aware GPU kernels, delivering up to \(2.2\times\) end-to-end speedups for models like OPT, LLaMA-2 \& 3, Qwen, Mistral across various batch sizes and sequence lengths without compromising accuracy. To our knowledge, this is the first work to demonstrate that contextual sparsity can scale effectively to large batch sizes, delivering substantial inference acceleration with minimal changes, making Polar Sparsity practical for large-scale, high-throughput LLM deployment systems.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义
- **研究背景**：大规模语言模型（LLM）推理需要高吞吐和低延迟，上下文稀疏性（每个token动态激活少量参数）是一种有前景的加速手段，但现有方法仅在单查询场景有效，无法扩展到大批量推理。
- **核心问题**：在批量推理中，MLP层的神经活跃并集随批次增大迅速萎缩（趋近稠密计算），导致稀疏性收益消失；而注意力层成为主要瓶颈，但其头部（head）稀疏性在批处理时保持稳定且与批次大小无关。
- **整体意义**：本文首次证明上下文稀疏性可以扩展到大批量场景，通过聚焦注意力头部稀疏性设计高效内核，实现可扩展的高吞吐推理，为实际部署提供可行方案。

## 2. 论文提出的方法论
- **核心思想**：提出“极地稀疏性”（Polar Sparsity），揭示稀疏性重要性从MLP层向注意力层转移：MLP稀疏性随批量增大失效，而注意力头部稀疏性保持稳定，适合批量场景。
- **关键技术细节**：
  - **动态MLP稀疏**：使用轻量两层预测器（路由器）预测神经元激活，采用动态top-k机制（算法2）逐层调整阈值以保持目标召回率（99%），并设计融合索引与矩阵乘法的Selective GEMM内核（算法3），支持批处理GEMM，实现近线性加速（最高5.5×）。
  - **Selective Head Attention（SHA）**：使用单层预测器根据注意力输出范数选择top-k头部；修改FlashAttention算法（算法1），仅对激活头部进行索引和内存访问，通过定制Selective FlashAttention内核减少IO和计算（近线性加速，最高2.8×）。对于GQA模型表现为组稀疏。
  - **算法流程**：路由器通过监督学习训练（冻结LLM参数，使用400k tokens from WikiText-2）；解码时先预测活跃神经元/头部，再调用稀疏内核执行。

## 3. 实验设计
- **数据集与场景**：
  - **精度评估**：使用九个零样本下游任务（COPA, OBQA, PIQA, RTE, Winogrande, HellaSwag, MMLU, ARC-e, ARC-c）和 LongBench（指令调优模型）评估生成性能。
  - **吞吐量评估**：在不同批量大小（1~512）、序列长度（1920、3968、8192）下测量解码吞吐量。
- **基准模型**：OPT（6.7B/30B/66B）、LLaMA-2（7B/13B）、LLaMA-3.1（70B）、Mistral-7B、Qwen-2.5-14B-Instruct。
- **对比方法**：
  - 基准：稠密推理、DejaVu（仅MLP稀疏）。
  - 与近期稀疏方法对比（LLaMA-2-7B）：ProbePruning、ReLUfication、ProSparse、CATS、TEAL、GRIFFIN、R-Sparse（精度表3）。

## 4. 资源与算力
- **硬件**：NVIDIA DGX A100 80GB GPU节点集群（未明确节点数量），使用CUDA Graphs和Triton内核。
- **训练数据**：从WikiText-2训练集抽取400,000个token用于路由器训练。
- **计算量**：文中未报告具体训练时长或总GPU小时数；路由器训练使用AdamW优化器，20轮早停，批大小64，学习率1e-4。
- **说明**：未提供完整的算力明细（如总GPU小时、训练时间），但给出了足够复现的实验配置。

## 5. 实验数量与充分性
- **实验数量**：
  - 精度评估：覆盖6个模型、9个下游任务（表1-2），以及指令调优模型在MMLU-PRO和LongBench上的结果。
  - 吞吐量评估：多个模型在不同批量大小、序列长度下的吞吐量曲线（图6-7、12-15），并给出Tensor平行和Pipeline平行两种设置。
  - 消融实验：附录中路由器延迟对比（图10）、不同GPU家族性能（图11）、稀疏率对延迟的影响。
- **充分性与公平性**：
  - 对比方法完整，包括稠密、DejaVu及近年主流稀疏方法。
  - 结果展示均值，但未报告多次运行的标准差或置信区间；尽管如此，使用CUDA Graphs的吞吐测试波动很小。
  - 实验覆盖多模型、多尺度、大范围批量（最高512），论证充分。但未在超长上下文（>16k）上测试。

## 6. 论文的主要结论与发现
- **核心结论**：Polar Sparsity在批量推理中实现高达2.2×端到端加速（OPT-66B），且精度损失均在1%以内（临界阈值下）。对于非ReLU模型（如LLaMA-2/3），仅应用注意力头部稀疏仍获得1.85×速。
- **关键发现**：
  - MLP稀疏性在批量增大时快速消失（图2）。
  - 注意力头部稀疏性保持稳定，且模型越大可接受的稀疏度越高（图3）。
  - 定制稀疏内核（Selective GEMM/Selective FlashAttention）实现近线性加速，优于未优化的稀疏实现。
  - 与现有方法相比，Polar Sparsity在多个基准上达到或超越现有方法（表3），且能扩展到大批量。

## 7. 优点
- **方法创新**：首次揭示“极地稀疏性”现象，并据此设计批处理可扩展的稀疏推理方案，思路新颖且有实际意义。
- **高效实现**：开发硬件感知的Selective FlashAttention和Selective GEMM内核，利用了FlashAttention的IO-awareness，减少内存访问，实现真实加速（而非仅FLOPs减少）。
- **广泛适用**：支持多种模型架构（OPT、LLaMA、Mistral、Qwen），包括非ReLU激活模型，无需修改原模型权重。
- **实验扎实**：在多个模型、批量大小、序列长度下进行系统评估，与多种近期方法对比，结果可靠。

## 8. 不足与局限
- **实验覆盖局限性**：
  - 仅在上下文长度≤16k上验证，未扩展至百万token的超长上下文（如DeepSeek-R1）。
  - 仅评估贪心解码，未涵盖beam search或推测解码等场景。
  - 缺少多次运行统计误差（未提供误差条上大多数图表）。
- **应用限制**：
  - 小批量（batch size=1）下加速有限，甚至因路由器开销可能无增益。
  - 固定top-k阈值，未采用动态或任务感知的头部选择，可能导致较难任务精度下降。
  - GQA模型（如LLaMA-3.1-70B）组稀疏效果较弱（临界阈值62.5%），精度退化更快。
  - 精度略有下降（<1%），可能需进一步微调恢复。
- **其他**：路由器训练需要额外数据（400k tokens），且训练过程未给出详细耗时，可复现性略受影响。

（完）
