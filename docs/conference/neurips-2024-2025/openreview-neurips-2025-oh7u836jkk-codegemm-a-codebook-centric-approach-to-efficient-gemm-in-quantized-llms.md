---
title: "CodeGEMM: A Codebook-Centric Approach to Efficient GEMM in Quantized LLMs"
title_zh: CodeGEMM：量化LLM中基于码本的高效GEMM方法
authors: "Gunho Park, Jeongin Bae, Byeongwook Kim, Baeseong park, Jiwon Ryu, Hoseung Kim, Se Jung Kwon, Dongsoo Lee"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=OH7U836jKk"
tags: ["query:edge-llm"]
score: 7.0
evidence: 基于码本的GEMM核，实现硬件感知的LLM推理加速
tldr: CodeGEMM针对量化LLM推理中反量化操作导致访问延迟和缓存压力的问题，提出码本为中心的GEMM核，用预计算质心-激活内积的Psumbook替换反量化，推理时直接按索引累加，消除逐元素查找。该核支持延迟-内存-精度折中探索，在极低位模型上实现高效矩阵乘法，是算子加速的重要进展。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-oh7u836jkk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oh7u836jkk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1428, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oh7u836jkk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1444, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oh7u836jkk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1453, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-oh7u836jkk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1455, \"height\": 460, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-oh7u836jkk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 822, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oh7u836jkk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1448, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oh7u836jkk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1428, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oh7u836jkk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1431, \"height\": 479, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oh7u836jkk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1430, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oh7u836jkk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1239, \"height\": 515, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oh7u836jkk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1025, \"height\": 550, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oh7u836jkk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 789, \"height\": 618, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oh7u836jkk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1442, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-oh7u836jkk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1417, \"height\": 1251, \"label\": \"Table\"}]"
motivation: 量化LLM推理中反量化频繁获取质心，延迟高且缓存压力大。
method: 预计算质心与激活内积并存储为Psumbook，推理时直接索引累加。
result: 降低延迟，减少缓存压力，支持低位量化模型。
conclusion: 码本中心方法可高效实现量化模型推理。
---

## Abstract
Weight-only quantization is widely used to mitigate the memory-bound nature of LLM inference. Codebook-based methods extend this trend by achieving strong accuracy in the extremely low-bit regime (e.g., 2-bit). However, current kernels rely on dequantization, which repeatedly fetches centroids and reconstructs weights, incurring substantial latency and cache pressure. We present CodeGEMM, a codebook-centric GEMM kernel that replaces dequantization with precomputed inner products between centroids and activations stored in a lightweight Psumbook. At inference, code indices directly gather these partial sums, eliminating per-element lookups and reducing the on-chip footprint. The kernel supports the systematic exploration of latency–memory–accuracy trade-offs under a unified implementation.
On Llama-3 models, CodeGEMM delivers 1.83x (8B) and 8.93x (70B) speedups in the 2-bit configuration compared to state-of-the-art codebook-based quantization at comparable accuracy and further improves computing efficiency and memory subsystem utilization.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **背景**：大型语言模型（LLM）规模持续增长，部署时面临内存瓶颈。权重量化（weight-only quantization）是缓解内存瓶颈的常用手段。码本（codebook）量化在极低位宽（如2-bit）下表现优异，因其非均匀表示能力。
- **核心问题**：现有码本量化推理核依赖**反量化（dequantization）**，即每步计算都需从码本中获取质心向量并重构权重，导致大量内存访问和缓存压力，尤其当码本较大（如AQLM的1×16配置需1MB共享内存）超出GPU可编程缓存容量时，延迟急剧上升。
- **整体含义**：需要设计一个码本中心的高效GEMM核，避免反量化开销，同时保持精度和灵活性。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：用**预计算的质心-激活内积表（Psumbook）**替代反量化。在推理时，输入激活与所有质心向量的内积被预计算并存储在轻量级Psumbook中，代码索引直接获取部分和（partial sum），无需逐元素查找码本和重构权重。
- **关键技术细节**：
  - **Psumbook构建**：将输入矩阵按向量长度`v`分割，每个输入向量与码本中所有质心（共2^b个）计算内积，存入Psumbook。公式：\[p_{ji} = \sum_{k=0}^{v-1} c_{ik} \times x_{jk} \]，其中`i`为质心索引，`j`为输入向量索引。
  - **检索与累加**：权重的代码（code）直接作为索引，从Psumbook中取出对应的部分和并累加，得到最终输出。
  - **空间复杂度**：Psumbook大小为`O(m·2^b·tw/v)`，远小于码本`O(m·2^b·v)`（`tw`为tile宽度），可放入共享内存。
  - **计算复杂度**：常规GEMM为`O(MNK)`，反量化核相同；CodeGEMM降低为`O(MNK·m/v)`，因为`C_build + C_read ≈ O(MNK·m/v)`。
  - **统一核**：支持不同超参数组合（码本数m、向量长度v、群组大小g、位宽b），可在单一核内探索延迟-内存-精度权衡。

## 3. 实验设计
- **数据集**：
  - **精度评估**：WikiText-2（困惑度），及MMLU（5-shot）、WinoGrande、HellaSwag、ARC-Easy、ARC-Challenge（0-shot）等标准任务。
  - **延迟评估**：使用Llama-3.1（8B和70B）线性层的形状，在NVIDIA A100 80GB GPU上测量。
- **基准方法**：
  - **基线**：cuBLAS FP16。
  - **均匀量化**：FlexRound、GPTQ。
  - **码本化量化**：AQLM（1×16和2×8）、QuIP#、QTIP、VPTQ。
  - **优化**：LUT-GEMM（用于均匀量化），以及PV-Tuning（后量化校准）。
- **评估维度**：
  - 核级延迟（单个Transformer块内所有线性层之和）。
  - 吞吐量（tokens/s）与精度（平均准确率）。
  - 内存占用（平均每权重的bits）与延迟/精度关系。
  - 效率分析（TFLOPS、功耗GFLOPS/W、GPU利用率、内存利用率）。

## 4. 资源与算力
- **硬件**：NVIDIA A100 80GB GPU（单卡）。
- **软件**：CUDA内核，基于PyTorch和HuggingFace transformers库进行端到端推理。
- **训练时长**：文中未明确提及，因为CodeGEMM属于**后训练量化**，无需额外训练。量化过程（如AQLM优化码本）的时间未报告。但精度评估涉及多个模型和数据集，总计算量未量化。

## 5. 实验数量与充分性
- **实验数量**：丰富且系统。
  - **核级延迟**：对8B和70B模型报告了多种量化配置的延迟（表2）。
  - **精度与内存对比**：图4展示了困惑度 vs bits per weight，涵盖m1v4、m2v8、m3v8等组合，不同群组大小（g=128,32,8,-1）。
  - **吞吐量-精度对比**：图5和表4、表5展示了多种方法在8B和70B上的token/s与平均准确率。
  - **消融/敏感性分析**：附录中分析了Psumbook构建与读取周期占比、tile尺寸敏感性（tw∈{32,64,128}，th∈{2048,4096}）、更高位宽影响、批量大小敏感性（表9）以及多种矩阵形状（表10）。
- **充分性**：实验覆盖了不同模型规模、不同超参数、对比了当前最先进方法，并提供了统计误差（如功率测量中的二西格玛区间）。消融实验验证了tile选择和批大小的影响。整体充分且客观。

## 6. 主要结论与发现
- **性能提升**：在2-bit配置下，CodeGEMM相比AQLM在Llama-3.1-8B上实现**1.83x**端到端加速，在70B上实现**8.93x**加速，同时保持可比精度。
- **计算效率**：CodeGEMM的GFLOPS/W（19.36）显著高于AQLM-2x8（10.18）和cuBLAS（4.95），内存利用率也更高（49.8% vs 19.96%）。
- **灵活性**：通过调整m和v，可系统探索精度-延迟-内存权衡。细粒度群组归一化（g=32）在增加极少内存开销下可显著提升精度。
- **扩展性**：模型越大（70B vs 8B），CodeGEMM相对于AQLM的优势越明显，主要因为AQLM的大码本（1×16）在70B上引发严重反量化开销。

## 7. 优点
- **创新性**：将反量化替换为Psumbook预计算，从根本上消除重复的码本查找和质心读取，降低计算和访存复杂度。
- **硬件友好**：Psumbook显著小于码本，可放入GPU共享内存，减少DRAM访问；核设计利用CUDA Core，对延迟敏感的小批量场景尤其有效。
- **统一性**：单一内核支持丰富的码本超参数组合，便于用户在实际部署中权衡。
- **实验全面**：不仅报告延迟，还分析了效率和利用率，并附有详细的附录敏感性分析。

## 8. 不足与局限
- **码本大小限制**：Psumbook需常驻共享内存，极大码本（如b=16对应2^16个质心）超出当前GPU缓存容量，文中因此采用b=8并通过细粒度归一化恢复精度，牺牲了浅层码本容量。
- **大批量性能**：当批大小M>32时，CodeGEMM（基于CUDA Core）落后于Tensor Core的cuBLAS。这是CUDA Core核的常见局限，并非算法缺陷，但在高吞吐数据中心（大batch）场景中受约束。
- **仅针对小批量场景优化**：作者承认该方法在连续批处理中批量较大时效率下降，而实际生产中大batch场景常见。
- **精度对比不足**：虽然精度可比，但CodeGEMM在2-bit下平均准确率略低于AQLM-1×16（即使使用PV-Tuning后，63.96% vs 65.82%），且在一些任务（如MMLU）上仍有差距。说明在极低位宽下，大码本的表示能力仍有一定优势。
- **未报告训练成本**：量化码本的训练/更新时间未给出，对于实际部署中的量化成本评估不完整。
- **实验硬件单一**：仅在NVIDIA A100上测试，未验证其他GPU架构或边缘设备。

（完）
