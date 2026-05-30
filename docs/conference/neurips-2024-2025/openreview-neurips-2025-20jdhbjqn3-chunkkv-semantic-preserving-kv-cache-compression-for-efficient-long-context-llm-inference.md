---
title: "ChunkKV: Semantic-Preserving KV Cache Compression for Efficient Long-Context LLM Inference"
title_zh: ChunkKV：面向高效长上下文LLM推理的语义保持KV缓存压缩
authors: "Xiang Liu, Zhenheng Tang, Peijie Dong, Zeyu Li, Liuyue, Bo Li, Xuming Hu, Xiaowen Chu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=20JDhbJqn3"
tags: ["query:edge-llm"]
score: 4.0
evidence: 语义保持的KV缓存压缩方法，用于高效长上下文推理
tldr: 现有KV缓存压缩方法按单个令牌评估重要性，忽略了令牌间的语义关系，导致上下文碎片化。ChunkKV以语义块为基本压缩单元，保留完整语言结构和上下文完整性。实验表明，在激进压缩下仍能保持关键语义，显著降低内存占用，支持高效长上下文推理。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1442, \"height\": 564, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1429, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1441, \"height\": 588, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1011, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1149, \"height\": 854, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1154, \"height\": 1014, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1143, \"height\": 1015, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1155, \"height\": 1050, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1150, \"height\": 1024, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1155, \"height\": 1051, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1142, \"height\": 1017, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1160, \"height\": 1052, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1156, \"height\": 1046, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1156, \"height\": 1052, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1311, \"height\": 1903, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1313, \"height\": 1870, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1148, \"height\": 844, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-20jdhbjqn3/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1436, \"height\": 598, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1301, \"height\": 365, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 728, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 754, \"height\": 568, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 753, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 752, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 771, \"height\": 513, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 755, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 942, \"height\": 548, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 656, \"height\": 427, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1441, \"height\": 408, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1442, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1454, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1435, \"height\": 519, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1251, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1260, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1144, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1440, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1446, \"height\": 1165, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1275, \"height\": 310, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1159, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 993, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1438, \"height\": 448, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1444, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1456, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1064, \"height\": 616, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1459, \"height\": 678, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1437, \"height\": 211, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 676, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-20jdhbjqn3/table-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1416, \"height\": 934, \"label\": \"Table\"}]"
motivation: 现有KV缓存压缩方法忽略令牌间语义关系，导致上下文碎片化。
method: 以语义块作为基本压缩单元，保留语言结构和上下文完整性。
result: 在激进压缩下保持关键语义，显著降低内存占用。
conclusion: ChunkKV通过语义保留的压缩实现了高效长上下文LLM推理。
---

## Abstract
Large Language Models (LLMs) require significant GPU memory when processing long texts, with the key value (KV) cache consuming up to 70\% of total memory during inference. Although existing compression methods reduce memory by evaluating the importance of individual tokens, they overlook critical semantic relationships between tokens, resulting in fragmented context and degraded performance. We introduce \method{}, which fundamentally reimagines KV cache compression by treating semantic chunks - rather than isolated tokens - as basic compression units. This approach preserves complete linguistic structures and contextual integrity, ensuring that essential meaning is retained even under aggressive compression. Our innovation includes a novel layer-wise index reuse technique that exploits the higher cross-layer similarity of preserved indices in \method{}, reducing computational overhead and improving throughput by 26.5\%. Comprehensive evaluations on challenging benchmarks: LongBench, Needle-In-A-HayStack, GSM8K, and JailbreakV demonstrate that \method{} outperforms state-of-the-art methods by up to 8.7\% in precision while maintaining the same compression ratio. These results confirm that semantic-aware compression significantly enhances both efficiency and performance for long-context LLM inference, providing a simple yet effective solution to the memory bottleneck problem. \emph{The code is available at \href{https://github.com/NVIDIA/kvpress}{link}.}

---

## 论文详细总结（自动生成）

## 论文中文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在处理长文本时，Key-Value（KV）缓存会占用大量GPU内存，甚至可达总内存的70%。现有KV缓存压缩方法（如H2O、SnapKV）通过评估单个token的重要性来裁剪缓存，但忽视了token之间的语义依赖关系，导致上下文碎片化，丢失关键语义信息。
- **研究动机**：完整语义信息通常出现在连续序列中（如主语、谓语、宾语构成一个语义块），而非孤立的token。因此，论文旨在设计一种以“语义块”为基本压缩单元的KV缓存压缩方法，保留完整的语言结构和上下文完整性，从而在激进压缩下依然维持模型性能。
- **整体含义**：ChunkKV通过语义感知的压缩，显著减少内存占用（可压缩至原大小的10%），同时保持甚至提升推理精度，为长上下文LLM的高效部署提供了简单有效的解决方案。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将连续的token分组为“语义块”（chunk），以块为单位判断重要性，保留完整的语义单元（如包含主语、谓语、宾语的短语），而不是对单个token独立裁剪。
- **关键技术细节**：
    - **ChunkKV算法**：
        - 使用一个观察窗口（observe window）计算查询（Q）与键（K）的注意力分数。
        - 将Key序列按固定块大小（chunk size，默认设为10）划分成若干块。
        - 累计每个块内所有token的注意力分数作为该块的重要性得分。
        - 使用Top-K策略选择得分最高的块，K = ⌊压缩后的最大长度 / 块大小⌋。
        - 保留选中的块对应的KV对，并拼接上最近观察窗口的KV对（保持原始顺序）。
    - **层间索引复用（Layer-Wise Index Reuse）**：
        - 观察到ChunkKV保留的KV索引在相邻层间具有更高的Jaccard相似度（例如LLaMA-3-8B上ChunkKV为57.74%，SnapKV仅27.95%）。
        - 因此，对每N_reuse层只计算一次ChunkKV的索引选择，后续层直接复用该索引，从而减少压缩计算开销。
    - **理论理解**（附录C）：从上下文学习（ICL）角度，连续块级KV缓存保留了完整的示例（语义信息），降低了对示例与问题之间KL散度可区分性的要求（即更小的下界），从而提升推理性能。

### 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集与场景**：
    - **长上下文任务**：LongBench（含17个子任务，如单文档QA、多文档QA、摘要、少样本学习、代码生成等，平均长度1K–18K tokens）、Needle-In-A-HayStack（NIAH，检索任务，8k和32k上下文）。
    - **上下文学习任务**：GSM8K（算术推理，1-shot CoT）、Many-shot GSM8K（50-shot，超4k tokens）、JailbreakV（安全对抗基准）。
- **对比方法**：StreamingLLM、H2O、SnapKV、PyramidKV（以及FullKV作为基线）。部分实验还对比了KIVI（量化方法）和Palu（训练型压缩方法）。
- **评估模型**：LLaMA-3-8B-Instruct、LLaMA-3.1-8B-Instruct、Mistral-7B-Instruct、Qwen2-7B-Instruct、DeepSeek-R1-Distill-Llama-8B，以及LLaMA-3-70B-Instruct（LongBench子实验）。
- **评估指标**：在NIAH中使用GPT-4o-mini进行LLM-as-a-Judge评估准确性；LongBench报告各子任务得分与平均分；GSM8K和JailbreakV报告准确率；并报告延迟、吞吐量、TTFT、TPOT等效率指标。

### 4. 资源与算力

- 论文明确说明效率实验使用A40 GPU（单卡），批大小为1，使用Flash Attention 2进行推理。未提及训练资源（ChunkKV无需训练）。
- 其他实验未详细说明GPU型号和数量，但推测使用常见GPU（如A40或类似）进行推理评估。

### 5. 实验数量与充分性

- **实验数量**：论文进行了大量实验，涵盖4种模型架构、5个主要基准（LongBench、NIAH、GSM8K、Many-shot GSM8K、JailbreakV）、多种压缩比例（10%、20%、30%）、不同KV缓存大小（96、128、256、512）、不同块大小（3、5、10、20、30）、索引复用层数消融（1、2、3、5、10、20、28/32），以及与量化方法KIVI的比较、混合压缩分析等。约20+组主要实验表格和多个可视化图。
- **充分性与客观性**：
    - 实验覆盖了多种任务类型（检索、推理、安全、多语言），多个主流开源模型，控制变量（压缩率、块大小、复用深度）进行消融，对比方法全面。
    - 所有主要实验重复3次并取均值，保证鲁棒性。
    - 使用了公开数据集和标准评估流程（如LLM-as-a-Judge），具有可复现性。
    - 但部分实验（如70B模型、多语言）报告较少，效率实验只在A40上测试，未在不同硬件上验证。

### 6. 论文的主要结论与发现

- **性能优越**：在不同模型、压缩比和任务上，ChunkKV普遍优于现有最先进的KV裁剪方法。例如在GSM8K 10%压缩率下，LLaMA-3.1-8B达到65.7%（SnapKV仅50.3%）；在LongBench 10%压缩率下，Qwen2-7B中文子任务提升2.2%。
- **语义保持优势**：通过保留连续语义块，避免了离散token方法中关键语义丢失的问题（如遗漏句子主语）。
- **效率提升**：层间索引复用技术使吞吐量提升高达26.5%，延迟降低20.7%，且性能损失极小（<0.6%）。
- **块大小稳健**：块大小在5-20范围内性能稳定，推荐默认值为10。
- **与量化方法互补**：ChunkKV在总生成时间上比KIVI 2-bit量化快27.3%，且性能相当。

### 7. 优点

- **方法创新**：首次提出以语义块为基本单位的KV缓存压缩，解决了离散token方法忽略语义关系的问题，简单有效。
- **计算优化**：层间索引复用技术利用了ChunkKV保留索引高相似度的特点，显著降低压缩开销，无需额外训练。
- **实验全面**：覆盖多种任务、模型、压缩比和消融分析，结果扎实可信。
- **理论支撑**：从上下文学习角度给出理论解释，增强方法严谨性。
- **实用价值**：可直接部署于现有LLM推理系统，显著减少内存占用，提高吞吐量，适合资源受限环境。

### 8. 不足与局限

- **适用场景限制**：面向需要保留核心语义的任务（如检索、推理）优化，在要求绝对逐词精确的任务（如法律、生物医学文档分析）中仍可能丢失信息。
- **块大小固定**：当前使用固定块大小（默认10），虽然性能稳健，但未利用语言自然边界（如句子结尾），可能造成不理想的切分。
- **混合策略未深入**：实验仅初步分析早期层用ChunkKV、深层用SnapKV的混合模型，发现任务依赖性，未设计自适应方法。
- **硬件测试有限**：效率实验仅在A40 GPU上进行，未验证不同GPU（如消费级RTX 4090）或分布式场景下的表现。
- **理论分析待完善**：附录C的理论推导是定性的，未给出严格界或实验验证噪声项ξθ(r)的具体值。
- **代码未提供**：论文提到代码将在公开链接中发布，但当前未提供，影响复现性。

（完）
