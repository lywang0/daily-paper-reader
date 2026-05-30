---
title: "Get More with LESS: Synthesizing Recurrence with KV Cache Compression for Efficient LLM Inference"
title_zh: 用更少获得更多：利用KV缓存压缩合成循环实现高效LLM推理
authors: "Harry Dong, Xinyu Yang, Zhenyu Zhang, Zhangyang Wang, Yuejie Chi, Beidi Chen"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=uhHDhVKFMW"
tags: ["query:edge-llm"]
score: 6.0
evidence: 面向大语言模型推理的内存高效KV缓存压缩
tldr: KV缓存内存是LLM推理的瓶颈。现有驱逐式缓存无法回溯被丢弃的远距离token。本文提出LESS，将恒定大小的小缓存与基于驱逐的方法结合，使得所有历史token在后续解码中仍可被查询，在降低内存占用同时保持任务精度，适用于资源受限的设备。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-uhhdhvkfmw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 821, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-uhhdhvkfmw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 741, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-uhhdhvkfmw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 689, \"height\": 1001, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-uhhdhvkfmw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1767, \"height\": 797, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-uhhdhvkfmw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 860, \"height\": 632, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-uhhdhvkfmw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 762, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-uhhdhvkfmw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 752, \"height\": 498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-uhhdhvkfmw/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 661, \"height\": 1036, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-uhhdhvkfmw/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1249, \"height\": 751, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-uhhdhvkfmw/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1250, \"height\": 738, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-uhhdhvkfmw/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1252, \"height\": 745, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-uhhdhvkfmw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 849, \"height\": 168, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-uhhdhvkfmw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 837, \"height\": 690, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-uhhdhvkfmw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 814, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-uhhdhvkfmw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 867, \"height\": 550, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-uhhdhvkfmw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 886, \"height\": 782, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-uhhdhvkfmw/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1738, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-uhhdhvkfmw/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 633, \"height\": 477, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-uhhdhvkfmw/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1749, \"height\": 207, \"label\": \"Table\"}]"
motivation: KV缓存内存占用限制了大模型部署，现有驱逐方法无法恢复被丢弃的远距离token。
method: 将恒定大小的小缓存与基于驱逐的缓存方法集成，使所有token在后续解码中可查询。
result: 在多种任务上降低了内存占用并保持或提升了精度。
conclusion: LESS通过混合缓存策略有效缓解了KV缓存内存瓶颈，支持更高效的推理。
---

## Abstract
Many computational factors limit broader deployment of large language models. In this paper, we focus on a memory bottleneck imposed by the key-value (KV) cache, a computational shortcut that requires storing previous KV pairs during decoding. While existing KV cache methods approach this problem by pruning or evicting large swaths of relatively less important KV pairs to dramatically reduce the memory footprint of the cache, they can have limited success in tasks that require recollecting a majority of previous tokens. To alleviate this issue, we propose LESS, a simple integration of a (nearly free) constant sized cache with eviction-based cache methods, such that all tokens can be queried at later decoding steps. Its ability to retain information throughout time shows merit on a variety of tasks where we demonstrate LESS can help reduce the performance gap from caching everything, sometimes even matching it, all while being efficient. Relevant code can be found at https://github.com/hdong920/LESS.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）推理时，键值（KV）缓存是内存瓶颈，当序列长度或批大小增加时，缓存占用远超模型自身大小。现有驱逐式缓存方法（如H2O、Λ-masking、TOVA）通过丢弃被判定为“不重要”的KV对来压缩缓存，但无法在后续解码步骤中回收被丢弃的远距离token信息，导致性能损失，尤其在需要回顾多数历史token的任务（如长文档摘要）中表现不佳。
- **整体含义**：论文旨在合成一种混合缓存策略，将恒定大小的低秩缓存与驱逐式稀疏缓存结合，使得所有历史token在后续解码中仍可被部分查询，从而在保持高效的同时缩小与全缓存之间的性能差距，甚至在某些任务上匹配全缓存表现。

### 论文提出的方法论

- **核心思想**：观察到全注意力输出与稀疏注意力输出之间的残差具有低秩特性（图3），因此可用低秩方法近似该残差。LESS（Low-rank Embedding Sidekick with Sparse policy）通过一个小型MLP学习被驱逐KV对的低秩表示，并递归更新到一个恒定大小的低秩状态（H和z），在注意力计算时与稀疏缓存输出融合。
- **关键技术细节**：
    - 定义核函数ϕ(q)和ψ(k)（公式1-2），均为带有GELU激活和绝对值操作的小型MLP，确保内积非负。
    - 注意力计算（公式3）：输出 = [低秩贡献] + [稀疏缓存贡献] / [低秩归一化项 + 稀疏缓存归一化项]。低秩贡献由ϕ(q)与历史低秩状态H相乘得到，稀疏缓存贡献由标准softmax注意力计算当前被缓存的KV对得到。
    - 缓存更新（公式4-5）：每当稀疏策略驱逐一个KV对（k,v）时，将其信息累加到低秩状态：H <- H + ψ(k)^T * v，z <- z + ψ(k)。因此H和z是恒定大小的递归状态，仅存储被丢弃token的聚合信息。
- **算法流程**（Algorithm 1）：
    1. 当前步骤，加载稀疏缓存（K_C, V_C）、低秩状态（H, z）。
    2. 拼接当前新token的键值到稀疏缓存，计算注意力输出。
    3. 通过稀疏策略确定下一个步骤的缓存和新驱逐的KV对集合D。
    4. 用D更新H和z，然后删除D。
    5. 存储更新后的稀疏缓存和低秩状态。

### 实验设计

- **数据集/场景**：
    - 语言建模：WikiText-103、PG-19（词级别困惑度）。
    - 分类：BoolQ（10-shot准确率）、MuTual（16-shot R@1）。
    - 摘要生成：CNN/DailyMail、XSum、MultiNews（使用ROUGE-1/2/L）。
    - 长序列分析：改变prompt长度观察Rouge-1变化。
    - 延迟/吞吐量：使用合成数据，在不同序列长度和批大小下测量。
- **基准（benchmark）设置**：
    - 全缓存（Full Cache）：存储所有KV对。
    - 基线（Baseline）：仅使用稀疏策略（H2O/Λ-masking/TOVA）在α%稀疏度下。
    - Baseline+：稀疏策略多缓存额外4个KV对（与LESS低秩缓存占用同等空间）。
    - H2O+Performer：用随机傅里叶特征核替换低秩核，作为非学习基线。
    - LESS（β%）：在β%稀疏度下训练的LESS，测试时可能在不同稀疏度下评估（迁移测试）。
- **对比方法**：
    - 稀疏策略：H2O、Λ-masking、TOVA。
    - 全文还对比了Baseline+和H2O+Performer。
- **模型尺寸**：Llama 2 7B、Llama 2 13B、Falcon 7B。

### 资源与算力

- 文中未明确训练LESS所需的具体GPU型号、数量或总时长，但指出：
    - 训练可在单GPU上完成（for all models we experiment with, can be done on a single GPU）。
    - 训练时每个注意力层独立训练，无需端到端，因此可并行。
    - 每个层使用Adam优化器，40个epoch，初始学习率0.001，每10 epoch减半，固定隐藏维度R'=512，dropout=0.3。
    - 训练数据：从C4训练集采样512序列（Llama 2）或1024序列（Falcon，因其上下文长度减半），总token数相同。
- 推理基准测试在NVIDIA A100 80G GPU上进行，使用FP16。

### 实验数量与充分性

- **实验数量**：覆盖多种任务（语言建模、分类、摘要生成）、多种模型、多种稀疏策略、多种稀疏度（2%/5%/10%等），以及消融研究（核大小、注意力概率重建、长序列分析）。共约10张表和多张图。
- **充分性与公平性**：
    - 设置了Baseline+公平比较相同显存开销下的性能。
    - 测试了迁移性（训练和测试稀疏度不同）。
    - 直接比较了H2O+Performer，证明学习核的必要性。
    - 在摘要任务中还展示了定性示例（附录D）。
    - 总体实验设计较为周全，但未包含业界更大尺度的模型（如70B以上）或更多新型稀疏策略（如StreamingLLM等）；也未进行跨领域的任务（如代码、多轮对话）评估。

### 论文的主要结论与发现

1. **性能提升**：LESS在语言建模、分类、摘要等任务上显著缩小与全缓存的差距，恢复因稀疏策略丢失的部分性能。例如在Falcon 7B的CNN/DailyMail上恢复41.4%的Rouge-1退化；在Llama 2 7B的WikiText上将困惑度从13.33降至10.75（2%稀疏）。
2. **优于等量额外token**：将同等内存分配给额外KV对（Baseline+）的效果远不如LESS，表明低秩状态更高效。
3. **恒定内存与便宜集成**：低秩状态仅占约4个KV对的存储（R=8），添加的MLP参数不足总参数2%（Llama 2 13B）。训练轻量，可独立于各层进行。
4. **迁移性**：训练于某稀疏度下的LESS可迁移至其他稀疏度，尤其从较低稀疏度向较高稀疏度迁移时仍有效。
5. **效率**：在大批大小下，LESS吞吐量接近纯稀疏策略，比全缓存提升1.7×，延迟降低1.1-1.3×。
6. **注意力更准确**：Hellinger距离显示LESS更接近原始注意力分布。

### 优点

- **方法简洁**：仅需在每层添加两个小MLP，不改变原始模型权重，无需端到端微调。
- **恒定缓存大小**：低秩状态大小与序列长度无关，显存开销固定且极小。
- **通用性**：可与任意驱逐式稀疏缓存配合（实验了三种不同策略）。
- **训练高效**：每层独立训练，可并行化，仅需单GPU。
- **推理效率高**：延迟和吞吐量接近纯稀疏方法，远优于全缓存。

### 不足与局限

- **仍无法完全匹配全缓存**：尤其在极端稀疏（2%）或长序列任务中，LESS与全缓存仍有差距。
- **训练依赖**：核函数需要离线训练，且需收集目标模型和目标稀疏策略下的注意力输入输出数据；不同模型/策略需重新训练。
- **部署略慢于纯稀疏策略**：多出的低秩计算开销约占总解码时间15%（表8）。
- **长序列性能仍下降**：长prompt下所有方法（包括全缓存）性能均下降，LESS只是减缓了下降趋势，并非根本解决方案（图8）。
- **实验局限**：
    - 未在更大模型（70B+）上验证。
    - 仅评估了三种稀疏策略，未涵盖所有主流方法（如Scissorhands、StreamingLLM等）。
    - 任务类型偏重摘要和标准语言建模，缺乏对复杂推理、开放域问答等的测评。
    - 未讨论低秩状态可能引入的偏差或幻觉风险（定性示例中未出现明显问题，但未系统分析）。

（完）
