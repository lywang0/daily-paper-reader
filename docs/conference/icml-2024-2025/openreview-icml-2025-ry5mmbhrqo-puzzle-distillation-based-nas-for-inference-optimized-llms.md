---
title: "Puzzle: Distillation-Based NAS for Inference-Optimized LLMs"
title_zh: Puzzle：基于蒸馏的NAS实现推理优化的LLM
authors: "Akhiad Bercovich, Tomer Ronen, Talor Abramovich, Nir Ailon, Nave Assaf, Mohammed Dabbah, Ido Galil, Amnon Geifman, Yonatan Geifman, Izhak Golan, Netanel Haber, Ehud Dov Karpas, Roi Koren, Itay Levy, Pavlo Molchanov, Shahar Mor, Zach Moshe, Najeeb Nabwani, Omri Puny, Ran Rubin, Itamar Schen, Ido Shahaf, Oren Tropp, Omer Ullman Argov, Ran Zilberstein, Ran El-Yaniv"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=RY5MMBHRqo"
tags: ["query:edge-llm"]
score: 9.0
evidence: 硬件感知的NAS结合蒸馏以优化LLM推理
tldr: Puzzle是一个硬件感知的神经网络架构搜索框架，通过块级知识蒸馏和混合整数规划，在数十亿参数规模上优化LLM推理速度。该框架在Llama-3.1-Nemotron-51B-Instruct模型上展示了显著的加速效果，同时保持了模型能力，为硬件感知的LLM加速提供了新范式。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1328, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 842, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 304, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 692, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 863, \"height\": 255, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 835, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 865, \"height\": 454, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 871, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 882, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 868, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 708, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 783, \"height\": 116, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1782, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 883, \"height\": 228, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 860, \"height\": 152, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 859, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 866, \"height\": 131, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 855, \"height\": 160, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 858, \"height\": 166, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 859, \"height\": 153, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 860, \"height\": 192, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 869, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 863, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 862, \"height\": 163, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1782, \"height\": 481, \"label\": \"Table\"}]"
motivation: LLM推理成本高，参数增加加剧部署难度。
method: 结合块级知识蒸馏和混合整数规划的硬件感知NAS，搜索高效架构。
result: 在51B模型上实现大幅推理加速，同时保持准确性。
conclusion: Puzzle证明了硬件感知NAS可有效优化大规模LLM推理效率。
---

## Abstract
Large language models (LLMs) offer remarkable capabilities, yet their high inference costs restrict wider adoption.
While increasing parameter counts improves accuracy, it also broadens the gap between state-of-the-art capabilities and practical deployability. We present **Puzzle**, a hardware-aware framework that accelerates the inference of LLMs while preserving their capabilities.
Using neural architecture search (NAS) at a large-scale, Puzzle optimizes models with tens of billions of parameters.
Our approach utilizes blockwise local knowledge distillation (BLD) for parallel architecture exploration and employs mixed-integer programming for precise constraint optimization.

We showcase our framework’s impact via Llama-3.1-Nemotron-51B-Instruct (Nemotron-51B) and Llama-3.3-Nemotron-49B, two publicly available models derived from Llama-70B-Instruct. Both models achieve a 2.17x inference throughput speedup, fitting on a single NVIDIA H100 GPU while retaining 98.4% of the original model's benchmark accuracies. 
These are the most accurate models supporting single H100 GPU inference with large batch sizes, despite training on 45B tokens at most, far fewer than the 15T used to train Llama-70B.
Lastly, we show that lightweight alignment on these derived models allows them to surpass the parent model in specific capabilities.
Our work establishes that powerful LLM models can be optimized for efficient deployment with only negligible loss in quality, underscoring that inference performance, not parameter count alone, should guide model selection.

---

## 论文详细总结（自动生成）

# 论文《Puzzle: Distillation-Based NAS for Inference-Optimized LLMs》中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- 大型语言模型（LLM）能力强大，但推理成本高昂，限制了其广泛应用。参数量的增加虽然提升了准确性，但也拉大了先进能力与可部署性之间的差距。
- 现有方法如从头训练或全局知识蒸馏，对于评估大量候选架构而言成本过高。而推理效率不仅取决于参数数量，还受硬件、推理引擎、量化级别、批量大小等实际因素影响。
- 论文提出 **Puzzle** 框架，旨在将训练好的LLM从适合训练的结构转变为针对特定硬件（如H100 GPU）优化的高效推理结构，同时保留其积累的知识和预测性能。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：采用分解式神经架构搜索（NAS）策略，通过块级局部蒸馏（BLD）并行训练大量块变体，构建“拼图块”库，再使用混合整数规划（MIP）从约 \(10^{138}\) 种可能架构中搜索满足推理约束的最优组合，最后通过全局知识蒸馏（GKD）微调块间兼容性。
- **关键技术细节**：
  - **搜索空间**：每个Transformer层可替换为不同的注意力和FFN子块。注意力选项包括GQA（变种KV头数）、线性层、no-op；FFN选项包括不同缩减比例的中间维度、线性层、no-op。
  - **块级局部蒸馏（BLD）**：并行独立训练每个子块变体，使其局部模仿父块输出（归一化MSE损失）。提出**解耦BLD**：分别训练注意力变体和FFN变体（冻结另一半为父块），然后组合成完整块，将训练复杂度从乘法降为加法。
  - **搜索算法**：使用混合整数规划，最大化各块得分之和，同时满足内存（参数+KV-cache）、吞吐量、延迟等约束。能快速生成针对不同硬件和场景的架构。
  - **全局知识蒸馏（GKD）**：最终阶段，用父模型指导子模型进行端到端训练，损失函数包含余弦相似度（隐藏层）和KL散度（输出分布），不包含语言建模损失（避免过拟合）。
  - **推理引擎适配**：改造TensorRT-LLM以支持非均匀块和不同KV头数的层，实现FP8量化下的高效推理。

## 3. 实验设计
- **数据集**：蒸馏混合（Distillation Mix）包含 FineWeb、Dolma、Buzz-V1.2 共224B token；BLD阶段使用1B token；GKD阶段使用45B token（也可缩减至几B token）。
- **Benchmark**：Winogrande、ARC Challenge、MMLU、HellaSwag、GSM8K、TruthfulQA、XLSum、MT-Bench、HumanEval、RULER（长上下文）、Arena Hard等。
- **对比方法**：
  - 与父模型 Llama-3.1-70B-Instruct 进行准确率和吞吐量对比。
  - 与Wanda（结构化稀疏）、低秩近似方法比较。
  - 与随机架构、贪心算法、参数最大化、no-op-only 等消融基线比较。
  - 与Llama-3.1-8B-Instruct、Mixtral 8X22B等模型的效率前沿对比。

## 4. 资源与算力
- 父模型 Llama-70B 训练用了15T token；Puzzle 的BLD+GKD总共最多45B token。
- 推理测试使用 NVIDIA H100 SXM GPU，FP8量化，TensorRT-LLM。
- 训练BLD时利用管道并行解耦，但未明确说明具体GPU数量和时长。GKD阶段使用45B token（可缩减），但训练细节未提具体卡数。
- 论文未明确给出完整训练所需GPU总时数，仅指出成本远低于从头训练。

## 5. 实验数量与充分性
- **实验数量丰富**：包括主实验结果（表1-5）、长上下文（表3/7/19）、对齐效果（表4）、训练预算削减（表6）、消融实验（附录F）等近20个表格。
- **消融覆盖全面**：涵盖数据集组成、训练token数量、块评分指标、耦合与解耦BLD、搜索空间限制、贪心搜索、随机基线、损失组成等。
- **公平性**：对比方法在同一吞吐约束下进行；吞吐量基于实际测量而非理论FLOPs；采用盲测人类评估；随机基线确保公平对比。但未与最新剪枝/蒸馏方法（如Minitron、ShearedLlama）进行直接比较，仅与Wanda和低秩方法对比。

## 6. 主要结论与发现
- Puzzle 能生成高效的非均匀架构，在保持98.4%父模型准确率的同时，实现2.17倍推理吞吐量加速，且可单卡H100运行。
- 训练成本极低（最多45B token），且可用更少token（如3.7B）恢复大部分性能。
- 发现中层（16-42层）对性能至关重要，FFN层比注意力层更不可替代。
- 解耦BLD大幅降低计算成本；KL散度作为块评分优于LM损失；全局KD可提升块间兼容性。
- 轻量级对齐（RLHF）能使衍生模型在特定任务上超越父模型。

## 7. 优点
- **创新性**：首次将分解式NAS成功应用于数十亿参数级LLM，结合BLD和MIP，实现硬件感知的高效优化。
- **实用性**：可针对不同硬件（如H100、RTX 4090）、不同约束（吞吐、内存、延迟）快速生成部署模型，且支持FP8和实际推理引擎。
- **低训练成本**：仅需父模型权重，不需要训练数据，适合“开源权重、闭源数据”场景。
- **消融充分**：对每个设计决策（块构建、评分、搜索、数据、损失）都进行了详细分析和验证。
- **可扩展性**：框架可推广到其他架构（如Mamba、多模态）和更大模型（已在405B上验证）。

## 8. 不足与局限
- **搜索空间限制**：当前仅支持替换为同维度子块，不支持变维嵌入，且未融合更多现代操作（如状态空间模型、可变窗口注意力）。
- **长上下文能力退化**：Nemotron-51B在超过16K token时性能下降明显，需要通过长上下文微调恢复。
- **对比不够全面**：与最新剪枝/蒸馏方法（如Minitron、ShearedLlama、SliceGPT等）缺乏直接比较；仅与Wanda和低秩方法对比，且这些方法未得到后续蒸馏提升的公平机会。
- **资源细节模糊**：未明确BLD和GKD训练所需GPU数量和时间，难以精确评估实际算力成本。
- **泛化性验证不足**：仅在Llama系列和部分模型上验证，未在更多架构（如Mistral、Gemma）上展示。
- **训练数据偏移风险**：蒸馏混合数据集可能与下游任务分布不完全匹配，可能引入偏差，但作者未详细分析。

（完）
