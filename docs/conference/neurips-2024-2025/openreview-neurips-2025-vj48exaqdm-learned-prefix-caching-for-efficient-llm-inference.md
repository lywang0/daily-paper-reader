---
title: Learned Prefix Caching for Efficient LLM Inference
title_zh: 学习型前缀缓存用于高效LLM推理
authors: "Dongsheng Yang, Austin Li, Kai Li, Wyatt Lloyd"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Vj48eXaQDM"
tags: ["query:edge-llm"]
score: 6.0
evidence: 学习型前缀缓存提升LLM服务效率
tldr: "前缀缓存是降低LLM推理开销的关键技术，但传统LRU策略远非最优。本文首次提出学习型前缀缓存方法LPC，基于对话内容分析预测哪些对话可能继续，结合最后访问时间指导缓存淘汰。在三个真实数据集上，LPC在维持同等命中率下减少18-47%的缓存需求，并在仿真环境中提升11%的预填充吞吐量。该方法可直接用于LLM服务系统的缓存管理优化。"
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-vj48exaqdm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 535, \"height\": 409, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vj48exaqdm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1446, \"height\": 257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vj48exaqdm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1027, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vj48exaqdm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1458, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vj48exaqdm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1457, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vj48exaqdm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 501, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vj48exaqdm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 893, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vj48exaqdm/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1457, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vj48exaqdm/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1458, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-vj48exaqdm/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1460, \"height\": 435, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-vj48exaqdm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vj48exaqdm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1132, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vj48exaqdm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 737, \"height\": 381, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vj48exaqdm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 941, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vj48exaqdm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 780, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-vj48exaqdm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1009, \"height\": 378, \"label\": \"Table\"}]"
motivation: LLM推理中前缀缓存策略（如LRU）与最优方案差距大，需要更智能的淘汰机制。
method: 提出LPC，利用对话内容分析学习缓存淘汰策略。
result: "在真实数据集上缓存需求降低18-47%，预填充吞吐量提升11%。"
conclusion: 学习型缓存管理能显著提升LLM服务效率，适用于边缘端推理系统。
---

## Abstract
Prefix caching is a key technique for reducing Large Language Model (LLM) inference costs. However, the prevalent least-recently-used (LRU) eviction algorithm has a large gap to the optimal algorithm. This paper introduces LPC, the first learned method to perform LLM prefix cache eviction. LPC leverages conversational content analysis to provide predictive guidance for eviction, determining which conversations are likely to continue. These insights, combined with last access timestamps, inform more effective cache management. Extensive evaluations across three real-world datasets demonstrate that LPC achieves 18-47% reductions in required cache sizes for equivalent hit ratios and has an 11% improvement in LLM prefilling throughput in an emulated environment.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义

- **研究背景**：前缀缓存（Prefix Caching）是降低大语言模型（LLM）推理延迟与计算成本的关键技术，通过复用已处理的输入前缀的Key-Value状态，避免冗余预填充计算。但在多轮对话场景中，传统缓存淘汰策略（如LRU）基于最近访问时间做决策，远未达到最优表现。论文指出LRU与理想Oracle策略之间存在巨大命中率差距（图1）。
- **核心问题**：如何设计一种智能的缓存淘汰策略，利用对话内容特征预测哪些对话更可能继续，从而显著提升前缀缓存命中率，同时保持极小的内存和计算开销。
- **整体意义**：本文提出LPC，是首个专门为LLM对话系统设计的学习型前缀缓存淘汰方法，有望大幅提升LLM服务系统的吞吐量和响应速度，降低硬件成本。

## 2. 论文提出的方法论

### 核心思想
LPC通过一个轻量级预测器，基于对话历史预测当前对话的“延续概率”，并结合最后访问时间动态调整得分，指导缓存淘汰决策。

### 关键技术细节

- **LPC框架**（图3）：包括预测器和淘汰算法两部分，替代LRU的纯时间戳策略。
- **预测器组成**：
  - **数据解析**：提取最近N轮（默认N=4）的用户提示词，以及对话轮次数作为特征。
  - **文本嵌入**：使用 `multilingual-e5-small` 模型（118M参数）将用户提示词编码为384维向量。输入长度限制512 token，通过平均分配并截取首尾各半的策略压缩长输入。
  - **MLP分类器**：3层MLP（每层128神经元），输入为文本嵌入与对话轮数的拼接，输出0~1的延续概率p。
- **训练**：仅训练MLP，文本嵌入模型冻结。使用加权二分类交叉熵损失，Adam优化器，学习率5e-4，20 epoch内收敛。预计算并缓存文本嵌入加速训练。训练时长约10分钟，支持每日重训。
- **淘汰算法**：
  - 使用最小堆存储KV块，优先级为动态更新的概率p′。
  - **插入**：对话完成时将KV块插入堆中，初始优先级为p。
  - **命中提升**：命中块移出堆并送入KV缓存。
  - **概率衰减**：每10秒对所有块执行衰减：`decay = exp(-(time_cur - time_last) × scale)`, `prob_cur = prob_original × decay / (prob_original × decay + (1 - prob_original))`，scale默认为10⁻²。
  - **淘汰**：始终淘汰堆顶（概率最小）的块。
- **共享块处理**：对多个对话共享的KV块，采用最大池化策略：`prob_block_cur = max(prob_block_cur, prob_new_cur)`，避免因单个低概率对话导致热门前缀被误淘汰。

## 3. 实验设计

- **使用的数据集**：
  - **LMSys**：100万对话，平均输入63 tokens，输出179 tokens，跟进率35%。
  - **ShareGPT**：9.5万对话，平均输入113 tokens，输出305 tokens，跟进率55%。
  - **Chatbot-Arena**：3.3万对话，平均输入36 tokens，输出155 tokens，跟进率8%。
- **Benchmark与对比方法**：
  - 主要基线：vLLM中的**LRU**淘汰策略。
  - Oracle策略（具有完美未来知识）用于上限对比。
  - 消融实验：对比仅使用轮次数作为输入的变体 `LPC_turns`、使用模型响应的变体、统一预测器 vs 专用预测器等。
- **评估指标**：命中率（Hit Ratio）、时间到首令牌（TTFT）、预填充吞吐量（req/s）、GPU计算活跃度（SM Active、SM Occupancy、Tensor Pipe Active等）。
- **实验场景**：
  - 不同缓存大小（60K~160K tokens，约15.6~40 GB）。
  - 不同用户思考间隔（λchat 变化）。
  - 仿真解耦预填充服务器（prefill-only）与推理模型（Qwen3-32B-FP8）。
- **公平性处理**：为LPC扣除1GB GPU内存开销，与LRU的可用缓存大小保持一致。

## 4. 资源与算力

- **硬件配置**：
  - GPU：NVIDIA H100（80GB HBM3），单GPU运行模型。
  - CPU：8个CPU核心，64GB CPU内存。
- **模型与软件**：Qwen3-32B-FP8（32B参数推理模型），vLLM框架，PyTorch。
- **训练资源**：预测器训练约需10分钟；嵌入模型冻结，仅MLP更新。
- **运行时开销**：预测器预留1GB GPU内存（约占总内存1.25%），可处理1000次/秒预测。实际GPU计算开销增量极低（SM Active增加0.72%等）。

> 注：论文未明确说明训练使用的GPU数量，但从描述看为单卡H100。

## 5. 实验数量与充分性

- **实验组数**：共进行了约20组以上实验（正文章节4.3~4.6 + 附录A、B的多项消融）。
- **覆盖范围**：
  - 主实验：缓存大小变化（3数据集 × 5+大小），聊天间隔变化（3数据集 × 4+间隔），吞吐量与延迟测量。
  - 消融研究：MC精度和F1比较、输入特征（用户提示 vs. 模型响应）、窗口长度（5 vs. 10）、统一预测器 vs. 专用、与Oracle对比、内存开销敏感性分析（0×/1×/2×/4×）。
  - 统计显著性：每个数据点至少重复5次，误差棒显示最大差异<0.013，相对变异<4.6%。
- **充分性与客观性**：实验设计较全面，涵盖了主要性能指标、多种工作负载、参数敏感度和消融分析。对比方法包括LRU和Oracle，且公平扣除LPC开销。但主要对比仅为LRU，未与更多启发式策略（如LFU、GDSF等）比较，略有局限。

## 6. 论文的主要结论与发现

- **命中率显著提升**：在全部三个数据集和缓存大小下，LPC的命中率相对LRU提升13%~98%（不同场景）。
- **缓存需求大幅降低**：达到相同命中率时，LPC可减少18%~47%的缓存大小（对应约7.2~18.8 GB内存节省）。
- **吞吐量与延迟改善**：在仿真解耦预填充环境中，LPC带来最高11%的预填充吞吐量提升；对约7%的请求，TTFT降低42~75%。
- **开销极小**：预测器仅需1GB GPU内存，计算开销可忽略（SM Active增加<1%）。训练时间短（约10分钟），支持每日重训。
- **鲁棒性**：在不同用户思考间隔下，LPC均保持5%~18%的命中率优势。

## 7. 优点

- **首次将学习型淘汰引入LLM前缀缓存**：填补了领域空白，方法具有创新性。
- **轻量化设计**：使用小模型（118M嵌入+3层MLP），内存与计算开销极低，适合生产部署。
- **内容感知**：利用对话语义特征，超越了纯时间戳的LRU。
- **通用性强**：与FlashAttention、推测解码等其他优化正交，可组合使用。
- **实验充分**：多数据集、多指标、消融丰富，并进行了统计显著性验证。
- **开源代码**：提供完整实现，便于复现与扩展。

## 8. 不足与局限

- **依赖合成时间戳**：真实对话时间戳未公开，论文使用指数分布模拟，可能不完全反映真实用户行为。
- **对比范围有限**：仅与LRU比较，未与LFU、GDSF、CACHEUS等其他启发式或学习型策略对比。
- **模型单一**：实验仅基于Qwen3-32B-FP8，虽然声称方法无关，但未在Llama、Mistral等其他模型架构上验证。
- **预测器重训假设**：每日重训假设数据分布相对稳定，但对于快速变化的话题（如新闻热点）可能不够及时。
- **基于文本的局限性**：预测器仅使用用户提示文本，未利用用户身份、时序模式等额外维度，可能导致性能上限（与Oracle仍有差距）。
- **共享块处理的简化**：最大池化策略可能在某些极端情况下不够精细（如多数对话已结束但一个长对话概率仍高）。

（完）
