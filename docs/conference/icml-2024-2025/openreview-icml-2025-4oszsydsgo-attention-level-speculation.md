---
title: Attention-Level Speculation
title_zh: 注意力级推测
authors: "Jack Cai, Ammar Vora, Randolph Zhang, Mark O'Connor, Mark C. Jeffrey"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=4OszSYdsgO"
tags: ["query:edge-llm"]
score: 7.0
evidence: 跨设备推测并行降低LLM推理中的注意力延迟
tldr: 长上下文LLM推理中注意力计算成为延迟瓶颈，传统并行策略收益递减。ALSpec引入注意力级推测并行，通过预测自注意力输出，在独立设备上提前执行后续操作，实现注意力和非注意力计算重叠。在128K上下文长度下注意力延迟降低5倍，端到端解码加速1.65倍。为异构计算环境下的高效推理提供新范式。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1769, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1526, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 706, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 867, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 837, \"height\": 1079, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 601, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1591, \"height\": 223, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1697, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 838, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1426, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1420, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1733, \"height\": 734, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1746, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1722, \"height\": 904, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1602, \"height\": 561, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 774, \"height\": 269, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1600, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 904, \"height\": 767, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 905, \"height\": 938, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 750, \"height\": 800, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 743, \"height\": 719, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 924, \"height\": 1011, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 900, \"height\": 954, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 750, \"height\": 582, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 742, \"height\": 555, \"label\": \"Table\"}]"
motivation: LLM处理长上下文时注意力计算延迟高，传统并行策略扩展性有限。
method: 提出注意力级推测并行（ALSpec），预测注意力输出并在单独设备上提前计算后续操作。
result: 在长上下文场景下，注意力延迟降低5倍，端到端解码速度提升1.65倍。
conclusion: ALSpec通过推测执行有效减轻了注意力瓶颈。
---

## Abstract
As Large Language Models (LLMs) grow in size and context length, efficient inference strategies are essential to maintain low-latency token generation. Unfortunately, conventional tensor and data parallelism face diminishing returns when scaling across multiple devices. We propose a novel form—attention-level speculative parallelism (ALSpec)—that predicts self-attention outputs to execute subsequent operations early on separate devices. Our approach overlaps attention and non-attention computations, reducing the attention latency overhead at 128K context length by up to 5x and improving end-to-end decode latency by up to 1.65x, all without sacrificing quality. We establish the fundamental pillars for speculative execution and provide an execution paradigm that simplifies implementation. We show that existing attention-approximation methods perform well on simple information retrieval tasks, but they fail in advanced reasoning and math. Combined with speculative execution, we can approximate up to 90% of self-attention without harming model correctness. Demonstrated on Tenstorrent's NPU devices, we scale up LLM inference beyond current techniques, paving the way for faster inference in transformer models.

---

## 论文详细总结（自动生成）

# 论文《Attention-Level Speculation》详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：大语言模型（LLM）的规模与上下文长度快速增长，推理时自注意力（self-attention）的计算开销随上下文线性增加，成为解码延迟的主要瓶颈。传统并行策略（张量并行、数据并行、流水线并行）在扩展设备数量时面临收益递减：张量并行存在通信开销，数据并行不降低单次延迟，流水线并行类似数据并行。
- **核心问题**：能否在不牺牲模型正确性的前提下，通过重叠注意力计算与其他操作（如前馈网络）来隐藏不断增长的注意力延迟？
- **整体含义**：本文提出一种新的推测并行范式——注意力级推测（Attention-Level Speculation, ALSpec），通过预测注意力输出，在单独设备上提前执行后续操作，实现注意力与非注意力的计算重叠，从而在长上下文场景下显著降低延迟，同时保持输出质量。

## 2. 方法论：核心思想、关键技术细节

### 2.1 核心思想
- **推测执行**：对每个Transformer层的自注意力输出进行推测：先用廉价近似方法（如attention sink）计算一个近似输出 $\tilde{A}_i$，同时并行计算精确输出 $A_i$。然后验证近似是否足够精确（L2距离小于阈值），若通过则采用近似结果并跳过精确路径的计算，从而实现重叠优化。
- **并行模式**：将设备分为两组，一组用于张量并行，另一组用于推测并行。推测成功时，后注意力操作（如前馈网络）与注意力计算完全重叠；推测失败时，回退到精确路径，延迟不超过数据并行。

### 2.2 关键技术细节
1. **低开销预测器**：采用attention sink（仅保留前4个token和最近S个token的窗口注意力），S远小于上下文长度（如128/256/512）。
2. **宽松验证机制**：基于Lipschitz连续性推导最终输出偏差的误差上界，采用简单阈值验证：$\|\tilde{A}_i - A_i\|_2 < \lambda \cdot \|A_i\|_2$，其中$\lambda$为超参数。实验表明$\lambda=0.10$时可在各项基准上保持正确性。
3. **推测式Flash Decode核心**：修改Flash Decode的KV缓存读取顺序，先读取第一个和最后一个chunk，将部分结果立即发送给接收设备作为推测输出，剩余部分继续计算完整注意力，从而几乎无额外开销地完成推测与验证。
4. **SGDC（静态图、动态并发）与优先级门控**：在保持主机端静态操作图的前提下，设备端根据优先级向量动态跳过或执行操作，实现推测路径的并发。两个设备间通过全收集（all-gather）同步优先级，通过以太网传输推测结果。

### 2.3 算法流程（文字说明）
- 对每一层：先执行前置操作（如LayerNorm），然后用attention sink计算推测输出$\tilde{x}$，在另一线程中执行后置操作（如前馈网络）。主线程同时计算精确注意力$x$。若$\|\tilde{x} - x\|_2 < \lambda \|x\|_2$，则提交推测结果，否则丢弃推测线程并重算后置操作。

## 3. 实验设计

### 3.1 使用的数据集/场景
- **正确性评估**：使用LM Evaluation Harness，涵盖多类任务：
  - QA: IFEval, GPQA (CoT)
  - 信息检索: SWDE, FDA
  - 数学: GSM8K (CoT), MATH (CoT), MGSM (CoT)
  - 长上下文: HotpotQA, RepoBench-P
  - 推理: MMLU PRO 子集（ECON, BUSINESS, PSYCH）带CoT
- **性能测量**：在Tenstorrent N150芯片上测量每层解码时所有内核的执行时间，推测不同上下文长度（1K~128K）下的延迟和吞吐量。同时也在NVIDIA H100 GPU上进行张量并行基准对比。
- **消融实验**：比较不同$\lambda$值（0.05~0.25）对任务准确率和推测命中率的影响；对比静态approximation（如全层attention sink、固定层attention sink）与动态ALSpec的正确性差异。

### 3.2 对比方法
- **基线**：未修改的原始模型（全注意力）。
- **静态近似**：仅使用attention sink（全部层或固定层子集）。
- **并行策略**：全张量并行（TP） vs. 张量并行+推测并行（SP+TP）。

## 4. 资源与算力

- **主要硬件**：Tenstorrent N150芯片（8个N150设备），Tenstorrent Metalium (TT-Metalium) 软件栈。每个N150芯片有72个Tensix计算核心，262 TFLOPS FP8性能。
- **GPU对比**：用于正确性评估的是NVIDIA A100或H100 GPU（BF16精度），性能估算在H100上通过SGLang+FlashInfer测量。
- **未说明训练时长**：论文侧重于推理加速，未涉及模型训练，因此未报告训练时长。

## 5. 实验数量与充分性

- **正确性评估**：在12个以上基准任务上评估，涵盖QA、IR、数学、长上下文、推理等，每个任务报告不同$\lambda$下的准确率与推测命中率（表1、表2）。此外还包含Llama 3.1 70B的验证（表2），表明方法在不同规模模型上一致有效。
- **性能评估**：在5种上下文长度（1K, 32K, 64K, 96K, 128K）和4种推测命中率（50%, 62.5%, 75%, 87.5%）下给出完整缩放曲线（图7），并与全TP对比。
- **消融实验**：通过“针在干草堆”实验（图3）说明动态推测优于静态近似；通过图2对比三种方法（全层attention sink、固定层attention sink、ALSpec）在多个任务上的正确性。
- **充分性**：实验覆盖了不同任务类型、不同模型规模、不同上下文长度，并提供了理论误差界（附录A）。但未在真实服务场景中测量端到端延迟（仅测量内核时间），且未与近期其他推测解码方法（如EAGLE、SpecInfer）直接比较。

## 6. 主要结论与发现

- **正确性保持**：在$\lambda=0.10$时，ALSpec在所有测试基准上达到与基线持平或更好的准确率，推测命中率大多超过50%（部分任务达90%）。
- **延迟显著降低**：在128K上下文长度下，注意力延迟降低5倍，端到端解码延迟提升1.65倍（87.5%推测命中率+4设备TP）。
- **优于静态近似**：动态推测避免了静态approximation在推理/数学任务上的质量下降。
- **通用性**：方法适用于不同层数、不同架构模型（Llama 3.1 70B验证）；可与张量并行组合，突破传统TP的缩放极限。

## 7. 优点

- **创新性**：首次将指令级值预测的思想引入Transformer推理，提出注意力级推测并行，开辟了新的加速维度。
- **实用性**：无需修改模型架构或重训练，仅需在推理层叠加预测-验证机制，实现简单。
- **理论支撑**：提供了基于Lipschitz连续性的误差界和概率误差界（附录A），为阈值选择提供理论依据。
- **实现优化**：推测式Flash Decode将推测与精确计算融合，几乎无额外开销；SGDC保证静态图动态并发，兼容现有框架。

## 8. 不足与局限

- **硬件依赖**：当前实现基于Tenstorrent N150的TT-Metalium，未给出通用GPU实现（仅估算）。在CUDA上的移植性和性能尚待验证。
- **实验覆盖**：性能测量仅基于内核时间，未考虑主机调度、通信延迟等实际开销；未与解码级推测（如推测解码）直接对比，也未测试混合使用场景。
- **推测命中率波动**：不同任务推测命中率差异大（如HotpotQA仅18%），阈值$\lambda$需针对应用场景调整。
- **偏差风险**：Lipschitz界推导有强假设（误差独立且零均值），实际误差方向可能不满足；验证阈值对最终输出偏差的影响在极端任务上可能仍需进一步分析。
- **应用限制**：仅限于单token解码阶段，不适用于预填充阶段；在推理稀缺资源场景下效果受限于设备数量。

（完）
