---
title: "Oracle-MoE: Locality-preserving Routing in the Oracle Space for Memory-constrained Large Language Model Inference"
title_zh: Oracle-MoE：内存受限大语言模型推理中oracle空间的局部保持路由
authors: "Jixian Zhou, Fang Dong, Ruijun Huang, Hengjie Cao, Mengyi Chen, Yifeng Yang, Anrui Chen, Mingzhi Dong, Yujiang Wang, Dongsheng Li, David A. Clifton, Qin Lv, Rui Zhu, Chun Zhang, Fan Yang, Tun Lu, Ning Gu, Li Shang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=wn6WHREK9k"
tags: ["query:edge-llm"]
score: 9.0
evidence: 面向内存受限边缘设备的MoE架构
tldr: 针对MoE模型在内存受限边缘设备上专家频繁交换导致延迟高的问题，提出Oracle-MoE架构。通过在oracle空间中保持局部性的路由机制，减少专家交换次数，使MoE真正发挥只需少量激活专家的优势。实验表明在边缘设备上推理延迟显著降低，内存占用符合限制。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 822, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 863, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 821, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 813, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 839, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1649, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1744, \"height\": 323, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 862, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 434, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 870, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 871, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1320, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1377, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1320, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1381, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1337, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1388, \"height\": 275, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1329, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wn6whrek9k/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1383, \"height\": 289, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-wn6whrek9k/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1663, \"height\": 510, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wn6whrek9k/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 690, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wn6whrek9k/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1283, \"height\": 663, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wn6whrek9k/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1060, \"height\": 274, \"label\": \"Table\"}]"
motivation: 现有MoE在边缘设备上专家交换频繁导致延迟不可接受。
method: 提出Oracle-MoE，在oracle空间中设计保持局部性的路由策略。
result: 显著降低边缘设备上MoE推理延迟，满足内存限制。
conclusion: Oracle-MoE解除了MoE在边缘部署的瓶颈，实现高效推理。
---

## Abstract
Mixture-of-Experts (MoE) is widely adopted to deploy Large Language Models (LLMs) on edge devices with limited memory budgets.
Although MoE is, in theory, an inborn memory-friendly architecture requiring only a few activated experts to reside in the memory for inference, current MoE architectures cannot effectively fulfill this advantage and will yield intolerable inference latencies of LLMs on memory-constrained devices. 
Our investigation pinpoints the essential cause as the remarkable temporal inconsistencies of inter-token expert activations, which generate overly frequent expert swapping demands dominating the latencies. 
To this end, we propose a novel MoE architecture, Oracle-MoE, to 
fulfill the real on-device potential of MoE-based LLMs. 
Oracle-MoE route tokens in a highly compact space suggested by attention scores, termed the *oracle space*, to effectively maintain the semantic locality across consecutive tokens to reduce expert activation variations, eliminating massive swapping demands. 
Theoretical analysis proves that Oracle-MoE is bound to provide routing decisions with better semantic locality and, therefore, better expert activation consistencies. 
Experiments on the pretrained GPT-2 architectures of different sizes (200M, 350M, 790M, and 2B) and downstream tasks demonstrate that without compromising task performance, our Oracle-MoE has achieved state-of-the-art inference speeds across varying memory budgets, revealing its substantial potential for LLM deployments in industry.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：混合专家（MoE）模型在理论上具有内存友好特性（推理时仅需加载少量激活专家），但在实际部署到内存受限的边缘设备（如手机、嵌入式GPU）时，因token级路由导致的**专家激活在连续token间高度不一致**，引发频繁的专家交换（swapping）操作，产生高达全内存推理15～30倍的延迟，其中50%～85%的延迟来自I/O开销。
- **研究意义**：填补MoE架构在边缘部署中“理论优势无法兑现”的空白，提出一种**从根本上减少专家交换需求**的架构，使MoE真正成为边缘设备上LLM部署的可行方案。

## 2. 方法论：核心思想、关键技术细节与公式
- **核心思想**：利用自然语言中连续token的**语义局部性**（相邻token语义相似），设计一种新的路由机制，使连续token倾向于激活相同的专家，从而大幅降低专家激活变化（Consecutive Semantic Difference, CSD），减少交换次数。
- **关键技术细节**：
  1. **语义组（Semantic Group）**：基于注意力分数矩阵（仅考虑下三角，即当前token与之前token的注意力）定义连通子图：若token tᵢ和tⱼ（i>j）的注意力分数大于阈值ε，且该组内所有token两两之间注意力均大于ε，则构成一个语义组。该定义可通过贪心算法高效求解。
  2. **Oracle空间构建**：每个语义组的组嵌入定义为该组内所有token嵌入的平均值（平均操作可降低token特有噪声，保留高阶语义）。收集所有语义组嵌入构成**oracle空间**，并通过SVD降维以提高计算效率。
  3. **路由机制**：
     - 训练阶段：在oracle空间中对语义组嵌入进行K-means聚类（聚类数等于专家数），每个token根据其所在语义组的聚类中心分配专家。
     - 推理阶段：自回归生成时，新token首先判断所属语义组（利用KV cache中的注意力分数），更新该组嵌入，然后路由到对应聚类中心的专家。
     - 公式：路由目标为 \( e_t = \arg\min_k \|z_{S(t)} - c_k\| \)，其中\( z_{S(t)} \)为语义组嵌入，\( c_k \)为聚类中心。
  4. **理论分析**：定义CSD（连续token专家集差异），证明在身份嵌入维度足够高时，oracle路由的CSD严格小于token级路由（Theorem 1）。
- **算法流程**（文字描述）：
  - 阶段1（预热）：用原token级MoE进行短期训练，收集语义组嵌入，通过SVD构建初始oracle空间。
  - 阶段2（训练）：对每批数据，计算语义组及其嵌入，通过K-means聚类分配专家，替换原路由层进行训练。
  - 阶段3（推理）：对于新输入，先预处理分出语义组；解码时，利用KV cache实时更新语义组，并按其聚类中心路由专家。

## 3. 实验设计
- **数据集**：
  - 预训练：Openwebtext。
  - 下游任务：TriviaQA（问答）、GLUE（分类）、MAG（分类）、Sci-Cite（分类）、XSum（摘要）。
- **Benchmark**：主要对比 **Switch Transformer**（典型token级MoE）。
- **对比方法**：三种专家交换策略——FIFO、LRU、SwapMoE（Kong et al., 2024）。Oracle-MoE报告三种策略的平均结果。
- **模型规模**：基于GPT-2架构的四种配置——2×4(192M)、4×8(295M)、8×16(729M)、9×24(2.06B)。（注：n×m(p)表示n个MoE层，每层m个专家，总参数量p）
- **硬件平台**：NVIDIA Jetson Xavier NX（384核Volta GPU，8 GiB显存，21 TOPS）。
- **评估指标**：
  - 专家激活变化（visualization）
  - 内存-延迟曲线（不同内存预算下的平均处理时间）
  - 首token延迟（first token latency）
  - 下游任务零样本性能（F1、Accuracy、Rouge-1等）

## 4. 资源与算力
- **硬件**：实验平台为NVIDIA Jetson Xavier NX（8 GiB显存）。论文未明确说明训练使用的具体GPU数量和总时长，仅提及：
  - 预热阶段后的聚类分析每层约**4分钟**（采样8192条数据）。
  - 预训练整体耗时**数十小时（tens of hours）**。
  - 路由延迟对比：token级路由约1e-4秒，Oracle-MoE路由约2.5e-4秒，远小于单次前向传播的3.5秒。
- **不足**：未提供完整的GPU小时数和分布式训练配置，对算力需求评估不够透明。

## 5. 实验数量与充分性
- **实验组数**：
  - 4种模型规模 × 3种交换策略（Oracle-MoE取平均，Switch Transformer分别测试）→ 多组内存-延迟曲线。
  - 5种下游任务性能对比（Table 1）。
  - 首token延迟对比（Table 2，仅50%内存预算）。
  - 专家激活变化可视化（Figure 6）。
  - 延迟组成分解（Figure 8）。
  - 附录中补充了DeepSeekMoE-16B和Qwen1.5-MoE-A2.7B上的激活不一致性比较（Table 4），以及细粒度专家设置下的验证（Section B.3）。
  - 专家预测准确率对比（85%-95% vs 40%-60%）。
- **充分性**：实验涵盖不同模型大小、不同交换策略、不同内存预算、多种下游任务，并与多种基线对比，结果清晰、趋势一致。但**缺少在更大规模模型（如100B+）上的验证**，且**硬件平台单一**（仅Jetson），公平性控制在同平台对比。

## 6. 主要结论与发现
- **Oracle-MoE在不降低下游任务性能的前提下，显著降低边缘设备上的推理延迟**：
  - 在729M模型上，最紧内存预算下，Oracle-MoE延迟仅比全内存推理增加约3秒，而Switch Transformer延迟增加高达2000%。
  - 首token延迟降低至Switch Transformer的1/2~1/4。
  - 专家激活变化（CSD）极低：每100个token仅变化4-6次，而基线为53-81次。
- **理论保证**：oracle空间路由的CSD严格小于token级路由，解释了实验增益。
- **额外提升**：Oracle-MoE的专家激活可高概率预测（85%-95%），可进一步通过异步加载优化延迟10%-15%。

## 7. 优点
- **方法创新性**：首次从**语义局部性**角度重构MoE路由，利用注意力分数定义语义组，提取高阶语义，替代传统token身份嵌入，理论新颖且与实际问题吻合。
- **效果显著**：在不牺牲模型质量的前提下，将边缘部署延迟从“不可接受”降低到“接近全内存推理”，实用性极强。
- **理论支撑**：提供了CSD定义和定理证明，从数学上论证了路由一致性的提升。
- **实验设计全面**：覆盖多种模型大小、多种交换策略、多个任务，包含消融（专家预测）和泛化验证（DeepSeekMoE、Qwen），结果可信度高。
- **实际友好**：提出的计算开销极小（额外聚类约4分钟/层，路由额外0.15ms），易于集成到现有训练流程。

## 8. 不足与局限
- **模型架构局限**：主要实验基于GPT-2风格的MoE，虽然附录在DeepSeekMoE和Qwen上做了验证，但未在更大规模（如100B+）或不同注意力机制（如Grouped-Query Attention）的现代MoE上充分测试。
- **硬件平台单一**：仅在Jetson Xavier NX上测试，未在手机、树莓派、Intel NUC等其他常见边缘设备上评估，结论泛化性受限。
- **话题切换场景**：文中虽测试了“频繁话题变化”的合成数据（Switch场景下Oracle-MoE仍优于基线），但极端短文本（如单个词）的语义划分可能不够稳定，实际应用中需要处理注意力阈值选择问题。
- **阈值依赖性**：语义组的连接依赖于预设的注意力阈值ε，论文未给出其选择原则或鲁棒性分析，可能存在超参数敏感性。
- **分布式与多卡场景**：论文完全针对单卡边缘推理，未讨论分布式MoE或模型并行等训练/推理场景中的适用性。
- **任务多样性**：下游任务集中在分类、QA、摘要，缺少生成式任务（如对话、代码生成）的详细评估；虽然零样本性能保持，但未与全参数微调对比。

（完）
