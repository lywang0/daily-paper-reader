---
title: "CHAI: Clustered Head Attention for Efficient LLM Inference"
title_zh: CHAI：面向高效LLM推理的聚类头注意力
authors: "Saurabh Agarwal, Bilge Acun, Basil Hosmer, Mostafa Elhoushi, Yejin Lee, Shivaram Venkataraman, Dimitris Papailiopoulos, Carole-Jean Wu"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=xcDRx8vzCa"
tags: ["query:edge-llm"]
score: 7.0
evidence: 通过注意力头聚类减少LLM推理的内存和计算
tldr: 当前LLM服务中多头注意力占据大量内存和计算。CHAI通过运行时聚类高相关性的注意力头，减少冗余计算和内存占用。实验表明在保持模型质量的同时，能够显著降低内存需求和加速推理。该方法为高效LLM推理提供了轻量级、即插即用的优化方案。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 679, \"height\": 518, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 619, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 617, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 814, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 631, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 628, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 702, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1666, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1693, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 683, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 681, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1653, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 612, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 718, \"height\": 457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 605, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 715, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 705, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 704, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 713, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 711, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1538, \"height\": 907, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1535, \"height\": 910, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1533, \"height\": 1848, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1538, \"height\": 2318, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1536, \"height\": 2322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1533, \"height\": 1848, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1531, \"height\": 2327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1531, \"height\": 2331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-xcdrx8vzca/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 988, \"height\": 453, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-xcdrx8vzca/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-xcdrx8vzca/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 863, \"height\": 331, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-xcdrx8vzca/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 330, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-xcdrx8vzca/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 854, \"height\": 128, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-xcdrx8vzca/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 865, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-xcdrx8vzca/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 607, \"height\": 159, \"label\": \"Table\"}]"
motivation: "多头注意力在LLM推理中占用超过50%的内存和计算，存在跨头冗余。"
method: 基于注意力头之间相关性进行运行时聚类，合并高度相关的头以减少计算。
result: 在多种LLM上验证，显著降低内存需求并加速推理，且不损失模型质量。
conclusion: CHAI通过利用注意力头冗余，实现了高效、实用的LLM推理优化。
---

## Abstract
Large Language Models (LLMs) with hundreds of billions of parameters have transformed the field of machine learning. However, serving these models at inference time is both compute and memory intensive, where a single request can require multiple GPUs and tens of Gigabytes of memory. Multi-head attention is one of the key components of LLMs, which can for over 50% of LLMs memory and compute requirement. We observe that there is a high amount of redundancy across heads on which tokens they pay attention to. Based on this insight, we propose Clustered HeadAttention ( CHAI ). CHAI combines heads with a high amount of correlation for self-attention at runtime, thus reducing both memory and compute. In our experiments, we show that CHAI is able to reduce the memory requirements for storing K,V cache by up to 21.4% and inference time latency by up to 1.73× without any fine-tuning required. CHAI achieves this with a maximum 3.2% deviation in accuracy across 3 different models (i.e. OPT-66B, LLAMA-7B, LLAMA-33B) and 5 different evaluation datasets.

---

## 论文详细总结（自动生成）

# CHAI: Clustered Head Attention for Efficient LLM Inference — 详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）在推理时面临严重的计算和内存瓶颈，其中多头注意力（Multi-Head Attention, MHA）是核心组件，可占LLM超过50%的内存和计算需求。随着模型规模增大（如LLaMA-65B每层64头），MHA的K、V缓存巨大，序列长度增加时内存压力急剧上升。
- **背景问题**：现有优化方法存在局限：
  - 剪枝方法（如DejaVu）需微调或推理时MLP预测，且对参数高效模型（如LLaMA）效果差；仅减少计算，不降低K、V缓存。
  - 注意力模块协同设计（如GQA）需重训练，成本高，且仅减少K、V缓存，不降低计算。
- **本文目标**：提出一种无需微调或重训练、同时降低计算和内存开销的运行时方法——**CHAI (Clustered Head Attention)**。

## 2. 方法论

### 核心思想
- **观察**：多个注意力头在相同序列上产生的注意力分数高度相似（冗余），如图2所示，LLaMA-7B中某些层内头部间相关性高于0.95，且冗余度随层数加深而增大。
- **方案**：在运行时将产生相似注意力输出的头部聚成簇，每个簇只计算一个代表头的自注意力，从而减少计算量和K、V缓存大小。

### 关键技术细节
- **离线确定每层簇数**：利用C4数据集上1024个样本，收集每层注意力输出，通过肘部图（Elbow plot）选择聚类误差趋于平缓时的簇数（图8）。该步骤对每个新模型仅执行一次。
- **在线确定簇成员**：每个推理请求开始时，先用原始MHA处理前5个token，根据这5个token的注意力输出进行K-Means聚类，确定每层头部到簇的映射。后续token则直接使用该映射，只计算每个簇的代表头（图9表明5个token后簇成员变化极少）。
- **推理流程**（图10）：
  1. 离线：模型级簇数确定。
  2. 在线：请求到达后，前5个token全量MHA计算，获取头部激活并聚类。
  3. 从第6个token起，使用Clustered Head Attention：只对每个簇的代表头执行Q、K投影和注意力计算，其他头复用代表头的注意力权重，但所有头的V向量仍保留并加权（图3）。
- **公式**：与传统MHA相比，CHAI将H个头分为k个簇，计算复杂度从O(H·T²)降为O(k·T²)，同时K、V缓存大小减少为原来的k/H（实际只移除K向量，V向量保留）。

## 3. 实验设计

- **模型**：OPT-66B、LLaMA-7B、LLaMA-33B，以及LLaMA2-70B（GQA模型）和量化模型（4-bit GPTQ）。
- **数据集**：5个常见NLP基准：PIQA、HellaSwag、Arc-Challenge、Arc-Easy、BoolQ。
- **基准方法**：完整MHA（基线）、DejaVu（不同稀疏度10%/30%/50%）、SpAtten、CHAI-static（使用离线固定簇成员）、CHAI（动态簇成员）。
- **评估指标**：准确率（精度变化）、K、V缓存大小（MB）、端到端时延（首token时延和后续token时延）。

## 4. 资源与算力

- **硬件**：NVIDIA V100 GPU集群。
- **模型配置**：
  - OPT-66B：8张GPU（单节点）。
  - LLaMA-33B：4张GPU。
  - LLaMA-7B：1张GPU。
- **训练/微调**：本文方法**无需任何微调或重训练**，仅需离线小样本（1024条C4数据）进行一次聚类分析。文中未报告离线分析的具体时长，但该过程仅为单次预处理，成本极低。
- **运行时开销**：在线聚类（K-Means）耗时约0.6ms/请求，占推理总时长的约0.008%。

## 5. 实验数量与充分性

- **共进行多组实验**：
  - 三个主流模型 × 五个数据集 = 15个主实验结果（表1-3）。
  - 与DejaVu在不同稀疏度（10%/30%/50%）和SpAtten对比。
  - 消融实验：CHAI-static（无动态聚类） vs CHAI。
  - 与量化结合实验（表4）。
  - 与GQA结合实验（表5）。
  - 剪枝Q、K、V vs 仅剪枝Q、K的对比（表6）。
  - 额外分析：聚类误差图、簇成员稳定性、平均相关性、不同数据集/样本量对簇数的影响。
- **充分性**：实验覆盖了不同规模（7B/33B/66B）和类型（OPT/LLaMA）的模型，五个多样化数据集，多个对比方法，并进行了消融和鲁棒性分析。对比方法（DejaVu、SpAtten）均为当时SOTA，且使用了官方实现或复现。实验设置公平（如DejaVu按作者报告稀疏比复现）。
- **不足**：未在更大模型（如70B以上）上做全面实验（仅LLaMA2-70B有初步GQA结合实验）；未与更多剪枝/量化方法（如SmoothQuant等）联合对比。

## 6. 主要结论与发现

- CHAI能在**无需微调**的情况下，将LLM推理时延降低最高**1.73倍**（首token，LLaMA-7B），后续token时延降低最高**5倍**；K、V缓存大小降低**21.4%**。
- 准确率变化**最大仅3.2%**（LLaMA-7B上HellaSwag下降3.2%，其他数据集大多在1%以内）。
- 相比DejaVu：DejaVu在LLaMA-7B上需稀疏度≤10%才能保持精度，此时加速有限；CHAI在所有稀疏度/模型上均优于DejaVu。
- 相比SpAtten：CHAI在LLaMA-7B/33B上显著更优。
- 动态簇成员（CHAI）优于静态簇成员（CHAI-static），说明需要按请求上下文调整。
- CHAI可与量化（GPTQ）和GQA协同工作，进一步降低开销。
- 仅修剪Q、K（保留V）比同时修剪Q、K、V更优（表6）。

## 7. 优点

- **无需微调/重训练**：直接对预训练LLM使用，适用性强。
- **同时降低计算和内存**：既加速推理，又减小K、V缓存，对比仅剪计算或仅减缓存的方法更具综合性。
- **运行时轻量**：只需前5个token全量计算后做一次快速聚类（0.6ms），后续无额外开销，且不需要自定义稀疏核。
- **跨模型跨数据集鲁棒**：在OPT、LLaMA系列上均表现稳定，且对量化模型同样有效。
- **可与其他优化正交结合**：如GQA、量化、FlashAttention等，可叠加使用。
- **开源实现**：基于Meta的xFormers构建，便于复现。

## 8. 不足与局限

- **未在超大规模模型（如175B）上验证**：实验最大为66B，且OPT-66B实验仅与MHA和CHAI对比，未与DejaVu在OPT-66B上做详细时间对比（因DejaVu未公开加速核）。
- **依赖前5个token全量MHA**：对于极短序列（<5 token）无法发挥优势；长序列下加速比更高。
- **仅适用于自回归解码**：不适用于编码器-解码器或双向模型。
- **准确率偏差在个别数据集上略大**：如LLaMA-7B HellaSwag下降3.2%，虽在可接受范围，但对精度敏感的应用需谨慎。
- **聚类方法简单**：使用K-Means，可能无法捕获更复杂的头部相似性模式；簇数由离线肘部图确定，可能存在主观性（但文中通过多数据验证了簇数稳定性）。
- **未与最新高效注意力变体（如MQA）对比**：但通过与GQA结合实验部分弥补。

（完）
