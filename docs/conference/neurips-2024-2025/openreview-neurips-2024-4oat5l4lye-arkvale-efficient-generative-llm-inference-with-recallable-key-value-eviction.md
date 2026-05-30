---
title: "ArkVale: Efficient Generative LLM Inference with Recallable Key-Value Eviction"
title_zh: ArkVale：基于可召回键值驱逐的高效生成式大语言模型推理
authors: "Renze Chen, Zhuofeng Wang, Beiquan Cao, Tong Wu, Size Zheng, Xiuhong Li, Xuechao Wei, Shengen Yan, Meng Li, Yun Liang"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=4oAt5L4lYe"
tags: ["query:edge-llm"]
score: 7.0
evidence: KV缓存驱逐以提升推理效率
tldr: 针对长上下文LLM推理中KV缓存过大的问题，ArkVale提出可召回键值驱逐机制，在保留高影响token的同时允许召回被驱逐的token，从而在压缩缓存的同时不丢失重要信息。实验表明，该方法在多种长上下文基准上显著降低内存消耗和延迟，并保持甚至提升推理准确性，为资源受限环境下的高效推理提供了可行方案。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-4oat5l4lye/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1395, \"height\": 280, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4oat5l4lye/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1421, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4oat5l4lye/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1429, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4oat5l4lye/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1127, \"height\": 1037, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4oat5l4lye/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1119, \"height\": 898, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4oat5l4lye/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 632, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4oat5l4lye/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 780, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4oat5l4lye/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1416, \"height\": 682, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4oat5l4lye/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1434, \"height\": 710, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-4oat5l4lye/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1448, \"height\": 465, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-4oat5l4lye/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1411, \"height\": 239, \"label\": \"Table\"}]"
motivation: 长上下文场景下KV缓存占用大量内存，限制批大小和吞吐量，并增加延迟。
method: 提出可召回KV驱逐机制，保留高影响token并召回被驱逐但后续需要的token，以压缩缓存。
result: 在多种长上下文任务上显著减少内存占用并保持甚至提升推理质量。
conclusion: ArkVale通过智能驱逐和召回策略，为长上下文LLM推理提供了高效的缓存管理方案。
---

## Abstract
Large Language Models (LLMs) are widely used in today's tasks of natural language processing. 
To support applications like multi-turn chats, document understanding, and content generation, models with long context lengths are growing in importance.
However, managing long contexts brings substantial challenges due to the expansion of key-value cache (KV cache). Longer KV cache requires larger memory, limiting the batch-size thus decreasing throughput. Also, computing attention over long KV cache incurs more memory access, hurting the end-to-end latency.
Prior works find that it is sufficient to use only the recent and high-impact tokens for attention computation, allowing the eviction of less vital tokens to shrink cache size.
Nonetheless, we observe a dynamic shift in token importance across different decoding steps. Tokens initially evicted might regain importance after certain decoding steps.
To address this, we propose ArkVale, a page-based KV cache manager that can recognize and recall currently important tokens evicted before. We asynchronously copy the filled page into external memory (e.g., CPU memory) as backup and summarize it into a much smaller digest by constructing the bounding-volume of its keys. Before attention computation, we measure all pages' importance based on their digests, recall the important ones, evict the unimportant ones, and select the top-ranked pages for attention computation. 
Experiment results show that ArkVale performs well on various long context tasks with negligible accuracy loss under 2k$\sim$4k cache budget and can improve decoding latency to $2.2\times$ and batching throughput to $4.6\times$ because it applies attention on only a small subset of pages and reduce per-sample memory usage of KV cache.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究背景**：大语言模型（LLM）在长上下文场景（如多轮对话、文档理解、内容生成）中日益重要。然而，长上下文导致键值缓存（KV cache）急剧膨胀，带来两大挑战：
  - 内存占用大：限制批处理大小，降低吞吐量。
  - 注意力计算中频繁访问大型KV cache，导致推理延迟增加。
- **已有工作**：先前方法（如StreamingLLM、H2O、TOVA）利用KV cache的稀疏性，仅保留最近或高影响力的token，驱逐次要token以压缩缓存。
- **核心问题**：这些方法忽略了token重要性的动态变化——最初被驱逐的token可能在后续解码步骤中重新变得重要，导致永久丢弃关键信息，损害模型准确性。
- **研究目标**：提出一种可召回被驱逐token的KV缓存管理方法，在保持缓存紧凑的同时，能够动态召回真正重要的token，实现高效且准确的推理。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 受到vLLM分页管理启发，将KV cache中的token组织成**页面（page）**，实现粗粒度管理。
- 每个页面填充后，异步复制到外部内存（如CPU内存）作为备份，并利用**边界体（bounding-volume）** 将页面的key压缩成一个很小的摘要（digest），保留在GPU上。
- 每次注意力计算前，利用当前query和所有页面摘要（包括已驱逐页面的摘要）动态评估各页面的重要性，召回高重要性页面、驱逐低重要性页面，并仅让排名最靠前的页面参与注意力计算。

### 关键技术细节
1. **页面组织与备份**：页面大小可配置（默认32 token）。页面填充后异步拷贝到CPU，GPU上保留压缩摘要。
2. **页面摘要构建**：采用两种边界体方法：
   - **边界球（Bounding-sphere）**：存储球心c和半径r。重要性估计公式：\( I(q, K) \approx q \cdot c + r|q| \)。
   - **边界长方体（Bounding-cuboid）**：存储最大值向量\( b_{\max} \)和最小值向量\( b_{\min} \)。重要性估计：\( I(q, K) \approx \sum_i \max(q_i b_{\max,i}, q_i b_{\min,i}) \)。
   - 两者均提供多种半径变体（max、center、mean），其中**cuboid-mean**表现最佳。
3. **页面重要性评估与召回/驱逐**：根据query与摘要的近似最大点积计算页面重要性分数，对所有页面（包括GPU中已缓存的、CPU中已驱逐的）排序。选取top-k页面参与注意力，若其中某些页面已被驱逐，则从CPU回传数据；同时驱逐GPU中排在底部的页面。
4. **超参数设置**：注意力参与页数 \( k = \min(C, c/2)/p \)，其中C为常量（默认1280），c为缓存容量（token数），p为页面大小。

### 算法流程（文字描述）
- 预填充阶段：一次性处理prompt，缓存初始KV，每填满一个页面即异步备份并生成摘要。
- 解码阶段：每步解码前，用query计算所有页面（GPU+CPU）的摘要得分 → 排序 → 召回top-k中的CPU页面 → 驱逐GPU底部页面 → 执行分页注意力 → 生成下一个token → 更新KV缓存（新token填满页面后同样备份并摘要）。

## 3. 实验设计

### 数据集与场景
- **主基准**：LongBench中的6个数据集：
  - HotpotQA（多文档问答）
  - NarrativeQA（单文档问答）
  - Qasper（学术论文问答）
  - GovReport（文本摘要）
  - TriviaQA（少样本问答）
  - PassageRetrieval（合成检索任务）
- **长距离依赖测试**：自定义passkey retrieval任务，上下文长度分别为10k、20k、30k，passkey插入深度0%~95%。
- **性能测试**：使用GovReport中的样本（长度约10k/20k/30k）测量延迟和吞吐量。

### 对比方法
- 原始完整KV cache模型（Origin）
- StreamingLLM
- H2O
- TOVA
- ArkVale（16页面大小和32页面大小两种配置）

### 缓存预算设置
- LongBench实验：512、1024、2048、4096 token四种预算。
- Passkey任务：同样四种预算。
- 性能实验：512、1024、2048、4096以及全量。

### 评估指标
- 模型性能：F1（HotpotQA等）、Rouge-L（GovReport）、Accuracy（PassageRetrieval、Passkey）
- 推理性能：解码延迟（ms）、相对吞吐量

## 4. 资源与算力

- **GPU**：单张NVIDIA A100 80GB PCIe
- **CPU**：Intel Xeon Gold 6348 @ 2.60GHz
- **软件栈**：CUDA 12.3、PyTorch 2.3.0、HuggingFace Transformers 4.40.0
- **训练时长**：方法无需训练，仅推理阶段应用，因此未报告训练资源。论文未给出所有实验的总运行时间，但根据延迟数据，单步解码在毫秒级，全实验应可在数小时至一天内完成。
- **注意**：H2O和TOVA在长上下文预填充阶段需要使用两阶段策略以避免OOM，这增加了计算开销。

## 5. 实验数量与充分性

### 实验类型
- **摘要精度消融**（Figure 7）：对比7种估计方法（centroid + 6种边界体变体）的召回准确率，在top-1至top-40范围内评估。
- **LongBench主实验**（Figure 8）：6个数据集 × 4种缓存预算 × 5种方法（Origin、ArkVale-16、ArkVale-32、StreamingLLM、H2O、TOVA），共约6×4×5=120个实验点（实际图中展示不同预算下的性能曲线）。
- **Passkey检索**（Table 1）：3种上下文长度 × 4种缓存预算 × 4种方法，共48个实验点，每个测试点生成20个不同插入深度的样本。
- **延迟分解**（Figure 9a）：3种长度 × 5种预算（含全量）共15组，每组测量各阶段耗时。
- **吞吐量对比**（Figure 9b）：3种长度 × 5种预算共15组，比较最大可达吞吐量。

### 充分性与公平性
- **充分性**：覆盖了多种长上下文任务（问答、摘要、合成检索、精确检索），并测试了不同缓存预算和页面大小，消融实验验证了摘要方法的选择。
- **公平性**：与SOTA驱逐方法在同一模型（LongChat-7b-v1.5-32k）和相同数据集上比较；对H2O/TOVA采用两阶段预填充以保证公平比较长距离依赖能力。
- **潜在偏差**：所有实验均在单一模型上进行，未扩展到其他架构（如Llama-3、Mistral等）；Passkey任务样本数仅20个，统计显著性未报告误差条。

## 6. 主要结论与发现

- **准确性**：ArkVale在6个LongBench数据集上，在2k~4k缓存预算下性能接近原始完整模型（Origin），显著优于StreamingLLM、H2O、TOVA。即使在512预算下，ArkVale在多数任务上仍保持相对较高水平。
- **长距离依赖**：Passkey检索任务中，ArkVale在10k~30k上下文长度下稳定达到95%~100%准确率，而基线方法最高仅40%，随预算减少急剧下降。
- **推理速度**：解码延迟最高加速2.2倍（平均1.7倍），主要来源于注意力计算从全量变为固定大小页面的子集。额外开销（估计、选择、召回）占比小。
- **吞吐量**：在40GB KV缓存内存限制下，最大吞吐量提升至原始模型的4.6倍（平均3.5倍）。
- **页面大小**：16与32表现相近，小预算下16略优（更多页面增加命中机会）。

## 7. 优点

- **动态召回机制**：首次提出可召回被驱逐token的方法，解决了重要性的动态变化问题，相比永久驱逐方法显著提升长距离依赖表现。
- **高效摘要技术**：利用边界体（bounding-volume）压缩页面key，存储开销极低（只需2个向量或1个向量+标量），估计准确度高（cuboid-mean达95% top-1召回准确率）。
- **异步备份与隐形开销**：页面备份在后台异步进行，召回/驱逐操作开销微秒级，几乎不影响主流程。
- **无训练要求**：直接应用于预训练模型，不需要微调或额外训练。
- **分页管理与注意力加速**：通过只对top-k页面执行注意力，大大减少内存访问和计算量，同时保持高精度。
- **全面的实验验证**：涵盖多种任务、缓存预算、消融分析，以及延迟/吞吐量测量，结果一致性高。

## 8. 不足与局限

- **备份内存占用**：每个页面的KV需要在CPU内存中保存完整副本，当上下文极长（如数百万token）时，CPU内存可能不足，需进一步卸载到磁盘，增加I/O开销。
- **预填充阶段开销**：预填充阶段异步拷贝难以完全隐藏，可能影响首token延迟。
- **模型通用性受限**：实验仅在LongChat-7b（基于Llama-2 7B微调）上验证，未测试其他架构（如GPT风格、MQA、GQA等）或更大模型（13B/70B）。
- **未报告统计误差**：主实验结果未给出误差条或置信区间，无法判断结果稳定性。
- **超参数敏感性**：默认参数C=1280是否对各类任务最优？未进行更细致的调参分析。
- **页面大小影响**：虽然16和32差别不大，但极端小预算时页面大小选择仍影响性能，论文未给出自适应选择策略。
- **与量化方法的结合**：未探索将ArkVale与KV量化（如Q-Hitter）联合使用来进一步降低内存。

（完）
