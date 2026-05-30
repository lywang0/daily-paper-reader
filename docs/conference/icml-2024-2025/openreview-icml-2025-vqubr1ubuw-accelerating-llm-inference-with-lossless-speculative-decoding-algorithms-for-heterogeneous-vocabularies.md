---
title: Accelerating LLM Inference with Lossless Speculative Decoding Algorithms for Heterogeneous Vocabularies
title_zh: 面向异构词表的无损推测解码算法加速LLM推理
authors: "Nadav Timor, Jonathan Mamou, Daniel Korat, Moshe Berchansky, Gaurav Jain, Oren Pereg, Moshe Wasserblat, David Harel"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=vQubr1uBUw"
tags: ["query:edge-llm"]
score: 7.0
evidence: 异构词表下的无损推测解码，加速LLM推理
tldr: 本文提出三种无损推测解码方法，消除了草稿模型与目标模型必须共享词表的限制。这些方法无需额外训练或修改即可与现成模型配合使用，在总结、编程等任务上实现了显著加速，同时保证了输出分布的无损性，为LLM推理加速提供了更灵活高效的方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有推测解码要求草稿模型与目标模型共享词表，限制了草稿模型的选择，通常需要从头训练。
method: 提出三种无需共享词表的无损推测解码方法，支持现成模型作为草稿，无需额外训练。
result: 在多种任务上的实验表明，该方法有效加速了推理，同时保持了输出分布的无损性。
conclusion: 通过打破词表限制，为LLM推理加速提供了更灵活的方案。
---

## Abstract
Accelerating the inference of large language models (LLMs) is a critical challenge in generative AI. Speculative decoding (SD) methods offer substantial efficiency gains by generating multiple tokens using a single target forward pass. However, existing SD approaches require the drafter and target models to share the same vocabulary, thus limiting the pool of possible drafters, often necessitating the training of a drafter from scratch. We present three new SD methods that remove this shared-vocabulary constraint. All three methods preserve the target distribution (i.e., they are lossless) and work with off-the-shelf models without requiring additional training or modifications. Empirically, on summarization, programming, and long-context tasks, our algorithms demonstrate significant speedups of up to 2.8x over standard autoregressive decoding. By enabling any off-the-shelf model to serve as a drafter and requiring no retraining, this work substantially broadens the applicability of the SD framework in practice.

---

## 论文详细总结（自动生成）

# 面向异构词表的无损推测解码算法加速LLM推理——中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有推测解码（Speculative Decoding, SD）方法要求草稿模型（drafter）与目标模型（target）必须共享相同的词表（vocabulary），这极大限制了草稿模型的选择范围。实践中，许多目标模型没有同族小型模型可用，或者需要从头训练专用草稿，成本高昂且无法复用。
- **整体含义**：本文提出三种**不需要共享词表**的**无损**推测解码算法，允许任意现成模型（off-the-shelf）作为草稿，无需额外训练或修改目标模型，从而显著拓宽SD的适用范围，并提供实际加速效果。

## 2. 论文提出的方法论

### 核心思想
- **打破词表同构限制**：通过字符串级中间表示或词表交集投影，实现不同词表间的通信。
- **三种算法**：
  1. **SLEM（String-Level Exact Match，算法2）**：将草稿生成的多token序列解码为文本，再用目标词表重新分词（re-tokenize），执行**精确匹配**验证。假设目标词表可被草稿词表表达且反之亦然（常见于实际分词器）。通过“回看对齐”机制处理非单射分词器。
  2. **TLI（Token-Level Intersection，算法4）**：将草稿分布投影到**两词表的交集**上（重新归一化），然后使用标准SD的拒绝采样验证。理论证明其接受率总不低于简单取并集的方法（算法1）。
  3. **SLRS（String-Level Rejection Sampling，算法3）**：在字符串级别执行拒绝采样，计算每个目标token被接受的概率ψ(t)（需枚举所有可能的分词序列）。理论上无损且接受率高于SLEM，但ψ(t)的计算量随token长度指数增长（引理3.1），仅适用于短token的草稿（如MambaByte）。

### 关键技术细节（文字描述）
- **SLEM流程**：① 将prompt用草稿词表分词；② 草稿自回归生成i个token并解码为文本；③ 用目标词表重新分词得到m个目标token；④ 目标模型并行计算m+1个位置的logits并采样；⑤ 寻找第一个不一致的位置，接受之前的一致token。
- **TLI流程**：将草稿分布q限制到T∩D上，再归一化，然后运行标准SD。
- **SLRS流程**：草稿生成直至满足停止条件，解码后重新分词，然后基于ψ(t)执行拒绝采样。

## 3. 实验设计

- **任务与数据集**：
  - 文本摘要：CNN/DailyMail
  - 代码生成：OpenAI HumanEval
  - 长上下文：SCROLLS
- **Benchmark**：对比**自回归解码（AR）**、标准SD（若有同族草稿）、以及本文的SLEM和TLI。
- **模型组合**：广泛覆盖，目标模型包括Mixtral-8x22B、DeepSeek-R1-Distill系列、phi-4、CodeLlama-13B、Gemma-2-9B等；草稿模型包括Qwen2.5-0.5B、tiny starcoder py、vicuna-68m、Llama-3.2-1B、Phi-3.5-mini等。注意许多组合中目标模型没有同族小型草稿（或同族但词表不同），如phi-4 + Phi-3.5-mini。

## 4. 资源与算力

- **GPU型号与数量**：
  - H100 NVL（1~4卡）
  - RTX 6000（1卡）
  - A6000（1卡）
  - A100 80GB PCIe（2卡）
- **训练**：**无需训练**，推理实验时间未单独报告。
- **备注**：论文未提供总计算耗时，但给出了每一步延迟（TTFT、TPOT），可估算推理成本。

## 5. 实验数量与充分性

- **实验组数**：
  - 表1（SLEM）：8个目标模型×多个草稿×3个数据集，约20+条记录。
  - 表2（TLI）：类似规模。
  - 附录D（表6、表7）补充更多组合（包括同族草稿如Gemma-2-2b）。
- **充分性**：
  - 覆盖了不同规模、不同分词器家族（BPE、SentencePiece、Unigram）的模型。
  - 考量了不同硬件（单卡/多卡、不同GPU型号）。
  - 提供了TTFT（首token延迟）、TPOT（每个输出token延迟）、Tokens/s、Speedup等多维度指标。
  - 同时展示了加速成功（最高2.8×）和失败（加速比<1）的案例，客观反映局限性。
- **公平性**：统一采用Hugging Face Transformers实现，温度设置明确（SLEM用0温度，TLI用1温度），与AR同条件对比。

## 6. 论文的主要结论与发现

- **SLEM和TLI在异构词表下依然有效**：在多个任务上获得1.2×~2.8×加速，尤其当草稿模型准确且速度够快时。
- **无需训练即可加速**：相比于训练专用草稿（如FastDraft），本文方法无需任何数据或计算资源。
- **已集成到主流库**：SLEM和TLI已被Hugging Face Transformers采纳为异构SD的默认算法（2024年10月和2025年2月）。
- **理论保证**：所有方法均为无损（lossless），且给出了接受率公式和约束条件。

## 7. 优点

- **创新性**：最早系统性解决SD中词表异构问题，提出三种不同策略，理论分析完整。
- **实用性**：无需训练，直接使用现成模型，极大降低部署门槛；集成到Hugging Face，影响广泛。
- **理论深度**：给出接受率上界（定理3.1、4.1）、计算复杂度分析（引理3.1）、约束条件表（表4）。
- **实验全面**：涵盖多种模型族、任务、硬件，并公开代码，可复现。
- **处理实际分词器问题**：对非单射分词器提出了“回看对齐”机制，增强了算法鲁棒性。

## 8. 不足与局限

- **依赖草稿质量**：所有SD方法一样，若草稿不准确或速度不够，加速可能微乎其微甚至倒退（论文中展示了一些<1的案例）。
- **SLRS计算开销大**：ψ(t)枚举随token长度指数爆炸，实际难以应用（仅适合短token草稿，如MambaByte）。
- **TLI依赖词表交集**：若交集很小，接受率低下；尽管实践中非空，但可能不总是充分。
- **SLEM假设词表双向可表达**：虽常见，但极端情况（如小词表缺少某些字符）可能失效。
- **实验未覆盖所有场景**：未测试多轮对话、流式场景，以及对超大模型（>100B）的扩展性。
- **非单射分词器处理不够优雅**：回看机制可能损失部分已接受的token，影响效率。
- **缺乏与传统SD（同词表）的定量对比**：论文主要展示异构加速，对同族草稿标准SD的对比仅限少数案例（如Gemma），未充分说明异构相对同族的劣势或优势。

（完）
