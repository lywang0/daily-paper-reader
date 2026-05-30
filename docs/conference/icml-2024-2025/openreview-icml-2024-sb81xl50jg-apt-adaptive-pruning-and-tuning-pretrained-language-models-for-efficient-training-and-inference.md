---
title: "APT: Adaptive Pruning and Tuning Pretrained Language Models for Efficient Training and Inference"
title_zh: APT：自适应剪枝与调优实现预训练语言模型的高效训练和推理
authors: "Bowen Zhao, Hannaneh Hajishirzi, Qingqing Cao"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=sb81Xl50JG"
tags: ["query:edge-llm"]
score: 6.0
evidence: 自适应剪枝与调优同时提升训练和推理效率
tldr: 现有参数高效微调无法提升推理效率，而结构化剪枝又增加训练成本。APT在微调早期动态识别重要参数，一并进行剪枝和调优。实验证明在保持准确率的同时，显著减少推理计算量并缩短训练时间。该方法兼顾训练和推理效率，实用性强。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-sb81xl50jg/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 787, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-sb81xl50jg/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1689, \"height\": 733, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-sb81xl50jg/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 684, \"height\": 1113, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-sb81xl50jg/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1764, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-sb81xl50jg/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 803, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-sb81xl50jg/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 792, \"height\": 432, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-sb81xl50jg/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1225, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sb81xl50jg/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1770, \"height\": 504, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sb81xl50jg/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1767, \"height\": 324, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sb81xl50jg/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 857, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sb81xl50jg/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 861, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sb81xl50jg/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1168, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sb81xl50jg/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1764, \"height\": 686, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sb81xl50jg/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1532, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sb81xl50jg/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1036, \"height\": 631, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sb81xl50jg/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1056, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sb81xl50jg/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1794, \"height\": 624, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-sb81xl50jg/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1394, \"height\": 343, \"label\": \"Table\"}]"
motivation: 现有方法难以同时提升LLM的训练和推理效率，存在权衡。
method: 在微调早期动态添加显著参数并剪枝不重要的参数，实现联合优化。
result: 在多个任务上训练和推理效率均优于基线，且性能相当。
conclusion: APT通过自适应机制有效平衡训练与推理效率。
---

## Abstract
Fine-tuning and inference with large Language Models (LM) are generally known to be expensive. Parameter-efficient fine-tuning over pretrained LMs reduces training memory by updating a small number of LM parameters but does not improve inference efficiency. Structured pruning improves LM inference efficiency by removing consistent parameter blocks, yet often increases training memory and time. To improve both training and inference efficiency, we introduce APT that adaptively *prunes* and *tunes* parameters for the LMs. At the early stage of fine-tuning, APT dynamically adds *salient* tuning parameters for fast and accurate convergence while discarding unimportant parameters for efficiency. Compared to baselines, our experiments show that APT maintains up to 98% task performance when pruning RoBERTa and T5 models with 40% parameters left while keeping 86.4% LLaMA models' performance with 70% parameters remaining. Furthermore, APT speeds up LMs' fine-tuning by up to 8$\times$ and reduces large LMs' memory training footprint by up to 70%. Our code and models are publicly available at https://github.com/ROIM1998/APT.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，现根据您提供的论文内容，对其进行结构化、深入、客观的总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在微调和推理过程中的计算成本高昂。现有的参数高效微调方法（如 LoRA）能降低训练内存，但无法提升推理效率；而结构化剪枝虽能提升推理效率，却往往增加了训练时间和内存成本。如何同时提升 LLM 的训练效率和推理效率，是一个亟待解决的挑战。
- **研究动机**：预训练语言模型中的参数对于下游任务的重要性不同。基于此，论文提出应在微调早期阶段动态地移除与下游任务无关的参数，这既能提升训练和推理效率，又不会严重损害模型性能。同时，通过动态添加重要的微调参数，可以弥补因剪枝带来的性能损失。
- **整体含义**：论文旨在打破“提升训练效率”与“提升推理效率”之间的权衡，提出一个统一的框架，使模型在训练和推理两个阶段都能实现高效，从而让 LLM 在资源受限的场景下更易于应用。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出 **APT（Adaptive Pruning and Tuning）** 方法，在微调早期阶段，通过一个名为 **APT adapter** 的模块，动态识别 LM 参数的重要性，对不重要的参数进行结构化剪枝（提升效率），同时对重要的微调层动态添加参数（提升性能），从而实现训练和推理效率的联合优化。
- **关键技术细节**：
    1.  **APT Adapter 架构**：基于 LoRA 结构，但引入了二进制剪枝掩码（`mi`, `mo`）和动态秩（`rapt`）。剪枝掩码控制哪些原始模型参数被冻结/剪除，动态秩控制可调（tuning）参数的数量。公式为： `Hapt(X) = mo ◦ (W + s * WB * WA)X ◦ mi`。
    2.  **低成本的适应性剪枝 (AP)**：
        - **离群点感知显著性评分**：计算参数块的显著性分数。不仅考虑了权重的梯度乘积，还引入了激活的峰度（kurtosis）来保留重要的离群参数，从而提升剪枝准确性。公式通过结合压缩后的激活-梯度乘积和激活峰度来计算。
        - **高效搜索**：将寻找要剪枝的块（注意力头、FFN 神经元、隐藏维度）问题形式化为一个延迟-显著性背包问题，通过按显著性密度排序和二分搜索来高效确定要保留的块。
    3.  **自适应且高效的调优 (AT)**：
        - 计算每个 APT adapter 的显著性（基于其内部参数 `WB` 的显著性之和）。
        - 动态地向更显著的 APT adapter 添加微调参数，即增加其秩 `rapt`。新添加的参数采用零初始化（`WB`）和随机高斯初始化（`WA`），以保证添加参数前后输出不变。
    4.  **高效自知识蒸馏**：
        - 为避免传统知识蒸馏需要加载一个完整的教师模型带来的巨大成本，APT 采用自蒸馏策略。
        - 学生模型（即被剪枝的模型）的微调层被复制一份作为教师模型。学生和教师模型共享模型的冻结参数，显著降低了训练内存和时长。蒸馏损失结合了 CoFi 的逐层蒸馏（`Llayer`）和监督微调损失（`Lft`）。

### 3. 实验设计：数据集、基准和对比方法

- **数据集**：
    - **小模型**：在 GLUE 基准（SST-2, MNLI, QQP, QNLI, CoLA, MRPC, RTE, STS-B）上进行理解和分类任务；SQuAD v2.0 用于问答任务；CNN/DM 用于摘要任务。
    - **大模型**：使用 GPT-4 生成的 Alpaca 数据集进行指令微调。
- **模型基准**：
    - BERT (基础版), RoBERTa (基础版), T5 (基础版), LLaMA-2 (7B 和 13B)。
- **对比方法**：
    - **基线方法**：全参数微调（FT）、LoRA 微调。
    - **剪枝方法**：LoRA+Prune（后训练剪枝）、Prune+Distill (CoFi)、LoRA+Prune+Distill。
    - **其他 SOTA 方法**：LLMPruner (针对 LLaMA 的任务无关剪枝)、PST (参数高效非结构化剪枝)、LRP (参数高效结构化剪枝)。

### 4. 资源与算力

- 论文明确说明，所有训练和评估工作均在**一块 NVIDIA A100 GPU** 上完成。
- 文章未明确说明具体训练时长，但提供了相对指标，如“时间-准确率”（TTA），例如在小模型上，APT 相比全微调加速了约 8 倍。对于大模型，训练时长通过每个 epoch 的时间来体现。
- **峰值内存**：论文详细报告了训练和推理的峰值内存，例如在裁剪 RoBERTa 时，APT 的训练内存仅为全微调的 70.1%；在裁剪 LLaMA-2 7B 时，仅为 LoRA 微调的 75.8%。

### 5. 实验数量与充分性

- **实验数量**：实验非常充分。涵盖了从 110M 参数（BERT/RoBERTa）到 13B 参数（LLaMA-2）的多种模型规模；包括分类、问答、摘要、指令跟随等多种任务类型；详细对比了多种基线方法和 SOTA 方法。
- **充分性判断**：实验设计合理且全面。
    - **公平性**：论文为所有对比方法设定了相同的剪枝稀疏度（如60%，30%），并尽量统一了超参数设置，如前文所述“没有进行任何超参数搜索以确保公平比较”。
    - **客观性**：除了主实验，还进行了：
        - **稀疏度分析**：图 3 展示了不同剪枝稀疏度下性能与推理效率的帕累托前沿。
        - **消融实验**：详细分析了“自适应剪枝”、“自适应调优”、“离群点感知显著性”、“自蒸馏”等每个核心组件的贡献（表 4, 5）。
        - **适应调优策略分析**：探究了初始秩和初始稀疏度的影响（图 5a, 5b）。
        - **蒸馏策略对比**：与传统的全模型教师蒸馏、LoRA 教师蒸馏进行了对比（表 10）。
- **结论**：总体来看，实验数量充足、设计严谨、对比客观，有力支撑了论文的结论。

### 6. 论文的主要结论与发现

- **效率与性能的平衡**：APT 成功实现了在几乎不损失任务性能的情况下，显著提升训练和推理效率的目标。
- **训练效率**：在裁剪 RoBERTa 和 T5 模型时，APT 的训练速度（达到 97% 全微调性能所需时间）比 LoRA+Prune 基线快 **8 倍以上**。在裁剪 LLaMA-2 7B 时，训练内存比全参数微调减少了 **70%**。
- **推理效率**：在保留 40% 参数的情况下，RoBERTa 和 T5 模型仍能保持高达 **98%** 的任务性能，并实现最高 2.4 倍的推理加速。LLaMA-2 7B 在保留 70% 参数时，保持了 **86.4%** 的平均性能。
- **性能恢复能力**：通过自适应调优和自蒸馏，APT 能显著恢复剪枝后模型的性能，效果优于简单的剪枝+重训练或剪枝+LoRA 组合。

### 7. 优点：方法或实验设计上的亮点

- **方法的创新性**：首次提出在微调 **早期** 同时进行“自适应剪枝”和“自适应调优”的范式，巧妙地平衡了训练效率、推理效率和模型性能，避免了以往方法的权衡。
- **核心技术的实用性**：
    - **离群点感知显著性**：考虑了离群参数的影响，使剪枝更精准，尤其对大模型有效。
    - **自蒸馏技术**：通过共享大部分参数来创建师生模型，非常实用，大幅降低了传统知识蒸馏带来的额外训练开销。
- **实验设计的全面性**：覆盖了从基础模型到主流大模型、多种任务类型的广泛评估，并且进行了详尽的消融和分析实验，结论可靠。

### 8. 不足与局限

- **性能差距**：在 LLaMA 等大模型上的性能恢复（86.4%）仍不及小模型上的表现（98%），尤其是在不使用蒸馏的情况下，这表明在极低资源场景下仍有改进空间。
- **推理速度提升有限**：虽然提升了，但提升幅度在某些硬件上可能未达到理论最大值（论文指出，因为 Ampere 架构 GPU 对维度有对齐要求）。
- **训练的不稳定性**：在微调过程中动态改变参数形状（增/减秩和剪枝）可能导致训练不稳定，为此不得不重置优化器状态。
- **知识蒸馏的额外成本**：尽管有了“自蒸馏”，但在小模型实验中，使用蒸馏仍会**增加** 22.5% 的训练时间和 11.7% 的训练内存，对于计算资源极度紧张的场景，这是一个权衡。
- **Adapter 选择范围**：论文仅探索了基于 LoRA 的 APT Adapter，对于其他类型的 PEFT 方法（如 Prefix-tuning）的适用性有待验证。

（完）
