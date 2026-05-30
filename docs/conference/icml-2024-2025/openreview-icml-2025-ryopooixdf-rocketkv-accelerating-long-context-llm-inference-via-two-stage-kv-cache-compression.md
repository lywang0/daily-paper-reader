---
title: "RocketKV: Accelerating Long-Context LLM Inference via Two-Stage KV Cache Compression"
title_zh: RocketKV：通过两阶段KV缓存压缩加速长上下文LLM推理
authors: "Payman Behnam, Yaosheng Fu, Ritchie Zhao, Po-An Tsai, Zhiding Yu, Alexey Tumanov"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=RyOpooIxDF"
tags: ["query:edge-llm"]
score: 7.0
evidence: KV缓存压缩实现硬件感知加速
tldr: LLM解码阶段KV缓存随输入增长，消耗内存带宽和容量。本文提出RocketKV，两阶段无训练压缩：第一阶段粗粒度永久逐出，第二阶段混合稀疏注意力。实验证明显著降低内存开销，加速推理。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 569, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 702, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1409, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 811, \"height\": 725, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 872, \"height\": 778, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1763, \"height\": 1952, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 846, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1715, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1762, \"height\": 850, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1760, \"height\": 868, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1674, \"height\": 1035, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1670, \"height\": 1044, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ryopooixdf/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1667, \"height\": 1047, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 890, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1365, \"height\": 1417, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1840, \"height\": 1077, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1198, \"height\": 1794, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1695, \"height\": 1417, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1717, \"height\": 1250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1718, \"height\": 1250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1710, \"height\": 1250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1710, \"height\": 1250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1364, \"height\": 1418, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1840, \"height\": 1077, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1717, \"height\": 1249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1718, \"height\": 1250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1718, \"height\": 1250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1718, \"height\": 1250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1364, \"height\": 1418, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1840, \"height\": 1077, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1718, \"height\": 1250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1717, \"height\": 1249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1717, \"height\": 1249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ryopooixdf/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1718, \"height\": 1249, \"label\": \"Table\"}]"
motivation: KV缓存随输入增长，成为内存和带宽瓶颈。
method: 结合粗粒度缓存逐出和细粒度混合稀疏注意力的两阶段压缩。
result: 在保持准确率的同时大幅减少内存使用和推理时间。
conclusion: RocketKV是一种有效的训练无关KV缓存压缩方法。
---

## Abstract
Transformer-based Large Language Models rely critically on the KV cache to efficiently handle extended contexts during the decode phase. Yet, the size of the KV cache grows proportionally with the input length, burdening both memory bandwidth and capacity as decoding progresses. To address this challenge, we present RocketKV, a training-free KV cache compression strategy containing two consecutive stages. In the first stage, it performs coarse-grain permanent KV cache eviction on the input sequence tokens. In the second stage, it adopts a hybrid sparse attention method to conduct fine-grain top-k sparse attention, approximating the attention scores by leveraging both head and sequence dimensionality reductions. We show that RocketKV provides a compression ratio of up to 400×, end-to-end speedup of up to 3.7× as well as peak memory reduction of up to 32.6% in the decode phase on an NVIDIA A100 GPU compared to the full KV cache baseline, while achieving negligible accuracy loss on a variety of long-context tasks. We also propose a variant of RocketKV for multi-turn scenarios, which consistently outperforms other existing methods and achieves accuracy nearly on par with an oracle top-k attention scheme. The source code is available here: https://github.com/NVlabs/RocketKV.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：Transformer-based LLM 在解码阶段依赖 KV 缓存来避免重复计算，但随着序列长度和批处理规模的增加，KV 缓存的大小线性增长，导致内存带宽和容量成为严重瓶颈。例如，Llama3.1-70B-Instruct 模型在 batch size=32、context length=32K 时，KV 缓存需要约 320GB（FP16），即使是高端硬件也难以承受。
- **研究背景**：已有工作表明，解码阶段仅需少量 KV token 即可维持精度。现有方法分为两类：①永久 KV token 驱逐（节省带宽和存储，但可能丢失后续需要的 token）；②动态 KV token 选择（只节省带宽，不节省存储）。但在低 token 预算下，现有方法的精度远低于 oracle top-k 注意力（Exact-TopK）。论文通过分析发现，理想情况下永久驱逐可以在约 1200 token 预算内匹配 oracle，进一步降低预算需要结合动态选择，从而提出两阶段压缩方案。
- **整体含义**：提出一个训练无关的两阶段 KV 缓存压缩框架 RocketKV，结合粗粒度永久驱逐和细粒度动态选择，在保持精度的同时大幅降低内存带宽和容量需求。

## 2. 方法论

### 2.1 核心思想
- RocketKV 包含两个连续阶段：
  - **第一阶段**：粗粒度永久 KV 缓存驱逐（采用 SnapKV），对输入序列中的 token 进行永久移除，保留大部分重要 token。
  - **第二阶段**：细粒度动态 KV token 选择（提出混合稀疏注意力 HSA），对剩余 KV token 进行 top-k 稀疏注意力，通过序列维度和头维度的联合降维来近似注意力分数。
- 引入**自适应压缩分解机制**，根据总压缩比 \(c\) 自动拆分两个阶段的压缩比例：
  \[
  r = \min(0.2 + 0.06 \times \log_2(c), 0.8)
  \]
  其中第一级压缩比为 \(c^r\)，第二级为 \(c^{(1-r)}\)，HSA 再将其均匀分配到序列维度和头维度。

### 2.2 关键技术细节
- **第一阶段（SnapKV）**：
  - 利用输入上下文与末尾观察窗口的聚合注意力分数，选择关键 token 保留。
  - 对 GQA 模型，按每个 attention group 聚合分数进行选择，避免冗余存储。
  - 使用较大的池化核（kernel size=63）以保留信息完整性。
- **第二阶段（HSA）**：
  - **步骤1**：将 key 张量沿序列维度分组为连续 page，存储每个 page 的元素级最大值（\(K_{\text{max}}\)）和最小值（\(K_{\text{min}}\)）作为辅助数据（类似 Quest）。
  - **步骤2**：对每个 query \(q\)，取头维度上绝对值最大的 \(k_1\) 个位置（仅计算这些位置以降低开销），然后根据 \(q\) 的符号选择 \(K_{\text{max}}\) 或 \(K_{\text{min}}\) 进行近似注意力分数计算，再选取序列维度上分数最大的 \(k_2\) 个 page。
  - **步骤3**：根据预测的 \(k_2\) 个索引，获取原始 key/value 进行稀疏注意力。
  - HSA 算法完全兼容 GQA，按 attention group 进行选择。

### 2.3 多轮对话变体 RocketKV-MT
- **问题**：在多轮对话中，永久驱逐可能丢失后续轮次重要的 token。
- **方案**：不在第一阶段永久驱逐，而是保留所有 KV token 但限制解码时仅从第一阶段过滤后的子集中动态选择。这样每轮解码的带宽节省与 RocketKV 相同，但不节省存储。在后续轮次中，重新对全部 KV 缓存进行过滤，保持灵活性。

## 3. 实验设计

### 3.1 数据集与基准
- **LongBench**：长上下文理解任务（Single QA, Multi QA, Summarization, Few-shot, Synthetic, Code 等）。
- **Needle-in-a-Haystack (NIAH)**：检索特定信息能力。
- **RULER**：多任务长上下文基准，覆盖不同序列长度（8K~96K）。
- **SCBench**：多轮对话场景下的 KV 缓存评估。

### 3.2 对比方法
- **Full-KV**：完整 KV 缓存基线。
- **Exact-TopK**：oracle 方法，精确 top-k token 选择。
- **DuoAttention**：流式头与检索头混合。
- **SnapKV**：永久驱逐基线。
- **Quest**：动态选择基线（使用 page 级近似 + 序列维度降维）。
- **SparQ**：动态选择基线（使用头维度降维）。
- **RocketKV** / **RocketKV-MT**：本文方法。

### 3.3 实验配置
- 模型：Llama3.1-8B-Ins、Mistral-7B-Ins-v0.2、LongChat-7B-v1.5（覆盖 GQA 和 MHA）。
- token 预算：从 256 到 4096（单轮），多轮场景下到 16384。
- 每个方法的总 token 预算统一包含近似注意力开销，确保公平比较内存流量。

## 4. 资源与算力
- **文中明确说明**：效率实验在 **NVIDIA H100 和 A100 GPU** 上运行，batch size=1，使用 FP16 精度，基于 gpt-fast 框架。具体 GPU 数量未提及，但推理实验通常在单卡上完成。
- **训练时长**：方法为训练无关，无需训练，因此无训练资源消耗。
- **未明确部分**：完整的推理加速实验中使用的具体 GPU 卡数、总运行时间等未详细报告。

## 5. 实验数量与充分性

### 5.1 实验数量
- **单轮场景**：在 Llama3.1-8B-Ins、Mistral-7B-Ins-v0.2、LongChat-7B-v1.5 三个模型上，针对 LongBench、NIAH、RULER（4~5 种序列长度）进行了大量对比，每个设置下 token 预算从 256 到 4096 共 5 档，共约 3 模型 × 3 基准 × 5 预算 ≈ 45 组主实验结果。
- **多轮场景**：SCBench 基准，token 预算 5 档，对比 6+ 方法，共约 30 组。
- **消融实验**：
  - 比较 HSA 与 Quest、SparQ 的单独效果（验证 HSA 优势）。
  - 比较自适应分解与静态 split factor（展示自适应有效性）。
  - NIAH 可视化热力图（直观展示检索能力）。
- **效率实验**：在 A100 和 H100 上测量端到端加速比和峰值内存节省（不同 token 预算和序列长度）。

### 5.2 充分性与公平性
- **充分性**：覆盖主流长上下文基准、多个模型、多种 token 预算，消融实验完整，NIAH 热力图提供直观验证。实验设计较为全面。
- **客观性**：与多个代表性基线比较，且通过统一 token 预算（包括近似开销）确保公平。代码已开源。
- **潜在偏差**：主要基于 7B/8B 规模模型，未在更大模型（如 70B）上验证；效率实验仅 batch size=1，实际部署中可能涉及更大 batch 和更复杂推理框架。

## 6. 主要结论与发现

- RocketKV 在保持与 Full-KV 几乎相同精度的前提下，可实现 **400× 压缩比**、**3.7× 端到端加速**（A100）、**32.6% 峰值内存减少**。
- 在 LongBench 上，RocketKV 在 token 预算 ≥512 时几乎无精度损失；NIAH 中 token 预算 256 即达到 100% 准确率（Llama3.1-8B-Ins）。
- 与现有方法（SnapKV、Quest、SparQ）相比，RocketKV 在低 token 预算下显著更优，且在高压缩比下差距更大。
- RocketKV-MT 在多轮对话中表现与 oracle top-k 注意力相当，克服了永久驱逐的缺陷。
- HSA 方法通过结合序列和头维度降维，优于单独使用一种维度的方法。

## 7. 优点

- **创新性**：首次系统性地结合永久驱逐和动态选择的两阶段框架，并引入自适应压缩分解，实现灵活且高效的压缩。
- **实用性**：训练无关，直接应用于预训练模型；兼容 GQA、FlashAttention、张量并行等主流技术；无需复杂系统优化（如 CPU Offloading）。
- **全面性**：涵盖多模型、多基准、多 token 预算，消融实验充分，代码开源。
- **有效性**：在极高压缩比（400×）下仍保持极低精度损失，多轮变体解决关键痛点。

## 8. 不足与局限

- **模型规模**：仅在 7B/8B 参数模型上验证，70B 级模型上的效果尚未公开。
- **批量大小**：效率实验仅 batch size=1，实际部署中更大 batch 可能影响加速比。
- **辅助存储开销**：HSA 需要存储 \(K_{\text{max}}\) 和 \(K_{\text{min}}\)，引入额外内存（但总量仍低于 Full-KV）。
- **多轮场景**：RocketKV-MT 不节省存储，仅节省带宽，且需要每次重新过滤全部历史 token，计算开销略增。
- **极端长序列**：在 96K 以上序列时，RocketKV 的精度仍有下降（可能受模型本身能力限制）。
- **公平性说明**：论文统一了 token 预算（包含近似开销），但不同方法的近似计算效率差异（如 HSA 的二维降维可能比 Quest/SparQ 略慢）未在效率实验中详细对比；论文使用 python 实现，声称可进一步优化，但未提供定制 CUDA 内核的具体加速数据。

（完）
