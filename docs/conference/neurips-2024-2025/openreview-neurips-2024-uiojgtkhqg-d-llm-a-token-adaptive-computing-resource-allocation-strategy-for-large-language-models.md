---
title: "D-LLM: A Token Adaptive Computing Resource Allocation Strategy for Large Language Models"
title_zh: D-LLM：面向大语言模型的令牌自适应计算资源分配策略
authors: "yikun jiang, Huanyu Wang, Lei Xie, Hanbin Zhao, Chao Zhang, Hui Qian, John C.S. Lui"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=UIOjGTKHQG"
tags: ["query:edge-llm"]
score: 8.0
evidence: 面向资源受限平台的自适应计算资源分配，适用于边缘部署
tldr: 大语言模型在资源受限平台上部署困难，而现有方法对所有令牌等量处理。D-LLM提出动态推理范式，为每个变压器层设计动态决策模块，根据令牌重要性自适应分配计算资源。实验表明该方法在保持精度的同时显著降低计算开销，特别适合边缘设备等资源受限环境。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-uiojgtkhqg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 846, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uiojgtkhqg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uiojgtkhqg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uiojgtkhqg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1444, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uiojgtkhqg/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1460, \"height\": 1084, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-uiojgtkhqg/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1434, \"height\": 422, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-uiojgtkhqg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 716, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uiojgtkhqg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1455, \"height\": 792, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uiojgtkhqg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1458, \"height\": 332, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uiojgtkhqg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1422, \"height\": 547, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uiojgtkhqg/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1420, \"height\": 406, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-uiojgtkhqg/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1424, \"height\": 217, \"label\": \"Table\"}]"
motivation: LLM在资源受限平台部署困难，且现有方法对所有令牌等量处理。
method: 为每个Transformer层设计动态决策模块，根据令牌重要性自适应分配计算资源。
result: 在保持精度的同时显著降低计算开销，适合边缘设备。
conclusion: D-LLM通过令牌自适应分配实现了资源高效的LLM推理。
---

## Abstract
Large language models have shown an impressive societal impact owing to their excellent understanding and logical reasoning skills. However, such strong ability relies on a huge amount of computing resources, which makes it difficult to deploy LLMs on computing resource-constrained platforms. Currently, LLMs process each token equivalently, but we argue that not every word is equally important. Some words should not be allocated excessive computing resources, particularly for dispensable terms in simple questions. In this paper, we propose a novel dynamic inference paradigm for LLMs, namely D-LLMs, which adaptively allocate computing resources in token processing. We design a dynamic decision module for each transformer layer that decides whether a network unit should be executed or skipped. Moreover, we tackle the issue of adapting D-LLMs to real-world applications, specifically concerning the missing KV-cache when layers are skipped. To overcome this, we propose a simple yet effective eviction policy to exclude the skipped layers from subsequent attention calculations. The eviction policy not only enables D-LLMs to be compatible with prevalent applications but also reduces considerable storage resources. Experimentally, D-LLMs show superior performance, in terms of computational cost and KV storage utilization. It can reduce up to 45\% computational cost and KV storage on Q\&A, summarization, and math solving tasks, 50\% on commonsense reasoning tasks.

---

## 论文详细总结（自动生成）

# 论文总结：D-LLM: A Token Adaptive Computing Resource Allocation Strategy for Large Language Models

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大语言模型（LLM）需要海量计算资源，难以部署在资源受限平台（如移动设备、边缘端）。现有LLM对所有token一视同仁地执行全部层，但自然语言中并非每个词同等重要（如冠词、标点等不关键token），简单任务与复杂任务也不应消耗相同资源。
- **目标**：提出一种动态推理范式，使LLM能够根据token重要性和任务难度自适应地分配计算资源，在保持性能的同时显著降低计算开销和存储消耗。

## 2. 方法论

### 核心思想
- 在每个Transformer层前添加一个轻量级**动态决策模块**，决定该层对当前token是执行还是跳过。每个token可拥有不同的执行路径，实现计算资源按需分配。

### 关键技术细节
- **决策模块设计**：由两个线性层+激活函数组成，输入当前token embeddings，输出二元分布（跳过/执行）。使用Gumbel-Softmax重参数化和straight-through estimator确保端到端可微训练。
- **可定制加速率**：引入加速率损失 \(L_{rate} = \frac{1}{N}\sum_n |\omega_n - \Omega|_1\)，其中\(\omega_n = 1 - \frac{1}{L}\sum_l \hat{b}^n_{l,1}\)，\(\Omega\)为用户目标加速率。
- **KV-cache驱逐策略**：当某层被跳过时，其KV-cache对后续token无用，故设计驱逐掩码（eviction mask）将这些层对应的key/value排除在自注意力计算之外，从而节省存储。同时保留前m个初始token的KV-cache（实验取m=2）。

### 模型训练
- 基于预训练LLM（如LLaMA）并使用LoRA进行参数高效微调，避免全量重训。总损失 \(L = L_{CE} + \alpha L_{rate}\)。

## 3. 实验设计

### 使用数据集/场景
- **Q&A与摘要**：Alpaca（PPL）、SAMSum（PPL）
- **数学求解**：GSM8K（准确率）、MaWPS（准确率）
- **常识推理**：BoolQ、PIQA、SIQA、OBQA、MMLU（准确率）

### 基准方法（Baseline & SOTA对比）
- **Baseline**：LLaMA2-7B / LLaMA3-8B + LoRA（全层执行）
- **对比方法**：
  - MoD (Mixture-of-Depths)：动态选择top-k token计算
  - Shortened-LLaMA：静态剪枝（基于PPL或Taylor指标）
  - Ada-Infer：基于early-exit的动态推理

### 实验设置
- 模型：LLaMA2-7B、LLaMA3-8B，均为32层
- 微调：仅LoRA（秩=？未明确），仅训练决策模块+LoRA
- 上下文长度：1024 tokens
- 超参数：α按任务不同（0.1~5），训练10~20 epochs

## 4. 资源与算力

- **GPU**：8× NVIDIA L20
- **框架**：PyTorch，AdamW优化器
- **速度**：每步训练约0.07秒
- **学习率**：9×10⁻³，前2个epoch warm up，后使用余弦退火
- **训练显存**：LoRA约26.2GB，D-LLM约32GB（额外5.8GB用于决策模块）
- **推理显存**：全模型13.9GB，D-LLM 50%加速时仅7.4GB
- **额外开销**：决策模块仅占1%参数、0.9% FLOPs，每模块推理延迟0.1ms（Transformer层约1.2ms）
- **未明确**：总训练时间、具体GPU型号（仅说NVIDIA L20）、单次实验epoch时长等。

## 5. 实验数量与充分性

- **主实验**：表1在9个数据集上对比5种方法（含baseline），报告准确率/PPL和FLOPs。
- **消融实验**：表2在LLaMA2/3上对比有无驱逐策略；表3分析保留初始token数量m；表5分析超参数α。
- **成本-性能曲线**：图2在三个数据集上展示不同FLOPs下的性能趋势。
- **可视化分析**：图3展示不同语法词在各层的执行率；图4展示不同任务/问题在各层的执行率。
- **定性示例**：附录A.7展示生成结果对比。
- **充分性评价**：
  - 实验覆盖Q&A、数学、常识推理三大类，共9个数据集，种类较全面。
  - 对比了当前主流的动态/静态剪枝方法，具有代表性。
  - 消融分析较完整（驱逐策略、保留token、超参数）。
  - **不足**：仅在7B/8B规模模型上验证，未在更大模型（如13B、70B）或不同架构（如Mistral）上测试；缺少推理延迟实际测量（仅给出FLOPs作为计算量指标，但实际推理速度受多种因素影响）；未报告多次运行的标准差。

## 6. 主要结论与发现

- D-LLM可在保持甚至提升模型性能的前提下，减少**40%~50%的计算开销**（FLOPs）和KV-cache存储。
- 动态决策模块能够根据任务难度和token重要性自适应分配层数：简单问题/不重要token执行更少层，复杂问题/关键token执行更多层。
- 不同语法成分（如数字、冠词、情态动词）在不同层的执行率存在差异，说明各层具有功能分化。
- 保留前2个初始token的KV-cache（不参与动态跳过）是最优设置。
- 与MoD、Shortened-LLaMA、Ada-Infer相比，D-LLM在更低计算成本下取得更好或相当的性能。

## 7. 优点

- **方法创新**：首次将token级动态层跳过引入LLM推理，并结合KV-cache驱逐策略，兼顾计算与存储效率。
- **轻量高效**：决策模块仅增加1%参数，不影响模型主体，且利用LoRA微调，训练成本低。
- **可定制加速率**：通过调节目标加速率Ω和超参数α，可灵活适应不同资源约束平台。
- **实验全面**：在多个基准、两种模型规模上进行了丰富的对比和消融，并有可视化分析增强可解释性。
- **代码开源**：提供GitHub仓库，便于复现。

## 8. 不足与局限

- **通用性待验证**：仅在LLaMA2-7B/8B上实验，未在更大模型（如13B/70B）或其他架构（如GPT、Falcon）上验证。决策模块在不同规模/架构上的迁移性未知。
- **实验未覆盖所有场景**：缺少实际端到端延迟（latency）测量；FLOPs虽能反映计算量，但实际吞吐量还受内存带宽、框架优化等影响。
- **训练依赖性**：需要针对每个任务进行微调（LoRA+决策模块），无法直接用于零样本/少样本推理。
- **初始token保留策略**：强制保留前m个token不跳过，可能限制简单long-context场景下的进一步加速；m的选取需手动调优。
- **决策模块训练稳定性**：使用Gumbel-Softmax和straight-through estimator，可能存在训练不稳定或出现模式坍塌的风险。
- **任务性能权衡**：在部分Q&A任务上（如Alpaca），D-LLM的PPL略高于baseline（但计算成本更低），说明存在一定性能-效率折衷。

（完）
