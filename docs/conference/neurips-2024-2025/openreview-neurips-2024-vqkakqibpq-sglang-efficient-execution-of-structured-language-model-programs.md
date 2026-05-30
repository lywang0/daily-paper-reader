---
title: "SGLang: Efficient Execution of Structured Language Model Programs"
title_zh: SGLang：结构化语言模型程序的高效执行
authors: "Lianmin Zheng, Liangsheng Yin, Zhiqiang Xie, Chuyue Sun, Jeff Huang, Cody Hao Yu, Shiyi Cao, Christos Kozyrakis, Ion Stoica, Joseph E. Gonzalez, Clark Barrett, Ying Sheng"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=VqkAKQibpq"
tags: ["query:edge-llm"]
score: 9.0
evidence: 结构化语言模型程序的高效执行系统，服务于框架
tldr: 现有系统缺乏对大语言模型复杂任务（多步生成、控制流等）的高效编程和执行支持。SGLang提供前端语言和运行时，通过RadixAttention实现KV缓存复用和压缩有限状态机加速结构化输出解码。实验表明，SGLang相比基线实现高达6.4倍吞吐量提升。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1380, \"height\": 137, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1405, \"height\": 951, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1419, \"height\": 1094, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1428, \"height\": 312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1425, \"height\": 262, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1426, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1429, \"height\": 263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1416, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1456, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1445, \"height\": 594, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1384, \"height\": 586, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1432, \"height\": 258, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1430, \"height\": 257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 687, \"height\": 663, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-vqkakqibpq/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 695, \"height\": 796, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-vqkakqibpq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1298, \"height\": 200, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-vqkakqibpq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1414, \"height\": 1568, \"label\": \"Table\"}]"
motivation: 缺乏高效执行复杂LLM程序的系统。
method: 设计前端语言和运行时，包含RadixAttention和压缩有限状态机等优化。
result: 相比基线实现高达6.4倍吞吐量提升。
conclusion: SGLang通过系统级优化实现了结构化LLM程序的高效执行。
---

## Abstract
Large language models (LLMs) are increasingly used for complex tasks that require multiple generation calls, advanced prompting techniques, control flow, and structured inputs/outputs. However, efficient systems are lacking for programming and executing these applications. We introduce SGLang, a system for efficient execution of complex language model programs. SGLang consists of a frontend language and a runtime. The frontend simplifies programming with primitives for generation and parallelism control. The runtime accelerates execution with novel optimizations like RadixAttention for KV cache reuse and compressed finite state machines for faster structured output decoding. Experiments show that SGLang achieves up to $6.4\times$ higher throughput compared to state-of-the-art inference systems on various large language and multi-modal models on tasks including agent control, logical reasoning, few-shot learning benchmarks, JSON decoding, retrieval-augmented generation pipelines, and multi-turn chat. The code is publicly available at https://github.com/sgl-project/sglang.

---

## 论文详细总结（自动生成）

# SGLang: 结构化语言模型程序的高效执行系统 — 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）正在被用于越来越复杂的任务，这些任务往往需要多次生成调用、高级提示技术（如分支-求解-合并、思维树等）、控制流以及结构化输入/输出。然而，现有的编程和推理系统缺乏对这些“语言模型程序”（LM Program）的高效支持。
- **核心问题**：
  - **编程困难**：开发LM程序需要大量字符串操作、实验性提示调优、脆弱的输出解析、多模态输入处理和并行机制实现，可读性差。
  - **执行低效**：现有推理引擎（如vLLM、TGI、TensorRT-LLM）未针对多调用结构优化，导致大量冗余计算和内存使用。例如，KV缓存无法跨调用复用；结构化输出约束解码只能逐token进行，速度慢。
- **整体含义**：提出SGLang系统，通过前端语言和后端运行时的协同设计，系统性地利用LM程序中的多调用结构来提升编程效率和执行性能。

## 2. 论文提出的方法论：核心思想与关键技术

### 2.1 核心思想
- **前端语言**（SGLang语言）：嵌入Python的领域特定语言，提供生成原语（`gen`、`select`、`extend`）和并行控制原语（`fork`、`join`），兼容Python语法，简化多调用工作流的编程。
- **后端运行时**（SGLang Runtime, SRT）：包含三个关键优化技术，加速执行。

### 2.2 关键技术细节
1. **RadixAttention（KV缓存复用）**
   - **核心**：将KV缓存视为传统缓存，用一个基数树结构管理。缓存所有请求的KV缓存（而不是丢弃），支持高效的共享前缀匹配、插入、淘汰（LRU策略）。
   - **树结构优势**：支持多级复用（如系统提示、对话历史、few-shot示例、思维树分支），覆盖各种复用模式。
   - **缓存感知调度**：按最长共享前缀优先排序等待请求，近似深度优先搜索顺序，最大化缓存命中率。提供理论证明（定理3.1）：离线情况下DFS顺序可达最优命中率。
   - **前端提示**：解释器在`fork`时发送前缀提示，帮助运行时正确插入树，体现前后端协同设计。
   - **分布式扩展**：支持张量并行和数据并行（每个worker维护子树，路由器维护元树）。

2. **压缩有限状态机（加速结构化输出解码）**
   - **背景**：约束解码（如JSON格式）需将正则表达式转为FSM，当前系统逐token解码，效率低。
   - **方法**：将原始FSM中的单一路径边（只有一个后继且只有一个合法字符的边）压缩为一条边，从而在解码时一次forward pass可生成多个token（跳转解码）。
   - **处理token化问题**：压缩边对应的字符串需用原始tokenizer重新分词，保证与LLM输入格式一致。
   - **优势**：通用性，适用于所有正则表达式。

3. **API推测执行（针对API-only模型，如GPT-4）**
   - **动机**：多个连续`gen`调用会导致重复API调用，重复支付输入token费用。
   - **方法**：在第一个`gen`调用中允许模型继续生成额外token（忽略停止条件），然后匹配这些额外输出用于后续`gen`调用，从而减少一次API调用和输入成本。

### 2.3 执行模式
- 解释器模式：默认，异步流式执行，支持程序内并行。
- 编译器模式：可转化为计算图，进行图优化（如代码移动以增加共享前缀长度）。

## 3. 实验设计

### 3.1 数据集与场景
- **任务类型**：5-shot MMLU、20-shot HellaSwag、ReAct Agent、Generative Agents、Tree-of-Thought（GSM-8K）、Skeleton-of-Thought（tip生成）、LLM Judge（分支-求解-合并）、JSON解码、多轮对话（短输出/长输出）、DSPy RAG流水线。
- **多模态**：LLaVA-v1.5-7B（图像，llava-bench-in-the-wild）、LLaVA-NeXT-34B（视频，ActivityNet）。
- **API模型**：OpenAI GPT-3.5（提取Wikipedia字段）。

### 3.2 Benchmark与对比方法
- **基线系统**：
  - Guidance（v0.1.8，llama.cpp后端）
  - vLLM（v0.2.5，默认API服务器）
  - LMQL（v0.7.3，HuggingFace Transformers后端）
  - 对于多模态模型，使用作者原始HuggingFace实现作为基线。
- **指标**：吞吐量（programs/s）、延迟（单程序平均延迟）。

### 3.3 消融实验
- 缓存命中率 vs. 延迟/吞吐量关系（通过部分禁用匹配token实现）。
- RadixAttention组件消融：无缓存、无树结构（表缓存）、FCFS调度、随机调度、无前端并行、无前端提示、完全优化。
- 压缩FSM组件消融：是否启用压缩、是否预计算FSM。
- 缓存感知调度开销测量（ShareGPT数据集，无复用机会）。

## 4. 资源与算力

- **GPU型号**：NVIDIA A10G（24GB）、A100G（80GB）。
- **模型规模**：
  - Llama-7B：单张A10G
  - Mixtral-8x7B：8张A10G（张量并行）
  - Llama-70B：4张A100G（80GB）
  - LLaVA-v1.5-7B：单张A10G
  - LLaVA-NeXT-34B：单张A100G（80GB）
- **精度**：float16。
- **算力说明**：未明确报告训练时长或总GPU小时数，但每个benchmark运行数分钟到一小时。分布式RadixAttention使用4个worker测试线性扩展。

## 5. 实验数量与充分性

- **实验数量**：约15个benchmark（涵盖零样本、少样本、多轮、多模态、约束解码、Agent等），加上生产环境部署（Chatbot Arena一个月观测）。消融实验3组，每个组件逐一验证。
- **充分性**：实验覆盖了主流LLM应用场景，对比了最先进推理系统和类似编程系统（Guidance、LMQL）。消融实验充分验证了各组件贡献。公平性方面：关闭所有改变计算结果的优化，保证同精度比较。但未提供误差棒或统计显著性检验（论文解释结果高度确定性）。
- **局限性**：缺失对更大模型（如175B规模）的测试；每个benchmark只报告了平均结果，未提供方差或多次运行结果。

## 6. 主要结论与发现

- **吞吐量提升**：相比基线系统，SGLang在Llama-7B上实现最高6.4倍吞吐量提升，延迟降低最多3.7倍。
- **多模型泛化**：在Mixtral-8x7B、Llama-70B和多模态模型上效果类似。
- **KV缓存复用效果**：缓存命中率范围50%~99%，平均达到最优命中率的96%。缓存感知调度是关键。
- **压缩FSM**：JSON解码吞吐量提升1.6倍，预计算FSM可避免2.4倍性能损失。
- **生产部署**：在Chatbot Arena，RadixAttention命中率52.4%~74.1%，首token延迟降低1.7倍。
- **API推测执行**：对GPT-3.5的字段提取任务，减少约3倍输入token成本。
- **系统设计**：前后端协同是性能增益的重要因素（关闭前端提示或前端并行会导致显著下降）。

## 7. 优点

- **系统性创新**：首次将KV缓存作为树结构LRU缓存管理，支持多级复用，配合缓存感知调度，理论最优性证明。
- **前后端协同设计**：前端原语（fork等）发送提示，帮助运行时优化前缀匹配，实现端到端优化。
- **通用性**：优化不依赖特定模型架构，可兼容连续批处理、分页注意力、张量/数据并行等现有技术。
- **结构化输出加速**：压缩FSM方法通用且高效，只需一次预处理即可复用给批量请求。
- **多模态支持**：通过图像哈希实现KV缓存复用，支持LLaVA等模型。
- **实用性**：代码开源，已部署于生产环境Chatbot Arena。

## 8. 不足与局限

- **实验覆盖不足**：
  - 未测试更大规模模型（如GPT-3 175B或PaLM类）。
  - 缺乏统计显著性检验（如误差棒）。
  - 仅使用A10G和A100G GPU，未覆盖更多硬件（如AMD、Intel GPU）。
- **方法局限性**：
  - **RadixAttention**：只支持exact token-level前缀匹配，不支持模糊语义匹配；LRU淘汰可能造成长序列中前缀被意外驱逐；存在饥饿问题（论文提及未来工作）。
  - **压缩FSM**：压缩边可能导致概率分布失真（如对应多个选择时无法准确计算概率），需要进一步研究。
  - **API推测执行**：依赖prompt工程确保模型匹配模板，准确率不是100%。
  - **编译器模式**：仅能处理无数据依赖控制流的程序，实际应用受限。
- **公平性风险**：缓存感知调度优先考虑长共享前缀，可能造成请求饥饿（论文提及需结合公平调度）。
- **对比基线选择**：vLLM使用较早版本（v0.2.5），未包含最新的RadixAttention功能，可能低估其后续性能。
- **未报告**：训练能耗、端到端成本分析、安全性或偏见讨论。

（完）
