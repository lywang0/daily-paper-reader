---
title: Accelerating Linear Recurrent Neural Networks for the Edge with Unstructured Sparsity
title_zh: 利用非结构化稀疏性加速面向边缘的线性循环神经网络
authors: "Alessandro Pierro, Steven Abreu, Jonathan Timcheck, Philipp Stratmann, Andreas Wild, Sumit Bam Shrestha"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=UNrfYfbLZ3"
tags: ["query:edge-llm"]
score: 4.0
evidence: 面向边缘的线性RNN加速，使用非结构化稀疏性
tldr: 线性循环神经网络在边缘流式应用中具有潜力，但需要硬件感知优化。本文通过缩放研究探索非结构化稀疏性对线性RNN性能与效率的影响，发现高度稀疏的模型在推理计算预算下始终能达到更优的效率-性能帕累托前沿。该工作为边缘设备上的高效序列建模提供了硬件感知的设计准则。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 754, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1609, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1761, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1714, \"height\": 648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 837, \"height\": 669, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 848, \"height\": 714, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 853, \"height\": 644, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1748, \"height\": 953, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 846, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1658, \"height\": 674, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1405, \"height\": 766, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-unrfyfblz3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1604, \"height\": 558, \"label\": \"Table\"}]"
motivation: 线性RNN在边缘设备部署中需要硬件感知优化以降低延迟和能耗。
method: 通过缩放实验研究非结构化稀疏性对线性RNN推理效率与性能的影响。
result: 高稀疏度线性RNN在多种计算预算下均优于非稀疏对应模型。
conclusion: 非结构化稀疏性是一种有效的边缘端线性RNN加速策略。
---

## Abstract
Linear recurrent neural networks enable powerful long-range sequence modeling with constant memory usage and time-per-token during inference. These architectures hold promise for streaming applications at the edge, but deployment in resource-constrained environments requires hardware-aware optimizations to minimize latency and energy consumption. 
Unstructured sparsity offers a compelling solution, enabling substantial reductions in compute and memory requirements--when accelerated by compatible hardware platforms. 
In this paper, we conduct a scaling study to investigate the Pareto front of performance and efficiency across inference compute budgets.
We find that highly sparse linear RNNs *consistently* achieve better efficiency-performance trade-offs than dense baselines, with $2\times$ less compute and $36$\% less memory at iso-accuracy.
Our models achieve state-of-the-art results on a real-time streaming task for audio denoising.
By quantizing our sparse models to fixed-point arithmetic and deploying them on the Intel Loihi 2 neuromorphic chip for real-time processing, we translate model compression into tangible gains of $42\times$ lower latency and $149\times$ lower energy consumption compared to a dense model on an edge GPU.
Our findings showcase the transformative potential of unstructured sparsity, paving the way for highly efficient recurrent neural networks in real-world, resource-constrained environments.

---

## 论文详细总结（自动生成）

# 论文总结：利用非结构化稀疏性加速面向边缘的线性循环神经网络

## 1. 核心问题与整体含义

- **研究动机**：线性RNN（如S5）在序列建模中展现出强大能力，尤其在推理时具有恒定内存和线性时间复杂度，非常适合边缘设备上的流式应用（如音频降噪）。然而，在资源受限的边缘环境中，仍需进一步降低延迟和能耗。
- **核心问题**：非结构化稀疏性（权重和激活的稀疏性）能否以及如何在保持性能的同时显著提升线性RNN在边缘硬件上的效率？具体包括四个子问题：能否训练出高稀疏度的线性RNN并保持性能？稀疏模型在不同计算预算下是否优于密集模型？定点量化能否进一步压缩而不损害性能？非结构化稀疏性与量化能否转化为在神经形态芯片上的实际延迟与能耗收益？
- **整体含义**：该工作验证了非结构化稀疏性+定点量化+神经形态硬件协同设计可大幅提升线性RNN在边缘场景的部署效率，为实时流式AI应用提供了可行路径。

## 2. 方法论：核心思想与关键技术

- **核心思想**：通过权重剪枝（迭代幅度剪枝IMP）和激活稀疏化（用ReLU替换GELU并插入额外ReLU）获得高度稀疏的线性RNN；然后结合量化感知训练（QAT）进行8/16位定点量化；最后映射到Intel Loihi 2神经形态芯片，利用其事件驱动架构有效加速非结构化稀疏计算。
- **关键技术细节**：
  - **模型架构**：基于S5模型，包含线性循环SSM块和门控线性单元（GLU）组成的非线性混合块。状态更新公式为：`x_k = diag(¯A) ⊙ x_{k-1} + ¯B^T u_k`，`y_k = ¯C^T x_k + diag(¯D) ⊙ u_k`。
  - **权重剪枝**：采用ERK策略分配各层稀疏率，使用三次多项式调度在训练过程中逐步增加整体稀疏率至90%（目标稀疏度）。
  - **激活稀疏化**：将GLU块中的GELU替换为ReLU，并在S5隐藏层残差连接后以及实部分量后插入ReLU，以获得更高比例的零激活值。
  - **量化**：使用静态对称量化，权重8位（除循环权重16位），激活16位（W8A16）。训练时采用量化感知训练（QAT）与剪枝联合进行。
  - **硬件映射**：将S5模型重新映射到Loihi 2的神经核上：复数矩阵拆分为实部和虚部两个突触层；元素级运算（ReLU、BatchNorm、Hadamard积等）融合到单个可编程神经元层中；利用事件驱动架构仅处理非零激活值。

## 3. 实验设计

- **数据集与场景**：
  - 主要任务：Intel Neuromorphic Deep Noise Suppression (N-DNS) Challenge的音频降噪任务。数据来自Microsoft DNS Challenge，包含干净语音和噪声样本混合生成带噪语音。训练/验证集各60,000个30秒样本，测试集12,000个样本。
  - 附加实验：SpeechCommands V2-35（关键词识别）用于验证帕累托前沿的迁移性。
- **基准（Benchmark）**：
  - 对比方法：密集训练（带GELU）的S5模型族，以及Spiking-FullSubNet XL（N-DNS挑战Track 1冠军，SI-SNR 15.2 dB）。
- **对比方式**：
  - 帕累托前沿比较：在计算预算（有效MACs、内存占用量）下对比稀疏模型（90%剪枝+ReLU激活稀疏）与密集模型的SI-SNR性能。
  - 硬件实现对比：将选定的iso-accuracy模型（稀疏-8 vs 密集-3）部署到Loihi 2（稀疏+量化）与Jetson Orin Nano（密集FP32）上，测量延迟、能量、吞吐量。

## 4. 资源与算力

- 论文未明确报告具体的GPU型号、数量和训练时长。仅在软件部分提到使用JAX 0.4.30、JaxPruner和AQT库，训练50个epoch（Adam优化器，SSM参数学习率0.002，其余0.008，余弦退火调度，无预热）。
- 硬件平台：Intel Loihi 2（Oheo Gulch系统，N3C1芯片，运行NxCore 2.5.8）；Jetson Orin Nano 8GB（Jetpack 6.2，CUDA 12.4，MAXN SUPER功耗模式）。Loihi 2测量基于单芯片测试，无指定系统规模细节。

## 5. 实验数量与充分性

- **主要实验**：
  - 帕累托分析：训练了多种尺寸的密集模型（宽度因子k∈[0.25,1.0]）和稀疏模型（k∈[0.5,3.0]），共约12个模型变体（图4标注1-12），在N-DNS上评估。
  - 消融与分析：分析了权重稀疏与激活稀疏的交互（图5：稀疏模型激活稀疏度低于密集模型）；量化效果对比（图6：QAT vs PTQ，FP32 vs 静态量化 vs FXP模拟 vs Loihi真实结果）。
  - 硬件性能测量：在Loihi 2上运行稀疏-8模型，在Jetson上运行密集-3模型，测量多种执行模式（token-by-token fall-through、pipelined、批处理等）下的延迟、能量、吞吐量。
  - 批处理扩展性：在不同批大小（1-16）下对比Loihi 2（模型复制）与Jetson的能耗和延迟（图7）。
  - 实时刻度下能量估算：考虑8ms实时延迟预算后重新缩放能量。
  - 补充实验：关键词识别任务（SpeechCommands V2-35）验证帕累托前沿（图9）。
- **充分性与公平性**：
  - 实验覆盖了性能-效率帕累托前沿、量化影响、硬件性能多个维度，实验设计较为全面。
  - 公平性方面：稀疏模型与密集模型在iso-accuracy条件下对比（选择性能相当的模型对），但硬件部署时Loihi 2使用W8A16量化而Jetson使用FP32，作者指出这一不对称性可能导致部分对比偏向Loihi 2。此外，未在Jetson上优化定点实现来获得公平比较。
  - 实验数量适中，但消融实验仅涉及一个模型尺寸（变体6），覆盖略有限。多次随机测试平均结果（8个样本）增加了可靠性。

## 6. 主要结论与发现

- **稀疏优势显著**：高度稀疏（90%剪枝+ReLU激活稀疏）的线性RNN在相同性能下所需的计算量低至密集模型的1/2，内存降低36%；在更高精度时（与Spiking-FullSubNet XL对比）计算量降低3.2倍，内存降低5.37倍。
- **稀疏 vs 密集的帕累托前沿**：稀疏模型在多种计算预算下均构成帕累托前沿，即更高效地利用计算和存储资源。
- **硬件收益巨大**：在实时逐token处理模式下，Loihi 2相比Jetson Orin Nano实现42倍更低延迟、149倍更低能耗（每token）；在批处理单一序列时，Loihi 2仍保持3-8倍优势（取决于批大小）。
- **量化可行性**：QAT能有效恢复静态定点量化的性能损失；FXP模拟与Loihi芯片之间存在微小性能差异（主要由整数溢出处理差异导致）。
- **交互规律**：权重稀疏模型在训练中倾向于降低激活稀疏度（相比密集模型），且激活稀疏度随深度下降，暗示信息流补偿机制。

## 7. 优点

- **方法完整且实用**：从训练剪枝、激活稀疏、量化到硬件部署形成了完整压缩加速流程，且基于开源硬件（Loihi 2）和流行框架（JAX）可复现。
- **帕累托分析清晰**：通过系统性缩放实验展示了稀疏模型在不同计算预算下的优越性，数据可视化直观。
- **硬件-算法联合设计**：利用Loihi 2事件驱动架构对非结构化稀疏的特殊支持，成功将模型压缩转化为实际延迟和能耗收益，验证了协同设计价值。
- **任务选择合理**：音频降噪是典型的边缘流式应用，对实时性和能耗敏感，结果有现实意义。
- **开源代码**：论文附带GitHub仓库（IntelLabs/SparseRNNs），有利于社区复现和扩展。

## 8. 不足与局限

- **实验覆盖有限**：主要聚焦于音频降噪单一任务，仅在关键词识别上做了初步验证。未涉及更大规模的语言模型或多模态任务，通用性有待验证。
- **硬件对比不够公平**：Loihi 2使用8/16位量化，而Jetson使用FP32，未在Jetson上利用TensorRT或INT8优化来公平对比。作者承认“更优的Jetson实现可能获得更好能效”，降低了直接比较的可信度。
- **量化精度分析不足**：仅报告了SI-SNR的最终差异，未深入分析各层量化误差积累（虽在附录图11中给出但缺乏具体解释），量化策略（W8A16）对更大或更深模型的适用性未知。
- **激活稀疏性损失**：模型在权重稀疏时激活稀疏度下降，且随深度增加显著降低（图5），表明现有ReLU方案在更深度网络中效率可能减弱。未探索更先进的激活函数（如近似top-k）。
- **Loihi 2批处理局限**：Loihi 2批处理需要复制模型实例，资源随线性增长，仅适合小模型和小批大小。
- **未报告训练成本**：缺少训练稀疏模型的额外计算开销（虽然稀疏化主要在权重剪枝阶段，但需要多次前向/反向传播）。训练时资源消耗信息缺失。
- **统计不确定性**：硬件性能测量仅基于8个测试样本，未报告多次运行的标准差或置信区间。

（完）
