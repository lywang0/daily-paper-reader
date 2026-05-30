---
title: Tandem Transformers for Inference Efficient LLMs
title_zh: Tandem Transformers：面向推理高效LLM
authors: "Aishwarya P S, Pranav Ajit Nair, Yashas Samaga B L, Toby James Boyd, Sanjiv Kumar, Prateek Jain, Praneeth Netrapalli"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=TN3fi7dwPo"
tags: ["query:edge-llm"]
score: 7.0
evidence: 结合小模型和大模型块模式的新型架构提升推理效率
tldr: 传统自回归LLM推理速度受限于顺序生成。Tandem transformers创新地结合一个小自回归模型和一个并行处理多个token的大模型，小模型通过注意力机制利用大模型的丰富表示。实验表明在保持生成质量的同时，显著加速推理。该架构为高效LLM推理提供了新的设计思路。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-tn3fi7dwpo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1330, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tn3fi7dwpo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1685, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-tn3fi7dwpo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1640, \"height\": 436, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 447, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1704, \"height\": 410, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1300, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 854, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 854, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1422, \"height\": 447, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1040, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1777, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-tn3fi7dwpo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1430, \"height\": 475, \"label\": \"Table\"}]"
motivation: 自回归LLM推理速度慢，现有投机解码等方法存在局限性。
method: 构建双模型架构：小模型自回归生成，大模型块模式验证，并通过注意力交互增强小模型。
result: 在多种基准上推理速度提升显著，且质量不下降。
conclusion: Tandem transformers通过模型协作实现了高效且准确的LLM推理。
---

## Abstract
The autoregressive nature of conventional large language models (LLMs) inherently limits inference speed, as tokens are generated sequentially. While speculative (Leviathan et al., 2023) and parallel (Stern et al., 2018) decoding techniques attempt to mitigate this, they face limitations: either relying on less accurate smaller models for generation or failing to fully leverage the base LLM's representations. We introduce a novel architecture, Tandem transformers, to address these issues. This architecture uniquely combines (1) a small autoregressive model and (2) a large model operating in block mode (processing multiple tokens simultaneously). The small model's predictive accuracy is substantially enhanced by granting it attention to the large model's richer representations. On the PaLM2 pretraining dataset, a tandem of PaLM2-Bison and PaLM2-Gecko demonstrates a 3.3% improvement in next-token prediction accuracy over a standalone PaLM2-Gecko, offering a 1.16x speedup compared to a PaLM2-Otter model with comparable downstream performance. We further incorporate the Tandem model within the speculative decoding (SPEED) framework where the large model validates tokens from the small model. This ensures that the tandem of PaLM2-Bison and PaLM2-Gecko achieves substantial speedup (around 1.14x faster than using vanilla PaLM2-Gecko in SPEED) while maintaining identical downstream task accuracy.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）的自回归生成方式导致推理速度慢，无法充分利用 GPU/TPU 的矩阵-矩阵乘法能力。
- **现有方法的局限**：
  - 投机解码（Speculative Decoding, SPEED）依赖较小的草案模型，但草案模型精度有限，影响加速效果。
  - 并行解码（Parallel Decoding）无法充分借助大模型的表示能力。
- **研究目标**：探究模型容量是否可以分解为“自然语言理解（NLU）”和“自然语言生成（NLG）”两部分，并设计更高效的架构。

## 2. 方法论：核心思想、关键技术细节

### 2.1 Tandem Transformers 架构

- **组成**：一个大的主模型（ML）和一个小的辅助模型（MS）。
- **工作流程**：
  1. ML 处理整个 prompt 并生成表示。
  2. MS 以自回归方式生成一批（block）γ 个 token，同时通过注意力机制访问 ML 对之前所有 token 的表示（经投影层对齐维度）。
  3. ML 块模式（非自回归）处理刚生成的 γ 个 token，并更新表示。
  4. 重复步骤 2-3 直到完整响应生成。
- **块长度 γ**：训练时固定，推理时可灵活调整；γ=0 退化为纯 ML，γ→∞ 退化为纯 MS。

### 2.2 训练方法

- **初始化**：使用预训练的 PaLM2-Bison（ML）和 PaLM2-Gecko（MS）。
- **训练策略**：
  - **冻结主模型**：仅更新 MS 和投影层，损失仅加在 MS 输出上（最佳配置）。
  - **两种蒸馏变体**：
    - **Tandem-CE**：仅用交叉熵损失训练。
    - **Tandem-Distil**：加入 logit 蒸馏损失（以 ML 的输出为目标），两个阶段训练（先 CE，后 CE+蒸馏，λ=0.5）。
- **投影层**：采用线性层对齐 ML 和 MS 的表示维度。

### 2.3 Tandem + SPEED（投机解码）

- **角色**：MS 作为草案生成器，ML 作为验证器。
- **优势**：MS 可访问 ML 表示，生成更准确的草案，每个块接受率提升约 11.24%。
- **自适应块长度（Adaptive Block Length）**：训练一个 2 层 MLP 路由器，根据 MS 的熵、top-k 概率等特征预测 token 被接受概率，动态决定是否继续生成或验证。

## 3. 实验设计

### 3.1 数据集和基准

- **训练数据**：PaLM2 预训练数据集。
- **评估任务**：
  - 生成任务：SQuAD v2、Natural Questions、TriviaQA、WebQuestions、LAMBADA（合称 Gen-tasks）。
  - 排名/理解任务：SuperGLUE、TyDiQA-GoldP。
  - 代码：MBPP。
  - 翻译：WMT22（x→en 平均）。
  - 摘要/语言建模：CNN/DailyMail、Reddit Posts、LM1B（用于延迟测试）。

### 3.2 对比方法

- **主模型（ML）**：PaLM2-Bison（最大）。
- **次级模型（MS）**：PaLM2-Gecko（小）、PaLM2-XXXS（更小）。
- **对照**：
  - 纯 PaLM2-Gecko
  - PaLM2-Gecko-Distil（仅 logit 蒸馏，无 Tandem）
  - PaLM2-Otter（中等大小）
  - PaLM2-Bison（基线大模型）
  - 标准 SPEED（PaLM2-Gecko-Distil 作为草案）

## 4. 资源与算力

- **硬件**：所有延迟评估在 TPUv5e 上完成。
- **训练细节**：文中未明确说明训练使用的 GPU/TPU 数量、训练时长、总计算量（FLOPS）等具体信息。
- **备注**：论文仅提到“总体上遵循 PaLM2 训练协议”，但未给出资源开销的量化数据。

## 5. 实验数量与充分性

- **实验组数**：
  - 预训练指标对比（表1）：准确率、CE 损失、相对准确率、TV 距离。
  - 下游任务评估（表3 及附录表9、10）：覆盖 5 个任务族，每个任务下有多个子任务。
  - SPEED 延迟实验（表2、4、5、7、8）：3 个数据集、2 种 batch（num-samples=1 和 4）、多种块长度 γ。
  - 自适应块长度实验（表5、6）。
  - 小次级模型实验（表4）。
  - 消融实验：冻结 vs 微调主模型、蒸馏 vs 非蒸馏。
- **充分性评价**：
  - **优点**：覆盖多任务、多数据集，对比了多种基线，统计了延迟和性能两个维度。
  - **不足**：仅在 PaLM2 系列模型上验证，缺少与其他架构（如 MoE、稀疏模型）的直接比较；未在开源模型（如 LLaMA）上复现；自适应块长度的训练细节不够深入。

## 6. 主要结论与发现

1. **Tandem 作为独立模型**：Tandem-CE 和 Tandem-Distil 在生成/理解任务上大幅优于 PaLM2-Gecko，与 PaLM2-Otter 性能相当，但推理速度快约 1.16×。
2. **Tandem + SPEED**：在保证输出与 PaLM2-Bison 完全相同的前提下，比标准 SPEED（使用 PaLM2-Gecko-Distil）快约 1.11–1.17×，相对于纯 PaLM2-Bison 加速约 2.19–2.61×。
3. **蒸馏增益**：logit 蒸馏可与 Tandem 互补，Tandem-Distil 优于 Tandem-CE。
4. **自适应块长度**：进一步减少次级模型运行次数，在三种数据集上再加速 1.04–1.09×。
5. **更小次级模型**：使用 PaLM2-XXXS 可进一步提升加速比（如 LM1B 上达 3.04× vs Bison）。

## 7. 优点

- **架构创新**：首次明确分离 NLU 和 NLG 的模型容量，并设计出可训练的“小模型依赖大模型表示”的耦合机制。
- **兼容性强**：可作为独立模型使用，也可无缝嵌入 SPEED 框架；支持不同大小次级模型。
- **高效且高质量**：在显著加速的同时，独立模型性能几乎不损失（与中等模型 Otter 相当），SPEED 版本输出无偏差。
- **实用设计**：推理时可灵活调整块长度、支持自适应策略，契合实际部署需求。

## 8. 不足与局限

- **实验覆盖有限**：仅在 PaLM2 系列上验证，无法确定对 GPT、LLaMA 等架构的通用性；代码和数据集未公开，复现困难。
- **算力信息缺失**：未报告完整训练/微调所需的计算资源、耗时、能耗，不利于公平比较。
- **消融实验不够全面**：
  - 未探讨 γ 从 0 到大的连续变化对性能的影响。
  - 未比较不同投影层设计（如 MLP vs 线性）的效果。
  - 自适应 γ 的路由器训练细节（如数据规模、训练轮数）未给出。
- **潜在偏差风险**：Tandem + SPEED 依赖 MS 的草案质量，虽然实验显示接受率高，但未分析在长尾、低资源任务上的鲁棒性。
- **未来方向未验证**：文中提到可用于 LoRA 替代等，但未提供实验证据。
- **其他**：未与 MoE、稀疏激活等专门优化推理的方法对比；未测评多轮对话场景；未讨论内存和带宽开销。

（完）
