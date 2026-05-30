---
title: "BlockDialect: Block-wise Fine-grained Mixed Format Quantization for Energy-Efficient LLM Inference"
title_zh: "BlockDialect: 面向节能LLM推理的块级细粒度混合格式量化"
authors: "Wonsuk Jang, Thierry Tambe"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Y0yXuQtPn8"
tags: ["query:edge-llm"]
score: 9.0
evidence: 面向节能LLM推理的块级混合格式量化，硬件感知细粒度缩放
tldr: BlockDialect提出了一种块级细粒度混合格式量化技术，通过为每个块从格式书中分配最优数字格式（如FP4变体）来更好地表示数据分布，从而降低LLM推理的内存和计算开销。该方法采用两阶段策略，在保持精度的同时显著提升能效，适用于边缘设备部署。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-y0yxuqtpn8/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 773, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y0yxuqtpn8/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 868, \"height\": 670, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y0yxuqtpn8/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 700, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y0yxuqtpn8/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 780, \"height\": 633, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y0yxuqtpn8/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1786, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y0yxuqtpn8/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 862, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y0yxuqtpn8/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1784, \"height\": 1231, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y0yxuqtpn8/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1776, \"height\": 588, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-y0yxuqtpn8/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1357, \"height\": 454, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1576, \"height\": 688, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 803, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 843, \"height\": 452, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 720, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 843, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 756, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 758, \"height\": 168, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1756, \"height\": 562, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1756, \"height\": 383, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 872, \"height\": 668, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 714, \"height\": 480, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1756, \"height\": 1498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1756, \"height\": 1498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-y0yxuqtpn8/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1756, \"height\": 1498, \"label\": \"Table\"}]"
motivation: LLM规模增大导致内存和计算成本高昂，现有量化方法难以捕捉细粒度块数据分布。
method: 提出块级细粒度混合格式量化，为每个块从格式书中分配最优格式，并引入FP4变体格式书DialectFP4。
result: 实验表明，BlockDialect在保持模型精度的同时显著降低了推理能耗和内存占用。
conclusion: BlockDialect通过硬件感知的混合格式量化实现了高效的LLM推理。
---

## Abstract
The rapidly increasing size of large language models (LLMs) presents significant challenges in memory usage and computational costs. Quantizing both weights and activations can address these issues, with hardware-supported fine-grained scaling emerging as a promising solution to mitigate outliers. However, existing methods struggle to capture nuanced block data distributions. We propose BlockDialect, a block-wise fine-grained mixed format technique that assigns a per-block optimal number format from a formatbook for better data representation. Additionally, we introduce DialectFP4, a formatbook of FP4 variants (akin to dialects) that adapt to diverse data distributions. To leverage this efficiently, we propose a two-stage approach for online DialectFP4 activation quantization. Importantly, DialectFP4 ensures energy efficiency by selecting representable values as scaled integers compatible with low-precision integer arithmetic. BlockDialect achieves 10.78% (7.48%) accuracy gain on the LLaMA3-8B (LLaMA2-7B) model compared to MXFP4 format with lower bit usage per data, while being only 5.45% (2.69%) below full precision even when quantizing full-path matrix multiplication. Focusing on how to represent over how to scale, our work presents a promising path for energy-efficient LLM inference.

---

## 论文详细总结（自动生成）

# 论文总结：BlockDialect: Block-wise Fine-grained Mixed Format Quantization for Energy-Efficient LLM Inference

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大语言模型（LLM）规模快速增长，导致内存占用和计算成本高昂。量化（Quantization）是降低这些成本的重要技术，但现有方法难以同时处理权重和激活值中的离群值（outliers），且通常只量化权重，激活值仍保持高精度，限制了能效提升。
- **背景**：硬件支持的细粒度块量化（如MX格式）逐步成熟（OCP标准、NVIDIA Blackwell支持），但现有块量化在固定格式（如FP4）下无法适应每个数据块的独特分布，存在浪费或低估表示范围的问题。
- **核心观察**：“如果一组数据值得拥有自己的缩放因子，为什么不能拥有自己的数字格式？”——传统方法关注“如何缩放”（how to scale），本文转向“如何表示”（how to represent）。

## 2. 方法论

### 核心思想
- **BlockDialect**：一种块级细粒度混合格式量化技术。将每个张量划分为细粒度块（如块大小32），为每个块从“格式书”（formatbook）中分配一个最优数字格式（称为“方言”），从而更精确地匹配块内数据分布。
- **DialectFP4**：一组16种FP4变体（方言）构成的格式书，覆盖不同的最大幅度和大幅值分布，最小粒度为0.5，与FP4 E2M1基格式共享多数值，便于硬件高效整型运算。

### 关键技术细节
1. **格式书设计**：基于对LLaMA3等模型的块级分布分析，FP4 E2M1的矩阵级分布匹配良好，但各块的最大幅度均匀分布，且部分块偏离整体趋势。因此设计16种FP4变体，满足：
   - 覆盖所有可能的块最大幅度（避免浪费/低估），
   - 不同的大幅值分布（优先准确表示大幅值），
   - 硬件高效：0.5粒度，多数值与FP4一致，便于4位无符号整数运算。
2. **离线权重量化**：权重块的最优方言通过预计算MSE选出，预量化后存储4位索引和4位方言ID。
3. **在线激活量化（两阶段方言选择）**：
   - **预处理**：将激活值转换为5位定点（3位整数+2位小数），范围[0,7.5]。
   - **第一阶段**：根据块的截断最大幅度（`BlockMaxTrunc`）选择一对共享最大幅度的方言。
   - **第二阶段**：通过逻辑运算统计落在每个方言“有利区间”（beneficial range）内的元素数量，选择计数更大的方言。有利区间定义为两个方言差异值与其相邻值的中点区间。通过预设计二进制逻辑（如5位比较）实现并行计数，避免了逐个MSE计算的开销。
4. **MAC运算**：量化后的4位值对应0.5*[0..15]的无符号整型，乘法使用4位无符号整数乘法后右移2位，累加后转换为FP16。所有乘积共享同一指数和，高效实现点积。
5. **全路径量化**：不仅量化线性层（激活×权重），还量化注意力块中的激活×激活（QK及score×V），通过自定义KV缓存结构（4位块存+高精度尾部）处理子通道量化问题。

## 3. 实验设计

### 数据集与任务
- **评估任务**：7个零样本常识推理任务（LAMBADA, HellaSwag, BoolQ, PIQA, WinoGrande, ARC-easy, ARC-challenge），以及WikiText2上的困惑度（PPL）。
- **额外实验**：GLUE（6任务）、MMLU，以及不同规模/架构模型（OPT-6.7B、LLaMA3-1B、Phi-2.7B、MobileLLM-125M、GPT2-1.5B）。

### Benchmark与对比方法
- **基线**：
  - MXFP4（硬件支持缩放，块大小16/32/64）
  - LLM-FP4（软件缩放，矩阵级混合格式）
  - Quarot（通过Hadamard矩阵减少离群值，W4A4或W4A4KV4）
  - NVFP4（NVIDIA浮点块缩放，FP8缩放因子+FP4数据）
  - 全精度FP16
- **配置**：块大小默认32，同时测试16、64以及动态分配。评估线性层（Linear）和全路径（All，包括注意力）。

### 主要实验结果
- **线性层**：BlockDialect-32在LLaMA3-8B上PPL 7.05，准确率72.24%，仅比全精度低2.21%；比MXFP4-32（PPL 8.23，准确率68.31%）提升显著，且有效位宽更低（4.28 vs 4.16）。
- **全路径**：BlockDialect-32在LLaMA3-8B上PPL 7.87，准确率68.57%，比全精度低5.88%，优于MXFP4-16（PPL 18.84，准确率58.22%），且比Quarot W4A4KV4（准确率66.01%）更优。
- **与其他模型**：LLaMA2-7B、Mistral-7B、OPT-6.7B均一致优于基线。

### 消融实验
- **块大小**：块越小精度越好，但有效位宽增加。动态分配（对下投影、QK等敏感层用小块）可平衡。
- **方言数量**：16种最佳，8种不足，24种性能下降。
- **与MSE对比**：本文两阶段方法性能接近精确MSE选择（PPL差距<0.04，准确率<0.6%）。
- **与SmoothQuant结合**：小幅提升（PPL降低0.09~0.48），但并非完全正交。
- **块形状**：1D与2D块在精度上无明显优劣。

## 4. 资源与算力

- **GPU**：所有实验在单张NVIDIA H100 GPU上完成。
- **训练/推理时长**：论文未明确给出训练或推理耗时。
- **硬件综合**：使用Synopsys Design Compiler在45nm Nangate库和130nm SkyWater库下综合MAC单元和量化/反量化逻辑，以评估面积、功耗（0.5GHz或100MHz），但未涉及推理全过程耗电测量。

## 5. 实验数量与充分性

- **实验数量**：约20+组，覆盖：
  - 3个主流7B级模型（LLaMA3-8B, LLaMA2-7B, Mistral-7B）的线性层/全路径对比
  - 7个零样本任务和PPL
  - 块大小、方言数、块形状、与SmoothQuant结合、与MSE对比、动态块分配等消融
  - 扩展到OPT-6.7B、小模型（LLaMA3-1B, Phi-2.7B, MobileLLM-125B, GPT2-1.5B）以及GLUE/MMLU任务
- **充分性**：实验充分且客观。对比方法均使用官方代码和默认配置，保证了公平性。消融实验覆盖了关键设计维度。但缺少对更大模型（如70B）的评估，部分消融分析（如块形状对解码阶段的影响）仅做了推断。

## 6. 主要结论与发现

- **主要结论**：BlockDialect通过为每个细粒度块选择最优的FP4变体，显著优于固定格式的MXFP4，且有效位宽更低。在4位量级下，全路径量化精度损失仅约2-5%。
- **发现**：
  - “如何表示”比“如何缩放”更重要：通过方言调整数值分布可更精确匹配块内数据。
  - 两阶段方言选择方法在效率上接近MSE精确选择，且硬件开销极低。
  - 方言格式书的16种变体能够平衡动态范围覆盖和大数值分布灵活性。
  - 使用4位整数MAC实现FP4级能效，同时支持5位中间表示的精度。

## 7. 优点 (方法/实验设计亮点)

- **创新性**：将“混合格式”从矩阵级细化到块级，并设计方言格式书，是首个在硬件友好框架下实现块级自适应格式的方法。
- **硬件实用性**：方言仅修改1-2个数值，保证0.5粒度和多数值复用，兼容4位整数乘法，综合功耗和面积接近原生FP4 MAC。
- **高效在线量化**：两阶段逻辑运算避免了实时MSE计算，硬件复杂度低（约5个时钟周期，功耗/面积与32个MAC相当）。
- **全路径覆盖**：不仅量化线性层，还量化注意力中的激活×激活，并设计KV缓存方案，实现了真正低精度的端到端推理。
- **实验全面**：跨多个模型、任务、块大小进行对比，消融分析充分，并与SmoothQuant组合探索协同效应。

## 8. 不足与局限

- **缩放因子开销**：由于每块需存储4位方言ID（加上5位共享指数），总开销9/块大小，比MX的5/块大小稍高，但有效位宽仍低于或等于MX。
- **大规模模型缺失**：未测试>10B的模型（如LLaMA-13B, 70B），实际部署中离群值可能更严重，泛化性待验证。
- **解码阶段优化**：KV缓存结构在处理长序列时仍有一定高精度元素（最多block size个），对极致长上下文可能仍有存储开销。
- **SmoothQuant协同有限**：两者并非完全正交，说明离群值处理方法可能存在冗余，未来可进一步研究联合优化。
- **实验完备性**：未报告训练/推理时间；综合结果基于45nm/130nm库，与先进工艺（如7nm）有差距；未进行实际芯片流片验证。
- **方言数量固定**：16种方言基于经验设定，理论上模型间最优数量可能不同，缺乏自动化选择机制。

（完）
