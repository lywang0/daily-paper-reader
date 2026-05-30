---
title: "MobileLLM: Optimizing Sub-billion Parameter Language Models for On-Device Use Cases"
title_zh: MobileLLM：面向设备端用例优化亚十亿参数语言模型
authors: "Zechun Liu, Changsheng Zhao, Forrest Iandola, Chen Lai, Yuandong Tian, Igor Fedorov, Yunyang Xiong, Ernie Chang, Yangyang Shi, Raghuraman Krishnamoorthi, Liangzhen Lai, Vikas Chandra"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=EIGbXbxcUQ"
tags: ["query:edge-llm"]
score: 9.0
evidence: 为移动设备优化亚十亿参数大语言模型
tldr: "移动设备上的大语言模型部署受限于成本和延迟。本文专注于设计高质量亚十亿参数模型，发现模型架构比数据量更重要。通过深度薄网络、嵌入共享和分组查询注意力机制，提出MobileLLM，在125M和350M规模上相比先前最优分别提升2.7%和4.3%准确率，为端侧部署提供了强大基线。"
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-eigbxbxcuq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 869, \"height\": 661, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-eigbxbxcuq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 868, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-eigbxbxcuq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 857, \"height\": 700, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-eigbxbxcuq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1765, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-eigbxbxcuq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 897, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-eigbxbxcuq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 694, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-eigbxbxcuq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 669, \"height\": 452, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1514, \"height\": 167, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1690, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1772, \"height\": 565, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 887, \"height\": 512, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 859, \"height\": 798, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 717, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 813, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1511, \"height\": 861, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1288, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1759, \"height\": 600, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1598, \"height\": 612, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 982, \"height\": 632, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1752, \"height\": 951, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1752, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1755, \"height\": 359, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-eigbxbxcuq/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1753, \"height\": 211, \"label\": \"Table\"}]"
motivation: 云端LLM成本高、延迟大，移动设备需要高效且高质量的小参数模型。
method: 采用深度薄网络、嵌入共享和分组查询注意力架构设计MobileLLM。
result: "在125M和350M参数上准确率分别提升2.7%和4.3%。"
conclusion: 良好的架构设计可在小参数规模下实现高精度，适合移动设备部署。
---

## Abstract
This paper addresses the growing need for efficient large language models (LLMs) on mobile devices, driven by increasing cloud costs and latency concerns. We focus on designing top-quality LLMs with fewer than a billion parameters, a practical choice for mobile deployment. Contrary to prevailing belief emphasizing the pivotal role of data and parameter quantity in determining model quality, our investigation underscores the significance of model architecture for sub-billion scale LLMs. Leveraging deep and thin architectures, coupled with embedding sharing and grouped-query attention mechanisms, we establish a strong baseline network denoted as MobileLLM, which attains a remarkable 2.7%/4.3% accuracy boost over preceding 125M/350M state-of-the-art models. Additionally, we propose an immediate block-wise weight-sharing approach with no increase in model size and only marginal latency overhead. The resultant models, denoted as MobileLLM-LS, demonstrate a further accuracy enhancement of 0.7%/0.8% than MobileLLM 125M/350M. Moreover, MobileLLM model family shows significant improvements compared to previous sub-billion models on chat benchmarks, and demonstrates close correctness to LLaMA-v2 7B in API calling tasks, highlighting the capability of small models for common on-device use cases.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLMs）在云端的部署成本高、延迟大，且能源消耗惊人；移动设备（如智能手机）的内存（DRAM）和电池容量有限，无法承载数十亿参数的大模型（如LLaMA-v2 7B）。因此，亟需设计可在设备端高效运行的高质量“亚十亿参数”LLMs（参数小于10亿）。
- **研究背景**：主流观点认为模型质量主要由数据量和参数量决定，但本文针对小规模LLMs（sub-billion）发现，**模型架构**远比参数量和数据量更重要。作者从移动端实际硬件限制（DRAM 6–12 GB，SRAM cache仅8–32 MB）出发，论证了“深度薄网络”+多种参数共享策略的巨大潜力。

## 2. 论文提出的方法论

### 2.1 核心思想
- 在参数量固定的前提下，通过**极深且极薄（deep and thin）** 的架构、**嵌入共享**（input-output embedding sharing）、**分组查询注意力（GQA）** 以及创新的**立即块级权重共享（immediate block-wise weight sharing）** 来最大化权重利用率，从而显著提升小模型的表现。

### 2.2 关键技术细节
- **SwiGLU激活函数**：替换传统FFN中的ReLU，提升模型表示能力（125M模型平均涨点约1.3%）。
- **深度-宽度权衡**：通过大量实验（19种不同深宽配置）证明深度比宽度更重要。对于125M模型，30层甚至42层比12层效果好很多。
- **输入-输出嵌入共享**：将输入嵌入权重同时作为输出全连接层权重，节省约12%参数，通过重新分配这些参数可完全弥补精度损失。
- **分组查询注意力（GQA）**：将key-value头数减少为query头数的1/n（如1/4），在不损失精度的情况下减少模型参数（约10%），并允许增大嵌入维度进一步提升性能。
- **立即块级权重共享（MobileLLM-LS）**：不增加模型大小（权重总数不变），仅通过复制相邻两个块并让它们共享权重。利用SRAM缓存的局部性，共享权重可以留在缓存中连续计算两次，只带来极小的延迟开销（约2.6%）。相比“全重复共享”或“反向共享”策略，这种方案在精度和延迟之间取得了最佳平衡。

### 2.3 算法流程（文字说明）
1. 基础模型预训练：使用Adam优化器，cosine学习率衰减，在0.25T/1T tokens上训练。
2. 逐步添加上述技巧（SwiGLU→加深→嵌入共享→GQA）形成MobileLLM基线。
3. 对MobileLLM进一步应用立即块级权重共享（即每相邻两层共享参数，但层计数加倍）得到MobileLLM-LS。
4. 下游任务微调：在Chat和API调用数据集上进行全参微调。

## 3. 实验设计

### 3.1 数据集与Benchmark
- **零样本常识推理**：ARC-easy, ARC-challenge, BoolQ, PIQA, SIQA, HellaSwag, OBQA, WinoGrande（8个任务）。
- **问答与阅读理解**：TriviaQA（1-shot/5-shot/64-shot F1）和RACE（middle/high accuracy）。
- **Chat任务**：AlpacaEval（单轮，win rate vs text-davinci-001）和MT-Bench（多轮，GPT-4打分1–10）。
- **API调用任务**：作者合成数据集，5000训练/2500测试样本，每样本平均8轮对话，评估EM intent、EM structure、Rouge-1/L。

### 3.2 对比方法
- 同规模模型包括：OPT-125M/350M/1.3B、BLOOM-560M、Galactica-125M、Cerebras-GPT-111M/256M/590M/1.3B、GPT-Neo-125M/1.3B、Pythia-160M/410M/1B、RWKV-169M/430M/1.5B、Falcon-1B、TinyLlama-1.1B、LaMini-GPT-124M/1.5B、Qwen1.5-500M/1.8B、MobiLlama-800M/1B 等。
- 更大规模的消融对比：LLaMA-v2 7B（仅API调用任务）。

## 4. 资源与算力

- **训练硬件**：32张NVIDIA A100 GPU（未说明具体型号，推测为80GB）。
- **每GPU batch size**：32。
- **探索实验**：120k iterations，0.25T tokens。
- **最终报告模型**：480k iterations，1T tokens。
- **总训练时间**：未明确给出，但附录G提到125M模型label训练约29h，350M约42h，KD训练则需93h/109h（3×左右）。
- **评估**：零样本任务使用Hugging Face模型统一评估，确保公平性。

## 5. 实验数量与充分性

### 5.1 实验组数
- **深度-宽度消融**：19种配置（9种125M + 10种350M）。
- **头数与KV头数消融**：125M和350M各16种组合（表13）。
- **层共享策略对比**：3种共享方式 + baseline（表2）。
- **层重复次数消融**：×2, ×3, ×4（表14）。
- **量化兼容性**：BF16 vs W8A8 PTQ（表15）。
- **知识蒸馏探索**：label vs label+KD（表16）。
- **下游Chat和API调用**：各包含多种模型对比。
- **扩展至更大规模**：600M、1B、1.5B（附录表8）。
- **最终汇总消融**：逐步添加技巧的完整路径（表10）。

### 5.2 充分性与公平性
- 消融实验充分覆盖了架构关键维度（深度、宽度、注意力头数、共享策略、量化、KD），统计严谨。
- 所有对比方法均使用Hugging Face官方权重在同一评估流程下进行，避免了评估偏差。
- 训练数据量（1T tokens）与先前工作一致或更大，符合公平对比。
- 缺少对“更大规模模型（如7B级）”的直接对比（仅API调用有7B对比），但论文重点在于sub-billion，扩展至1.5B已说明泛化力。

## 6. 论文的主要结论与发现

1. **架构至关重要**：对于亚十亿参数LLMs，深度比宽度更关键，一反主流“缩放定律”中架构影响小的观点。
2. **MobileLLM在125M和350M规模上分别比先前SOTA提升2.7%和4.3%平均准确率**（零样本常识推理）。
3. **立即块级共享（MobileLLM-LS）** 在不增加模型大小且仅增加~2.6%延迟的情况下，进一步带来0.7–0.8%精度提升。
4. **在Chat和API调用等真实设备端任务上**，MobileLLM-350M性能接近甚至超过LLaMA-v2 7B（API调用EM结构匹配）。
5. **设计原则可扩展**：MobileLLM-600M/1B/1.5B同样显著优于同规模现有模型。
6. **与量化兼容**：W8A8 PTQ仅损失不到0.5%精度。

## 7. 优点

- **问题定位精准**：从硬件限制（DRAM、SRAM）出发，论证了sub-billion模型的必要性，而非盲目追求大模型。
- **方法论简洁有效**：利用权重共享（嵌入共享、GQA、块级共享）在不增加参数的情况下提升性能，实用性强。
- **实验极其全面**：覆盖深度-宽度、头数、共享策略、重复次数、量化、KD、下游任务等多个维度，消融清晰。
- **落地导向**：在真实iPhone 13上测量延迟，并展示Chat和API调用样例，验证了可行性和实用性。
- **开源思维**：对比方法均使用公开权重，评估过程透明可复现。

## 8. 不足与局限

- **训练数据规模相对较小**：最终模型仅训练1T tokens，而现代大模型通常使用数T甚至数十T tokens，可能存在欠训练导致的潜力未完全释放。
- **缺乏与更大模型（如7B）的系统对比**：仅API调用任务有直接对比，其他任务未展示更大型号的性能上界，对“小模型能否替代大模型”的说服力有限。
- **知识蒸馏（KD）探索不成功**：KD反而降低性能，作者归因于训练时间过长，但未深入分析原因，也未尝试其他蒸馏策略（如特征层蒸馏）。
- **块级共享的延迟测量仅限Apple MPS后端**：可能在其他硬件（如高通NPU）上未验证，通用性存疑。
- **Chat和API调用数据集为合成数据**：未使用真实用户对话数据，可能引入分布偏差，低估真实场景难度。
- **仅考虑next-token损失训练**：未对比其他预训练目标（如Prefix LM、去噪自编码）对下游任务的影响。
- **论文未提供开源模型权重**（截至写作），复现成本较高。

（完）
