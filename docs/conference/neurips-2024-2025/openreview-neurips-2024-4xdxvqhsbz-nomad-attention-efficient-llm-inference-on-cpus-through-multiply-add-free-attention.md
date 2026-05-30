---
title: "NoMAD-Attention: Efficient LLM Inference on CPUs Through Multiply-add-free Attention"
title_zh: NoMAD-Attention：通过无乘加注意力在CPU上高效推理LLM
authors: "Tianyi Zhang, Jonah Wonkyu Yi, Bowen Yao, Zhaozhuo Xu, Anshumali Shrivastava"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=4xDxVQHsbZ"
tags: ["query:edge-llm"]
score: 9.0
evidence: 利用CPU SIMD寄存器进行硬件感知的LLM推理加速
tldr: 针对CPU上LLM推理中大量乘加运算的挑战，本文提出NoMAD-Attention，利用现代CPU的SIMD寄存器实现超低延迟查找，替代传统乘加操作。该方法无需微调即可应用于预训练模型，实验表明在CPU上显著加速注意力计算。该工作为在边缘设备CPU上部署LLM提供了一种硬件感知的高效方案。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-4xdxvqhsbz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1420, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4xdxvqhsbz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1435, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4xdxvqhsbz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1433, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4xdxvqhsbz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 290, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4xdxvqhsbz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 687, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4xdxvqhsbz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1434, \"height\": 409, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4xdxvqhsbz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1439, \"height\": 293, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-4xdxvqhsbz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1423, \"height\": 620, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-4xdxvqhsbz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 704, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-4xdxvqhsbz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 657, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-4xdxvqhsbz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 917, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-4xdxvqhsbz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1048, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-4xdxvqhsbz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1466, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-4xdxvqhsbz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1460, \"height\": 454, \"label\": \"Table\"}]"
motivation: CPU上LLM推理受限于大量乘加矩阵操作，需要利用SIMD寄存器特性实现高效计算。
method: 提出NoMAD-Attention算法，用SIMD寄存器查找替代注意力中的乘加运算，实现硬件感知的加速。
result: 实验证明无需微调即可在CPU上显著提升LLM推理速度，保持模型精度。
conclusion: 该方法有效利用CPU硬件特性，为边缘端LLM推理提供了实用的加速方案。
---

## Abstract
Large Language Model (LLM) inference on Central Processing Units (CPU) is challenging due to the vast quantities of  Multiply-Add (MAD) matrix operations in the attention computations. This paper highlights a rare gem in modern CPUs, Single-Instruction-Multiple-Data (SIMD) registers, which allows for ultra-low-latency lookups in a batch. We leverage this unique capability to propose NoMAD-Attention, an efficient attention algorithm that replaces MAD operations with in-register lookups. Through hardware-aware algorithmic designs, NoMAD-Attention achieves the computation of attention scores using repeated fast accesses to SIMD registers. NoMAD-Attention works with pre-trained attention-based LLMs without model finetuning. Extensive empirical evaluations demonstrate that NoMAD-Attention maintains the quality of the original LLMs well and speeds up the 4-bit quantized LLaMA-7B-based model by up to $2 \times$ at 16k context length.

---

## 论文详细总结（自动生成）

# NoMAD-Attention: 基于无乘加操作的CPU高效LLM推理方法

## 1. 论文的核心问题与整体含义

- **研究动机**：大语言模型（LLM）在CPU上的推理受到注意力机制中大量乘加（Multiply-Add, MAD）矩阵操作的严重制约。CPU并行核心有限，处理大量重复性MAD操作的效率远低于GPU，导致CPU推理延迟高，阻碍了LLM在边缘设备（如个人电脑、移动设备）上的普及。
- **背景观察**：现代CPU配备了单指令多数据（SIMD）寄存器（128–512位），支持超低延迟的批量查找（shuffle）。这一硬件特性在LLM推理中尚未被充分利用。
- **核心贡献**：提出NoMAD-Attention算法，利用SIMD寄存器的快速查找能力**完全替代注意力中的MAD操作**，无需对预训练模型进行微调，即可在CPU上实现显著加速，同时保持模型质量。

## 2. 方法论：核心思想与关键技术细节

- **核心思想**：将查询-键点积的计算转化为**基于SIMD寄存器的查找**，从而规避昂贵的MAD指令。
- **关键技术**：
  1. **产品量化（PQ）将点积转化为查找**：将键向量分割为S个子向量，每个子向量独立量化到16个质心（4-bit代码）。对查询，计算每个子向量与所有质心的点积，构建查找表（LUT）。键被替换为其量化代码，点积估计即为LUT中对应代码的累加。
  2. **将查找表压缩到SIMD寄存器**：受限于SIMD寄存器宽度（128位），若使用FP32存储点积，每个子量化器只能容纳4个质心。采用**8位动态量化**，将FP32点积映射到0-255整数，使得每个子量化器可容纳16个质心（16×8=128位），从而LUT可完全放入寄存器。
  3. **重组键缓存内存布局**：传统键缓存按行存储键向量，不利于SIMD shuffle。NoMAD将量化代码按**转置分块**方式存储（块大小32，每个子量化器的代码连续排列），配合shuffle指令实现批量查找（一次处理16个键，通过位操作处理另外16个键）。
  4. **FIM指导的质心学习**：使用Fisher信息矩阵（FIM）对重建误差加权，优先保证重要键的编码质量，减少量化对模型质量的损害。

- **算法流程**（以解码单步为例）：
  - 对当前键向量kt，计算其量化代码并插入键代码缓存。
  - 对当前查询qt，为每个子量化器s计算动态量化后的LUT（16个8位值）。
  - 初始化累加器（16位无符号整数，防溢出）。
  - 以32个键为块并行处理：加载LUT到SIMD寄存器，通过shuffle指令批量查找，累加。
  - 反量化累加结果，除以√d，经softmax得到注意力分数。

## 3. 实验设计

- **模型**：LLaMA-7B、LLaMA-13B、LLaMA-2-7B、LLaMA-2-13B（质量评估）；CodeLlama-7B（效率评估，16-bit及4-bit权重）。
- **数据集与任务**：
  - 困惑度：WikiText-2、C4（上下文长度2048）。
  - 零样本准确率：SciQ、Arc Easy、Arc Challenge、HellaSwag、WinoGrande、PIQA。
  - 附加评估：MMLU（STEM/社会科学/人文/其他）、GPQA、MGSM（英语）。
- **对比方法**：原始Attention（基于MAD），以及整数量化键缓存（INT8/INT4）作为消融对比。
- **效率指标**：解码延迟、吞吐量（tokens/sec）、首token时间（prompt处理）。
- **消融实验**：
  - 不同子向量维度（dsub = 1, 2, 4）。
  - FIM指导聚类 vs. 无FIM聚类。
  - 8-bit量化LUT vs. 32-bit原始LUT。
  - 延迟分解（各部分耗时占比）。

## 4. 资源与算力

- **硬件**：
  - 速度/吞吐量测试：Intel Xeon E5-2695 V3（14核，支持AVX2），512GB DDR4 RAM。
  - 质量/困惑度测试：2块NVIDIA A100-40GB GPU。
- **软件框架**：基于llama.cpp、FAISS（C++/C实现）；PyTorch + HuggingFace Transformers用于质心学习及GPU原型。
- **算力开销**：质心学习耗时较低（例如LLaMA-7B dsub=1需4分钟保存激活与梯度 + 27分钟加权k-means），但论文未报告完整训练或推理的总算力。

## 5. 实验数量与充分性

- **实验组数**：覆盖4个LLM系列、7个下游任务、3种dsub配置、2种权重精度、多种消融（FIM、LUT量化、延迟分解、额外评估共约20+组子实验）。
- **充分性**：实验设计较全面，既验证了质量保持（困惑度+准确率），又验证了效率提升（延迟/吞吐量），并深入分析了各组件贡献（延迟分解）和压缩策略影响（消融表）。
- **公平性**：对比基准为原始Attention（实现于llama.cpp），并使用相同软硬件环境；附录还对比了整数量化键缓存，证明NoMAD在类似压缩率下质量更好且速度更快。但缺少与其他近似注意力方法（如FlashAttention的CPU移植、稀疏注意力）的直接对比。

## 6. 主要结论与发现

- **质量保持**：dsub=1时困惑度和准确率几乎无损（如LLaMA-7b WikiText-2困惑度5.68 vs 5.74）；dsub=2时轻微下降；dsub=4时下降较明显但仍有可用性。
- **推理加速**：在4-bit CodeLlama-7b上，16k上下文长度下，解码吞吐量提升1.78×（dsub=1）至2.07×（dsub=4）；16-bit模型提升1.46×–1.56×。提示处理（16k）加速1.63×–1.79×。
- **延迟分解**：注意力点积计算延迟降低5.24×–14.77×，成为不随上下文增长的主要瓶颈。
- **FIM聚类**有效提高模型质量（dsub=4时困惑度从21.39降至9.23）。
- **8-bit LUT量化**几乎不引入额外质量损失。

## 7. 优点

- **硬件感知设计**：深入利用CPU SIMD寄存器特性（shuffle指令的低延迟、高吞吐），将计算范式从“乘加”转为“查找”，创新性强。
- **无需微调**：可直接应用于预训练模型，兼容多种注意力变体（GQA、ALiBi），实用范围广。
- **高质量保持**：通过FIM加权聚类、动态LUT量化等技巧在低压缩率下保持模型能力。
- **开源实现**：基于llama.cpp，便于集成和复现。
- **低内存开销**：码本仅需数MB（如LLaMA-7B为8.4MB），远小于模型大小。
- **广泛验证**：涵盖多种模型规模、任务类型，消融实验完整，并额外测试了Llama-3。

## 8. 不足与局限

- **硬件依赖性**：方法仅适用于支持SIMD的CPU（AVX2/NEON），不适用于GPU、TPU或低端嵌入式处理器。
- **质量-速度权衡**：dsub增大（更高压缩）导致质量显著下降，限制了压缩上限；dsub=4在部分任务上准确率下降>5%。
- **校准数据需求**：需要少量校准数据（16条2048长度序列）学习码本，增加一步预处理。
- **实验覆盖不足**：未与主流近似注意力方法（如FlashAttention-CPU、Token Merging）对比；仅测试LLaMA/CodeLlama系列，未覆盖其他架构（如GPT-NeoX、Falcon、Mistral）。
- **长上下文扩展性**：实验最长16k上下文，未测试更长（32k、64k）场景下的表现；随上下文增加，shuffle操作次数线性增长，绝对延迟仍可能成为瓶颈。
- **仅关注注意力头**：未讨论对其他组件（MLP、LayerNorm）的潜在协同优化。
- **重复性限制**：论文提及代码为xMAD.ai专有，未直接开源（但算法描述足够详细）。

（完）
