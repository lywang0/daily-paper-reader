---
title: "KV Cache is 1 Bit Per Channel: Efficient Large Language Model Inference with Coupled Quantization"
title_zh: KV缓存每通道1比特：耦合量化实现高效大型语言模型推理
authors: "Tianyi Zhang, Jonah Wonkyu Yi, Zhaozhuo Xu, Anshumali Shrivastava"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=pNnvzQsS4P"
tags: ["query:edge-llm"]
score: 5.0
evidence: KV缓存的耦合量化实现高效LLM推理
tldr: 该论文发现KV缓存激活向量通道间高度依赖，联合熵增长慢于独立熵之和，利用此特性提出耦合量化方法，在极低比特（每通道1比特）下实现高效压缩。实验表明该方法在保持模型质量的同时大幅减少KV缓存内存占用，加速LLM推理，是内存高效推理的重要技术。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-pnnvzqss4p/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 749, \"height\": 563, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pnnvzqss4p/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 695, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pnnvzqss4p/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1438, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pnnvzqss4p/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 561, \"height\": 347, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pnnvzqss4p/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1431, \"height\": 449, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pnnvzqss4p/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1424, \"height\": 758, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pnnvzqss4p/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1425, \"height\": 757, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pnnvzqss4p/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1432, \"height\": 763, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-pnnvzqss4p/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1433, \"height\": 763, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1435, \"height\": 881, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 1238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1171, \"height\": 537, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1441, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 730, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 494, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1425, \"height\": 879, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1391, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1123, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1369, \"height\": 174, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1451, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 775, \"height\": 576, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1180, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1183, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 703, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-pnnvzqss4p/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 946, \"height\": 631, \"label\": \"Table\"}]"
motivation: 大模型部署中KV缓存成为内存和延迟瓶颈，现有低位量化精度下降严重。
method: 利用通道间耦合性进行联合量化。
result: 每通道1比特量化，接近无损。
conclusion: 耦合量化可实现极低位KV缓存压缩。
---

## Abstract
Efficient deployment of Large Language Models (LLMs) requires batching multiple requests together to improve throughput. As batch size, context length, or model size increases, the size of key and value (KV) cache quickly becomes the main contributor to GPU memory usage and the bottleneck of inference latency and throughput. Quantization has emerged as an effective technique for KV cache compression, but existing methods still fail at very low bit widths. Currently, KV cache quantization is performed per-channel or per-token independently. Our analysis shows that distinct channels of a key/value activation embedding are highly interdependent, and the joint entropy of multiple channels grows at a slower rate than the sum of their marginal entropy, which implies that per-channel independent quantization is sub-optimal. To mitigate this sub-optimality, we propose Coupled Quantization (CQ), which couples multiple key/value channels together for quantization to exploit their interdependence and encode the activations in a more information-efficient manner. Extensive experiments reveal that CQ compares favorably with existing baselines in preserving model quality, and improves inference throughput by 1.4–3.5$\times$ relative to the uncompressed baseline. Furthermore, we demonstrate that CQ can preserve model quality reasonably with KV cache quantized down to 1 bit.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：大语言模型（LLM）部署时，批量处理请求是提升吞吐量的关键。但随着批量大小、上下文长度或模型规模的增加，KV缓存的大小迅速成为GPU内存的主要消耗者，并成为推理延迟和吞吐量的瓶颈。
- **现有方法的不足**：现有KV缓存量化方法（如KIVI、KVQuant）均采用**每通道独立量化**或**每令牌独立量化**。这些方法忽略了通道之间的相互依赖性，导致在极低比特（如1比特/激活）时模型质量急剧下降。
- **核心发现**：论文通过信息论分析发现，KV激活嵌入的**不同通道之间存在高度依赖性**，多通道的联合熵增长速率慢于各通道边际熵之和。这意味着独立量化是次优的，**联合编码多个通道可以更高效地利用信息**。
- **整体目标**：提出一种利用通道间依赖性的耦合量化方法，在极低位宽（低至1比特/激活）下仍能保持模型质量，从而大幅降低KV缓存内存占用并加速推理。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将多个连续通道**耦合（耦合）在一起**，进行联合量化。每个通道组共享一个多维码本，以利用通道间的互信息，实现更信息高效的编码。
- **关键技术细节**：
  - **通道分组**：将每个注意力头的KV激活通道划分为**不重叠的连续组**，每组包含`c`个通道。
  - **联合量化（Coupled Quantization, CQ）**：对每组学习一组**多维质心**（维度等于组内通道数）。量化时，每个组向量被映射到最近的质心（基于L2距离）。
  - **质心学习**：
    - **均匀聚类**：使用k-means（k-means++初始化）最小化量化误差（公式5）。
    - **Fisher信息引导聚类**：利用对角Fisher信息矩阵（梯度的平方）对每个激活的重要性加权，通过**加权k-means**优化质心（公式6），以更好地保留重要激活的精度。
  - **推理优化**：设计融合GPU内核，将中心点缓存至共享内存，减少随机访问延迟，实现高效反量化。
- **表示法**：`CQ-<c>c<b>b`表示组大小c，码本比特数b。例如CQ-4c8b对应每激活2比特（8/4=2）。

## 3. 实验设计：数据集、基准、对比方法

- **模型**：LLaMA-7b、LLaMA-13b、LLaMA-2-7b、LLaMA-2-13b、Mistral-7b，以及LLaMA-3-8b（附录）。
- **数据集**：
  - **困惑度**：WikiText-2、C4。
  - **零样本准确率**：WinoGrande、PIQA、ARC Challenge（Arc-C）、ARC Easy（Arc-E）、HellaSwag。
  - **长上下文**：GSM8K（链式思考）、MMLU（少样本链式思考，细分为STEM、人文、社科、其他）。
  - **其他**：LongBench（与KIVI对比）、Passkey Retrieval。
- **对比方法**：
  - 未压缩的FP16基线。
  - 整数量化（INT4、INT4-g128、INT2、INT2-g128）。
  - NormalFloat量化（NF4、NF4-g128、NF2、NF2-g128）。
  - KVQuant（稠密版本及稠密+1%稀疏版本），包括1比特、2比特、4比特配置。
  - KIVI（附录对比）。
- **评估指标**：比特每激活（BPA）、困惑度、准确率、吞吐量、延迟。

## 4. 资源与算力

- **硬件**：4块NVIDIA A100 40GB GPU。
- **软件**：PyTorch、HuggingFace Transformers。
- **质心学习时间**：附录表9给出了各配置的质心学习时间，例如LLaMA-7b在CQ-8c8b配置下需14分钟，CQ-8c10b需104分钟。所有质心学习均在单GPU上完成。
- **质心存储开销**：占总模型权重的0.232%～3.984%（取决于配置）。
- **未明确**：论文未报告完整实验（如所有基准测试）的总计算时间或GPU小时数。

## 5. 实验数量与充分性

- **实验数量**：丰富且全面。
  - 主表（表1、表2）覆盖5个模型×2个困惑度数据集+3个零样本基准×多种比特率。
  - 消融实验（表5、表6、图5）验证通道耦合数量、Fisher引导、键/值单独量化效果。
  - 长上下文（表3）和滑动窗口（表4）实验。
  - 附录中包含LLaMA-3、LongBench、Passkey Retrieval、子1比特量化（16c12b）等额外实验。
  - 对比方法全面（INT、NF、KVQuant、KIVI），且报告了相同BPA下的公平比较。
- **充分性与客观性**：
  - 实验设计较为公平：校准数据统一使用WikiText-2训练集16个序列；KVQuant也采用相同校准数据。
  - 困惑度和准确率均报告，且结果可复现（代码未开源，但算法描述详细）。
  - 不足：未报告统计显著性检验（如置信区间），但提供了误差条（如延迟测量）。
  - 实验覆盖了多个主流LLM系列和多种任务类型，具有较好的代表性。

## 6. 论文的主要结论与发现

- **耦合量化显著优于独立量化**：在相同比特率下，CQ的困惑度和准确率均优于所有对比的稠密量化方法。
- **1比特量化接近无损**：CQ-8c8b（1比特/激活）在WikiText-2上LLaMA-7b困惑度8.09，而FP16为5.68；结合128令牌滑动窗口全精度缓存后，困惑度仅增加0.3-0.33。
- **吞吐量提升**：CQ-8c8b相比FP16实现了**最大15倍批量大小**和**1.4-3.5倍吞吐量提升**。
- **Fisher信息引导有效**：加权质心学习进一步降低了困惑度（例如CQ-8c8b从32.12降至8.09）。
- **耦合通道数量增加改善质量**：随着组内通道数增加，模型质量持续提升，验证了通道依赖性的利用效果。

## 7. 优点

- **方法新颖**：首次系统性地利用KV缓存通道间的依赖性进行联合量化，理论动机清晰（信息论）。
- **极低位量化表现突出**：在1比特/激活下仍能保持合理质量，远超现有方法。
- **设计实用**：
  - 引入Fisher信息引导质心学习，改善重要性保留。
  - 融合GPU内核和共享内存优化，实现高效推理。
  - 滑动窗口策略提供质量与压缩的灵活折衷。
- **实验充分**：覆盖多模型、多任务、多基线，并包含消融、泛化性、子1比特等深度分析。
- **可部署性**：质心学习离线完成，推理时额外开销小，且跨数据集泛化好。

## 8. 不足与局限

- **安全性未评估**：论文承认“损失压缩影响模型质量”，但未研究对毒性、偏见、幻觉等安全维度的影响（附录也提到）。
- **校准依赖**：需要少量校准数据（16个序列），但实验显示跨数据集泛化良好，理论上仍存在域外失效风险。
- **质心存储开销**：随着比特率增加，码本大小指数增长，例如CQ-8c10b的质心参数占模型权重的3.984%，在一定场景下抵消部分压缩收益。
- **延迟未见明显优势**：附录表14显示CQ的预填充和解码延迟与KIVI相当，未显著优于FP16（尤其在滑动窗口模式下）。
- **统计显著性缺失**：未提供多次运行的标准差或置信区间（除延迟外），可能影响结论稳健性。
- **代码未开源**：降低可复现性，但算法细节已充分公开。

（完）
