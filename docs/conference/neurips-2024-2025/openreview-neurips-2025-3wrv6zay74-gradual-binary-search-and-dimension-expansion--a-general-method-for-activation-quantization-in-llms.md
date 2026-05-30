---
title: "Gradual Binary Search and Dimension Expansion : A general method for activation quantization in LLMs"
title_zh: 逐步二分搜索与维度扩展：一种LLM激活量化的通用方法
authors: "Lucas Maisonnave, Cyril Moineau, Olivier BICHLER, Fabrice Rastello"
date: 2025-05-08
pdf: "https://openreview.net/pdf?id=3Wrv6Zay74"
tags: ["query:edge-llm"]
score: 7.0
evidence: 面向边缘LLM部署的激活量化方法
tldr: 针对边缘设备上LLM激活量化异常值问题，本文利用Hadamard矩阵比随机旋转更有效减少异常值的理论优势，结合逐步二分搜索和维度扩展，实现了通用激活量化方法，降低内存和推理延迟。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-3wrv6zay74/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1421, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3wrv6zay74/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 629, \"height\": 409, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3wrv6zay74/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1150, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3wrv6zay74/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1417, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3wrv6zay74/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1391, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3wrv6zay74/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 511, \"height\": 393, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-3wrv6zay74/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1455, \"height\": 853, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3wrv6zay74/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1464, \"height\": 818, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3wrv6zay74/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1467, \"height\": 542, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3wrv6zay74/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1467, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3wrv6zay74/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1420, \"height\": 542, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3wrv6zay74/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1431, \"height\": 540, \"label\": \"Table\"}]"
motivation: LLM激活中的异常值阻碍低比特量化在边缘设备上的部署。
method: 应用Hadamard矩阵减少异常值，结合二分搜索和维度扩展进行量化。
result: 有效降低异常值影响，实现低比特量化，减少内存和推理时间。
conclusion: 该方法显著提升了LLM在边缘设备上的量化效率。
---

## Abstract
Large language models (LLMs) have become pivotal in artificial intelligence, demonstrating strong capabilities in reasoning, understanding, and generating data. However, their deployment on edge devices is hindered by their substantial size, often reaching several billion parameters. Quantization is a widely used method to reduce memory usage and inference time, however LLMs present unique challenges due to the prevalence of outliers in their activations. In this work, we leverage the theoretical advantages of Hadamard matrices over random rotation matrices to push the boundaries of quantization in LLMs. We demonstrate that Hadamard matrices are more effective in reducing outliers, which are a significant obstacle in achieving low-bit quantization. Our method based on a gradual binary search enables 3-bit quantization for weights, activations, and key-value (KV) caches, resulting in a 40% increase in accuracy on common benchmarks compared to SoTA methods. We extend the use of rotation matrices to support non-power-of-2 embedding dimensions, similar to the Qwen architecture, by employing the Paley's algorithm. Our experimental results on multiple models family like Mistral, LLaMA, and Qwen demonstrate the effectiveness of our approach, outperforming existing methods and enabling practical 3-bit quantization.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：大型语言模型（LLMs）参数量巨大（数十亿），难以部署在边缘设备上。量化是减小内存和推理时间的常用方法，但LLMs的**激活值中存在异常值（outliers）**，严重阻碍了低比特量化（如4-bit、3-bit）的实现。
- **现有局限**：传统均匀量化受异常值影响大，导致性能下降。已有方法如SmoothQuant、LLM.int8() 等处理异常值，但效果有限。旋转矩阵（如随机正交矩阵、Hadamard矩阵）可用于分散异常值，但理论基础不清，且对非2次幂嵌入维度支持不足。
- **本文目标**：利用Hadamard矩阵在理论上减少异常值的优势，结合高效的**逐步二分搜索（Gradual Binary Search, GBS）** 和**维度扩展（Dimension Expansion）**，实现通用的3-bit权值-激活-KV缓存（WAKV）量化，提升低比特下LLMs的部署可行性。

## 2. 方法论
### 核心思想
- 采用旋转矩阵（Hadamard矩阵）对激活和权值进行变换，将异常值分散到更多维度，从而降低量化难度。
- 使用**逐步二分搜索**对每个投影层（projection）独立寻找最优的**裁剪比率（clipping ratio）**，以最小化困惑度（PPL）为目标，而非传统量化误差。
- 针对非2次幂嵌入维度（如Qwen的1536维），提出**维度扩展**：在权值中填充零，使维度可生成Hadamard矩阵（利用Paley算法），并证明在一定计算预算下增加维度可提升量化性能。

### 关键技术细节
- **Hadamard矩阵优势**：理论证明（Theorem 3.1）对于含异常值的向量，Hadamard变换后最大绝对值衰减为 \( O(1/\sqrt{n}) \)，优于随机正交矩阵的 \( O(\sqrt{2\log n / n}) \)；且Hadamard矩阵达到理论最优（Theorem 3.2）。
- **逐步二分搜索（Algorithm 1）**：对模型中的每个线性投影层（按顺序）进行量化，同时使用二分搜索优化该层的裁剪比率。目标函数为困惑度（PPL），假设其关于裁剪比率是凸的。每次搜索迭代中，评估两个候选值，保留PPL更低的那个，逐步收敛。
- **维度扩展（Section 4.2）**：在权值矩阵末尾添加d行/列零，使维度满足Paley算法生成Hadamard的条件（n-1为素数且≡3 mod 4）。Lemma 4.1给出扩展上限：\( d \leq n(b-b')/b' \)，以保证扩展后的比特运算量不超过直接使用更高比特。扩展后的旋转矩阵可与权值融合，推理时无额外计算开销（仅需FHT）。

## 3. 实验设计
- **数据集与评估指标**：
  - 困惑度（PPL）：WikiText2。
  - 基准测试（成功率）：PIQA、HellaSwag (HS)、Arc-Easy、Arc-Challenge、Winogrande、Lambada，并计算平均准确率（AVG）。
- **对比方法**：基线为FP16，主要对比**QuaRot**（使用随机正交旋转的4-bit量化方法）。此外在附录中与**SpinQuant**（学习旋转）和**DFRot**（精细旋转）对比。
- **评估场景**：4-bit和3-bit WAKV量化，覆盖6个模型：
  - Mistral-7B Instruct v0.3 / Mistral-7B v0.1
  - LLaMA2-7B / LLaMA3-8B
  - Qwen2.5-7B Instruct / Qwen2.5-1.5B Instruct
- **其他实验**：维度扩展效果（图2，增加不同维度数对AVG的影响）；GBS过程分析（附录C，起始状态为FP16 vs 4-bit）；PPL与AVG相关性（附录D）。

## 4. 资源与算力
- **明确说明**：使用**1块A100 GPU**进行量化和逐步二分搜索。
- **时间**：对最大模型（7B/8B）约耗时**4天**（使用10%的WikiText2训练集）。
- **内存**：限制上，对LLaMA3-8B无法增加超过2036个扩展维度（受限于A100显存）。

## 5. 实验数量与充分性
- **数量**：主要实验表1（4-bit）和表2（3-bit）共6个模型×2个精度=12组结果，每组报告PPL和6个基准的平均AVG。附加实验：
  - 附录E中分别与SpinQuant和DFRot对比（共8组额外实验）。
  - 维度扩展消融实验（图2，对4个模型在3-bit下测试不同扩展维度）。
  - GBS过程分析（附录C，2组可视化）。
- **充分性**：覆盖了主流开源LLM系列（Mistral, LLaMA, Qwen），包含不同规模和架构（含非2次幂维度模型）。对比了当前最先进的旋转量化方法（QuaRot, SpinQuant, DFRot）。指标包括PPL和多项下游任务准确率，较为全面。**客观性**：方法开源部分代码基于QuaRot，实验设置一致。未报告多轮随机种子下的误差棒（因计算成本），但结果趋势清晰。
- **公平性**：所有量化均基于相同的基础代码（QuaRot）和相同评估流程，对比公平。

## 6. 主要结论与发现
- **Hadamard矩阵理论优势**：严格证明Hadamard矩阵比随机正交矩阵更有效减少异常值幅度，且达到理论最优。
- **GBS效果显著**：在4-bit下，GBS平均提升约3-6%的AVG；在3-bit下，使原来几乎失效的量化（如QuaRot在Mistral-7B上AVG仅22%）大幅提升至61%左右，提升约40个百分点。PPL改善达2个数量级（如LLaMA3-8B从1315降至12.62）。
- **维度扩展可行且有益**：扩展维度可提升量化性能（图2），且在计算预算内实现。使Non-power-of-2架构（如Qwen）也能应用Hadamard旋转。
- **方法通用性**：提出的GBS可嵌入多种旋转方法（SpinQuant、DFRot）并提升其性能（附录E）。

## 7. 优点
- **理论贡献**：首次严格证明Hadamard矩阵在减少量化异常值方面优于随机旋转矩阵，并给出最优性结论。
- **方法创新**：提出逐步二分搜索优化裁剪比率，以困惑度为目标，避免了传统量化误差的局限性，简洁高效。
- **实用性**：通过维度扩展和Paley算法，使方法适用于任何嵌入维度（不限于2次幂），增加了通用性。
- **实验全面**：在多个系列模型和不同精度下验证，并对比最新方法，结果支撑充分。

## 8. 不足与局限
- **计算成本高**：GBS需逐层量化并多次计算PPL，单个7B模型耗时4天，对更大模型可能难以扩展。文中提及可通过减少训练数据量（目前10%）来加速。
- **维度扩展的权衡**：扩展维度会增加权值存储和计算量，尽管推理时无额外成本，但量化过程仍受影响。Lemma 4.1给出上限，但实际扩展越多，内存占用越大，可能受显存限制。
- **未报告误差棒**：由于计算开销，未进行多次重复实验或统计显著性检验，结果可能受随机性影响。
- **仅后训练量化（PTQ）**：方法为PTQ，未与量化感知训练（QAT）结合；若结合可能进一步提升性能。
- **应用限制**：当前仅评估了7B/8B规模模型，未在更大模型（如70B）上验证；也未在非Transformer架构上测试。
- **未来方向**：文中建议混合计算、选择性扩展维度以降低开销，但未实现。

（完）
