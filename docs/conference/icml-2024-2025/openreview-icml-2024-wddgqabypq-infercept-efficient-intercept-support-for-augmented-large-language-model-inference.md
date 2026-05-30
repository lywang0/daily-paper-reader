---
title: "InferCept: Efficient Intercept Support for Augmented Large Language Model Inference"
title_zh: InferCept：增强型大语言模型推理的高效截断支持
authors: "Reyna Abhyankar, Zijian He, Vikranth Srivatsa, Hao Zhang, Yiying Zhang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=wDDGQabYPQ"
tags: ["query:edge-llm"]
score: 6.0
evidence: 面向增强LLM的推理框架
tldr: "现有推理系统未优化增强LLM（如工具调用），导致大量冗余计算。本文提出InferCept，首个面向增强LLM的推理框架，支持高效截断生成，减少37-40%的模型前向时间。它最小化GPU资源浪费并将节省的内用于服务更多请求。"
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-wddgqabypq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1763, \"height\": 773, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wddgqabypq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1766, \"height\": 987, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wddgqabypq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 840, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wddgqabypq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1780, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wddgqabypq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1785, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-wddgqabypq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1073, \"height\": 558, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-wddgqabypq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 259, \"label\": \"Table\"}]"
motivation: 增强LLM因外部交互导致不必要重计算，浪费资源。
method: 设计拦截机制，在LLM生成过程中高效暂停并复用上下文。
result: "减少37-40%模型前向时间，提升吞吐量。"
conclusion: InferCept填补了增强LLM推理系统的空白，显著提升效率。
---

## Abstract
Large language models are increasingly integrated with external environments, tools, and agents like ChatGPT plugins to extend their capability beyond language-centric tasks. However, today's LLM inference systems are designed for standalone LLMs. They treat each external interaction as the end of LLM generation and form a new request when the interaction finishes, causing unnecessary recomputation of already computed contexts, which accounts for 37-40% of total model forwarding time. This paper presents **InferCept, the first LLM inference framework targeting augmented LLMs** and supporting the efficient interception of LLM generation. InferCept minimizes the GPU resource waste caused by LLM interceptions and dedicates saved memory for serving more requests.InferCept improves the overall serving throughput by **1.6x-2x** and completes 2x more requests per second compared to the state-of-the-art LLM inference systems.

---

## 论文详细总结（自动生成）

# 论文总结：InferCept: 增强型大语言模型推理的高效截断支持

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）越来越多地与外部环境、工具和智能体（如ChatGPT插件）集成，以扩展其能力。然而，现有LLM推理系统是为独立LLM设计的，在处理外部交互（如工具调用、等待人类响应）时，错误地将每次外部交互视为LLM生成的结束点，并在交互完成后形成新的请求。这导致已经计算过的上下文（KV缓存）被不必要地重新计算，约占模型前向总时间的37-40%。
- **背景问题**：增强型LLM的截断（interception）具有独特性质：截断时间变化极大（从毫秒到分钟），上下文长度和截断次数各异，且截断期间上下文无法使用但之后又需要。现有系统（如vLLM）采用“丢弃”策略，导致大量GPU资源浪费；简单扩展如“保留”或“交换”也存在内存占用或带宽瓶颈。
- **整体含义**：需要一个专门针对增强型LLM、能够高效处理截断的推理系统，以最小化GPU内存浪费，提升整体服务吞吐量。

## 2. 论文提出的方法论

### 核心思想
**最小浪费截断（min-waste interception）**：通过动态选择最优策略（保留、丢弃或交换）处理截断请求的上下文，最小化GPU内存浪费，从而用相同GPU资源服务更多请求。

### 关键技术细节
1. **三种基础策略的浪费量化**：
   - **Discard（丢弃）**：浪费 = 重计算时间 × 上下文内存 + 增加迭代时间导致其他请求内存浪费。
   - **Preserve（保留）**：浪费 = 截断持续时间 × 上下文内存。
   - **Swap（交换）**：浪费 = 2 × 交换时间 × 总批次内存（进出各一次）。

2. **优化交换（Swap）**：
   - **交换流水线（Swap Pipelining）**：将每层KV缓存交换视为一个流水线阶段，与模型前向计算重叠。
   - **交换分块（Swap Chunking）**：将序列交换拆分为多个迭代，每迭代交换量不超过GPU-CPU链路带宽预算，使交换延迟被模型前向隐藏。

3. **优化重计算（Recomputation）**：
   - **重计算分块（Recomputation Chunking）**：将上下文重计算分成多个块，每个块的大小不超过GPU饱和点（GPU Saturation Point，即GPU核心能并行处理的查询令牌数），从而与其他解码请求混合执行，提高GPU利用率并减少单次迭代时间。

4. **请求间动作调度**：
   - **截断调度**：对每个截断请求计算其保留浪费和分块丢弃浪费的最小值，按浪费降序排序，优先用交换预算交换高浪费请求，其余根据比较结果选择保留或丢弃。
   - **恢复调度**：维护运行队列、交换队列和等待队列，按FCFS（先到先服务）顺序选择请求加入批次，确保公平性。

5. **截断持续时间估计**：
   - 对于可变或未预配置的截断，动态估计 \(\hat{T}_{INT} = t_{now} - t_{call}\)，在混合工作负载下达到Oracle性能的93%。

## 3. 实验设计

### 使用的数据集/场景
论文研究了六种典型增强场景：
- **算术（Math）**：GSM8K-XL数据集，调用计算器工具，截断时间极短（平均0.2 ms）。
- **问答（QA）**：Multihop QA Wikipedia数据集，调用维基百科检索，截断时间中等且因网络延迟有波动。
- **虚拟环境（VE）**：ALFWorld数据集，交互式文本环境，截断时间较短且稳定。
- **聊天机器人（Chatbot）**：ShareGPT数据集，模拟人类对话，截断时间长（平均28.6秒）且方差大。
- **图像生成（Image）**：ChatGPT生成系列提示，调用Stable Diffusion，截断时间长且方差大。
- **文本转语音（TTS）**：类似方法，调用Bark TTS模型。

### Benchmark
- 混合工作负载：均匀采样上述六种场景的请求。
- 单一工作负载：单独测试QA和Chatbot。

### 对比方法
- **vLLM**（原始版本，无截断优化）  
- **ImprovedDiscard**（保持原始到达时间的丢弃策略）  
- **Preserve**（保留上下文）  
- **Swap**（同步交换）  
- **InferCept**（完整系统）

## 4. 资源与算力

- **GPU型号和数量**：NVIDIA A100 GPU。  
  - GPT-J-6B：1个GPU  
  - Vicuna-13B：1个GPU（单卡）或2个GPU（张量并行）  
  - Llama3-70B：4个GPU（张量并行）  
- **训练时长**：论文未提及训练耗时，主要关注推理阶段的性能和调度。  
- **说明**：实验在推理服务场景下进行，不涉及模型训练。

## 5. 实验数量与充分性

- **实验数量**：  
  - 端到端性能实验：在三种模型（6B、13B、70B）及不同GPU配置下，报告了归一化延迟、吞吐量（完成请求/秒）和首令牌时间（TTFT）随请求到达率的变化（图2）。  
  - 技术分解实验：逐步添加各项技术（改善丢弃、分块重计算、预算交换、启发式保留、最小浪费调度），展示对归一化延迟和GPU内存浪费的贡献（图3）。  
  - 单一工作负载实验：QA和Chatbot场景下与vLLM的对比。  
  - 截断持续时间估计准确性实验：动态估计与Oracle对比（93%性能）。  
- **充分性**：实验覆盖了多种模型规模、多种增强场景、多种对比基线，并进行了详细的消融分析。方法足够公平（所有基线采用相同硬件和数据）、客观（报告了关键性能指标）。但缺少与其他调度策略（如FastServe的MLFQ）的对比，且未在更大规模集群（如多节点）上验证。

## 6. 主要结论与发现

- **InferCept显著优于现有系统**：  
  - 在相同归一化延迟下，可持续1.6×-2×更高的请求到达率。  
  - 完成请求数/秒提高2×以上。  
  - 将GPU内存浪费降低至0.69%（对比vLLM的27%）。  
  - 模型越大，改进越明显（70B模型下归一化延迟降低1.3×-12×）。
- **关键发现**：  
  - 没有任何单一策略通用最优，需要动态选择。  
  - 分布式环境（多GPU）下由于模型权重占比降低，KV缓存空间更大，InferCept优势更突出。  
  - 交换流水线和分块可有效隐藏交换延迟，几乎消除浪费。  
  - 重计算分块与解码请求混合，提高GPU利用率。

## 7. 优点

- **方法创新性**：首次提出专门针对增强型LLM截断的推理框架，提出“最小浪费”统一优化目标。
- **技术全面**：同时优化了丢弃、保留、交换三种策略，并引入流水线、分块、动态调度等技术。
- **实验充分**：涵盖多种模型规模、多种增强场景、多种对比基线，并进行了消融分析，证明了各技术贡献。
- **性能提升显著**：在多个指标上均大幅超越现有最优系统。
- **可扩展性**：基于vLLM的PagedAttention实现，模块化设计，易于集成到其他推理系统。
- **对截断时间估计的鲁棒性**：动态估计方法接近Oracle性能。

## 8. 不足与局限

- **实验覆盖不足**：仅使用A100 GPU，未在H100或其他硬件上验证；未测试多节点分布式场景；未与其他高级调度策略（如FastServe的MLFQ）对比。
- **偏差风险**：部分增强场景（如Image、TTS）的执行时间和人类响应时间基于估计或取样，可能不完全反映真实分布。
- **应用限制**：  
  - 假设截断可被“挂起”并后续恢复，但某些工具调用可能要求无状态，需重新设计。  
  - 依赖离线配置（如GPU饱和点、交换预算），对动态波动的适应性有限。  
  - 公平性采用FCFS，可能不适用于需要优先级或SLA差异化的场景。
- **未考虑安全/隐私**：截断期间上下文可能在CPU内存中暴露，未讨论数据保护措施。
- **对非KV缓存上下文（如待处理API返回）的处理**：论文假定上下文仅包含KV缓存，但实际中可能需要管理更多状态。

（完）
