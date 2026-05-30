---
title: "Sim-LLM: Optimizing LLM Inference at the Edge through Inter-Task KV Reuse"
title_zh: Sim-LLM：通过任务间KV重用优化边缘LLM推理
authors: "Ruikun Luo, Changwei Gu, Qiang He, Feifei Chen, Song Wu, Hai Jin, Yun Yang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=z1Cvcovlms"
tags: ["query:edge-llm"]
score: 8.0
evidence: 通过KV缓存重用优化边缘LLM推理
tldr: 针对边缘服务器上LLM推理KV缓存内存消耗大的问题，本文提出Sim-LLM，利用任务间相似性重用KV缓存，显著降低GPU内存占用，且计算开销小，适用于资源受限的边缘节点。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-z1cvcovlms/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 642, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z1cvcovlms/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z1cvcovlms/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 428, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z1cvcovlms/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 881, \"height\": 388, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z1cvcovlms/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1421, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z1cvcovlms/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1199, \"height\": 681, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z1cvcovlms/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 713, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z1cvcovlms/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1343, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z1cvcovlms/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 721, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z1cvcovlms/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 721, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z1cvcovlms/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 703, \"height\": 314, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z1cvcovlms/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 853, \"height\": 267, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-z1cvcovlms/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 749, \"height\": 201, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z1cvcovlms/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 955, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z1cvcovlms/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 898, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z1cvcovlms/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 506, \"label\": \"Table\"}]"
motivation: KV缓存导致边缘节点GPU内存消耗大，现有压缩方法计算开销高。
method: 基于任务相似性重用KV缓存，减少冗余存储。
result: 降低了KV缓存内存占用，提升了边缘推理效率。
conclusion: Sim-LLM为边缘LLM推理提供了轻量级KV缓存优化方案。
---

## Abstract
KV cache technology, by storing key-value pairs, helps reduce the computational overhead incurred by *large language models* (LLMs). It facilitates their deployment on resource-constrained edge computing nodes like edge servers. However, as the complexity and size of tasks increase, KV cache usage leads to substantial GPU memory consumption. Existing research has focused on mitigating KV cache memory usage through sequence length reduction, task-specific compression, and dynamic eviction policies. However, these methods are computationally expensive for resource-constrained edge computing nodes. To tackle this challenge, this paper presents Sim-LLM, a novel inference optimization mechanism that leverages task similarity to reduce KV cache memory consumption for LLMs. By caching KVs from processed tasks and reusing them for subsequent similar tasks during inference, Sim-LLM significantly reduces memory consumption while boosting system throughput and increasing maximum batch size, all with minimal accuracy degradation. Evaluated on both A40 and A100 GPUs, Sim-LLM achieves a system throughput improvement of up to 39.40\% and a memory reduction of up to 34.65%, compared to state-of-the-art approaches. Our source code is available at https://github.com/CGCL-codes/SimLLM.

---

## 论文详细总结（自动生成）

# Sim-LLM 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：在边缘计算系统中部署大语言模型（LLM）时，KV 缓存（Key-Value Cache）的存储开销随序列长度、批大小和层数线性增长，导致 GPU 内存消耗巨大，限制了边缘节点的吞吐量和可支持的批大小。
- **现有方法局限**：已有的 KV 缓存压缩方法（如序列长度压缩、逐层/逐 token 的剪枝、动态驱逐策略）虽然在减少内存方面有一定效果，但计算开销高，不适合资源受限的边缘节点。
- **核心观察**：边缘服务器由于服务区域有限、处理任务常反映局部热点事件，任务之间普遍存在语义相似性（Figure 1）；并且相似任务生成的 KV 缓存也具有强相似性（Figure 2a, 2b）；重用相似 KV 不会显著影响模型性能（Figure 4）。
- **整体含义**：Sim-LLM 首次从任务级视角出发，利用任务间相似性重用 KV 缓存，以降低内存、提升吞吐量，且引入额外计算开销极小，特别适合边缘场景。

## 2. 方法论

### 核心思想
- 缓存已处理任务的顶层（top-layer）KV 和嵌入向量，当新任务与某缓存任务相似（余弦相似度 > 0.8）时，直接重用该顶层 KV，跳过大多数层的 KV 计算，从而减少内存和计算。
### 关键技术细节
1. **任务相似性识别**：
   - 使用**余弦相似度**衡量任务语义相似性（阈值设为 0.8，通过实验权衡速度与精度得出）。
   - 对于小批量任务，直接遍历比较；对大批量任务，采用**局部敏感哈希（LSH）** 将任务嵌入映射到桶中，快速找到潜在相似任务，降低查找开销。
2. **KV 管理器（KV_Manager）**：
   - 仅缓存顶层 KV（因为顶层包含最丰富的语义信息），避免存储所有层的 KV，大幅减少内存。
   - 采用**最近最少使用（LRU）** 策略驱逐过期缓存，优先保留频繁重用的任务 KV。
   - 对于不相似的任务（没有匹配），采用“三明治”结构：仅缓存底部三层和顶部三层的 KV，中间层 KV 不计算，减少参数和计算。
3. **跨节点 KV 共享**：
   - 结合 LSH 和**原型学习（prototype learning）**：每个边缘服务器维护一个全局特征表，记录各服务器处理的任务原型。
   - 当本地无匹配时，通过查询全局特征表，将任务卸载到最可能含有相似任务的其他边缘服务器，避免多跳查询导致的资源浪费。
   - 传输时仅传输任务嵌入或序列（而非整个 KV 缓存），减少通信开销；若目标服务器繁忙，则传回 KV 缓存。
4. **推理加速**：
   - 对于匹配的任务，直接使用缓存的顶层 KV 进行推理，跳过中间层计算，加速预填充阶段（prefilling）。
   - 对于批处理，当一半以上任务匹配时，未匹配任务延迟到下一批次处理，保证整体加速效果。

## 3. 实验设计

- **模型**：TinyLlama-1.1B、Llama2-7B、Llama2-13B、InternLM2-7B（中英双语）。
- **基准数据集**：使用 OpenCompass 和 lm-eval-harness 框架，涵盖五大能力：
  - **推理**：CMNLI、HellaSwag、PIQA；
  - **语言**：CHID、WSC；
  - **知识**：CommonSenseQA、BoolQ；
  - **考试**：MMLU、CMMLU；
  - **理解**：RACE-H/M、XSum、C3。
- **评估指标**：困惑度（PPL）、吞吐量（tokens/s）、GPU 内存占用、零样本准确率。
- **对比方法**：原生 Transformer、H2O、StreamingLLM、ZipCache、ArkVale（均为 KV 缓存压缩/剪枝/量化领域 SOTA）。
- **场景**：单节点（A100 80GB）和多节点（4台 A40 40GB x 4 每台）环境，模拟边缘计算系统。

## 4. 资源与算力

- **单节点实验**：1 块 NVIDIA A100 80GB GPU。
- **多节点实验**：4 台物理服务器，每台配备 4 块 NVIDIA A40 40GB GPU（共 16 块 A40）。
- **未明确说明**：文中未提及训练/评估的总时长、GPU 小时数等具体算力消耗细节。

## 5. 实验数量与充分性

- **实验组数**：约 7 大类实验，包括：
  - 吞吐量与内存对比（Figure 7，2 个子图，4 种基线 + 本方法）；
  - PPL 随缓存大小变化（Figure 8，3 种模型）；
  - 延迟与内存对比（Figure 9，2 种模型）；
  - 源层选择影响（Figure 10，2 个子图）；
  - 相似任务比例影响（Figure 11，2 个子图）；
  - 余弦相似度阈值影响（Figure 12，3 个子图）；
  - 零样本准确率（Table 2，4 种模型 × 多项基准）；
  - 最大批大小与吞吐量（Table 3，多序列长度 + 多 GPU）；
  - 突发/均匀负载延迟（Table 1）；
- **充分性评价**：实验覆盖了多种模型大小、多种基准任务、多种缓存配置、多 GPU 环境，并进行了消融（源层、阈值、相似比例）和对比（与 4 个 SOTA 方法），总体上较为充分、客观、公平。但未报告误差棒（因计算资源有限），对结果的统计显著性支撑略有不足。

## 6. 主要结论与发现

- **性能提升**：相比最优基线（ArkVale），Sim-LLM 在 A40 上平均实现吞吐量提升 **33.04%**（最高 39.40%），GPU 内存减少 **30.05%**（最高 34.65%）。
- **质量保持**：零样本准确率与原生模型相当（如 Llama-7B 平均 46.89 vs 原生 48.41，差距 < 1.5%）；PPL 在较大缓存尺寸下甚至优于原生（因重用相似 KV 提供了额外上下文）。
- **鲁棒性**：在不同相似比例、不同缓存大小、不同阈值下均能保持稳定性能提升。
- **可扩展性**：支持跨节点共享，在突发负载下通过 LRU 策略保持高效。

## 7. 优点

- **创新性**：首次从任务级相似性角度优化 KV 缓存，而非传统的 token/层压缩，思路新颖。
- **轻量高效**：仅缓存顶层 KV + 使用 LSH 加速查找，额外计算开销极小，特别适合边缘节点。
- **实用性强**：结合原型学习实现跨节点 KV 共享，减少通信开销；与现有 MHA/GQA 注意力兼容，可同时使用 FlashAttention 等底层优化。
- **实验充分**：覆盖多个模型、多种下游任务、消融实验、多 GPU 场景，结果可靠。

## 8. 不足与局限

- **依赖任务相似性**：当推理任务间缺乏语义相似性时（如突发随机话题），Sim-LLM 退化为标准推理，优势消失。
- **额外存储开销**：需要长期存储顶层 KV 和嵌入向量，当缓存容量过大（如序列长度 > 4096）时，内存节省可能被抵消（Figure 9b 所示）。
- **模型同质性要求**：跨节点共享要求所有边缘服务器部署相同模型（KV 形状一致），不适用于异构模型场景。
- **缺少误差棒**：实验未报告误差棒或置信区间，统计显著性不够透明。
- **未讨论隐私/安全**：任务缓存和跨节点传输可能涉及用户数据隐私问题，论文未涉及相关讨论。
- **仅测试了英文/中文模型**：未在更大模型（如 70B+）或更多语言上验证。

（完）
