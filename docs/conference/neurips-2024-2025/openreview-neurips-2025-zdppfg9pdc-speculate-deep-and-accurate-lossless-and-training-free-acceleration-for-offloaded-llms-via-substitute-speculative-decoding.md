---
title: "Speculate Deep and Accurate: Lossless and Training-Free Acceleration for Offloaded LLMs via Substitute Speculative Decoding"
title_zh: 深度且准确的推测：通过替代投机解码实现卸载LLM的无损无训练加速
authors: "Pei-Shuo Wang, Jian-Jia Chen, Chun-Che Yang, Chi-Chih Chang, Ning-Chi Huang, Mohamed S. Abdelfattah, Kai-Chiang Wu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ZDpPfg9pDc"
tags: ["query:edge-llm"]
score: 7.0
evidence: 投机解码加速内存受限GPU上的卸载LLM
tldr: 针对内存受限GPU上的大模型推理，提出替代投机解码方法，利用小型草稿模型生成候选token并由目标模型并行验证，有效减少卸载权重的数据传输，实现无损加速，无需额外训练，适用于边缘端有限内存场景。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zdppfg9pdc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1363, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zdppfg9pdc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zdppfg9pdc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1443, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zdppfg9pdc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1432, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zdppfg9pdc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1244, \"height\": 635, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zdppfg9pdc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1243, \"height\": 679, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1452, \"height\": 1056, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 732, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 503, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 630, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 772, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 470, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zdppfg9pdc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 569, \"height\": 155, \"label\": \"Table\"}]"
motivation: 大模型部署在内存有限的消费级GPU上，卸载虽保质量但推理慢。
method: 使用小型替代模型作为草稿，通过投机解码减少卸载权重传输次数。
result: 在保持模型质量的同时，显著加速推理。
conclusion: 投机解码是加速卸载模型的有效手段，适用于边缘设备。
---

## Abstract
The immense model sizes of large language models (LLMs) challenge deployment on memory-limited consumer GPUs.
    Although model compression and parameter offloading are common strategies to address memory limitations, compression can degrade quality, and offloading maintains quality but suffers from slow inference.
    Speculative decoding presents a promising avenue to accelerate parameter offloading, utilizing a fast draft model to propose multiple draft tokens, which are then verified by the target LLM in parallel with a single forward pass. This method reduces the time-consuming data transfers in forward passes that involve offloaded weight transfers.
    Existing methods often rely on pretrained weights of the same family, but require additional training to align with custom-trained models. Moreover, approaches that involve draft model training usually yield only modest speedups. This limitation arises from insufficient alignment with the target model, preventing higher token acceptance lengths.
    To address these challenges and achieve greater speedups, we propose SubSpec, a plug-and-play method to accelerate parameter offloading that is lossless and training-free. SubSpec constructs a highly aligned draft model by generating low-bit quantized substitute layers from offloaded target LLM portions. Additionally, our method shares the remaining GPU-resident layers and the KV-Cache, further reducing memory overhead and enhance alignment.
    SubSpec achieves a high average acceptance length, delivering 9.1$\times$ speedup for Qwen2.5 7B on MT-Bench (8GB VRAM limit) and an average of 12.5$\times$ speedup for Qwen2.5 32B on popular generation benchmarks (24GB VRAM limit).

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题背景**：大型语言模型（LLMs）参数量巨大，难以部署在内存有限的消费级GPU（如8GB-24GB VRAM）上。常用策略包括模型压缩（如量化）和参数卸载。压缩会损失模型质量；卸载虽然保质量，但因PCIe数据传输频繁，推理速度极慢（通常每秒仅1-2个token）。
- **现有方法的不足**：投机解码（Speculative Decoding）利用小型草稿模型快速生成多个候选token，再由目标模型并行验证，可减少昂贵的卸载权重传输。但现有方法要么依赖同系列预训练小模型（需额外训练对齐），要么草稿模型对齐度不足，导致平均接受长度（τ）较低（一般低于7），加速效果有限。
- **论文目标**：提出一种**无损、无需训练**的插拔式加速方法**SubSpec**（Substitute Speculative Decoding），通过构建高度对齐的草稿模型，显著提升卸载场景下LLM的推理吞吐量。

## 2. 论文提出的方法论

### 核心思想
SubSpec利用低比特量化替代层（substitute layers）构建草稿模型，使其完全驻留在GPU上；同时共享目标模型中已驻留GPU的层和KV-Cache，实现草稿模型与目标模型的极高对齐度。在此基础上采用**树状投机解码**（tree-based speculative decoding），扩展更深层的草稿树，从而获得极高的平均接受长度（τ ≈ 30），大幅减少昂贵的目标模型前向传播次数。

### 关键技术细节
- **草稿模型构建**：
  - **低比特替代权重**：对目标模型中被卸载的层，使用快速、无需数据的量化方法（如HQQ）生成4-bit量化替代层，完全置于GPU。
  - **共享GPU驻留层**：草稿模型直接复用目标模型中保留在GPU的相同层权重。
  - **共享KV-Cache**：草稿模型与目标模型共用同一KV-Cache，减少显存占用并增强对齐，且无需额外预填充。
- **优化的草稿树构建**：
  - **上下文感知动态草稿树**：基于EAGLE-2和SpecExec的方法扩展到更深层（D可达48）。通过迭代生成候选token，每次保留top-k个最高累计概率的路径。
  - **应对累计概率偏差**：在贪婪解码下，低概率路径可能因后续高概率token而获得虚高的累计概率，导致正确路径被截断。为此提出**草稿概率锐化**（Draft Probability Sharpening）：在树采样前对草稿模型输出分布施加低温（如0.2），使分布更尖锐，抑制低概率路径。
- **互补优化**：
  - **异步数据传输**：在目标层计算的同时，预取下一层卸载参数到GPU，重叠计算与数据传输。
  - **分块预填充**：将长提示分割为固定长度块（如256 tokens），逐步构建KV-Cache，减少预填充阶段峰值显存，从而允许更多目标层驻留GPU。

### 公式与流程说明
- 传统自回归解码总时间：\(T_N^{AR} = N \cdot t_{\text{Target}}\)
- 投机解码总时间：\(T_N^{SD} = \frac{N}{\tau} (D \cdot t_{\text{Draft}} + \gamma \cdot t_{\text{Target}})\)
- 加速比：\(\frac{T_N^{AR}}{T_N^{SD}} = \frac{\tau}{D \cdot (t_{\text{Draft}}/t_{\text{Target}}) + \gamma}\)
- 在卸载场景中，\(t_{\text{Target}}\)因数据传输极大，因此最大化τ比降低\(t_{\text{Draft}}\)更重要，这解释了为何需高度对齐的草稿模型。

## 3. 实验设计

### 数据集/场景与Benchmark
使用五个多样化的生成任务：
- **多轮对话**：MT-Bench
- **代码生成**：HumanEval
- **数学推理**：GSM8K
- **指令遵循**：Alpaca
- **摘要**：CNN/Daily Mail

此外，在附录中补充了推理模型（DeepSeek-R1蒸馏版、QWQ）上的评估，使用AIME 2024、MATH 500、GPQA Diamond、LiveCodeBench。

### 对比方法
- 基线：vanilla offloading（无投机解码）
- EAGLE-2（使用预训练草稿模型，需要训练）
- 同系列小模型（如Qwen2.5 1.5B、Llama3.2 1B）作为草稿模型
- 部分实验对比了SpecExec、Dovetail等（见附录）

### 实验设置
- 硬件：单张RTX 4090（PCIe 4.0 x16），Intel i7-13700K，128GB DDR5 RAM
- 显存限制：8GB（7B/8B模型）、12GB（14B模型）、24GB（32B模型）
- 生成温度：greedy（温度=0）和stochastic（温度=0.6）
- 草稿模型参数：SubSpec使用HQQ 4-bit量化（group size 64），top-k=6，最佳草稿深度D=48（通过网格搜索确定）
- 所有方法使用相同上下文感知动态草稿树算法，batch size=1

## 4. 资源与算力

- **GPU型号**：单张NVIDIA RTX 4090
- **数量**：1张
- **训练时长**：无需训练（training-free），量化过程在单卡上数分钟即可完成（7B至70B模型）
- **推理时间**：论文未给出总推理时间，但展示了吞吐量（tokens/s）和加速比
- **说明**：文中明确表示SubSpec无需训练，量化开销极小，因此算力需求主要集中在推理阶段。

## 5. 实验数量与充分性

- **主要实验**：在5个标准benchmark上，对4种目标模型（Llama3.1 8B、Qwen2.5 7B/14B/32B）分别在两种温度条件下进行对比，共约40组主实验（每种方法×每个数据集）。
- **消融实验**：在MT-Bench（8GB）上逐步添加组件（替代层+层共享、共享KV-Cache、概率锐化、异步传输），共4组。
- **额外实验**：附录中包含推理模型评估（4个模型×4个数据集）、不同草稿温度影响、SpecExec参数扫描、量化目标模型对比等。
- **统计**：报告了SubSpec的5次独立运行标准差（0.101 tokens/s），但主要表格未给出误差棒，理由为“太耗时”。
- **充分性评价**：实验覆盖了常见模型家族（Llama、Qwen）、多种任务类型、不同显存约束，对比了多种主流方法，且包含消融和扩展实验，设计较为全面。但缺乏对更多架构（如MoE）和更大模型（>70B）的评估，且未提供统计显著性检验。

## 6. 论文的主要结论与发现

- **SubSpec实现了10–12.5倍加速**：在8GB/12GB/24GB显存限制下，相比基线卸载推理，SubSpec将吞吐量提升至可用水平（如Qwen2.5 7B达到25 tokens/s，Qwen2.5 32B达到6.5 tokens/s）。
- **平均接受长度τ接近30**：远高于现有方法（通常<14），验证了草稿模型高度对齐带来的优势。
- **无需训练、无损质量**：SubSpec仅需一次快速量化，不改变目标模型输出，保持原始精度。
- **在随机采样（温度=0.6）下仍保持5.8–7.8倍加速**，具有鲁棒性。
- **消融实验证明每个组件均贡献显著**（7%–13%吞吐量提升），其中异步传输和概率锐化最为关键。

## 7. 优点

- **创新性**：首次提出利用量化替代层构建高度对齐草稿模型的思路，结合层共享和KV-Cache共享，最大化对齐度。
- **实用性**：完全无需训练，即插即用，可应用于任意微调后的LLM；量化过程仅数分钟，适合实际部署。
- **性能优异**：在消费级显卡上实现了接近本地推理的体验（如25 tokens/s），远超现有卸载方案。
- **实验设计严谨**：对比了多种基线，进行了网格搜索确定最佳深度，并提供了消融和扩展实验。
- **开源代码**：已提供GitHub仓库，可复现结果。

## 8. 不足与局限

- **最低显存要求较高**：SubSpec需保留整个草稿模型（含量化替代层）在GPU，例如Qwen2.5 7B要求约7.1GB，导致可驻留的目标层数少于某些方法。但最终吞吐量仍更优。
- **量化粒度单一**：仅尝试4-bit量化，未探索2-bit或3-bit可能带来的显存节省与对齐度权衡。
- **架构适用性有限**：主要针对密集Transformer架构，未研究MoE等混合专家模型。
- **缺少统计误差**：除一次标准差外，未报告置信区间或误差棒，结论的稳定性缺乏充分量化。
- **未在更大模型（>70B）上验证**：虽然推理了32B模型，但更大规模可能面临新的瓶颈。
- **随机采样下加速比下降**：温度=0.6时加速比降至6–8倍，说明方法对确定解码更优。

（完）
