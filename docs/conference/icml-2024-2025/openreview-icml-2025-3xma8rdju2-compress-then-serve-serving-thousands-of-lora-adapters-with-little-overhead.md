---
title: "Compress then Serve: Serving Thousands of LoRA Adapters with Little Overhead"
title_zh: 先压缩后服务：以极低开销服务数千个LoRA适配器
authors: "Rickard Brüel Gabrielsson, Jiacheng Zhu, Onkar Bhardwaj, Leshem Choshen, Kristjan Greenewald, Mikhail Yurochkin, Justin Solomon"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=3XMA8RDJu2"
tags: ["query:edge-llm"]
score: 6.0
evidence: 基于压缩的服务多LoRA适配器减少开销
tldr: 该论文提出联合压缩LoRA适配器到共享基的方法，并配以适配器专用缩放矩阵，支持高效服务数千个适配器。通过聚类学习，进一步减少存储和加载开销，使LLM服务框架能够同时管理大量定制化模型，显著提升了多租户场景下的服务效率。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-3xma8rdju2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 866, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3xma8rdju2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 862, \"height\": 574, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3xma8rdju2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 842, \"height\": 572, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3xma8rdju2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 828, \"height\": 558, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3xma8rdju2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1765, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3xma8rdju2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 871, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3xma8rdju2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 871, \"height\": 444, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 756, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1773, \"height\": 539, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1204, \"height\": 913, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1206, \"height\": 1233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 396, \"height\": 2286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 350, \"height\": 2297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 296, \"height\": 2308, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1399, \"height\": 540, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1396, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1775, \"height\": 1751, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1774, \"height\": 1602, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1775, \"height\": 1751, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1775, \"height\": 1608, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1775, \"height\": 1751, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1775, \"height\": 1644, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1774, \"height\": 1535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1774, \"height\": 1669, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1770, \"height\": 517, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1771, \"height\": 539, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 816, \"height\": 638, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 816, \"height\": 564, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1785, \"height\": 566, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3xma8rdju2/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1787, \"height\": 678, \"label\": \"Table\"}]"
motivation: 服务大量LoRA适配器时连续加载卸载导致高延迟。
method: 将多个LoRA适配器联合压缩到共享基，并学习适配器聚类以进一步优化。
result: 方法在保持精度的同时大幅降低了存储和加载开销。
conclusion: 该压缩方法使LLM服务框架能高效支持海量LoRA适配器，适用于个性化服务。
---

## Abstract
Fine-tuning large language models (LLMs) with low-rank adaptations (LoRAs) has become common practice, often yielding numerous copies of the same LLM differing only in their LoRA updates. This paradigm presents challenges for systems that serve real-time responses to queries that each involve a different LoRA. Prior works optimize the design of such systems but still require continuous loading and offloading of LoRAs, as it is infeasible to store thousands of LoRAs in GPU memory. To mitigate this issue, we investigate the efficacy of compression when serving LoRAs. We propose a method for the joint compression of LoRAs into a shared basis paired with LoRA-specific scaling matrices. We extend our algorithm to learn clusters of LoRAs that are amenable to joint compression, allowing it to scale gracefully to large LoRA collections. Our experiments with up to 1000 LoRAs demonstrate that compressed LoRAs preserve performance while offering major throughput gains in realistic serving scenarios with over a thousand LoRAs, maintaining 80\% of the throughput of serving a single LoRA.

---

## 论文详细总结（自动生成）

# Compress then Serve: Serving Thousands of LoRA Adapters with Little Overhead 论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：随着大语言模型（LLM）微调中低秩适配（LoRA）的普及，大量用户各自拥有专属的LoRA适配器（数千个），需要提供实时推理服务。但GPU内存无法同时存储所有适配器，导致频繁的加载/卸载操作，严重降低系统吞吐量。现有系统（如S-LoRA、vLLM）虽优化了调度，但无法根本解决内存瓶颈。
- **研究目标**：通过对多个LoRA适配器进行联合压缩，在不显著损失下游任务性能的前提下，大幅减少参数总量和内存占用，从而提升多LoRA推理服务的吞吐量。核心挑战是在极低开销下支持数千个适配器的并发服务。

## 2. 方法论

### 核心思想
将一组LoRA适配器联合压缩到一个共享的低秩子空间，每个适配器仅保留一个较小的缩放矩阵（或对角阵），从而显著减少存储和传输开销。对于大规模适配器集合，引入聚类机制：将相似适配器分组，每组独立进行联合压缩，以保持重建质量。

### 关键技术细节
- **Joint Diagonalization (JD)**：对于每个LoRA的更新矩阵 $B_i A_i$（$r_i$ 秩），学习共享的 $U \in \mathbb{R}^{d_B \times r}$ 和 $V \in \mathbb{R}^{d_A \times r}$，以及适配器专属的 $\Sigma_i$，使得 $B_i A_i \approx U \Sigma_i V^\top$。优化目标为所有适配器的 Frobenius 范数重建误差之和。
  - **JD-Full**：$\Sigma_i$ 为 $r \times r$ 全矩阵，约束 $U$ 和 $V$ 正交。
  - **JD-Diag**：$\Sigma_i$ 为对角矩阵，$U$ 和 $V$ 不约束正交。
- **优化算法**：交替最小二乘法（对 $U$、$V$、$\Sigma_i$ 迭代求解），或基于特征值迭代的GPU加速算法。
- **聚类扩展**：当适配器数量很大（$n \gg r^2$）时，聚类可将适配器分为 $k$ 簇，每个簇拥有独立的 $U_j, V_j$ 和簇内共享的 $r$ 秩。聚类目标函数为簇内JD重建误差总和，通过交替优化簇分配和簇内JD求解。
- **理论保障**：定理1给出了重建误差的上界，与 $L$ 矩阵的奇异值分布相关，证明聚类可缓解 $n$ 增长对重建误差的影响。

## 3. 实验设计

### 数据集与场景
- **训练数据集**：从 Super-NaturalInstructions（Wang et al. 2022）中选取1000个自然语言指令任务（涵盖分类、生成、推理等），训练了1000个 LoRA 适配器，基于 Mistral-7B-Instruct-v0.2 模型，秩均为16。
- **评估指标**：主要指标为 Rouge-L，辅以 Rouge-1、精确匹配、交叉熵损失、压缩后与原模型的一致率。报告相对性能（压缩后/原始LoRA）。
- **推理场景**：在 vLLM 多LoRA推理引擎中，模拟异步请求（输入莎士比亚十四行诗，生成10个token），测量吞吐量（请求/秒）。

### 对比方法
- **未压缩 LoRA**（原始 rank-16）
- **TIES-merging**（合并所有LoRA为单一适配器）
- **SVD**（独立压缩每个 LoRA 至不同秩）
- **JD-Diag**（本文方法）
- **JD-Full**（本文方法）
- **Clustering + JD-Full**（本文方法）

### 实验规模
- 对 10、50、100、500、1000 个 LoRA 分别测试多种压缩秩（8/16/32/64/128/256）及不同聚类数（5/7/10/25）。
- 每个设置重复3次，报告均值和标准差。
- 吞吐量实验中，匹配 GPU 内存占用相同条件下比较 vLLM 原生多LoRA与压缩版本。
- 额外进行了消融实验（不同LoRA秩、收敛判据、隐私泄漏、随机LoRA重建对比等）。

## 4. 资源与算力

- **GPU 型号**：吞吐量实验使用单张 **H100 80GB** GPU，内存限制为40%（约32GB），模拟低成本硬件场景。
- **训练细节**：未明确说明训练1000个LoRA所用的GPU数量及时长。文中仅提及使用Huggingface库、量化配置（4-bit QLoRA）进行训练。
- **备注**：联合压缩算法（JD）可离线CPU预计算，推理时仅需GPU执行线性代数运算。实验未详细报告预计算耗时。

## 5. 实验数量与充分性

- **实验充分性**：实验覆盖了多种规模（4～1024个LoRA）、多种压缩秩、多种聚类配置，并重复多次。指标全面（Rouge、损失、一致率、吞吐量），对比基线包括 TIES、SVD、原生LoRA。消融实验包含不同LoRA秩、收敛性、隐私性、随机重建对比等。
- **客观公平性**：性能比较基于相对值（相对于原始LoRA），消除任务间绝对难度差异。吞吐量实验在控制GPU内存相同条件下进行，公平对比vLLM多LoRA基线。
- **潜在不足**：仅使用单一基础模型（Mistral-7B），未验证在其他模型大小或架构上的泛化性；吞吐量实验仅测试了10 token生成长度和特定输入分布；未与量化等互补压缩技术联合评估。

## 6. 主要结论与发现

- **性能保持**：JD 压缩（尤其是 JD-Full 结合聚类）在压缩比高达90%以上时，仍能保持原始LoRA 99%+ 的性能（Rouge-L），甚至有时略优于原始LoRA。
- **吞吐量提升**：在服务1000个LoRA时，压缩版本相比vLLM原生多LoRA，吞吐量提升约1.6倍，且达到单LoRA服务吞吐量的80%。
- **聚类有效性**：当 $n \geq 100$ 时，聚类显著优于单组JD，能有效控制重建误差；25个簇、16秩的JD-Full可匹配1000个LoRA的性能。
- **重建误差与性能非线性关系**：中等重建误差（约60%）不损害甚至提升泛化，聚类场景下更明显。推荐使用重建误差 <0.6 作为选择超参数的准则。
- **隐私初步**：联合压缩不会导致任务间信息泄漏（交叉任务性能无提升）。

## 7. 优点

- **方法创新**：联合压缩 + 聚类框架为多LoRA服务提供了可扩展的解决方案，正交于现有系统优化。
- **理论支撑**：给出了重建误差的上界，揭示聚类的重要性，并指导超参数选择。
- **实用性强**：成功集成到vLLM（结合Punica kernel），实现真实吞吐量提升；代码和1000个LoRA模型将开源。
- **实验严谨**：大规模（1000个LoRA）、多指标、多次重复，并进行了多种消融，结果可信。
- **隐私关注**：对联合压缩可能导致的信息泄漏进行了初步验证，表明无显著风险。

## 8. 不足与局限

- **模型泛化性**：仅实验了Mistral-7B，未在其他大小或架构（如Llama、Falcon）上验证。
- **场景限制**：吞吐量实验仅在40% GPU内存、单次生成10 token条件下进行；实际应用可能有更大上下文或更复杂生成长度。
- **增量更新**：论文未讨论新LoRA加入时如何高效更新压缩基底，需定期重新计算。
- **压缩与量化未结合**：未探索JD压缩与量化（如4-bit）的联合收益，两者理论上独立可组合。
- **隐私分析初步**：仅测试了多任务交叉性能，未系统评估成员推断或数据重构攻击。
- **聚类计算开销**：聚类和JP压缩预处理时间未报告，对于极大量LoRA（如百万）可能成为瓶颈。

（完）
