---
title: "SkipGPT: Each Token is One of a Kind"
title_zh: SkipGPT：每个Token独一无二
authors: "Anhao Zhao, Fanghua Ye, Yingqi Fan, Junlong Tong, Jing Xiong, Zhiwei Fei, Hui Su, Xiaoyu Shen"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=d7v2iUSa9s"
tags: ["query:edge-llm"]
score: 7.0
evidence: 动态层剪枝用于高效LLM推理
tldr: 现有静态层剪枝忽略了token级和层级的动态差异。SkipGPT提出动态层剪枝框架，通过全局token感知路由和MLP/注意力层特化策略，智能分配计算资源。实验表明在保持性能的同时显著降低推理计算量。该方法为资源受限场景下的LLM部署提供了新的方向。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 762, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1754, \"height\": 923, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 854, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 824, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 735, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 820, \"height\": 543, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 728, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1753, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1754, \"height\": 917, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1570, \"height\": 912, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1553, \"height\": 290, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1551, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-d7v2iusa9s/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1536, \"height\": 559, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-d7v2iusa9s/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1813, \"height\": 1198, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-d7v2iusa9s/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1811, \"height\": 1571, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-d7v2iusa9s/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1795, \"height\": 1592, \"label\": \"Table\"}]"
motivation: LLM深层架构导致计算开销大，现有静态剪枝无法适应token和层级的动态性。
method: 提出全局token感知路由和组件特定剪枝策略，动态跳过无关层。
result: 在多种LLM上实现计算量大幅降低，且性能损失极小。
conclusion: SkipGPT利用动态剪枝优化LLM推理效率，适合资源有限环境。
---

## Abstract
Large language models (LLMs) achieve remarkable performance across tasks but incur substantial computational costs due to their deep, multi-layered architectures. Layer pruning has emerged as a strategy to alleviate these inefficiencies, but conventional static pruning methods overlook two critical dynamics inherent to LLM inference: (1) *horizontal dynamics*, where token-level heterogeneity demands context-aware pruning decisions, and (2) *vertical dynamics*, where the distinct functional roles of MLP and self-attention layers necessitate component-specific pruning policies. We introduce **SkipGPT**, a dynamic layer pruning framework designed to optimize computational resource allocation through two core innovations: (1) global token-aware routing to prioritize critical tokens and (2) decoupled pruning policies for MLP and self-attention components. To mitigate training instability, we propose a two-stage optimization paradigm: first, a disentangled training phase that learns routing strategies via soft parameterization to avoid premature pruning decisions, followed by parameter-efficient LoRA fine-tuning to restore performance impacted by layer removal. Extensive experiments demonstrate that SkipGPT reduces over 40% model parameters while matching or exceeding the performance of the original dense model across benchmarks. By harmonizing dynamic efficiency with preserved expressivity, SkipGPT advances the practical deployment of scalable, resource-aware LLMs. Our code is publicly available at: https://github.com/EIT-NLP/SkipGPT.

---

## 论文详细总结（自动生成）

# SkipGPT：每个Token独一无二 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大型语言模型（LLM）虽然性能优异，但其深度、多层的Transformer架构导致推理计算成本极高，且现有层剪枝方法存在两大关键盲区：
  - **水平动态（Horizontal Dynamics）**：不同token在序列中的计算需求存在差异，但现有静态剪枝或固定比例分配方法忽略了这种token级异质性。
  - **垂直动态（Vertical Dynamics）**：同一层内的MLP和自注意力模块功能不同，但大多数剪枝方法将其视为一个整体，剪枝策略过于粗糙。
- **动机**：从人类大脑高效运作（100万亿突触连接仅需30瓦）中获得启发，LLM存在结构冗余和计算分配不均问题，需要更精细、动态的剪枝策略。
- **整体意义**：引入SkipGPT，一个动态层剪枝框架，通过全局token感知路由和解耦剪枝策略，在保持甚至超越原始模型性能的同时显著降低计算量，推动资源感知型LLM的实用部署。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：在推理过程中，为每个token动态决定是否执行MLP模块或自注意力模块，在全局稀疏度约束下灵活分配计算资源。
- **关键技术细节**：
  1. **全局稀疏度（Global Sparsity）**：定义稀疏度为在前向传播中跳过的模块数占总模块数的比例，允许计算资源在宽度（每层参与计算的token数）和高度（每个token经过的模块数）上灵活分配，而非固定层或token的预算。
  2. **路由实现（Routing Implementation）**：在每个MLP和注意力模块前放置一个线性路由器（两层输出为skip/execute概率）。利用Gumbel-Softmax重参数化和Straight-Through Estimator（STE）实现离散二值决策的可微优化：
     - 前向：采样离散值（0跳过，1执行）。
     - 反向：使用软概率传播梯度，更新路由器参数。
  3. **两阶段训练范式**：
     - **第一阶段：路由器调优（Router Tuning）**：冻结模型所有参数，仅优化轻量路由器（参数仅占LLaMA2-7B的0.007%）。损失函数包含语言建模损失和稀疏度正则项 \( \mathcal{L}_{\text{all}} = \mathcal{L}_{\text{lm}} + \alpha |T - r| \)，其中 \( T \) 为目标稀疏度，\( \alpha \) 控制惩罚强度（实验取8）。Gumbel-Softmax温度 \( \tau \) 从5线性退火至1。
     - **第二阶段（可选）：LoRA微调（LoRA Fine-Tuning）**：冻结路由器，仅微调LoRA适配器（低秩矩阵）以恢复因深度剪枝而可能损失的性能。
  4. **训练稳定性应对**：联合训练范式（路由器与模型参数同时优化）会导致随机初始化的路由器迫使模型参数过早适应次优路由策略，形成恶性循环；两阶段训练有效避免了这一问题。

## 3. 实验设计

- **模型**：LLaMA2-7B、LLaMA2-13B、LLaMA3.1-8B。
- **数据集**：
  - **训练数据**：RedPajama-Data-1T-Sample（85万样本，共10亿token），每个样本截断至4096 token。同时从该数据集中取100个随机样本作为校准集（用于静态方法计算块重要性）。
  - **评估基准**：
    - 常识推理：BoolQ、PIQA、HellaSwag（HeSw）、WinoGrande、ARC-easy（ARC-E）、ARC-challenge（ARC-C）、OpenbookQA（OBQA）。
    - 困惑度（Perplexity）：WikiText2（WT2）、PTB。
- **对比方法**：
  - **静态剪枝基线**：ShortGPT、Shortened LLaMA（PPL/Taylor变体）、LaCo、Joint Layer Drop（细粒度移除注意力或MLP层）、LLM-Pruner、SliceGPT。
  - **动态剪枝基线**：MoD-D（MoD的变体，解耦注意力与MLP）、D-LLM（token级逐层决策）、SkipGPT-Joint（联合训练变体，作为两阶段消融基线）。
  - **额外对照**：Dense原模型 + LoRA、静态方法 + LoRA微调恢复。
- **训练配置**：路由器调优使用2e-3恒定学习率，10,000步；LoRA微调使用2e-4学习率、余弦调度、10%预热，AdamW优化器，batch size 16。所有模型训练均使用单个A800（80GB）GPU。

## 4. 资源与算力

- **硬件**：单个A800（80GB）GPU。
- **训练时间**：
  - 路由器调优：约4小时完成。
  - LoRA微调：未明确总时长，但作为可选阶段，其开销较小（仅需单卡）。
- **参数规模**：路由器总参数量仅占原模型参数的0.007%（LLaMA2-7B），极为轻量。

## 5. 实验数量与充分性

- **实验组数**：涵盖3个模型系列（7B/8B/13B），2种剪枝比例（25%和40%），7个常识推理数据集 + 2个困惑度数据集；对比8种基线方法（静态+动态），并包含多种消融实验（如联合训练、LoRA恢复、不同稀疏度水平）。
- **消融分析**：
  - 两阶段训练 vs 联合训练（SkipGPT-Joint）。
  - 路由器调优后性能 vs 最终LoRA微调后性能（SkipGPT-RT vs SkipGPT-RT-L）。
  - 不同稀疏度下（20%~80%）的性能变化（通过缩放规律实验探索剪枝极限）。
  - 路由行为分析：注意力与MLP模块冗余对比（5种目标稀疏度）、上下文长度对激活率的影响（100-token滑动窗口，50个样本平均）。
- **充分性与公平性**：实验设计较为全面，覆盖主流剪枝方法和多尺度评估；对比中注意了参数比例的一致性（如Joint Layer Drop和SkipGPT按模块参数比例剪枝）；消融实验验证了关键设计选择（两阶段、解耦路由）。评估使用了标准库lm-evaluation-harness，可复现性较好。

## 6. 主要结论与发现

- **性能表现**：
  - SkipGPT-RT（仅路由器调优）在25%参数剪枝下对LLaMA2-7B/13B保留超过90%原始模型性能；对LLaMA3.1-8B在25%剪枝时保留超过95%，在40%剪枝时保留超过80%，且此时几乎所有基线方法均严重崩塌。
  - SkipGPT-RT-L（+LoRA微调）可完全恢复甚至超越原始模型性能（在LLaMA2-7B上平均准确率69.50%，接近dense+LoRA的69.98%）。
- **两阶段训练的有效性**：联合训练（SkipGPT-Joint）性能显著下降（如LLaMA2-7B平均准确率仅48.16%），验证了随机初始路由器与预训练参数间的冲突导致不稳定。
- **路由分析洞察**：
  - **注意力模块比MLP模块冗余性更高**：在不同目标稀疏度下，注意力模块的平均稀疏率均高于MLP模块（例如目标稀疏度30%时注意力稀疏率33.19%，MLP为26.33%），提示未来架构可减少注意力模块比例。
  - **上下文长度对计算需求的影响**：随着序列增长，后续token需要更多注意力计算（激活率从约0.5升至0.75）但更少MLP计算（激活率从约0.7降至0.5），推测模型早期需MLP进行任务识别，后期依赖注意力处理已累积的上下文。
- **剪枝缩放规律**：LLaMA2-13B在高达80%稀疏度下才出现明显的困惑度上升，揭示当前LLM存在惊人的层冗余（远超预期），可能源于Transformer架构对所有token统一计算的设计低效。

## 7. 优点

- **方法创新性**：首次同时考虑水平动态（token级自适应）和垂直动态（注意力与MLP解耦），突破了传统静态剪枝和固定比例动态分配的限制。
- **训练高效**：路由器轻量（0.007%参数），单卡4小时完成训练，无需修改原始模型参数；LoRA可选且进一步提升性能，整体开销远低于微调整个模型。
- **性能优越**：在40%高剪枝率下仍能匹配甚至超越原始模型，远超现有静态和动态剪枝方法。
- **分析工具价值**：路由器调优后可直接分析原始模型各模块重要性，揭示了注意力与MLP冗余差异、上下文长度对计算的非单调影响，为未来架构设计提供依据。
- **代码开源**：提供了完整可复现代码。

## 8. 不足与局限

- **实验覆盖范围**：
  - 仅评估了英文通用推理和语言建模任务，未涉及多语言、多模态、长上下文生成（如文档摘要、对话）、或需要知识库的任务，泛化性有待验证。
  - 主要聚焦于LLaMA系列，未在其他架构（如GPT、BLOOM、Mistral）上验证，可能受模型结构偏好的影响。
- **训练代价虽低但仍需额外步骤**：路由器调优需要一小部分训练数据（10亿token）和单GPU计算，对于完全无法访问原始预训练数据的场景可能受限（虽然路由器本身很小，但调优过程仍依赖一定数据）。
- **动态路由本身增加推理复杂度**：虽然跳过模块节省计算，但每个token前都需要运行路由决策（线性层），引入微小额外开销；在大规模推理中需权衡实际速度提升（文中未提供延迟或吞吐量测量）。
- **理论分析不足**：未从理论上证明两阶段训练优于联合训练的根本原因，仅通过实验观察；也没有量化不同稀疏度下路由器的决策稳定性或最优性边界。
- **应用限制**：剪枝后模型的结构不再“密集”，可能影响硬件并行效率（虽然跳过模块通过残差连接保持相同维度和计算图），实际部署中需考虑与批量处理、KV缓存、投机解码等技术的兼容性报告不够详细。

（完）
