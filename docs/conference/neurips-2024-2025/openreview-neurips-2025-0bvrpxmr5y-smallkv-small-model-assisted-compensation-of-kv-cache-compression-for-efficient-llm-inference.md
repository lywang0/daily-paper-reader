---
title: "SmallKV: Small Model Assisted Compensation of KV Cache Compression for Efficient LLM Inference"
title_zh: SmallKV：小模型辅助KV缓存压缩补偿以实现高效LLM推理
authors: "Yi Zhao, Yajuan Peng, Nguyen Cam-Tu, Zuchao Li, Wang Xiaoliang, hai zhao, Xiaoming Fu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=0BVrpXMr5Y"
tags: ["query:edge-llm"]
score: 6.0
evidence: 小模型辅助KV缓存补偿实现高效推理
tldr: SmallKV利用小模型与目标模型注意力矩阵的相似性，设计补偿机制缓解KV缓存驱逐导致的性能损失，在保持推理质量的同时降低内存占用，为资源受限场景下的高效推理提供新方法。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-0bvrpxmr5y/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1427, \"height\": 316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0bvrpxmr5y/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 825, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0bvrpxmr5y/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 627, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0bvrpxmr5y/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 800, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0bvrpxmr5y/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1436, \"height\": 951, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0bvrpxmr5y/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 496, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0bvrpxmr5y/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 491, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0bvrpxmr5y/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1038, \"height\": 882, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-0bvrpxmr5y/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1196, \"height\": 519, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-0bvrpxmr5y/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 578, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0bvrpxmr5y/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1014, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0bvrpxmr5y/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 555, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0bvrpxmr5y/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0bvrpxmr5y/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1163, \"height\": 139, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0bvrpxmr5y/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1160, \"height\": 140, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0bvrpxmr5y/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1175, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0bvrpxmr5y/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1322, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-0bvrpxmr5y/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 842, \"height\": 137, \"label\": \"Table\"}]"
motivation: 现有KV缓存驱逐策略不可逆且忽略边际信息重要性，影响性能。
method: 使用小模型辅助生成补偿token，恢复被驱逐缓存的关键信息。
result: 在压缩缓存的同时保持了模型性能。
conclusion: 小模型辅助补偿能有效权衡内存与质量。
---

## Abstract
KV cache eviction has emerged as an effective solution to alleviate resource constraints faced by LLMs in long-context scenarios. However, existing token-level eviction methods often overlook two critical aspects: (1) their irreversible eviction strategy fails to adapt to dynamic attention patterns during decoding (the saliency shift problem), and (2) they treat both marginally important tokens and truly unimportant tokens uniformly, despite the collective significance of marginal tokens to model performance (the marginal information over-compression problem). To address these issues, we design two compensation mechanisms based on the high similarity of attention matrices between LLMs with different scales. We propose SmallKV, a small model assisted compensation method for KV cache compression. SmallKV can maintain attention matching between different-scale LLMs to: 1) assist the larger model in perceiving globally important information of attention; and 2) use the smaller model’s attention scores to approximate those of marginal tokens in the larger model. Extensive experiments on benchmarks including GSM8K, BBH, MT-Bench, and LongBench demonstrate the effectiveness of SmallKV. Moreover, efficiency evaluations show that SmallKV achieves 1.75 - 2.56 times higher throughput than baseline methods, highlighting its potential for efficient and performant LLM inference in resource constrained environments.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义
- **研究动机**：大语言模型（LLM）在长上下文推理中面临 GPU 内存瓶颈，KV 缓存驱逐（eviction）是缓解资源压力的有效手段，但现有 token 级驱逐方法存在两个关键缺陷：
  1. **Saliency Shift 问题**：解码过程中 token 重要性动态变化，但不可逆的驱逐策略无法自适应，导致全局重要的 token 被错误驱逐。
  2. **Marginal Information Over-Compression 问题**：将边际重要（marginally important）的 token 与真正不重要的 token 同等对待，而边际 token 的集体贡献对模型性能至关重要，过度压缩导致性能下降。
- **整体含义**：本文提出 SmallKV，通过引入一个小模型（SLM）辅助大模型（LLM）进行 KV 缓存压缩补偿，在不显著增加计算开销的前提下保持模型性能，适用于资源受限的推理环境。

## 2. 方法论
- **核心思想**：利用同一模型系列中不同规模 LLM 的注意力矩阵具有高度相似性，借助 SLM 的完整注意力信息来指导 LLM 的 KV 缓存驱逐和注意力近似。
- **关键技术细节**：
  - **相似性匹配（Similarity Matching）**：在预填充阶段，对 LLM 和 SLM 的每层注意力头计算 Jaccard 相似度（基于 TopK 索引），建立映射关系 \( f(i) = \arg\max_j S(A_i, A'_j) \)。
  - **Saliency Shift 补偿**：解码时，SLM 维护完整 KV 缓存（\( C_s^{\text{all}} \)），LLM 基于 SLM 的注意力分数执行驱逐（而非自身压缩后的缓存），从而保留全局重要信息，避免错误驱逐。
  - **Marginal Information 补偿**：将 token 分为关键（critical）、边际（marginal）、不重要（unimportant）三级。关键 token 保留完整 KV；边际 token 仅保留 V 缓存，利用 SLM 的注意力分数近似其注意力输出（公式 (6)）；不重要 token 完全驱逐。计算时，关键 token 用 Flash Attention 加速，边际 token 用矩阵乘法并行执行。
- **算法流程**：
  1. Prefill：并行前向 LLM 和 SLM，计算注意力矩阵，建立映射关系。
  2. Decode：SLM 前向更新注意力；LLM 并行更新 KV 缓存（保留关键 token 的 KV 和边际 token 的 V）；LLM 各注意力层并行计算两类 token 的注意力输出并求和，输出新 token。

## 3. 实验设计
- **数据集与场景**：
  - GSM8K（数学推理）
  - BBH（语言理解）
  - MT-Bench（多轮对话）
  - LongBench（长上下文，含 5 个子任务：单/多文档 QA、摘要、少样本学习、代码补全）
- **基准方法**：H2O（基于累积注意力分数驱逐）、PyramidInfer（金字塔式分层处理）。
- **模型组合**：Qwen2-0.5B+Qwen2-7B、Qwen2.5-0.5B+Qwen2.5-14B、Qwen2-7B+Qwen2-72B（INT4）、LLaMA 3.2-1B+LLaMA 3.1-8B。
- **评价指标**：accuracy（GSM8K、BBH）、score（MT-Bench）、子任务精确指标（LongBench）、效率指标（TPOT、TTFT、吞吐量）。

## 4. 资源与算力
- 所有实验在 **8 张 NVIDIA A100 (80GB) GPU** 上完成，环境为 CUDA 12.0、PyTorch 2.4.0、Transformers 4.45.1。
- 效率分析在单张 A100 上进行。
- 该方法为推理阶段方法，不涉及训练，因此未提及训练时长；但 SLM 的额外前向和相似性匹配会引入一定开销（文中通过实验量化）。

## 5. 实验数量与充分性
- **实验组数**：包含 4 种模型组合 × 5 个 KV 预算（100%、80%、60%、40%、20%、10%、5%）的三大基准测试（图 5）；LongBench 上 3 个预算的详细结果（表 1）；效率测试（表 2，2 种场景）；消融实验（图 6，去除边际补偿、去除两种补偿）；SLM 规模影响实验（图 7，4 种 SLM）；附加分析（相似性量化、SLM 压缩、层跳过等）。
- **充分性**：覆盖多种模型规模、任务类型、压缩比率，对比方法为当前主流，结果客观公正。消融和规模实验验证了各组件的有效性及性能权衡。实验设计较为全面。
- **公平性**：所有方法使用相同数据集和 greedy 解码，基线采用公开实现；SmallKV 的 SLM 开销已计入效率对比。

## 6. 主要结论与发现
- SmallKV 在所有模型组合和 KV 预算下显著优于 H2O 和 PyramidInfer，尤其在 **低预算（如 5%～10%）** 下性能保持稳定（如 GSM8K 5% 预算约 73% vs H2O 36.7%）。
- 效率上，SmallKV 相比基线方法实现了 **1.75×～2.56× 吞吐量提升**，且兼容 Flash Attention。
- 消融实验证实：saliency shift 补偿和 marginal information 补偿均对性能有贡献，且后者在预算充足时效果更明显。
- SLM 规模越大性能越好，但在资源有限时需权衡开销（如 5% 预算下增大 SLM 可带来 30%-84% 性能提升）。

## 7. 优点
- **创新性**：首次利用不同规模模型间注意力相似性来设计补偿机制，而非简单驱逐或量化。
- **双重补偿**：同时解决 saliency shift 和 marginal over-compression 两个实际问题，方案设计合理。
- **兼容性**：可与 Flash Attention、推测解码（speculative decoding）等高效技术结合，实际开销可控。
- **实验全面**：覆盖多种模型系列、大小、任务类型和压缩率，消融与规模实验充分。
- **效率显著**：在低预算下性能几乎无损，且吞吐量大幅提升。

## 8. 不足与局限
- **理论证明缺失**：注意力相似性的原因尚缺乏严格理论证明，仅凭经验观察。
- **不是无损压缩**：注意力近似引入误差，极端预算下仍有性能损失。
- **额外开销**：单独部署时 SLM 的前向和内存占用不可忽略，虽可与推测解码共享，但文中未完全消除。
- **跨系列泛化性不确定**：实验仅针对同一系列（Qwen、LLaMA），跨系列模型的相似性可能较低（如文中 Qwen2-7B vs Llama3-1B 相似度仅 0.56），方法泛化性需进一步验证。
- **未大规模验证**：最大模型为 72B（INT4），未测试更大规模（如 100B+）或 MoE 架构。
- **社会影响未讨论**：未涉及公平性、安全性、伦理等方面的潜在风险。

（完）
