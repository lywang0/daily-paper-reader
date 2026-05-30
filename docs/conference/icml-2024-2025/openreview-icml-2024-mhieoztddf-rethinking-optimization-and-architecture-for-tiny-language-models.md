---
title: Rethinking Optimization and Architecture for Tiny Language Models
title_zh: 重新思考小型语言模型的优化与架构
authors: "Yehui Tang, Kai Han, Fangcheng Liu, Yunsheng Ni, Yuchuan Tian, Zheyuan Bai, Yi-Qi Hu, Sichao Liu, SHANGLING JUI, Yunhe Wang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=mHIEOZtDDF"
tags: ["query:edge-llm"]
score: 9.0
evidence: 优化移动设备上的小型语言模型
tldr: 该研究基于1B参数的小型语言模型，系统分析了神经架构、参数初始化和优化策略的影响，提出了若干设计公式，为移动设备上高效部署语言模型提供了实证指导。其实验结果为资源受限环境下的LLM推理优化提供了重要参考。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-mhieoztddf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 841, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mhieoztddf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 672, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mhieoztddf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 811, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mhieoztddf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1493, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mhieoztddf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1747, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mhieoztddf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 714, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mhieoztddf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 810, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mhieoztddf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 680, \"height\": 336, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mhieoztddf/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 677, \"height\": 336, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mhieoztddf/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 671, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mhieoztddf/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1748, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-mhieoztddf/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1760, \"height\": 1208, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 854, \"height\": 269, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 855, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 851, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 856, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 855, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1744, \"height\": 569, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 847, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 927, \"height\": 189, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1079, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1169, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-mhieoztddf/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 905, \"height\": 314, \"label\": \"Table\"}]"
motivation: 移动设备上部署语言模型面临计算和内存挑战。
method: 通过大量实验分析1B模型的架构、初始化与优化策略的影响。
result: 总结出若干设计公式，可指导高效小型语言模型构建。
conclusion: 该工作为移动端LLM高效部署提供了实用的优化准则。
---

## Abstract
The power of large language models (LLMs) has been demonstrated through numerous data and computing resources. However, the application of language models on mobile devices is facing huge challenge on the computation and memory costs, that is, tiny language models with high performance are urgently required. Limited by the highly complex training process, there are many details for optimizing language models that are seldom studied carefully. In this study, based on a tiny language model with 1B parameters, we carefully design a series of empirical study to analyze the effect of each component. Three perspectives are mainly discussed, i.e., neural architecture, parameter initialization, and optimization strategy. Several design formulas are empirically proved especially effective for tiny language models, including tokenizer compression, architecture tweaking, parameter inheritance and multiple-round training. Then we train PanGu-$\pi$-1B Pro and PanGu-$\pi$-1.5B Pro on 1.6T multilingual corpora, following the established formulas. Experimental results demonstrate the improved optimization and architecture yield a notable average improvement of 8.87 on benchmark evaluation sets for PanGu-$\pi$-1B Pro. Besides, PanGu-$\pi$-1.5B Pro surpasses a range of SOTA models with larger model sizes, validating its superior performance. The code will be released soon. The code is available at https://github.com/YuchuanTian/RethinkTinyLM.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLMs）在云端展示出强大能力，但将其部署在移动设备等资源受限场景时，面临极高的计算和内存成本。现有研究多集中于大型模型（数十亿参数以上），针对**小型语言模型（~1B参数）** 的系统性优化方法却很少被深入分析。
- **整体含义**：本文以1B参数的小模型为基准，从架构设计、参数初始化、优化策略三个维度进行大量实证研究，提炼出若干有效设计公式，并基于这些公式构建了 **PanGu-π Pro** 系列模型，在多项基准上超越同规模甚至更大规模的SOTA模型，为移动端高效语言模型部署提供了实用指导。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：针对小型模型面临的参数冗余、遗忘问题、收敛缓慢等挑战，提出四项关键改进：
  1. **紧凑分词器**：移除低频词汇，将词表从100k压缩至48k（覆盖97.86%语料），使嵌入和头层参数占比从38.19%降至18.07%，释放参数给主网络。
  2. **架构调整**：在固定1B参数下，深度比宽度和FFN扩展率更重要。推荐深度约20层，扩展率2.77，平衡性能与推理速度。
  3. **参数初始化**：
     - 随机初始化：推荐所有层使用相同标准差（常数初始化）。
     - 参数继承：从大型模型（如PanGu-π-7B）继承参数，通过层重要性分析（首尾层更关键）和层内重要性度量（可学习二值掩码优于L1/L2/Taylor）进行剪枝式迁移。
  4. **模型优化**：
     - 批量大小与学习率：建议批量大小 < 4M，学习率缩放因子 r=0.5。
     - 多轮训练：针对小型模型更严重的数据遗忘问题，提出第二轮训练按损失采样困难样本（采样率50%），以较低成本提升性能。

### 3. 实验设计：数据集、benchmark、对比方法

- **预训练数据**：1.6T tokens，中英文约1:1，来自互联网多源语料。
- **评估基准**：使用OpenCompass框架，涵盖：
  - 考试：C-Eval、CMMLU、MMLU、AGI-Eval
  - 知识/推理：BoolQ、AX-b、PIQA
  - 理解：EPRSTMT、XSum、C3
- **对比方法**：包括TinyLLaMA-1.1B、Chinese-LLaMA2-1.3B、Sheared-LLaMA-1.3B、Open-LLaMA-3B、MobileLLaMA系列、RWKV-5-1.5B、Phi-1.3B/Phi2-2.7B、Qwen-1.8B等，参数范围1B~3B。

### 4. 资源与算力

- **训练与推理硬件**：
  - 预训练及最终评估使用 **Huawei Ascend 910** 芯片，未说明具体数量及训练时长。
  - 架构速度测试在 **单张NVIDIA V100 GPU** 上完成（FP16，batch size 20，生成510 tokens）。
- **算力信息不足**：文中未给出整体训练所需GPU·天等具体数字，复现成本难以精确估计。

### 5. 实验数量与充分性

- **实验组数丰富**：各部分独立实验包括：
  - 分词器大小（6种：8k/16k/32k/48k/72k/100k）
  - 深度与宽度组合（约30种随机采样，以及5组典型配置）
  - 扩展率（4种）
  - 随机初始化方法（3种），参数继承方法（4种：L1/L2/Taylor/Learned）
  - 批量大小×学习率（6×4组合）
  - 多轮训练：采样率（5档）、轮数（1/2/3轮）
  - 附注：注意力头数、权重衰减、GQA对比等
- **充分性与公平性**：所有消融实验均控制模型总参数量~1B，并在相同数据子集（50B或5B tokens）上训练，结果客观。评估使用多个下游任务取平均，避免单任务偏差。

### 6. 论文的主要结论与发现

- **紧凑分词器**：48k词汇覆盖97.86%语料，参数占比降至18.07%，性能最佳。
- **深度优先**：深度与性能正相关（Spearman r=0.528），但需权衡推理速度；推荐1B模型深度20层。
- **参数继承优势显著**：可学习掩码继承大模型参数，训练损失更低，最终平均性能提升约6分。
- **多轮训练缓解遗忘**：两轮训练（第二轮采样50%困难样本）使平均准确率提升约2.85分。
- **最终模型表现**：PanGu-π-1B Pro平均得分51.28，较原版（42.41）提升8.87；PanGu-π-1.5B Pro以1.5B参数（比Qwen-1.8B少16.67%）得分60.64，超越Qwen-1.8B（55.04）及Phi2-2.7B（45.09）等更大模型，达到SOTA。

### 7. 优点

- **系统性实证**：首次对1B级别小模型的架构、初始化、优化进行全链条分解研究，每个因素独立验证，结论可靠。
- **实用导向**：提出的设计公式（如“参数量1B时深度20”“词表覆盖>90%”“批量<4M”）可直接指导工程实践。
- **高效迁移**：参数继承方法结合层+神经元双重剪枝，既利用大模型知识又压缩模型，思路新颖。
- **开源贡献**：代码已公开（GitHub），便于复现和后续研究。
- **公平对比**：在统一评估框架（OpenCompass）下与多个开源模型比较，指标覆盖全面。

### 8. 不足与局限

- **算力细节缺失**：未报告预训练所需GPU卡数、天数等资源消耗，影响复现和规模评估。
- **规模外推性未验证**：所有实验基于1B模型，对更小（<500M）或稍大（2~3B）模型的适用性尚需验证。
- **多轮训练策略简单**：仅基于损失采样困难样本，可能忽略结构多样性；更先进的数据筛选或课程学习可能进一步提升。
- **依赖已有大模型**：参数继承需要预先存在对应的大模型（如7B），限制了无大模型场景下的通用性。
- **未深入探讨数据质量**：相比Phi系列使用“教科书质量”数据，本文仅提及数据量而未分析数据质量对性能的影响。
- **架构探索有限**：仅调整了MLP扩展率和深度宽度，未涉及MoE、线性注意力等更高效的架构，附录中GQA仅做初步对比。

（完）
