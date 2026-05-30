---
title: "CateKV: On Sequential Consistency for Long-Context LLM Inference Acceleration"
title_zh: CateKV：利用顺序一致性加速长上下文LLM推理
authors: "Haoyun Jiang, Haolin li, jianwei zhang, Fei Huang, Qiang Hu, Minmin Sun, Shuai Xiao, Yong Li, Junyang Lin, Jiangchao Yao"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=u7dlwgKstN"
tags: ["query:edge-llm"]
score: 6.0
evidence: 面向长上下文LLM推理加速的混合KV缓存方法
tldr: 长上下文LLM推理面临内存和延迟挑战。本文发现某些注意力头表现出顺序一致性，据此提出CateKV混合KV缓存方法：对一致头仅保留关键token信息，对自适应头保留大部分KV对，从而减少缓存大小和计算开销，同时保持高精度。该方法为LLM推理加速提供了轻量级缓存策略。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-u7dlwgkstn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 711, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u7dlwgkstn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 868, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u7dlwgkstn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 827, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u7dlwgkstn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 751, \"height\": 597, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u7dlwgkstn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 826, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u7dlwgkstn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1742, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u7dlwgkstn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 853, \"height\": 311, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u7dlwgkstn/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1695, \"height\": 837, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u7dlwgkstn/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1580, \"height\": 2362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u7dlwgkstn/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 749, \"height\": 407, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-u7dlwgkstn/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 750, \"height\": 408, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-u7dlwgkstn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1774, \"height\": 940, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u7dlwgkstn/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 859, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u7dlwgkstn/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u7dlwgkstn/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1695, \"height\": 837, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u7dlwgkstn/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1195, \"height\": 507, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u7dlwgkstn/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1732, \"height\": 1162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u7dlwgkstn/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1606, \"height\": 1078, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-u7dlwgkstn/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1740, \"height\": 566, \"label\": \"Table\"}]"
motivation: 长上下文LLM推理中内存和计算需求巨大。
method: 利用注意力头的顺序一致性，提出混合KV缓存方法CateKV，差异化缓存策略。
result: 降低了KV缓存大小和计算开销，同时保持了推理精度。
conclusion: CateKV通过识别注意力模式有效压缩缓存，适用于长上下文场景。
---

## Abstract
Large language models (LLMs) have demonstrated strong capabilities in handling long-context tasks, but processing such long contexts remains challenging due to the substantial memory requirements and inference latency. In this work, we discover that certain attention heads exhibit sequential consistency in their attention patterns, which can be persistently identified using a coefficient-of-variation-based algorithm. Inspired by this observation, we propose CateKV, a hybrid KV cache method that retains only critical token information for consistent heads, thereby reducing KV cache size and computational overhead, while preserving the majority of KV pairs in adaptive heads to ensure high accuracy. We show the unique characteristics of our algorithm and its extension with existing acceleration methods. Comprehensive evaluations on long-context benchmarks show that, while maintaining accuracy comparable to full attention, CateKV reduces memory usage by up to $2.72\times$ and accelerates decoding by $2.18\times$ in single-sample inputs, and boosts throughput by $3.96\times$ in batch scenarios.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLMs）在处理长上下文任务（如文档问答、信息检索）时表现出色，但随着上下文长度增长，自回归推理需要存储所有键值（KV）缓存，导致巨大的内存消耗和推理延迟。例如，Llama-3-8B模型从1K扩展到1M tokens时，推理延迟增加超过3000倍。因此，加速长上下文LLM推理至关重要。
- **现有方法局限**：现有加速方法分为**KV缓存驱逐策略**（如StreamingLLM、SnapKV）和**KV缓存检索策略**（如Quest、ShadowKV）。驱逐策略会丢弃部分KV对，导致精度损失；检索策略保留全部KV对，但无法缓解内存压力，限制了批处理吞吐量。部分方法（如MInference、DuoAttention）关注不同注意力头的异构稀疏性，但未充分利用预填充阶段与解码阶段之间的关联。
- **本文核心洞察**：作者发现某些注意力头在预填充和解码阶段表现出**顺序一致性**（sequential consistency），即注意力模式高度稳定，只关注少量关键token；而另一些头则动态变化，需要更大的注意力空间。基于此，提出**混合KV缓存方法CateKV**，通过预填充阶段的经验指导解码阶段的缓存策略，在保证精度的同时减少内存和计算开销。

## 2. 论文提出的方法论

### 2.1 核心思想
- **头部分类**：将注意力头分为两类：
  - **一致头（Consistent heads）**：注意力模式稳定，在整个解码过程中始终关注少数关键token。
  - **自适应头（Adaptive heads）**：注意力分布随解码步变化，需要保留大部分KV对以维持精度。
- **混合缓存策略**：
  - 对一致头：仅保留少量关键token的KV对（如1.56%的稀疏预算），显著减少缓存大小。
  - 对自适应头：保留大部分KV对（如通过保留比例η控制），确保精度。
- **参考数据集静态识别**：利用参考数据集（如RULER的Variable Tracking任务）计算每个头被分类为一致头的频率，基于自适应头比例r确定模型的固定头部分类结果，避免在每个样本上动态分类的开销。

### 2.2 关键技术细节
- **观察矩阵与变异系数（CV）分数**：
  - 在预填充阶段，使用**观察窗口**（最后Lobs个query token）计算注意力矩阵A，排除初始和最近的token。
  - 将A二值化（基于分位数阈值和缩放因子），得到频率向量C，表示每个token被识别为关键的次数。
  - 计算**变异系数分数**：$score = \frac{\sqrt{\frac{1}{n'}\sum_i (C_i - \mu(C))^2}}{\mu(C)}$，其中$n'$是非排除的token数。高分数表示注意力高度集中且行间相似，对应一致头。
- **分类规则**：给定自适应头比例r，通过分数阈值$\Gamma(r)$将头分为一致头（分数 > 阈值）和自适应头（分数 ≤ 阈值）。
- **缓存与解码**：
  - 一致头：在预填充阶段直接缓存选出的top-k chunk（按chunk最大值选取），解码时直接使用缓存的KV对。
  - 自适应头：保留大部分KV对（保留比例η），解码时可选择全量或查询感知检索。
- **GQA支持**：对于分组查询注意力（GQA），观察矩阵取组内各头的均值。

### 2.3 理论分析
- 论文给出了Rademacher复杂度界和token保留精度的下界定理，指出三个关键影响因素：**度量有效性**（λ，分数排序能正确表征token相关性）、**预算控制**（适当设置一致头和自适应头的保留预算）、**分类准确性**（P_head）。

## 3. 实验设计

### 3.1 数据集与任务
- **RULER**（12个合成任务，上下文长度8K-256K，重点128K）：包含单/多文档QA、变量追踪等，评估长上下文理解。
- **LongBench**（21个任务，6大类）：包括NarrativeQA、Qasper、MultiFieldQA、HotpotQA等，仅使用长度>4096的样本。
- **Needle in a Haystack (NIAH)**：从20K到1M tokens的“大海捞针”测试，评估检索能力。

### 3.2 模型与基线
- **模型**：LLaMA-3-8B-Instruct-1048K、Phi-3-Mini-128K、Llama-3.1-8B、Yi-9B-200K、Qwen2.5-7B、以及更大规模的Qwen2.5-32B、Yi-34B-200K、Phi-4-14B。
- **基线方法**：
  - 驱逐型：StreamingLLM、SnapKV、PyramidKV。
  - 检索型：Quest、ShadowKV。
  - 头部分类型：DuoAttention。
  - 预填充加速：MInference（仅结合实验）。
- **公平性设置**：与驱逐方法和头部分类方法比较时，保持相同KV缓存大小（如41%）；与检索方法比较时，保持相同计算预算（如1.6%稀疏注意力）。

### 3.3 实验场景
- **单样本推理**：测量内存和延迟，最大输入长度取全注意力能处理的极限。
- **批处理推理**：样本长度40K，最大批量下比较吞吐量。
- **消融实验**：自适应头比例r（0.1-1.0）、自适应头保留比例η（0-1.0）、一致头稀疏预算（512-8192）。
- **与其他方法集成**：CateKV + DuoAttention、CateKV + MInference、CateKV + Quest、CateKV + ShadowKV。

## 4. 资源与算力

- **文中明确**：所有实验在**单张NVIDIA A100-80G GPU**上完成。
- **未说明**：未提及训练或识别阶段的具体耗时、GPU数量、是否多卡并行。参考数据集大小为100个样本（长度128K），训练前离线处理一次即可，成本较低。

## 5. 实验数量与充分性

- **实验数量多**：覆盖4个主要benchmark（RULER、LongBench、NIAH）、5个主流模型（以及3个更大规模模型）、多个上下文长度（8K-1M）、与7种以上基线对比。
- **消融实验全面**：对三个核心超参数（r、η、稀疏预算）进行了详尽的消融，并展示了与各种加速方法的组合效果。
- **公平性考量**：与驱逐型/头部分类型方法保持相同缓存大小；与检索型方法保持相同计算预算；所有基线均使用相同chunk size（8）等设置，较为公平。
- **充分性评估**：实验覆盖了主流评估集和多种模型规模，证明了方法的通用性和鲁棒性。但未在更大模型（如65B以上）或非英语任务上验证，也未讨论训练集分布对头部分类的影响。

## 6. 论文的主要结论与发现

- **顺序一致性现象普遍存在**：在LLaMA-3、Phi-3、Yi等不同模型的不同层中均观察到一致头和自适应头，且头部分类结果跨样本高度稳定（重叠率>80%），可基于参考数据集静态确定。
- **CateKV性能优异**：
  - 在RULER-128K上，仅保留41% KV缓存时，平均精度84.61%，优于所有基线（如DuoAttention 83.76%），与全注意力（84.10%）相当。
  - 在LongBench上，使用42%缓存时，平均精度仅下降不超过0.3%；与检索方法结合后，内存减半且精度损失<0.2%。
  - 在NIAH上，从20K到1M tokens均保持接近全注意力的检索能力。
- **效率大幅提升**：
  - 单样本：Phi-3模型内存节省2.11倍、解码加速1.79倍；Llama-3通过进一步压缩可达2.72倍内存节省和2.18倍解码加速。
  - 批处理：Llama-3吞吐量提升3.96倍（批处理大小从12增至52）。
- **可集成性强**：CateKV可与DuoAttention、MInference、Quest、ShadowKV等结合，实现进一步加速或内存节省。
- **自适应头比例r存在临界点**（约0.2），低于该值时精度显著下降；一致头对稀疏预算不敏感，可用极少数token（如0.78%）保持性能。

## 7. 优点

- **创新性洞察**：首次提出注意力头的“顺序一致性”概念，揭示了预填充与解码阶段之间的相关性，为混合缓存策略提供了理论基础。
- **方法轻量高效**：基于变异系数的分类算法计算简单，仅需一次离线预处理；无需修改模型架构或从头训练，即插即用。
- **理论分析支撑**：给出了Rademacher复杂度界和token保留精度的下界定理，将影响因素归结为度量有效性、预算控制和分类准确性，指导实践。
- **实验设计严谨**：在多个benchmark、多种模型、不同上下文长度上验证，与多种最新方法公平对比，并展示了广泛的组合潜力。
- **实用性强**：实际意义大，能直接降低长上下文LLM推理部署成本，提升吞吐量。

## 8. 不足与局限

- **实验覆盖局限**：
  - 主要验证在8B左右规模的模型，更大模型（如LLaMA-70B、GPT-4级别）未测试，分类模式是否扩展尚不明确。
  - 仅在英文任务（RULER、LongBench、NIAH）上评估，未涉及中文或多语种长上下文任务。
  - 未在训练任务（如预训练、微调）上验证，仅关注推理加速。
- **头部分类的偏差风险**：
  - 头部分类依赖参考数据集（Variable Tracking任务），若下游任务分布与参考集差异较大（如代码生成、数学推理），分类可能不准确，导致精度下降。论文未探讨跨任务泛化。
  - 使用静态固定头类型，忽略样本内动态变化（即使是一致头，极端情况下也可能需要更多token）。
- **超参数敏感性**：自适应头比例r和保留比例η需要手动调整（文中给出了推荐值，但未给出自动调优方法），不同模型或任务可能需要重新调节。
- **对比的完整性**：与DuoAttention对比时，仅比较了LLaMA-3和LLaMA-3.1（因为DuoAttention只提供这两个模型的支持），未与其他头分类方法（如RazorAttention）在更多模型上对比。
- **应用限制**：CateKV仅加速解码阶段，预填充阶段仍使用全注意力。对于极长输入（如>1M），预填充本身也成为瓶颈，需与MInference等预填充加速方法结合，但未系统评估联合优化的总体加速比。

（完）
