---
title: "Týr-the-Pruner: Structural Pruning LLMs via Global Sparsity Distribution Optimization"
title_zh: Týr-the-Pruner：通过全局稀疏分布优化实现LLM结构化剪枝
authors: "Guanchen Li, Yixing Xu, Zeping Li, Ji Liu, Xuanwu Yin, Dong Li, Emad Barsoum"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=rAuRLePL2R"
tags: ["query:edge-llm"]
score: 4.0
evidence: 结构化剪枝减小模型大小，间接支持资源高效推理
tldr: 本文针对LLM结构化剪枝中局部剪枝忽略全局拓扑、全局剪枝未端到端优化的问题，提出Tyr-the-Pruner框架，通过构建超网并重复应用局部剪枝进行搜索，实现全局稀疏分布优化，提升推理效率。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-raurlepl2r/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1464, \"height\": 678, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raurlepl2r/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 846, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raurlepl2r/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 689, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raurlepl2r/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1457, \"height\": 841, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raurlepl2r/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1451, \"height\": 928, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-raurlepl2r/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1446, \"height\": 445, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 1237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1451, \"height\": 482, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 752, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 668, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 684, \"height\": 175, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1444, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 730, \"height\": 158, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 957, \"height\": 805, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1447, \"height\": 548, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 867, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 691, \"height\": 1079, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 692, \"height\": 1077, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 692, \"height\": 1077, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 695, \"height\": 1076, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 693, \"height\": 1076, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 694, \"height\": 1076, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 695, \"height\": 1074, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-raurlepl2r/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 696, \"height\": 1074, \"label\": \"Table\"}]"
motivation: 现有结构化剪枝方法难以同时保持性能和全局稀疏性。
method: 端到端搜索框架，构建超网并优化全局稀疏分布。
result: 在保持性能的同时提升LLM推理效率。
conclusion: Tyr-the-Pruner是一种有效的全局结构化剪枝方法。
---

## Abstract
Structural pruning enhances hardware-agnostic inference efficiency for large language models (LLMs) yet often fails to maintain comparable performance. Local pruning performs efficient layer-by-layer compression but ignores global topology. Although global pruning aims to identify an optimal sparse model, intuitive methods typically adopt a two-stage paradigm that first evaluates substructure saliency and then applies global pruning, which ignores inter-structure dependencies and fails to achieve end-to-end optimization. To address these limitations, we propose Týr-the-Pruner, an efficient end-to-end search-based global structural pruning framework. This framework constructs a supernet by repeatedly applying local pruning across a range of sparsity ratios to each layer in an LLM, with the core goal of determining the optimal sparsity distribution under a target overall sparsity ratio. Concretely, we introduce an effective local pruning and an expectation error accumulation approach to improve supernet construction. Furthermore, we employ an iterative prune-and-search strategy with coarse-to-fine sparsity granularity to ensure efficient search convergence. Experimental results show that Týr-the-Pruner achieves state-of-the-art structural pruning, retaining 97% of the dense model's performance while removing a challenging 50% of Llama-3.1-70B's parameters.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：大型语言模型（LLM）在部署时面临高计算和存储成本，结构化剪枝是重要的压缩手段，但现有方法存在显著局限。
- **两种现有方法的不足**：
  - **局部剪枝**：逐层独立剪枝，效率高但忽略全局拓扑依赖，导致各层稀疏率必须均匀，无法个性化优化。
  - **全局剪枝**：试图寻找最优稀疏模型，但常见方法是先评估子结构显著性再全局排序，忽略子结构间的相互依赖，且依赖反向传播的显著性估计效率低、在有限校准数据下易过拟合，缺乏端到端优化。
- **研究目标**：实现一种**端到端优化、高效且可保持性能**的全局结构化剪枝框架。

## 2. 方法论：核心思想、关键技术细节

### 2.1 核心思想
构建一个**超网络**，该超网络通过对LLM每一层以不同稀疏率进行局部剪枝得到多个剪枝副本。目标是利用**进化搜索**在该超网络中，在满足目标总稀疏率约束下，找到最优的**层间稀疏率分布**。

### 2.2 关键技术细节

- **有效局部剪枝**：
  - **冗余结构识别**：同时利用泰勒展开的**一阶梯度信息**和**二阶Hessian矩阵信息**设计冗余通道识别指标，比仅用单种信息更准确。
  - **权重调整**：剪枝后，利用最优脑外科医生(OBS)方法对剩余权重进行调整，以补偿剪枝误差。
  - **渐进式剪枝**：采用细粒度、渐进式剪枝，使未剪枝权重能逐步均匀补偿损失，并可利用Sherman-Morrison-Woodbury公式快速更新逆Hessian矩阵，复杂度O(d_in²)。
  - **剪枝单元**：FFN以单个通道为原子单元；MHA先计算o_proj层每个输出通道的显著性，再按所属head聚合（平均），以head为原子单元。

- **期望误差累积**：
  - **问题**：超网络中多个稀疏结构共存，导致误差反向传播路径不明确。
  - **方法**：对于第ℓ层的E个稀疏结构，定义期望输出激活为各结构输出激活的**加权平均**，权重为 $1 - S_e$（S_e为该结构稀疏率），低稀疏率（更可靠）的结构获得更高权重。这使得深层剪枝能意识到浅层剪枝的影响，实现各稀疏结构间的**均衡感知**。

- **迭代式剪枝-搜索策略**：
  - **核心流程**：采用“粗到细”的稀疏粒度迭代过程。
    1. 在粗粒度稀疏间隔下构建超网。
    2. 进行进化搜索，找出当前最优稀疏分布。
    3. 缩小稀疏间隔（通常减半），以当前最优分布为中心构建新超网。
    4. 重复上述步骤，直至达到目标细粒度。
  - **搜索优化目标**：采用**蒸馏启发式度量**，即最小化稀疏模型和稠密模型在中间层激活和最终logits之间的差异，避免单一任务过拟合。
  - **进化搜索操作**：通过在不同层之间随机**移位稀疏率**产生变异，评估候选性能，筛选优秀者繁殖。
  - **效率保障**：采用多层验证策略（2K → 16K → 128K tokens）筛选候选，加速搜索过程。

- **算法流程**：包含局部剪枝函数、超网构建函数、进化搜索函数和主函数，具体见论文Algorithm 1-4。

## 3. 实验设计

- **数据集**：
  - **校准数据**：FineWeb-Edu子集（来自Common Crawl），提取约400万tokens（约1000个样本，最大输入长度4096）。
  - **评估数据集**：
    - **语言理解**：WikiText-2测试集（perplexity指标）。
    - **下游任务**：0-shot准确率：ARC-Easy, ARC-Challenge, BoolQ, HellaSwag, OpenbookQA, RTE, WinoGrande；5-shot准确率：MMLU。

- **Benchmark方法**：ShortGPT、LaCO+、SliceGPT、Wanda-SP、LLM-Pruner、ZipLM、OSSCAR、FLAP等8种主流结构化剪枝方法。
  - **进一步对比**：SearchLLM、ProbePruning、Adapt-Pruner、CFSP、PruneNet、DISP-LLM、EvoP、DarwinLLM。

- **实验场景**：
  - 模型：Llama-2 (7B, 13B, 70B)、Llama-3.x (2-3B, 0-8B, 1-8B)、Llama-3.1 (8B, 70B)、Mistral (7B-v0.3, Nemo)。
  - 稀疏率：12.5%, 25%, 37.5%, 50%。
  - 目标结构：注意力头和FFN中间神经元，**非均匀稀疏**。

- **公平性**：所有对比方法使用相同的FineWeb-Edu校准样本进行复现，确保比较公平。

## 4. 资源与算力

- **硬件**：4块 AMD Instinct™ MI250 (64GB) 加速器。
- **规模**：小于13B参数的模型仅在单个加速器上运行。
- **内存与存储管理**：超网络中所有子结构存储在磁盘而非HBM，通过整数列表追踪当前选中结构，确保HBM中只加载一个完整LLM。例如，7B模型HBM占用约14-16GB，存储占用39.6GB；70B模型HBM占用约140GB，存储占用414.7GB。迭代间存储可清理以节省空间。
- **论文未明确提及**：单次实验或整个搜索过程的精确时长、消耗的总GPU小时数，仅在3.3节提到“单个世代仅需190秒”。总体搜索时间消耗不可忽略，但作者认为在模型压缩中可接受。

## 5. 实验数量与充分性

- **实验数量**：大量、系统性的实验。
  - 主要性能对比（Table 1）：覆盖4种稀疏率 × 8种对比方法 × 8种模型 = 256组对比，此外还有更广泛的进一步对比（Table 9）。
  - 超大规模模型验证（Table 2）：Llama-2-70B和Llama-3.1-70B在50%稀疏率下的实验。
  - 消融实验：局部剪枝组件（Table 4）、超网构建组件（Table 4）、搜索方向（Table 5）、迭代数量（Table 6）。
  - 兼容性实验（Table 7）：与量化（AWQ、SmoothQuant、RTN）和结构化稀疏（SparseGPT、ALPS）联合使用。
  - 推理效率测试（Table 3, Figure 4）。
  - 统计显著性分析（Table 11）：多个随机种子下5次重复实验。
  - 剪枝+微调实验（Table 10）。
- **充分性与客观性**：
  - **充分**：实验覆盖了多种主流LLM系列、不同参数量级、不同稀疏率、多种评估指标，并进行了详尽的消融和对比，实验设计全面。
  - **客观**：所有对比方法使用相同校准数据进行复现，保证了公平性。实验结果记录了标准偏差，验证了稳定性。

## 6. 主要结论与发现

- **性能卓越**：Týr-the-Pruner在几乎所有稀疏率和LLM模型上取得了**最先进(SOTA)** 的结果。
  - 在低稀疏率（12.5%, 25%）下持续最优。
  - 在高稀疏率（37.5%, 50%）下显著优于其他方法。
  - 例如，在Llama-3.1-8B上，37.5%稀疏率时，本文方法比FLAP方法在WikiText2困惑度上低3.45，平均下游准确率高10.26%。
- **规模可扩展**：在70B规模的Llama-3.1模型上，**50%稀疏率下仍能保持97%的稠密模型性能**，远超其他方法（如SliceGPT仅62%，ZipLM为89%）。
- **加速效果明显**：以Llama-3.1-8B为例，50%稀疏率使首Token时间(TTFT)降低43%，解码吞吐量提升38%。
- **迭代搜索有效**：迭代式剪枝-搜索策略优于一次性细粒度搜索，能在更少世代的搜索中获得更好的稀疏分布和性能。
- **兼容性好**：与量化和非结构化稀疏等后续压缩技术配合良好，能进一步压缩而不显著损失精度。
- **非先验性**：找到的最优稀疏分布并非遵循“浅层/深层对剪枝更敏感”的简单假设，而是完全因模型而异，证明了方法能自适应地挖掘模型特性。

## 7. 优点（方法或实验设计亮点）

- **端到端优化**：通过搜索直接优化全局稀疏分布，避免了传统两阶段方法（显著性评估+全局排序）的缺点。
- **有效的超网构建**：结合了基于泰勒展开的高效局部剪枝（同时利用一、二阶信息、渐进式剪枝）和解决多路径误差累积问题的期望误差累积法。
- **高效的搜索策略**：采用迭代式“粗到细”搜索，将巨大的搜索空间分解为多个小空间，显著提升收敛速度和搜索效果。
- **蒸馏启发式搜索指标**：使用模型相似度而非单任务损失，避免过拟合，增强泛化性。
- **资源效率**：通过将超网子结构存储于磁盘，有效控制HBM占用，使得在单卡或少量GPU上也能处理大规模模型。
- **实验设计规范**：使用统一的高质量校准数据复现基线方法，确保了比较的公平性；提供了统计显著性分析，增强了结果的可信度。
- **兼容性验证**：验证了与量化、非结构化稀疏等技术的兼容性，展示了方法的实用性和扩展性。

## 8. 不足与局限

- **搜索时间成本**：虽然相比一次性搜索有提升，但整个迭代搜索过程（多次构建超网和进化搜索）的时间成本仍然不可忽视。作者也承认这是一个局限，并表示将在未来工作中继续优化。
- **实验覆盖范围**：
  - 主要聚焦于Llama和Mistral系列的Decoder-only架构。论文未提及对Encoder-only（如BERT）或Encoder-Decoder架构的适用性。
  - 校准数据来源为FineWeb-Edu，虽然质量高，但可能不完全代表所有下游任务的分布。对于完全不同的数据分布（如代码、专业领域文档），性能可能会变化。
- **应用限制**：
  - 虽然实现了硬件无关加速，但非均匀稀疏仍可能在极端情况下（如方差极大）导致少量效率损失，因为会产生大量“瘦”矩阵乘法。
  - 需要存取完整超网数据于磁盘或HBM，对磁盘空间和存储I/O有一定要求。
- **偏差风险**：搜索过程中的随机性（随机种子变动会影响校准样本选择和随机稀疏移位）会导致最终结果有小幅波动。论文已通过统计显著性分析展示了波动范围在可接受内。
- **理论基础**：局部剪枝中的权重调整和冗余识别基于Taylor展开和Hessian矩阵的近似，这些近似在数据分布有显著偏移时可能不精确。

（完）
