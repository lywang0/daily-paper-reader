---
title: "SPD: Sync-Point Drop for Efficient Tensor Parallelism of Large Language Models"
title_zh: SPD：面向大语言模型高效张量并行的同步点丢弃
authors: "Han-Byul Kim, Duc N.M Hoang, Arnav Kundu, Mohammad Samragh, Minsik Cho"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=23zxLtvder"
tags: ["query:edge-llm"]
score: 7.0
evidence: 减少张量并行中的通信开销，面向分布式LLM推理
tldr: 大规模LLM分布式推理中张量并行的通信开销成为瓶颈。SPD通过选择性丢弃注意力输出的同步点，设计无通信的块结构，并根据注意力块敏感性采用不同策略。实验表明在保持模型质量的同时，显著降低通信延迟并提升扩展性。该方法为异构计算环境下的高效LLM推理提供了优化手段。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1759, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1761, \"height\": 241, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1767, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 535, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 854, \"height\": 851, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 837, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1773, \"height\": 1198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1747, \"height\": 772, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1745, \"height\": 349, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-23zxltvder/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 710, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-23zxltvder/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 563, \"height\": 203, \"label\": \"Table\"}]"
motivation: 张量并行中的通信开销限制了LLM分布式推理的可扩展性和低延迟。
method: 提出同步点丢弃（SPD），在注意力输出上选择性丢弃同步，并设计无通信块。
result: 在多种LLM和配置下，通信开销降低，端到端推理延迟减少。
conclusion: SPD通过减少同步开销有效提升了张量并行的效率。
---

## Abstract
With the rapid expansion in the scale of large language models (LLMs), enabling efficient distributed inference across multiple computing units has become increasingly critical. However, communication overheads from popular distributed inference techniques such as Tensor Parallelism pose a significant challenge to achieve scalability and low latency. Therefore, we introduce a novel optimization technique, Sync-Point Drop (SPD), to reduce communication overheads in tensor parallelism by selectively dropping synchronization on attention outputs. In detail, we first propose a block design that allows execution to proceed without communication through SPD. Second, we apply different SPD strategies to attention blocks based on their sensitivity to the model accuracy. The proposed methods effectively alleviate communication bottlenecks while minimizing accuracy degradation during LLM inference, offering a scalable solution for diverse distributed environments: SPD offered about 20\% overall inference latency reduction with < 1\% accuracy regression for LLaMA2-70B inference over 8 GPUs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义
- **研究背景**：大规模语言模型（LLM）的分布式推理广泛采用张量并行（Tensor Parallelism, TP），但TP需要在设备间频繁执行集体通信（sync-point），成为性能瓶颈，尤其当设备间带宽受限时，通信延迟严重影响推理延迟。
- **核心问题**：如何在保持模型质量的前提下，降低TP中的通信开销，提升分布式推理的效率和可扩展性。
- **整体含义**：提出一种名为**Sync-Point Drop (SPD)** 的系统-模型协同优化技术，通过选择性丢弃注意力输出后的同步点，大幅减少通信量，同时通过块级敏感度分析和针对性恢复策略，将精度损失控制在可接受范围内。

## 2. 方法论

### 核心思想
- 保留TP的计算并行性，但移除注意力输出后的 all-reduce 同步操作，使各设备独立计算，避免通信等待。
- 设计新的块结构，确保即使缺少同步，前向传播仍能保持与TP近似的数值结果。
- 根据不同块对SPD的敏感度，采用差异化策略（零样本丢弃、蒸馏、头分组）恢复精度。

### 关键技术细节

#### (a) 无偏置线性层的块设计（图3a）
- **MLP输入**：将残差连接 `X` 与当前设备的注意力输出 `Y_i` 相加作为MLP输入（`X + Y_i`），避免缺少其他设备信息导致的严重偏差。
- **MLP输出**：拆解原始残差连接：`Y_i` 作为注意力输出残差加在同步前；`X` 作为块输入残差加在同步后，使得最终输出为 `X + ΣY_i + ΣZ_i`（与全TP一致）。

#### (b) 有偏置线性层的块设计（图3b）
- 由于输出投影层的偏置无法按列切分，需进一步解耦：偏置残差（`b`）加在同步后，而部分权重乘积（`P_i`）加在同步前，形成 `X + ΣP_i + b + ΣZ_i` 的形式。

#### (c) 块级敏感度识别（图4、算法1）
- 利用校准数据（WikiText2训练集128样本，序列长度2048），通过渐进替换法：对第 `i` 块，先对 `i+1` 到最后一块应用SPD，再对 `i` 块应用SPD，测量困惑度差异作为敏感度。
- 将块分为三类：
  - **ISB（不敏感块）**：敏感度 ≤ τ1，直接零样本丢弃同步。
  - **SB（敏感块）**：τ1 < 敏感度 ≤ τ2，应用块到块蒸馏（B2B）恢复精度。
  - **ESB（极度敏感块）**：敏感度 > τ2，先进行注意力头分组初始化（HG），再蒸馏。

#### (d) 块到块蒸馏（B2B）
- 以原TP块为教师，SPD块为学生，仅训练指定块的参数；使用均方误差（MSE）损失，优化目标 `min MSE(SPD(θ_spd, x), TP(θ, x))`，学习率 `5e-5`（LLaMA2）或 `1e-6`（OPT），10个epoch。

#### (e) 注意力头分组初始化（HG）
- 针对ESB，利用校准数据计算每个注意力头的注意力得分，通过最大化同一设备内各头得分的欧氏距离，将功能分散的头分配到同一设备。
- 进一步匹配MLP分区：选择使MLP输出范数（加残差前）最大的组合，确保各设备内自注意力与MLP协调工作。
- 物理上重排序QKV和输出投影层权重，使对应头落在同一设备上。

## 3. 实验设计

### 数据集
- **校准数据**：WikiText2训练集，随机128个样本，序列长度2048。
- **评估数据**：
  - 零样本任务：ARC、HellaSwag、LAMBADA、PIQA、SciQ、WinoGrande（平均准确率）。
  - MMLU任务（附录中展示）。

### Benchmark
- **模型**：LLaMA2（7B,13B,70B）和OPT（6.7B,13B,30B,66B）。
- **并行设置**：4-GPUs 和 8-GPUs 分布式推理（大模型仅8-GPUs）。
- **带宽条件**：高带宽（HBW，300GB/s）和低带宽（LBW，10GB/s）；2节点设置中节点间50GB/s。
- **对比方法**：
  - 无SPD（全TP，基线）。
  - 零样本丢弃（ZS）：对所有块直接应用SPD。
  - ZS + 蒸馏（ZS+B2B）：对SB和ESB应用蒸馏。
  - ZS + 蒸馏 + 头分组（ZS+B2B+HG）：对ESB先头分组再蒸馏。

## 4. 资源与算力
- **硬件**：NVIDIA A100-80G GPU 节点。
- **带宽控制**：低带宽通过关闭CUDA-direct link实现（10GB/s）。
- 文中未明确说明训练总时长、总GPU数量或使用的具体节点数量（仅提到1节点×8GPU和2节点×4GPU配置）。蒸馏和头分组使用校准数据，预处理成本较低，但未量化。

## 5. 实验数量与充分性
- **实验组数**：覆盖3个模型系列（LLaMA2, OPT）共7种规模，2种并行度（4/8 GPU），2种带宽（HBW/LBW），2种节点配置，以及多种SPD比例（25%~100%）。每个实验报告了准确率和加速比曲线。
- **消融实验**：
  - 块设计选择：比较不同残差连接位置对困惑度的影响（表1a,1b），验证设计的正确性。
  - 策略对比：ZS vs ZS+B2B vs ZS+B2B+HG，清晰展示各策略的恢复效果。
- **充分性与公平性**：实验较为充分，多模型、多设置下结果一致；对比了不同SDP比例下的变化趋势，且使用相同校准和评估流程。但未与系统级优化（如all-reduce算法改进）或模型级量化/剪枝作联合比较，可能忽略组合优化效果。

## 6. 主要结论与发现
- SPD能显著降低通信延迟，尤其低带宽下收益更大：对LLaMA2-70B在LBW下70% SPD获得~19.7%加速，零样本准确率下降<1%。
- 零样本丢弃即可安全应用于大部分块（ISB比例随模型增大而增加：LLaMA2-70B有75% ISB，OPT-66B有84%），无需额外调优。
- 块到块蒸馏有效恢复敏感块精度，头分组初始化进一步改善极度敏感块（主要出现在小模型中）。
- OPT模型因更高冗余性对SPD更鲁棒，几乎所有块可零样本应用而不明显损失精度。
- 加速效果在跨节点环境（2节点）同样显著，超过10%加速。

## 7. 优点
- **创新性**：从系统-模型协同角度直接移除通信同步点，机制简单而有效，不同于传统仅优化通信操作的方法。
- **模块化策略**：基于敏感度分类，避免全面蒸馏或头分组的额外开销，实现细粒度精度-效率权衡。
- **强实验支撑**：涵盖多种模型、并行配置、硬件带宽，结果普遍一致；消融实验验证了设计选择和策略的有效性。
- **实用性**：可与其他分布式并行（数据并行、流水线并行）结合（附录C.2），适用于异构环境。
- **低校准成本**：仅需128样本，蒸馏仅训练少量块参数，头分组仅需重新排权重，无需大规模重训练。

## 8. 不足与局限
- **适用范围**：仅针对张量并行中的注意力输出同步点，不直接解决其他同步点（如MLP输出 all-reduce）或跨节点通信瓶颈。
- **校准依赖**：敏感度识别和头分组依赖于校准数据分布，若校准数据与真实推理数据分布差异大，可能影响效果；未测试分布偏移下的鲁棒性。
- **蒸馏开销**：对于敏感块需要额外蒸馏步骤（10 epoch，128样本），虽然规模小，但仍需一定计算资源；大规模模型（如70B）也可能因块数多而累积成本。
- **长文本推理**：实验仅针对固定序列长度128或2048，未讨论生成阶段（尤其自回归解码）中SPD的影响。由于SPD改变注意力输出，可能影响KV缓存和长距离依赖，可能出现误差累积。
- **精度损失权衡**：虽然总体准确率下降<1%，但在某些任务上可能有较大波动（如LLaMA2-7B在100% SPD时下降>5%）。文中仅报告平均准确率，未给出每个任务的具体差异。
- **与其他优化的兼容性**：未实验SPD与量化、剪枝等模型级优化联合使用的效果，理论上可能存在协同或干扰（如量化后的精度损失可能被SPD放大）。
- **理论分析缺失**：未提供SPD导致数值误差的理论上界或对注意力模式影响的分析，主要依赖经验结果。

（完）
