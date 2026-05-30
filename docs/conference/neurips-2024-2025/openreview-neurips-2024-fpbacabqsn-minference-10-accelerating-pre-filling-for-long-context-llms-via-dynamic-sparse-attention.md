---
title: "MInference 1.0: Accelerating Pre-filling for Long-Context LLMs via Dynamic Sparse Attention"
title_zh: MInference 1.0：通过动态稀疏注意力加速长上下文LLM的预填充
authors: "Huiqiang Jiang, YUCHENG LI, Chengruidong Zhang, Qianhui Wu, Xufang Luo, Surin Ahn, Zhenhua Han, Amir H. Abdi, Dongsheng Li, Chin-Yew Lin, Yuqing Yang, Lili Qiu"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=fPBACAbqSN"
tags: ["query:edge-llm"]
score: 4.0
evidence: 动态稀疏注意力加速LLM预填充，可迁移至边缘设备
tldr: 长上下文LLM推理中预填充阶段计算量巨大，本文提出MInference，通过识别注意力矩阵中的三种独特模式，实现动态稀疏注意力计算，大幅加速预填充。在1M token输入下，将A100上的处理时间从30分钟降至数分钟。该方法为边缘设备上的长序列推理提供了潜在的加速途径，但当前主要针对GPU。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1419, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1413, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1423, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1434, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1422, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 737, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 467, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 739, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1448, \"height\": 1794, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 776, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 851, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1318, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-fpbacabqsn/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1013, \"height\": 515, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-fpbacabqsn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1376, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fpbacabqsn/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1221, \"height\": 605, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fpbacabqsn/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1439, \"height\": 653, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fpbacabqsn/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fpbacabqsn/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1441, \"height\": 146, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fpbacabqsn/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1435, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fpbacabqsn/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1065, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fpbacabqsn/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fpbacabqsn/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1337, \"height\": 1773, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-fpbacabqsn/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1344, \"height\": 1374, \"label\": \"Table\"}]"
motivation: 长上下文LLM预填充因注意力二次复杂度而极慢，需要高效的稀疏计算方法。
method: 提出MInference，利用动态稀疏注意力模式来加速预填充计算。
result: 在1M token输入下显著降低预填充时间，保持模型精度。
conclusion: 动态稀疏注意力是加速长上下文LLM推理的有效技术，有潜力部署于边缘设备。
---

## Abstract
The computational challenges of Large Language Model (LLM) inference remain a significant barrier to their widespread deployment, especially as prompt lengths continue to increase. Due to the quadratic complexity of the attention computation, it takes 30 minutes for an 8B LLM to process a prompt of 1M tokens (i.e., the pre-filling stage) on a single A100 GPU. Existing methods for speeding up prefilling often fail to maintain acceptable accuracy or efficiency when applied to long-context LLMs. To address this gap, we introduce MInference (Milliontokens Inference), a sparse calculation method designed to accelerate pre-filling of long-sequence processing. Specifically, we identify three unique patterns in long-context attention matrices-the A-shape, Vertical-Slash, and Block-Sparse-that can be leveraged for efficient sparse computation on GPUs. We determine the optimal pattern for each attention head offline and dynamically build sparse
indices based on the assigned pattern during inference. With the pattern and sparse indices, we perform efficient sparse attention calculations via our optimized GPU kernels to significantly reduce the latency in the pre-filling stage of longcontext LLMs. Our proposed technique can be directly applied to existing LLMs without any modifications to the pre-training setup or additional fine-tuning. By
evaluating on a wide range of downstream tasks, including InfiniteBench, RULER, PG-19, and Needle In A Haystack, and models including LLaMA-3-1M, GLM-4-1M, Yi-200K, Phi-3-128K, and Qwen2-128K, we demonstrate that MInference effectively reduces inference latency by up to 10x for pre-filling on an A100, while maintaining accuracy. Our code is available at https://aka.ms/MInference.

---

## 论文详细总结（自动生成）

# 论文总结：MInference 1.0: Accelerating Pre-filling for Long-Context LLMs via Dynamic Sparse Attention

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：长上下文大语言模型（LLM）在推理的预填充（pre-filling）阶段，由于注意力机制的二次复杂度（O(n²)），处理超长提示词（如1M tokens）时延迟极高。例如，单张A100 GPU处理1M tokens的输入需要约30分钟，其中注意力计算占90%以上。
- **整体含义**：现有加速方法（如固定稀疏注意力）要么需要昂贵训练或微调，要么无法适应注意力的动态稀疏性，在长上下文场景中精度或效率不足。因此，需要一种无需额外训练、能动态预测稀疏模式并高效计算的方法。

## 2. 方法论

### 核心思想
- 利用长上下文LLM注意力矩阵中存在的三种可泛化稀疏模式（A-shape、Vertical-Slash、Block-Sparse），通过离线为每个注意力头分配最优模式，并在推理时动态构建稀疏索引，仅计算重要的注意力权重，从而大幅降低预填充延迟。

### 关键技术细节
1. **模式识别**：
   - **A-shape**：注意力集中在初始token和局部窗口，相对稳定，无需动态索引构建。
   - **Vertical-Slash (VS)**：注意力集中在特定token（竖线）和固定间隔的token（斜线），位置动态变化。
   - **Block-Sparse**：注意力分布分散但具有空间聚类性，可用块级稀疏表示。
2. **离线模式搜索**：
   - 使用**内核感知的最优稀疏模式搜索**，对每个注意力头，以目标FLOPs为约束，通过召回率（attention output recall）选择最优模式与参数（如竖线/斜线数量、块数）。
3. **在线动态索引构建**：
   - **VS头**：利用最后64个查询向量与所有键向量计算近似注意力，提取Top-k竖线和斜线索引。
   - **Block-Sparse头**：对查询和键进行64×64块均值池化，计算块级注意力，取Top-k块索引。
4. **稀疏注意力计算**：
   - 基于FlashAttention、Triton和动态稀疏编译器PIT，开发三种优化GPU内核（块稀疏、竖线-斜线混合稀疏、A-shape局部窗口），高效执行稀疏矩阵乘法。

### 公式与算法
- 稀疏注意力公式：\( A(M) = \text{Softmax}\left( \frac{1}{\sqrt{d}} QK^\top - c(1-M) \right) \)，其中 \(M\) 是动态稀疏掩码。
- 优化目标：最小化 \( \|A(M) - A_{\text{dense}}\| \)，同时最小化稀疏计算时间 + 索引开销时间。

## 3. 实验设计

### 数据集与场景
- **InfiniteBench**：10个任务（检索、QA、代码、摘要等），平均长度~214K tokens。
- **RULER**：13个复杂任务（多跳追踪、聚合、检索等），长度从4K到128K。
- **Needle In A Haystack**：检索任务，上下文长度1K~1M tokens。
- **PG-19**：语言建模任务，提示词长度达100K tokens。

### 对比方法
- 五种无训练稀疏注意力基线：StreamingLLM、StreamingLLM w/ dilated、StreamingLLM w/ strided、InfLLM、Ours w/ static（使用静态稀疏索引）。
- 全注意力（FlashAttention-2）作为上界。

### 实验覆盖
- 模型：LLaMA-3-8B-262K/1M、GLM-4-9B-1M、Yi-9B-200K、Phi-3-Mini-128K、Qwen2-7B-128K，以及LLaMA-3-70B-1M。
- 消融实验：移除动态模式、仅用单个模式、结合KV缓存压缩方法（SnapKV）。
- 扩展实验：在更大模型（70B）上验证。

## 4. 资源与算力

- **硬件**：单张Nvidia A100 GPU（80GB），使用bfloat16精度。
- **代码实现**：基于FlashAttention、Triton和PIT，提供PyTorch自定义实现。
- **搜索时间**：最优模式搜索约15分钟（单张A100）。
- **推理速度**：在1M上下文时，预填充延迟从30分钟降至3分钟（10×加速）；结合张量并行和上下文并行，可在8×A100上降至22秒。

## 5. 实验数量与充分性

- **实验组数**：在四大基准（InfiniteBench、RULER、Needle、PG-19）上进行了大量实验，覆盖多种数据集长度和任务类型。每个基准均报告了多个模型的对比结果。
- **消融实验**：包括7种变体（仅静态、仅A-shape、仅VS、仅BS、仅竖线、仅斜线、结合SnapKV），全面评估各组件贡献。
- **充分性与公平性**：
  - 所有实验使用相同的贪婪解码设置，保证稳定。
  - 对比方法均使用官方推荐配置，且均在单A100上运行。
  - 结果表格包含多个随机种子？文中未明确说明误差棒，但指出“greedy decoding”避免随机性。
  - 实验设计较全面，覆盖了主要长上下文场景，消融实验充分。

## 6. 主要结论与发现

- MInference可在不降低模型精度（甚至略有提升）的前提下，实现最高10×的预填充加速。
- 动态稀疏索引构建是其关键：使用静态索引会导致性能严重下降（如KV检索任务几乎失效）。
- 三种模式缺一不可：移除任一模式均造成不同程度的性能损失（尤其BS和VS对动态任务重要）。
- 兼容性：可与KV缓存压缩方法（如SnapKV）协同工作，性能不变或微增。
- 泛化性：模式搜索配置可跨不同长度和域迁移（如LLaMA-3-262K的配置直接用于1M版本依然有效）。

## 7. 优点

- **无需训练**：直接应用于预训练LLM，无需额外微调或预训练，实用性强。
- **动态稀疏**：通过在线近似高效构建稀疏索引，兼顾准确性与速度。
- **内核感知优化**：搜索过程考虑GPU实际FLOPs，保证加速效果，而非理论稀疏率。
- **实现开源**：代码公开，基于Triton便于移植到其他硬件（如H100、MI300X）。
- **广泛验证**：在多种模型（8B~70B）和基准上验证，结果稳定可靠。

## 8. 不足与局限

- **短上下文效率低**：当上下文较短（如10K tokens）时，构建动态索引的时间占比可达30%，加速效果不明显。
- **高稀疏率风险**：如果目标稀疏率极高，模型性能可能显著下降（文中未具体量化，但提及“noticeably decline”）。
- **仅针对预填充阶段**：未涉及解码阶段加速，但可与之组合（如与SnapKV结合）。
- **硬件依赖**：当前实现针对GPU，未验证在CPU或边缘设备上的性能。
- **实验偏差风险**：实验均基于固定超参数（如last_q=64, block_size=64），未充分探索这些参数对性能的影响；对比基线可能未完全调优（如InfLLM的设置固定）。

（完）
