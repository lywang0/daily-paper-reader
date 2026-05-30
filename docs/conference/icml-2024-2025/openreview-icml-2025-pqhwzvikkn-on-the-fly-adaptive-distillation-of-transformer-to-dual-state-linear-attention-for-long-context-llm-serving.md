---
title: On-the-Fly Adaptive Distillation of Transformer to Dual-State  Linear Attention for Long-Context LLM Serving
title_zh: 面向长上下文LLM服务的在线自适应Transformer到双状态线性注意力蒸馏
authors: "Yeonju Ro, Zhenyu Zhang, Souvik Kundu, Zhangyang Wang, Aditya Akella"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=pqHWzviKKN"
tags: ["query:edge-llm"]
score: 8.0
evidence: 面向高效LLM服务的新型线性注意力机制
tldr: 自注意力机制在处理长文本时计算和内存成本高昂，线性注意力虽降低复杂度但存在短距偏差。本文提出双状态线性注意力（DSLA），通过两个隐藏状态分别保存历史语境和跟踪近期信息，缓解短距偏差。进一步引入在线自适应蒸馏框架DSLA-Serve，在动态负载下平衡效率与精度，适用于长上下文LLM服务。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 851, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 780, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 226, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 855, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 813, \"height\": 267, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 821, \"height\": 314, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 855, \"height\": 283, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1587, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1557, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1239, \"height\": 521, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 830, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1460, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqhwzvikkn/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1766, \"height\": 322, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-pqhwzvikkn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1740, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqhwzvikkn/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 852, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqhwzvikkn/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 862, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqhwzvikkn/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 742, \"height\": 332, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqhwzvikkn/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 812, \"height\": 118, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqhwzvikkn/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1745, \"height\": 408, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqhwzvikkn/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 864, \"height\": 141, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqhwzvikkn/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 863, \"height\": 157, \"label\": \"Table\"}]"
motivation: 长上下文LLM推理中自注意力计算成本高，线性注意力存在短距偏差。
method: 提出双状态线性注意力DSLA和在线自适应蒸馏框架DSLA-Serve。
result: 在长文本任务中保持精度的同时显著降低计算和内存开销。
conclusion: DSLA及其服务框架有效提升了长上下文LLM服务的效率与精度的平衡。
---

## Abstract
Large language models (LLMs) excel at capturing global token dependencies via self-attention but face prohibitive compute and memory costs on lengthy inputs. While sub-quadratic methods (e.g., linear attention) can reduce these costs, they often degrade accuracy due to overemphasizing recent tokens. In this work, we first propose *dual-state linear attention* (**DSLA**), a novel design that maintains two specialized hidden states—one for preserving historical context and one for tracking recency—thereby mitigating the short-range bias typical of linear-attention architectures. To further balance efficiency and accuracy under dynamic workload conditions, we introduce 
DSLA-*Serve*, an online *adaptive distillation* framework that progressively replaces Transformer layers with DSLA layers at inference time, guided by a sensitivity-based layer ordering. 
DSLA-*Serve* uses a chained fine-tuning strategy to ensure that each newly converted DSLA layer remains consistent with previously replaced layers, preserving the overall quality. Extensive evaluations on commonsense reasoning, long-context QA, and text summarization demonstrate that 
DSLA-*Serve* yields **2.3×** faster inference than Llama2-7B and **3.0×** faster than the hybrid Zamba-7B, while retaining comparable performance across downstream tasks. Our ablation studies show that DSLA’s dual states capture both global and local dependencies, addressing the historical-token underrepresentation seen in prior linear attentions.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究动机**：大规模语言模型（LLM）依靠自注意力机制捕获全局依赖，但面对长序列输入时面临 O(T²) 的计算复杂度和线性增长的 KV 缓存内存消耗，成为推理瓶颈。  
- **现有局限**：线性注意力（如 GLA、Mamba）虽将复杂度降为 O(T)，却因单隐藏状态的设计导致**短距偏差**——过分关注近处 token 而忽略历史语境。混合架构（如 Zamba）虽部分缓解，但静态设计无法在推理时灵活权衡效率与精度。  
- **整体目标**：在保证长上下文任务精度的前提下，实现**按需动态**的推理加速和内存压缩，以适应真实服务器负载波动（时间/空间不均衡）。

## 2. 方法论

### 核心思想
- 提出**双状态线性注意力（DSLA）**：维护两个独立的隐藏状态：一个用于**保留历史语境**，一个用于**追踪近期信息**，并通过对比正则化强迫两者专门化，从而模拟全自注意力的注意分布。
- 提出**DSLA-Serve 在线自适应蒸馏框架**：基于敏感性排序，在推理时**逐步将 Transformer 层替换为 DSLA 层**，动态平衡精度与效率。

### 关键技术细节
1. **DSLA 模块**（公式用文字描述）
   - 两个隐藏状态更新：  
     S₁ᵗ = G₁ᵗ ⊙ S₁ᵗ⁻¹ + kᵗᵀ vᵗ  
     S₂ᵗ = G₂ᵗ ⊙ S₂ᵗ⁻¹ + kᵗᵀ vᵗ  
     其中 G₁、G₂ 为数据驱动的遗忘门；G₁ 初始化为接近单位矩阵（保持历史），G₂ 随机初始化（侧重近期）。
   - 输出：oᵗ = qᵗ [γ·S₁ᵗ + (1‑γ)·S₂ᵗ]  
     其中 γ 为每层可学习的权重系数。
   - 对比正则化：损失函数 L = L_dist + λ·L_cont  
     L_dist 为 DSLA 输出与教师 Transformer 输出的 KL 散度，L_cont 为 G₁ 与 G₂ 的余弦相似度，驱动两状态专门化。

2. **层敏感性排序**
   - 使用**注意力熵**衡量各层对线性化替代的敏感度：Entropy(A) = Σ Aₜᵢ log Aₜᵢ（对最终 query 的注意分布）。  
   - 熵越低→关注 token 越集中→对线性化越不敏感→优先转换。从低敏感性层开始逐步替换。

3. **链式微调（Chained Fine‑Tuning）**
   - 按敏感性升序依次将 Transformer 层蒸馏为 DSLA 层，每完成一层即**永久固化**，后续层训练时看到的是已经含有前序 DSLA 层的混合架构，避免训练/部署结构不一致。

4. **自适应转换逻辑**
   - 运行时监控 GPU 内存/请求长度，当压力超过阈值时，从最小敏感性层开始逐层转换，直到内存缓解或精度接近服务级目标（SLO）为止。对长上下文请求优先转换。

5. **批处理考虑**
   - 批内请求若路径分歧（部分需要 DSLA，部分仍需自注意力），则拆分为子批处理，转换层后合并。论文指出 KV 缓存节省远大于拆分开销。

## 3. 实验设计

### 数据集与场景
- **长上下文理解**：Multi‑Document QA（HotpotQA、2WikiMQA）、Code Understanding（LCC、Repobench）、Few‑shot Learning（TREC、Samsum、TriviaQA）、Perplexity（WikiText‑2、Lambada）、文本摘要（CNN/DailyMail、XSum）。
- **短上下文基准**：7 个常识推理任务（Winogrande、HellaSwag、PIQA、ARC‑E、ARC‑C、MMLU、LogiQA）。
- **端到端系统**：基于 Azure LLM 推理迹增强的多轮会话回放，包含不同 prompt 长度分布。

### 基准方法
- 全注意力：Llama2‑7B（教师模型）
- 线性复杂度：RetNet‑6.7B、GLA‑7B、Mamba‑7B
- 混合架构：Zamba‑7B
- 另比较了 LoLCATs（不同线性化方法）和 Phi‑Mamba（1.5B 尺度）

### 评估指标
- 长上下文：准确率 / F1 / ROUGE / 困惑度
- 短上下文：各任务准确率及平均
- 效率：Prefill 延迟、解码每 token 延迟、端到端归一化延迟、KV 缓存节省

## 4. 资源与算力

- **微调硬件**：4× A100 80GB GPU，使用 AdamW 优化器（学习率 1e‑4→5e‑5，cosine 衰减）。
- **微调数据**：1.6B tokens 采样自 SlimPajama。
- **微调时长**：每层（7B 模型）约 5 小时（1B tokens），总培训成本约为全预训练（858 GPU‑天）的 **0.07%**。
- **推理测试**：A6000 49GB GPU 用于下游任务评估，A100 80GB 用于延迟测量。

## 5. 实验数量与充分性

- **覆盖维度广泛**：包括 7 个长文本任务、7 个短文本任务、2 个摘要数据集、端到端系统仿真、注意力模式可视化、敏感性指标对比。
- **消融实验充分**：
  - 隐藏状态数量（1→2→4→8 状态）：证明 2 状态足够且最优。
  - 不同敏感性指标（熵、异常值比例、下游准确率）对比，验证熵的普适性。
  - 与不同线性化方法（LoLCATs）在同等教师模型下对比。
  - 不同模型尺度（1.5B 的 Phi‑1.5）和不同骨干（Llama2‑7B‑chat）验证泛化性。
- **公平性**：所有基线均使用公开预训练权重或作者提供的配置，实验设置保持一致（如 GLA、Mamba 使用同规模 7B 模型，Zamba 使用原版代码但指出硬件差异导致性能差距）。DSLA 的训练数据量（1.6B tokens）远小于基线模型，但性能仍具竞争力。
- **结论**：实验组数量合理，覆盖了主要场景和消融需求，结果客观可信。

## 6. 主要结论与发现

1. **DSLA 缓解短距偏差**：双状态分别捕获历史和近期分布，注意力图更接近 Transformer，而单状态 GLA 严重偏向最后若干 token。
2. **DSLA‑Serve 实现动态加速**：在模拟真实负载下，端到端每 token 延迟降低 2.29×；相比纯 Transformer 加速 2.3×，相比 Zamba 加速 3.0×。
3. **长文本性能保持或超越**：25% 转换率下在多文档 QA 上甚至优于原始 Llama2‑7B（如 HotpotQA +5.44），50% 转换时仍差距微小。
4. **短文本任务无显著退化**：50% 转换时平均准确率仅下降 3%，优于纯线性模型 GLA/Mamba。
5. **两状态优于更多状态**：2 状态即达到最佳精度—效率平衡，更多状态收益递减。

## 7. 优点

- **方法创新性**：首次提出双状态线性注意力，并通过对比正则化驱动两状态专门化，理论清晰且实现简便。
- **自适应服务框架**：DSLA‑Serve 将离线蒸馏与在线动态转换结合，支持按需权衡，直接面向实际服务负载波动问题。
- **链式微调保证一致性**：解决混合架构训练‑部署不一致关键问题，可扩展至任意比例转换。
- **实验全面且高效**：训练成本仅占全预训 0.07%，却在大范围任务上取得竞争性能，证明方法的实用价值。
- **解释性强**：通过 γ 可视化展示不同层对历史/近期需求差异（早层/晚层偏近期，中层偏历史），符合认知。

## 8. 不足与局限

1. **双架构内存开销**：为支持快速切换，需同时加载 Transformer 和 DSLA 参数，增加模型权重内存占用。作者建议使用 offloading 缓解，但未在实验中实现。
2. **转换率上限**：超过 75% 层转换时性能下降明显，高压力场景下的最大转换率受限（论文中设置最大 50% 用于高负载）。
3. **批处理分裂开销**：路径分歧导致子批拆分，虽声称影响小但未提供量化测量数据。
4. **对比基线硬件差异**：Zamba-7B 在 A100 上显著慢于论文中的 H100 报告值，作者归因于内存带宽限制，但未在同硬件上使用优化实现（如 FlashAttention）重新评估。
5. **敏感性指标泛化性**：注意力熵在单任务时可能不如下游准确率直观，且部分任务（如图 13c）显示熵与准确率不完全一致。
6. **长期稳定性未验证**：端到端实验仅基于单次模拟轨迹，未在长时间多轮对话下测试离线模型漂移或累积误差。

---

（完）
