---
title: "xLSTM 7B: A Recurrent LLM for Fast and Efficient Inference"
title_zh: xLSTM 7B：用于快速高效推理的递归大语言模型
authors: "Maximilian Beck, Korbinian Pöppel, Phillip Lippe, Richard Kurle, Patrick M Blies, Günter Klambauer, Sebastian Böck, Sepp Hochreiter"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=LV3DpKD08B"
tags: ["query:edge-llm"]
score: 5.0
evidence: 递归LLM架构实现快速推理和恒定内存
tldr: 针对LLM推理速度和内存效率需求，提出基于xLSTM架构的7B参数模型。该递归架构具有序列长度线性计算缩放和恒定内存特点，在保持竞争力的同时实现更快推理。与Transformer模型对比，在推理吞吐量上展示优势，适合资源受限场景。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 843, \"height\": 575, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1790, \"height\": 714, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 634, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 873, \"height\": 640, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 876, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 874, \"height\": 526, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 865, \"height\": 651, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1079, \"height\": 1616, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1791, \"height\": 648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1785, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1786, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1784, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 906, \"height\": 691, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 822, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 823, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 814, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 823, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 815, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lv3dpkd08b/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 821, \"height\": 475, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-lv3dpkd08b/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1837, \"height\": 933, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lv3dpkd08b/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 843, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lv3dpkd08b/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 873, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lv3dpkd08b/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 834, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lv3dpkd08b/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1448, \"height\": 462, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lv3dpkd08b/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1778, \"height\": 615, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lv3dpkd08b/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1779, \"height\": 437, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lv3dpkd08b/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1777, \"height\": 342, \"label\": \"Table\"}]"
motivation: 现有Transformer推理慢，内存开销随序列增长。
method: 基于xLSTM架构，实现线性计算缩放和恒定内存。
result: 在推理吞吐量上优于同等规模Transformer模型。
conclusion: xLSTM 7B是一种高效推理的递归LLM替代方案。
---

## Abstract
Recent breakthroughs in solving reasoning, math and coding problems with Large Language Models (LLMs) have been enabled by investing substantial computation budgets at inference time. Therefore, inference speed is one of the most critical properties of LLM architectures, and there is a growing need for LLMs that are efficient and fast at inference. Recently, LLMs built on the xLSTM architecture have emerged as a powerful alternative to Transformers, offering linear compute scaling with sequence length and constant memory usage, both highly desirable properties for efficient inference. However, such xLSTM-based LLMs have yet to be scaled to larger models and assessed and compared with respect to inference speed and efficiency. In this work, we introduce xLSTM 7B, a 7-billion-parameter LLM that combines xLSTM’s architectural benefits with targeted optimizations for fast and efficient inference. Our experiments demonstrate that xLSTM 7B achieves performance on downstream tasks comparable to other similar-sized LLMs, while providing significantly faster inference speeds and greater efficiency compared to Llama- and Mamba-based LLMs. These results establish xLSTM 7B as the fastest and most efficient 7B LLM, offering a solution for tasks that require large amounts of test-time computation. Our work highlights xLSTM’s potential as a foundational architecture for methods building on heavy use of LLM inference. Our model weights, model code and training code are open-source.
Model: https://huggingface.co/NX-AI/xLSTM-7b
Code: https://github.com/NX-AI/xlstm and
https://github.com/NX-AI/xlstm-jax.

---

## 论文详细总结（自动生成）

# xLSTM 7B 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在推理（inference）时计算开销巨大，尤其是Transformer架构的KV缓存随序列长度线性增长，导致生成速度慢、内存占用高。随着测试时计算扩展（test-time compute scaling）成为提升模型推理能力（如数学、代码）的关键手段，对推理效率和速度的需求日益迫切。
- **研究动机**：现有线性递归神经网络架构（如Mamba、RWKV、xLSTM）虽具备线性计算缩放和恒定内存的优点，但xLSTM此前仅被验证到1.3B参数规模，未经过大规模训练和推理效率的系统评估。本文旨在将xLSTM扩展到7B参数，并针对推理速度和训练效率进行优化，验证其作为高效递归LLM的潜力。
- **整体含义**：提出并开源了xLSTM 7B模型，在保持与同等规模Transformer和Mamba模型竞争下游性能的同时，实现了更快的推理速度和更低的显存消耗，尤其适合需要大量测试时计算或边缘部署的场景。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：基于xLSTM架构中的mLSTM单元，通过修改块结构、优化训练稳定性和融合推理内核，实现高效的训练和推理。
- **关键技术细节**：
  - **块结构优化（post-up projection block）**：将mLSTM操作在模型嵌入维度（而非更高维度）上运行，并添加位置前馈SwiGLU MLP层，增加高度优化的矩阵乘法的FLOPs比例，减少mLSTM计算开销。替代原先的pre-up projection块，并丢弃通道卷积和可学习跳跃连接。
  - **多头部mLSTM**：使用8个头，每个头的维度dhv=512，查询/键维度dqk=dhv/2，总记忆状态大小约为134.2 MB。
  - **训练稳定性优化**：
    - 使用RMSNorm替代LayerNorm作为预归一化层。
    - 对输入门和遗忘门预激活进行soft-capping（a=15），对最终logits也进行soft-capping（a=30）。
    - 输入门偏置初始化为-10，以抑制早年的梯度尖峰。
  - **融合生成内核**：编写定制的Triton内核，将mLSTM递归模式下的多个操作融合，减少GPU内核启动和内存传输。
  - **序列打包与内存重置**：在打包多个文档时，通过将遗忘门设为0来在文档边界重置记忆状态。
- **公式或算法流程**（文字说明）：
  - 递归模式（生成）：给定输入xt和上一时间步的隐状态ht-1、细胞状态Ct-1、归一化状态nt-1、最大值状态mt-1，通过输入门、遗忘门、输出门的指数/ sigmoid激活更新记忆，并计算当前隐状态ht。
  - 并行模式（训练）：利用线性递归性质，通过分块并行计算整个序列的隐藏状态，无需物化中间记忆状态，类似于FlashLinearAttention。

## 3. 实验设计：数据集 / 场景、benchmark、对比方法

- **预训练数据集**：
  - 主要使用DCLM数据集（2.3T tokens），训练上下文长度8192。
  - 第二阶段（cool-down）加入FineWeb-Edu、Cosmopedia、ProofPile-2、TheStack、SFT数据集（NuminaMath、MetaMathQA、Tulu v3.1、OpenHermes 2.5、GSM8K、Smoltalk等）。
  - 长上下文版本（xLSTM 7B LCTX）用32K上下文训练，额外的长上下文数据包括LongDataCollections、LongAlign10k、AntiHayStack、LongAlpaca12k。
- **Benchmark**：
  - 语言下游性能：Open LLM Leaderboard v2（BBH、MMLU-PRO、MATH、MUSR、GPQA、IFEval）和v1（ARC-C、MMLU、HellaSwag、Winogrande、TruthfulQA、OpenBookQA、PIQA）。
  - 长上下文评估：RULER基准（4K到131K token的合成任务）。
  - 速度基准：单张NVIDIA H100 GPU，batch size=1，测量生成吞吐量、生成时间与内存、首Token时间、预填充吞吐量。
- **对比方法**：
  - Transformer：Llama-3.1-8B、Llama-2-7B、OLMo-7B、Gemma-7B、Ministral-8B、Bloom-7B1、GPT-J-6B、Pythia-6.9B、Qwen2.5-7B、Gemma-2-9B、DCLM-7B。
  - 混合递归模型：Zamba2-7B。
  - 纯递归模型：Falcon-Mamba-7B（含pre-decay版本）、MambaCodestral-7B（v0.1）、RWKV-v5-Eagle-7B、RWKV-v6-Finch-7B。

## 4. 资源与算力

- **训练硬件**：128块NVIDIA H100 GPU。
- **训练总token数**：2.3T tokens。
- **训练步数**：550K步（前2000步batch size 128，再2000步batch size 256，之后512；linear warmup 3000步，指数衰减54万步，线性cool-down 7000步）。
- **优化器**：AdamW（lr=5e-4，β1=0.99，β2=0.95，weight decay 0.1，gradient clipping=0.5）。
- **其他**：使用FSDP和激活检查点减少显存。

## 5. 实验数量与充分性

- **实验组数**：
  - 主训练：一次7B模型完整训练（2.3T tokens）。
  - 消融实验（160B tokens/76K步）：
    - 块结构对比（pre-up vs post-up，三个规模：160M、400M、1.4B、7B）。
    - 头数量消融（4、8、16、32 heads）。
    - 归一化层类型（LayerNorm vs RMSNorm）。
    - Soft-capping有无。
    - 输入门偏置初始化（0、-2、-5、-10）。
    - 学习率调度器（指数衰减 vs 余弦）。
    - 固定输入门实验。
  - 速度对比：多个配置（预填充长度、生成长度、batch size）。
  - 长上下文：标准xLSTM 7B和LCTX版本在RULER上的对比。
- **充分性评价**：
  - **公平性**：所有对比模型均使用相同或官方实现，速度测试中使用torch.compile、CUDA Graphs优化所有模型，并在附录中与vLLM框架对比，尽量排除实现差异。
  - **客观性**：使用标准benchmark（LM Evaluation Harness）和公开数据集，结果可复现。
  - **覆盖范围**：涵盖下游任务、长上下文、推理速度、内存、预填充吞吐量等多个维度，消融实验覆盖了架构关键组件。但消融实验仅训练160B tokens（不到完整训练的1/14），规模较小，可能存在不稳定性。另外未与更大规模模型（如70B）对比。

## 6. 论文的主要结论与发现

- **核心结论**：xLSTM 7B在7B参数规模的LLM中实现了**最快的推理速度和最高的效率**，同时在下游任务上达到与Transformer和Mamba相当的竞争力。
- **具体发现**：
  - 优化的post-up projection块带来3.5×训练加速，仅轻微增加验证困惑度。
  - 在RULER长上下文评估中，xLSTM 7B LCTX（32K训练）在131K上下文时仍能达到20%平均准确率，展示出良好的外推能力。
  - 与Mamba相比，xLSTM 7B生成速度快约50%，显存消耗更低。
  - 与Llama相比，生成速度不随预填充长度下降，且恒定内存。
  - 预填充吞吐量比Codestral Mamba高约70%。
  - 消融实验证实了soft-capping、负输入门偏置初始化、RMSNorm对稳定性和性能的必要性。

## 7. 优点

- **创新性**：将xLSTM架构成功扩展到7B级别，并针对训练和推理效率做了实质性优化（块结构、门限软上限、融合内核）。
- **实用性**：开源模型权重、代码和训练代码，便于社区复现和应用。
- **推理性能突出**：在单GPU、batch size=1的设置下，生成速度、首Token时间、内存消耗均优于同等规模的Transformer和Mamba，非常适合边缘设备和实时交互。
- **实验全面且公平**：速度对比中统一优化所有基线（torch.compile、CUDA Graphs），并加入vLLM对比，减少实现偏差。
- **稳定性贡献**：提出了针对xLSTM的稳定训练技巧（gate soft-capping、输入门偏置初始化），并验证其在7B规模的有效性。

## 8. 不足与局限

- **下游性能非最优**：在Open LLM Leaderboard v2上，xLSTM 7B的平均得分（0.260）低于Qwen2.5-7B（0.379）、Gemma-2-9B（0.346）等，仅处于中游。作者承认需要更大、更精心的训练数据（尤其是数学和代码）才能匹配最强模型。
- **消融实验规模有限**：消融实验仅基于160B tokens，可能无法完全反映完整2.3T训练下的规律。例如头数量消融中，不同头数差异不大，但长上下文表现上8头稍好，缺乏更大训练量的验证。
- **长上下文能力有提升空间**：xLSTM 7B LCTX在131K上下文准确率仅20%，远低于Llama 3 8B（后者经过专门的长上下文微调），尽管作者指出记忆容量有限是固有约束。
- **缺乏与纯Transformer最大模型的对比**：未与最新70B+模型对比，也未讨论架构在更大规模下的可扩展性。
- **未涉及指令微调效果**：论文仅报告预训练模型性能，未展示经过SFT/RLHF后的表现，而实际应用中微调是常见步骤。
- **推理速度对比的局限性**：速度测试在单GPU、batch size=1上进行，未测试高并发推理场景（如服务集群）。xLSTM递归模式可能不适合连续批处理（continuous batching），而vLLM对Transformer的优化更成熟。

（完）
