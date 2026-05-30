---
title: "QuantSpec: Self-Speculative Decoding with Hierarchical Quantized KV Cache"
title_zh: "QuantSpec: 基于分层量化KV缓存的自推测解码"
authors: "Rishabh Tiwari, Haocheng Xi, Aditya Tomar, Coleman Richard Charles Hooper, Sehoon Kim, Maxwell Horton, Mahyar Najibi, Michael W. Mahoney, Kurt Keutzer, Amir Gholami"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=7SHbJENgHX"
tags: ["query:edge-llm"]
score: 9.0
evidence: 面向边缘设备LLM推理的自推测解码与量化KV缓存
tldr: QuantSpec提出了一种自推测解码框架，结合分层量化KV缓存，专为边缘设备上的长上下文LLM推理设计。草稿模型共享目标模型架构但使用量化KV缓存，降低了内存和延迟开销。实验表明，该方法在边缘设备上显著加速了推理，同时保持了生成质量，解决了长上下文场景中KV缓存成为瓶颈的问题。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1778, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1752, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1589, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 856, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1787, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1080, \"height\": 923, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1064, \"height\": 890, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-7shbjenghx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1064, \"height\": 714, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1782, \"height\": 883, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 765, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 693, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1669, \"height\": 583, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1666, \"height\": 535, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 861, \"height\": 273, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1497, \"height\": 1260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-7shbjenghx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1669, \"height\": 941, \"label\": \"Table\"}]"
motivation: 边缘设备上长上下文LLM推理中，KV缓存是主要瓶颈，现有推测解码方法速度提升有限。
method: 提出自推测解码框架，草稿模型与目标模型共享架构，但使用分层量化KV缓存以降低开销。
result: 在边缘设备上实现了显著的推理加速，同时保持生成质量。
conclusion: 通过量化KV缓存的自推测解码，有效提升了边缘设备上的LLM推理效率。
---

## Abstract
Large Language Models (LLMs) are increasingly being deployed on edge devices for long-context settings, creating a growing need for fast and efficient long-context inference. In these scenarios, the Key-Value (KV) cache is the primary bottleneck in terms of both GPU memory and latency, as the full KV cache must be loaded for each decoding step. While speculative decoding is a widely accepted technique to accelerate autoregressive decoding, existing methods often struggle to achieve significant speedups due to inefficient KV cache optimization strategies and result in low acceptance rates. To address these challenges, we propose a novel self-speculative decoding framework, QuantSpec, where the draft model shares the architecture of the target model but employs a hierarchical 4-bit quantized KV cache and 4-bit quantized weights for acceleration. QuantSpec maintains high acceptance rates ($>$90\%) and reliably provides consistent end-to-end speedups upto $\sim2.5\times$, outperforming other self-speculative decoding methods that use sparse KV cache for long-context LLM inference. QuantSpec also reduces the memory requirements by $\sim 1.3\times$ compared to these alternatives.

---

## 论文详细总结（自动生成）

# 论文总结：QuantSpec: Self-Speculative Decoding with Hierarchical Quantized KV Cache

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）在长上下文推理场景中，Key-Value（KV）缓存成为GPU内存和延迟的主要瓶颈。每个解码步骤都需要加载完整的KV缓存，导致效率低下。
- **现有方法不足**：推测解码（speculative decoding）虽能加速自回归解码，但传统方法（如使用稀疏KV缓存的自推测解码）存在接受率低、加速效果有限的问题，且往往需要维护两个模型各自的KV缓存，增加内存开销。
- **本文贡献**：提出QuantSpec——一种自推测解码框架，通过分层4-bit量化KV缓存和4-bit量化权重，同时优化草稿模型与目标模型的KV缓存共享，实现了高接受率（>90%）和最高约2.5倍端到端加速，同时减少约1.3倍内存需求。

## 2. 方法论：核心思想、关键技术细节与算法流程

- **核心思想**：自推测解码中，草稿模型与目标模型共享相同架构，但使用量化后的KV缓存和权重以降低带宽负载。QuantSpec通过层级量化使得草稿模型仅加载低精度部分，目标模型则利用完整精度，从而避免存储两份独立KV缓存。
- **关键技术细节**：
  - **分层量化KV缓存（Hierarchical KV Cache）**：将INT8 KV缓存分解为两个INT4分量（upper 4-bit和lower 4-bit）。草稿模型仅使用upper 4-bit（C₄ᴺᵁ），目标模型同时使用upper和lower以重构INT8（C₈ = 2⁴·C₄ᴺᵁ + C₄ᴺᴸ）。本质上是利用INT8 = INT4 + residual，从而消除冗余存储。
  - **双全精度缓存缓冲区（Double Full-Precision Buffer）**：为解决per-group量化与推测解码中频繁回退导致的重复量化/反量化开销，维护大小为2G（G为量化组大小）的全精度缓冲区，分为CF1和CF2两部分。仅在缓冲区满时（每G步一次）量化第一部分，并将第二部分移至第一部分，从而以极小开销支持灵活回退。
  - **量化策略**：对key cache沿通道轴（channel-wise）量化，对value cache沿token轴量化；均采用非对称量化、组大小为head dimension（128），以减少量化误差。
  - **权重量化**：草稿模型权重也采用4-bit量化，进一步减少加载权重时的内存带宽。
- **算法流程**（见于附录Algorithm 1）：
  1. **预填充阶段（Prefill）**：计算完整KV缓存，然后将早期token量化成分层缓存，最近G个token保留在全精度缓冲区。
  2. **解码阶段**：循环执行推测和验证。
     - 草稿模型使用上层4-bit缓存和全精度缓冲区生成γ个候选token。
     - 目标模型加载8-bit缓存（上层+下层）和全精度缓冲区，验证候选token，接受匹配的token，拒绝第一个不匹配的token并修正。
     - 若全精度缓冲区满，则量化CF1并追加到量化缓存，然后将CF2移至CF1。

## 3. 实验设计：数据集、场景、基准与对比方法

- **数据集**：
  - 语言建模：WikiText-2、C4、PG-19（长上下文书籍语料）。
  - 长上下文摘要：∞BENCH Sum（平均输入~171k tokens）、Multi-LexSum（平均~90k tokens）。
- **模型**：
  - 主要实验：Llama-2-7B-32K-Instruct、LWM-Text-Chat-128k。
  - 额外实验（附录I）：Mistral-7B-v0.3、Llama-3.1-8B。
- **基准方法**：
  - 自回归解码（Autoregressive baseline, AR）。
  - 基于稀疏KV的自推测解码：StreamingLLM（保留注意力池token）和SnapKV（保留重要token）。为保证公平，草稿KV预算设为原上下文长度的1/4（与QuantSpec的4-bit量化一致）。
- **评估指标**：接受率（%）、峰值GPU内存（GB）、相对于AR的加速比（×）。
- **场景**：上下文长度4k/8k/16k/32k/64k/128k，批量大小1（节省模式下），部分实验使用1或2块GPU。
- **超参数**：推测长度γ通过网格搜索（在8k长度上选取最优值），稀疏方法最优γ=1，QuantSpec最优γ通常为4或6。

## 4. 资源与算力

- **GPU型号与数量**：节点配备8块NVIDIA RTX A6000 GPU。报告中明确提及“所有实验在配备8×A6000的节点上执行”。
- **训练时长**：未明确说明训练（模型微调）时长，QuantSpec主要针对推理阶段优化，不涉及模型重训练。仅对预训练模型进行量化校准，但未提供具体耗时。
- **推理资源**：根据不同上下文长度和模型，使用1或2块GPU进行推理 benchmark。

## 5. 实验数量与充分性

- **实验组数**：
  - **主要对比实验**（Table 4）：涵盖2个模型、6种上下文长度×数据集组合，共14行（含稀疏基线）。
  - **消融实验**（Figure 5）：探究weight-only、KV-only、以及同时量化对加速比的影响，在不同上下文长度（4k-32k）下的趋势。
  - **核函数加速**（Table 5）：对比FlashAttention FP16与QuantSpec INT4/INT8内核的延迟，在64k和256k长度下。
  - **额外模型验证**（Appendix Table 7）：Mistral-7B和Llama-3.1-8B在16k/32k/128k下的结果。
  - **超参数搜索**（Appendix Table 6）：对每个数据集-方法对搜索最优γ。
  - **接受率随γ变化**（Figure 9）：展示QuantSpec优于稀疏方法的稳定性。
- **充分性评价**：实验设计较为全面，覆盖了主流长上下文模型、不同任务（语言建模、摘要）、多种长度，并提供了消融和内核加速数据。与稀疏基线在同一KV预算下对比，公平合理。但未测试更大规模模型（如70B），也未评测其他推测解码方法（如Medusa、Eagle）。

## 6. 主要结论与发现

- QuantSpec在所有测试上下文长度（4k–128k）上均实现优于稀疏KV基线的加速比，最高达2.49×（LWM-128k, Multi-LexSum），且内存减少约1.3×。
- 接受率稳定在90%以上，远高于稀疏方法（尤其在长摘要任务中）。随推测长度γ增加，QuantSpec接受率下降较慢，而稀疏方法急剧下降。
- 量化策略选择的指导原则：短上下文（4k）时，权重量化贡献主要加速；中等长度（8k–16k）时，权重和KV量化贡献相当；长上下文（>32k）时，KV量化主导加速。与理论分析（Section 3）一致。
- 自定义INT4注意力内核相比FP16 FlashAttention实现高达2.88×加速（256k长度），INT8内核也获得1.51×加速。

## 7. 优点：方法与实验设计的亮点

- **创新性**：
  - 首次提出层级量化KV缓存用于自推测解码，巧妙利用INT8分解为两个INT4，避免草稿模型额外存储。
  - 双全精度缓冲区设计解决了per-group量化与推测回退之间的效率冲突，仅每G步执行一次量化。
  - 结合权重量化与KV量化，根据不同上下文长度动态适应，实现端到端优化。
- **实验设计的亮点**：
  - 使用广义屋顶线模型（roofline model）分析推理瓶颈，从理论上指导量化策略选择，实验验证了理论预测。
  - 与稀疏KV基线在同一“四分之一KV预算”下比较，保证了公平性。
  - 提供了完整的超参数搜索和消融实验，明确各组件贡献。
  - 自定义CUDA内核并公开延迟数据，展示了底层优化效果。

## 8. 不足与局限

- **实验覆盖范围有限**：仅测试了7B/8B参数量的模型，未对更大规模模型（如13B、70B或融合MoE）进行评估。这些模型的KV缓存更大，QuantSpec的加速优势是否保持尚需验证。
- **未与更多推测解码方法比较**：仅对比了稀疏KV的自推测解码，未与其他常见的推测解码（如Medusa、Eagle、Big Little Decoder等）或基于预测的方法比较。
- **硬件单一性**：所有实验在NVIDIA A6000 GPU上进行，未在更广泛的边缘设备（如Jetson、手机SoC）或不同架构（如AMD、Apple Silicon）上测试，结论的泛化性存在局限。
- **性能与精度的权衡**：虽然论文声称perplexity几乎无下降（Table 2），但仅检验了INT8目标模型；INT4草稿模型是否在某些敏感任务上引入更多偏差未充分讨论。量化误差可能对生成质量有细微影响，尤其需要长程依赖的推理任务。
- **实际部署延展性**：双全精度缓冲区需要保证草稿模型推理时能快速访问上层4-bit缓存，对内存控制器和并行计算有特殊要求，实际工程实现复杂度较高。
- **超参数依赖**：推测长度γ需针对每个数据集进行搜索，虽然论文给出指导，但在动态变化的应用场景中可能不够鲁棒。

（完）
