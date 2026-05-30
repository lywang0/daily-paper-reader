---
title: Accurate LoRA-Finetuning Quantization of LLMs via Information Retention
title_zh: 通过信息保留实现准确的LoRA微调量化大语言模型
authors: "Haotong Qin, Xudong Ma, Xingyu Zheng, Xiaoyang Li, Yang Zhang, Shouda Liu, Jie Luo, Xianglong Liu, Michele Magno"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=jQ92egz5Ym"
tags: ["query:edge-llm"]
score: 8.0
evidence: 面向资源受限硬件的量化与LoRA微调
tldr: 针对LoRA微调量化导致模型性能严重下降的问题，本文提出IR-QLoRA，通过信息校准量化和弹性连接两大技术保留信息。统计校准量化使量化参数准确保留原始信息，基于微调的弹性连接使LoRA能利用弹性表示变换。实验表明在低比特量化下仍保持高精度。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-jq92egz5ym/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1771, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jq92egz5ym/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 842, \"height\": 1085, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jq92egz5ym/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 824, \"height\": 1350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jq92egz5ym/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 847, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-jq92egz5ym/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1732, \"height\": 1099, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 859, \"height\": 1340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 858, \"height\": 1259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 882, \"height\": 705, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 870, \"height\": 466, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 877, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 877, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1757, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1771, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 881, \"height\": 1028, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 866, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1760, \"height\": 196, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1757, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1775, \"height\": 455, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1781, \"height\": 1431, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1730, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-jq92egz5ym/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1778, \"height\": 2324, \"label\": \"Table\"}]"
motivation: 现有量化方法使LoRA微调失效，模型准确率下降。
method: 提出信息校准量化和信息弹性连接，从统一信息视角保留模型信息。
result: 在低比特量化下，IR-QLoRA显著优于现有方法。
conclusion: IR-QLoRA使量化LLM能有效利用LoRA微调，适合部署。
---

## Abstract
The LoRA-finetuning quantization of LLMs has been extensively studied to obtain accurate yet compact LLMs for deployment on resource-constrained hardware. However, existing methods cause the quantized LLM to severely degrade and even fail to benefit from the finetuning of LoRA. This paper proposes a novel IR-QLoRA for pushing quantized LLMs with LoRA to be highly accurate through information retention. The proposed IR-QLoRA mainly relies on two technologies derived from the perspective of unified information: (1) statistics-based Information Calibration Quantization allows the quantized parameters of LLM to retain original information accurately; (2) finetuning-based Information Elastic Connection makes LoRA utilizes elastic representation transformation with diverse information. Comprehensive experiments show that IR-QLoRA can significantly improve accuracy across LLaMA and LLaMA2 families under 2-4 bit-widths, e.g., 4-bit LLaMA-7B achieves 1.4% improvement on MMLU compared with the state-of-the-art methods. The significant performance gain requires only a tiny 0.31% additional time consumption, revealing the satisfactory efficiency of our IR-QLoRA. We highlight that IR-QLoRA enjoys excellent versatility, compatible with various frameworks (e.g., NormalFloat and Integer quantization) and brings general accuracy gains. The code is available at https://github.com/htqin/ir-qlora .

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

大语言模型（LLMs）在自然语言理解任务中表现卓越，但其巨大的参数规模和计算需求使得在资源受限硬件（如边缘设备）上的部署面临严峻挑战。量化是一种有效的压缩手段，但低比特量化会导致显著的精度退化。LoRA（低秩适配）微调与量化相结合（即LoRA微调量化）成为一种流行的范式，旨在以较低资源消耗恢复量化模型的性能。然而，现有方法（如QLoRA、QA-LoRA）存在严重问题：量化导致的信息损失无法被LoRA有效恢复，尤其是在极低比特（≤3bit）和大模型规模（≥30B）下，模型性能严重下降，甚至LoRA微调后仍无法达到原始模型的精度。例如，4比特LLaMA-30B在MMLU上的精度（57.7%）低于原始未微调模型（58.2%）。因此，本文提出IR-QLoRA，旨在通过信息保留来提升量化LLM的精度。

## 2. 方法论

### 核心思想
从统一信息论视角出发，针对量化过程的信息损失和LoRA表示能力不足两个问题，分别提出两种技术：
- **信息校准量化（ICQ）**：通过最大化量化权重的信息熵，使量化后的参数保留原始权重中的信息。
- **信息弹性连接（IEC）**：引入无参数弹性变换，增强LoRA对原始特征信息的利用，多样化其表示形式。

### 关键技术细节

#### 2.1 信息校准量化（ICQ）
- **问题分析**：量化后权重可取值数量大幅减少（如4bit只有16个值），导致信息熵急剧下降。互信息I(ŵ; w) = H(ŵ) - H(ŵ|w)，对于确定性量化，H(ŵ|w)=0，因此最大化互信息等价于最大化H(ŵ)。
- **方法**：
  - 引入校准常数τ，修改量化公式：ŵ = NF_k((w - τ)/s)。
  - **初始化**：τ₀ = 权重中位数（基于正态分布的对称性）。
  - **优化**：在区间[τ₀ - λσ, τ₀ + λσ]内线性搜索（λ=0.1，n=100个候选），选择使熵最大的τ*。
  - 对τ和缩放因子s进行双重量化以节省存储。
  - 推理时：y' = x * (ŵ * dequant(s) + dequant(τ))。

#### 2.2 信息弹性连接（IEC）
- **问题分析**：LoRA的表示能力受限于低秩矩阵，且后一矩阵无法直接访问原始输入特征。
- **方法**：
  - 在LoRA的两个子单元（U1和U2）中分别添加参数无连接：
    - U1(x) = xℓ₁ + β₁ * repeat(mean_over_gcd_groups(x))
    - U2(x') = x'ℓ₂ + β₂ * repeat(x'_mean_groups)
  - β为可学习标量，通道分组与重复确保维度匹配。
  - 这些操作可合并到LoRA矩阵中，不增加推理开销。
  - 最终输出：y = y' + α * U2(U1(x))。

## 3. 实验设计

### 数据集
- **微调数据集**：Alpaca（52K指令数据）、Flan v2（1836个任务的合集）。
- **评估基准**：
  - MMLU（57个语言任务，5-shot）
  - CommonsenseQA（HellaSwag、PIQA、WinoGrande、ARC-e、ARC-c、BoolQ、OBQA，0-shot）

### 对比方法
- QLoRA、QA-LoRA、PEQA、QLoRA w/ GPTQ、NormalFloat量化等。
- 模型系列：LLaMA（7B/13B/30B/65B）、LLaMA2（7B/13B）。

### 实验设置
- 使用Nvidia Tesla A100 GPU，batch size 16，训练步数：Alpaca上10,000步，Flan v2上20,000步。
- LoRA参数：r=64，α=16，dropout 0.1（≤13B）或0.05（≥30B）。
- 优化器：paged AdamW，学习率2e-4（≤13B）或1e-4（≥30B），梯度裁剪0.3。

## 4. 资源与算力

论文明确说明所有实验在Nvidia Tesla A100 GPU上进行，但未具体说明使用的GPU数量。训练时长在消融实验中给出：对于LLaMA-7B，原始训练时间15.40小时，IR-QLoRA仅增加0.07小时（0.46%）；LLaMA-13B增加0.08小时（0.31%）；LLaMA-30B增加0.36小时；LLaMA-65B增加0.41小时。总体额外时间开销极小。

## 5. 实验数量与充分性

论文进行了大量实验，涵盖：
- **主实验结果**：在MMLU上的5-shot精度，覆盖LLaMA 7B/13B/30B/65B和LLaMA2 7B/13B，对比4种以上方法，包括NormalFloat、QLoRA、QA-LoRA等（见表1、2、3）。
- **极低比特实验**：2bit和3bit量化（表9）。
- **整数量化变体**：将ICQ/IEC集成到QA-LoRA框架中（表10）。
- **消融实验**：分别评估ICQ和IEC的贡献，包括对ICQ单独（无LoRA）、IEC子单元U1/U2的消融（表4、5），以及熵的量化验证（图4）。
- **效率消融**：参数量和训练时间对比（表6、7）。
- **CommonsenseQA基准**：0-shot结果（表8）。
- **案例分析**：文本生成案例对比（表16）。

这些实验覆盖了不同模型规模、不同比特宽度、不同微调数据集、不同量化框架，消融实验充分，对比方法全面，实验设计较为客观公平。

## 6. 主要结论与发现

- IR-QLoRA在所有设置下均显著优于现有SOTA方法。例如，4-bit LLaMA-7B在MMLU上比QLoRA高2.4%（38.4%→40.8%），比QA-LoRA高1.4%。
- 在极低比特（2-3bit）下优势更明显：2-bit LLaMA-7B在Flan v2微调后MMLU平均33.7%，仅比16bit低0.9%，而基线QLoRA仅33.5%。
- IEC和ICQ的协同效果超过单独使用，证明两者互补。
- ICQ能有效提高量化权重的信息熵（平均增加0.07），且无需微调即可提升精度。
- IEC引入的参数极少，可合并到LoRA中，不增加推理成本。
- IR-QLoRA具有良好的通用性，可无缝集成到不同量化框架（如NormalFloat和Integer量化）中。

## 7. 优点

- **创新性**：从信息论角度系统分析量化信息损失，提出直接最大化熵的校准方法，以及增强LoRA表示能力的弹性连接，思路新颖。
- **高效性**：额外计算开销极小（0.31%训练时间、少量存储），推理无额外成本。
- **通用性**：兼容多种量化框架（NF4、整数量化），可在QLoRA、QA-LoRA等基础上直接改进。
- **实验充分**：覆盖多个模型族、多比特宽度、多数据集、多基线，消融完善。
- **实际意义**：使量化LLM能有效利用LoRA微调，显著降低部署门槛。

## 8. 不足与局限

- **实验覆盖**：仅评估了LLaMA和LLaMA2系列，未涉及其他主流LLM（如GPT、PaLM、Falcon等），通用性可能受限。
- **场景局限**：主要评估语言理解（MMLU）和常识推理（CommonsenseQA），未涉及生成任务（如翻译、摘要）、指令跟随等更广泛场景。
- **偏差风险**：校准常数的搜索区间（λσ）和经验参数（λ=0.1, n=100）可能无法保证对所有模型/层最优，存在过拟合风险。
- **硬件依赖**：实验基于A100，未在更受限的边缘设备上验证实际部署性能。
- **缺失完整消融**：未详细讨论不同搜索区间大小对精度的影响，也未对比其他熵最大化方法（如直方图均衡化）。
- **可复现性**：虽然开源代码，但训练超参数（如学习率、优化器设置）与基线完全一致，缺乏对敏感性的分析。

（完）
