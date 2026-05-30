---
title: "SparQ Attention: Bandwidth-Efficient LLM Inference"
title_zh: SparQ注意力：带宽高效的大语言模型推理
authors: "Luka Ribar, Ivan Chelombiev, Luke Hudlass-Galley, Charlie Blake, Carlo Luschi, Douglas Orr"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=OS5dqxmmtl"
tags: ["query:edge-llm"]
score: 8.0
evidence: 带宽高效注意力，节省内存带宽
tldr: LLM推理中注意力层的内存带宽是瓶颈。本文提出SparQ Attention，通过选择性获取缓存历史，在保持准确率的同时将注意力数据传输减少8倍。该方法无需预训练修改或微调，可直接用于现有模型。实验表明显著提升推理吞吐量。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 804, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 760, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 752, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1758, \"height\": 971, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 687, \"height\": 1043, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 850, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 837, \"height\": 281, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 836, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 840, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 850, \"height\": 442, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1637, \"height\": 1985, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1078, \"height\": 1970, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1640, \"height\": 1987, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1330, \"height\": 1950, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1662, \"height\": 645, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1648, \"height\": 654, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1548, \"height\": 1204, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 787, \"height\": 574, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-os5dqxmmtl/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1018, \"height\": 582, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-os5dqxmmtl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 797, \"height\": 150, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-os5dqxmmtl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1762, \"height\": 742, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-os5dqxmmtl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 849, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-os5dqxmmtl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 857, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-os5dqxmmtl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1013, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-os5dqxmmtl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1250, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-os5dqxmmtl/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1363, \"height\": 1212, \"label\": \"Table\"}]"
motivation: 注意力层内存带宽瓶颈限制了LLM推理吞吐量。
method: 设计选择性获取缓存历史的注意力机制，减少数据传输量。
result: 注意力数据传输减少8倍，推理吞吐量提升。
conclusion: SparQ Attention是一种通用、高效的LLM推理加速技术。
---

## Abstract
The computational difficulties of large language model (LLM) inference remain a significant obstacle to their widespread deployment. The need for many applications to support long input sequences and process them in large batches typically causes token-generation to be bottlenecked by data transfer. For this reason, we introduce **SparQ Attention**, a technique for increasing the inference throughput of LLMs by utilising memory bandwidth more efficiently within the attention layers, through selective fetching of the cached history. Our proposed technique can be applied directly to off-the-shelf LLMs during inference, without requiring any modification to the pre-training setup or additional fine-tuning. We show that SparQ Attention brings up to 8x savings in attention data transfers without substantial drops in accuracy, by evaluating Llama 2 and 3, Mistral, Gemma and Pythia models on a wide range of downstream tasks.

---

## 论文详细总结（自动生成）

# 论文总结：SparQ Attention: Bandwidth-Efficient LLM Inference

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）推理中，自回归生成需要每步都从内存加载完整的键值（KV）缓存，这随着序列长度和批处理规模的增加成为严重的内存带宽瓶颈。尽管现代硬件算力强大，但实际推理速度受限于数据传输而非计算（memory bandwidth bound）。
- **整体含义**：本文提出SparQ Attention，一种无需修改预训练或微调即可直接应用于现有LLM的注意力机制优化技术。通过对注意力层的KV缓存进行选择性获取，大幅减少内存数据传输量（最高可达8倍），从而显著提升推理吞吐量，同时保持任务准确率几乎不变。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：利用注意力自然存在的稀疏性（只有少数token获得高注意力权重），通过两步近似来减少数据读取：
  1. 只用查询向量（query）的部分重要分量（top-r）与所有键（keys）计算近似注意力分数，从而只读取键缓存的部分列。
  2. 基于近似分数选出top-k的token，然后只获取这些token的完整键和值，计算最终注意力输出。
- **关键技术细节**：
  - **查询向量稀疏性**：实验发现查询向量的分量呈重尾分布（leptokurtic），因此选取绝对值最大的r个分量即可近似注意力分数。
  - **均值重新分配**：维护一个运行均值值向量$\bar{v}$，用近似注意力分数对top-k的得分进行加权，然后与$\bar{v}$插值，补偿未选中token的贡献。
  - **自适应温度调节**：软max温度采用$\tau = \sqrt{d_h \cdot \|q \circ m_q\|_1 / \|q\|_1}$，平衡极端情况。
  - **针对GQA的适配**：对分组查询注意力（GQA）模型，先按组内求和查询绝对值再选top-r，求和近似分数再选top-k。
- **算法流程**（文字描述）：
  1. 对每个注意力头，计算查询向量绝对值的top-r索引，只从键缓存中读取这些行的分量，得到近似注意力分数$\hat{s}$。
  2. 在$\hat{s}$上取top-k位置，获取这些位置的完整键和值。
  3. 用$\hat{s}$中top-k的权重和$\alpha$作为插值因子，将top-k注意力输出与均值值向量混合，得到最终输出。
- **数据传输节省**：对于单个注意力头，每次前向传输量为$S r + 2k d_h + 4 d_h$，而密集基线为$2S d_h + 2 d_h$。通过调节r和k可控制压缩比。

## 3. 实验设计

- **数据集与场景**：
  - **SQuAD**（1-shot问答）：通过添加无关上下文增加序列长度（4k-8k字符约1k-2k tokens）。
  - **TriviaQA**（0-shot问答）：类似构造。
  - **CNN/DailyMail**（0-shot摘要）：ROUGE-L评估。
  - **WikiText-103**（语言建模）：以bits per character (BPC)评估。
  - **Text Repetition**（人工构造）：要求模型从上下文中逐字重复句子，评估精确检索能力。
  - **Needle in a Haystack**（长序列检索）：在32k序列中插入“针”，测试检索能力。
  - **序列长度缩放实验**：使用Vicuna模型（基于Llama 2微调以适应16k最大长度），通过增加混淆上下文来延伸序列（达128k）。
- **Benchmark与对比方法**：
  - 对比方法：**H2O**（缓存驱逐策略）、**LM-Infinite**（固定局部窗口+初始token）、**FlexGen**（基于精确注意力分数的top-k值获取，理论下限1/2压缩）。
  - 每个方法基于固定KV缓存传输预算（k）进行对比。
- **模型**：Llama 2 (7B, 13B)、Llama 3 (8B)、Mistral (7B)、Gemma (7B)、Pythia (1.4B, 2.8B, 6.9B)，共8个模型。

## 4. 资源与算力

- 论文中未明确说明完整实验所需的GPU型号、数量及总训练时长。仅提及在IPU（Graphcore Bow Pod 16）和GPU（A100 40GB、A10G）上进行了微基准性能测试，但未给出完整实验的算力统计。因此，无法精确评估训练/推理资源消耗。

## 5. 实验数量与充分性

- **实验数量**：
  - 主要实验：在5个数据集 × 8个模型（共40组），每组覆盖压缩比1/2、1/4、1/8（部分还包含1/16）。
  - 消融实验：含键缓存压缩对比（与Oracle、随机低秩投影对比）、软max温度选择（多种变体）、超参数k和r的网格扫描。
  - 序列长度缩放实验：两种长序列任务（SQuAD扩展、Needle in a Haystack）跨越8k-128k长度。
  - 微基准性能测试：在IPU和GPU上测量延迟与加速比，涵盖多种batch size和序列长度。
- **充分性与客观公平**：
  - 覆盖多模型家族、多种下游任务（问答、摘要、语言建模、精确检索）。
  - 对比了三种主流的稀疏/缓存策略方法，且对H2O与官方实现做了交叉验证。
  - 消融实验系统，验证了每个设计选择的必要性。
  - 微基准测试显示理论加速在实际硬件中可达到（近7.4x加速）。
  - 不足之处：未在更大规模（如70B模型）或更多样化任务（如代码生成、多轮对话）上验证；Needle in a Haystack任务仅测试了Llama 2变体；对比方法中FlexGen压缩比有限（>=1/2），而SparQ突破了此限制。

## 6. 主要结论与发现

- SparQ Attention在压缩比1/2到1/8范围内，几乎所有任务上表现与密集基线持平或仅有极微小下降，而H2O和LM-Infinite在部分任务（如SQuAD、文本重复）上出现显著下降。
- 对GQA模型（Llama 3, Mistral），未使用均值重新分配步骤仍获得良好结果。
- 超参数选择简单：建议固定k=128，调节r以平衡压缩比和性能。
- 微基准测试显示，在IPU上接近理论加速（7.41x），在GPU上可达3-4x加速（受数据量影响）。
- 与缓存驱逐策略相比，SparQ Attention保留完整的KV缓存，避免了永久信息丢失，因此在需要从长上下文中精确检索信息的任务中表现更稳健。

## 7. 优点

- 无需额外训练或微调：可直接应用于任何预训练LLM，实用性强。
- 理论分析扎实：从算术强度、注意力稀疏性、查询重尾分布等多角度推导，设计有据。
- 方法简洁高效：两步近似结合均值重分配，在极低计算开销下实现大幅带宽节省。
- 鲁棒性强：跨模型家族（Llama、Mistral、Gemma、Pythia）和多种任务表现一致。
- 性能提升显著：在带宽受限的硬件（IPU）上几乎获得理论加速，GPU上也有实际收益。
- 论文实验全面，消融分析充分，包括超参数选择、温度、Oracle对比等。

## 8. 不足与局限

- **实验覆盖有限**：最大模型仅13B（Llama 2 13B），未在更大模型（如70B、175B）上验证。长序列实验仅使用Vicuna 7B，且需RoPE缩放。
- **未涉及多轮对话、代码生成等场景**：这些任务可能对稀疏注意力更敏感。
- **硬件微基准存在局限性**：在GPU上小batch size下加速不明显，需进一步融合kernel才能发挥潜力。存储两次K（S-major和dh-major）增加了50%内存使用。
- **对比方法强度不均衡**：FlexGen压缩比有下限1/2，无法在更高压缩下对比；H2O和LM-Infinite在某些任务上表现不佳，但SparQ未与更新方法（如StreamingLLM、Scissorhands）对比。
- **缺少理论保证**：虽实验显示近似准确，但未提供严格的近似误差界。
- **偏差风险**：任务构造（如SQuAD混淆上下文）可能偏向于SparQ的假设（注意力稀疏），在自然长上下文任务中表现可能不同。

（完）
