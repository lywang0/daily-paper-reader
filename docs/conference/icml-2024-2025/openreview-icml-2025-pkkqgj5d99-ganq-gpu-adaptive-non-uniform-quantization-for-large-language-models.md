---
title: "GANQ: GPU-Adaptive Non-Uniform Quantization for Large Language Models"
title_zh: "GANQ: 面向大语言模型的GPU自适应非均匀量化"
authors: "Pengxiang Zhao, Xiaoming Yuan"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=pkKQGJ5d99"
tags: ["query:edge-llm"]
score: 8.0
evidence: GPU自适应非均匀量化用于高效LLM推理
tldr: GANQ提出了一种GPU自适应非均匀量化框架，利用基于查找表的混合精度通用矩阵乘法（mpGEMM）来高效执行LLM推理。该方法无需训练，通过层级的后训练量化，自适应地选择非均匀量化方案以匹配GPU硬件特性，在减少内存和计算开销的同时保持了模型精度，为LLM部署提供了硬件高效的解决方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-pkkqgj5d99/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1739, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pkkqgj5d99/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1130, \"height\": 386, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-pkkqgj5d99/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1598, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pkkqgj5d99/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 848, \"height\": 706, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pkkqgj5d99/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1681, \"height\": 508, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pkkqgj5d99/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1680, \"height\": 465, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pkkqgj5d99/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 853, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pkkqgj5d99/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1681, \"height\": 674, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pkkqgj5d99/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1677, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pkkqgj5d99/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1599, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pkkqgj5d99/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1770, \"height\": 597, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pkkqgj5d99/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1593, \"height\": 523, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pkkqgj5d99/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1417, \"height\": 474, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pkkqgj5d99/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1417, \"height\": 807, \"label\": \"Table\"}]"
motivation: 现有硬件不支持混合精度矩阵乘法，导致量化后的低比特推理效率低下。
method: 提出GPU自适应的非均匀量化框架，采用基于查找表的mpGEMM，无需训练即可进行层级后训练量化。
result: 在多个LLM上展示了优越的量化性能，显著降低了推理资源需求。
conclusion: GANQ通过硬件自适应的非均匀量化，实现了高效且精确的LLM推理。
---

## Abstract
Large Language Models (LLMs) face significant deployment challenges due to their substantial resource requirements. While low-bit quantized weights can reduce memory usage and improve inference efficiency, current hardware lacks native support for mixed-precision General Matrix Multiplication (mpGEMM), resulting in inefficient dequantization-based implementations. Moreover, uniform quantization methods often fail to capture weight distributions adequately, leading to performance degradation. We propose GANQ (GPU-Adaptive Non-Uniform Quantization), a layer-wise post-training non-uniform quantization framework optimized for hardware-efficient lookup table-based mpGEMM. GANQ achieves superior quantization performance by utilizing a training-free, GPU-adaptive optimization algorithm to  efficiently reduce layer-wise quantization errors. Extensive experiments demonstrate GANQ's ability to reduce the perplexity gap from the FP16 baseline compared to state-of-the-art methods for both 3-bit and 4-bit quantization. Furthermore, when deployed on a single NVIDIA RTX 4090 GPU, GANQ's quantized models achieve up to 2.57$\times$ speedup over the baseline, advancing memory and inference efficiency in LLM deployment.

---

## 论文详细总结（自动生成）

## 论文总结：GANQ：面向大语言模型的GPU自适应非均匀量化

### 1. 核心问题与研究动机

- **背景**：大语言模型（LLMs）参数量巨大，推理时对显存和算力要求极高。权重量化是降低资源消耗的重要手段，但现有硬件（如GPU）不原生支持混合精度矩阵乘法（mpGEMM，即低比特权重×高精度激活），导致实际推理时需先进行反量化，引入额外开销，抵消了部分量化收益。
- **现有方法局限**：均匀量化难以适配LLM权重高度非均匀的分布（尤其存在离群值），导致量化误差大；已有的非均匀量化方法多基于启发式（如k-means聚类、手工设计的幂指数映射），缺乏理论保证且泛化性差。
- **核心目标**：提出一种**硬件自适应、训练免费、后训练的非均匀量化框架**，直接针对基于查找表（LUT）的mpGEMM进行优化，在减小量化误差的同时提升推理速度。

### 2. 方法论：核心思想与关键技术

- **核心思想**：将权重矩阵的每一行视为独立通道，为每行学习一个**非均匀码本（codebook）** 和一个**查询矩阵（query matrix）**，以最小化量化后该层输出与原始输出的Frobenius范数误差。该问题分解为多个独立的混合整数二次规划（MIQP）子问题。
- **关键技术细节**：
  - **问题建模**：对线性层 $Y=WX$，最小化 $\|WX - \tilde{W}X\|_F^2$，其中 $\tilde{W}_{i,j}=T_{i, Q_{i,j}}$，$T_i\in\mathbb{R}^{2^N}$ 为码本，$Q_{i,j}\in\{0,\dots,2^N-1\}$ 为索引。
  - **交替方向优化**：将问题分解为两个子问题——更新索引矩阵 $S$（离散）和更新码本 $T$（连续）。
    - **更新码本 $T$**：闭式解，通过Cholesky分解和最小二乘法计算。
    - **更新索引 $S$**：利用Cholesky分解后矩阵的下三角结构，通过**回代（back-substitution）** 从最后一列向前逐列贪心求解，每列仅需寻找最接近的码本值。
  - **GPU自适应并行**：所有行的子问题均可独立并行求解，通过矩阵运算在GPU上批量执行，提升效率。
  - **与离群值处理技术兼容**：可先提取稀疏离群值（保留0.5%的参数），对剩余稠密部分用GANQ量化，进一步降低量化范围。
- **算法流程**（简化为文字）：
  1. 输入权重矩阵 $W$、校准数据激活 $X$，初始化码本 $T^0$。
  2. 计算 $H=XX^\top$，执行Cholesky分解得到下三角矩阵 $L$。
  3. 迭代 $k=0,\dots,K-1$：
     - 从最后一列到第一列，用回代法更新索引矩阵 $S^{k+1}$（每列选择最接近的码本值）。
     - 用闭式解批量更新码本 $T^{k+1}$。
  4. 返回最终码本 $T^K$ 和查询矩阵 $Q^K$。

### 3. 实验设计

- **数据集与评测任务**：
  - **语言建模困惑度（PPL）**：WikiText-2、C4、PTB（序列长度2048）。
  - **零样本下游任务**：HellaSwag、BoolQ、RTE、WinoGrande、ARC-Easy、ARC-Challenge（共6项）。
  - **长上下文与推理能力**：LongBench、GSM8K。
  - **推理速度与显存**：单序列生成1024 tokens，报告CUDA时间和峰值显存。
- **基准方法**：
  - **基础权重量化**（无离群值处理）：RTN（四舍五入）、GPTQ、OmniQuant。
  - **带离群值处理的权重量化**：GPTQ (g128)、AWQ (g128)、OmniQuant (g128)、SqueezeLLM。
  - **全精度FP16**作为上界。
- **模型规模**：OPT（125M–6.7B）、LLaMA-7B、LLaMA-2-7B/8B、LLaMA-3-8B、LLaMA-3.2-1B/3B（含Instruct版本）。
- **比特宽度**：主要测试4-bit和3-bit。

### 4. 资源与算力

- **硬件**：所有实验在**单张NVIDIA RTX 4090 GPU**（24GB显存）上完成。
- **时间**：量化LLaMA-2-7B（约7B参数）用时约**1小时**（迭代 $K=10$）。
- **校准数据**：OPT模型用32条序列，LLaMA模型用128条序列，每条2048 tokens，取自C4数据集第一个分片。

### 5. 实验数量与充分性

- **实验数量**：论文报告了超过**15个表格**的结果，覆盖多个模型家族（OPT、LLaMA、LLaMA-2/3/3.2）、多种量化配置（4/3-bit）、多个评测数据集（PPL+零样本+长上下文+推理）。
- **消融与兼容性分析**：
  - 对比了有/无离群值处理的版本（GANQ vs GANQ*）。
  - 测试了与SqueezeLLM离群值提取方法的兼容性。
  - 分析了不同预条件策略对结果的影响（附录A）。
- **充分性评价**：实验全面，对比方法覆盖了当前主要PTQ基线，且在多个模型尺度上验证。结果呈现在主表和附录中，公平性较好（均使用相同校准数据和推理核）。但**缺少与更多较新方法**（如QuIP#、AQLM等）的对比，且**未对更大模型如70B进行实验**（可能受限于单卡RTX 4090显存）。

### 6. 主要结论与发现

- **量化性能**：GANQ在4-bit和3-bit下几乎在所有模型和数据集上**取得最低困惑度**，部分情况下（如OPT-2.7B 4-bit）甚至**低于FP16基线**（12.33 vs 12.47），表明其非均匀量化能更好地拟合权重分布。
- **零样本任务**：LLaMA-2-7B在6个任务的平均准确率上，4-bit达到64.23%（FP16为64.47%），3-bit仍有62.22%，显著优于RTN/GPTQ/OmniQuant。
- **推理加速**：结合基于LUT的推理核，GANQ在单卡RTX 4090上相较FP16基线达到**最高2.57×加速**（OPT-6.7B, 3-bit），显存从约13GB降至约4GB。
- **与离群值处理集成**：GANQ*（加离群值提取）进一步降低PPL，但推理速度略慢；用户可根据需求在精度和速度间权衡。
- **效率**：量化7B模型仅需1小时，内存友好（无需梯度），相比需要梯度的OmniQuant（>3小时）和SqueezeLLM（仅支持≤2.7B模型）更具实用优势。

### 7. 优点

1. **理论驱动**：将量化问题形式化为混合整数二次规划，提出**回代贪心算法**高效求解，有严谨的数学推导。
2. **硬件自适应**：专门为基于LUT的mpGEMM设计，无需反量化，直接加速推理。
3. **训练免费且高效**：仅需少量校准数据，无需反向传播，并行计算适合GPU，随模型规模线性扩展。
4. **兼容性强**：可与现有离群值处理技术（稀疏/低秩分解）无缝集成，进一步提升性能。
5. **实验充分**：覆盖多个模型家族、比特宽度、任务类型，并报告了推理速度/显存，具有实际部署参考价值。

### 8. 不足与局限

1. **实验规模限制**：最大模型仅到8B（LLaMA-3-8B），未在更大模型（如70B/405B）上验证。可能受限于单卡RTX 4090显存（仅24GB，无法加载70B模型）。
2. **对比方法不够全面**：缺少与近期更先进方法（如QuIP#、AQLM、FP6-LLM等）的比较，也未与权重-激活联合量化方法对比。
3. **离群值处理依赖简单阈值**：默认保留0.5%的离群值，该比例是否最优未做系统消融。
4. **推理速度仅测试单序列场景**：批处理（batch > 1）下的速度可能不同，LUT核在批量较大时可能受限于查找表带宽。
5. **代码与复现**：虽提供GitHub仓库链接，但未明确说明是否完全开源所有配置和脚本，附录中缺少部分实验的详细设置（如迭代次数K对性能的影响）。
6. **局限性说明**：论文未讨论对某些敏感任务（如偏见、幻觉）的量化影响，仅关注困惑度和标准准确性。

（完）
