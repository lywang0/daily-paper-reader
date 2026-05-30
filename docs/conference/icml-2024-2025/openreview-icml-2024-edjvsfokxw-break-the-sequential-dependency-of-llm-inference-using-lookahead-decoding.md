---
title: Break the Sequential Dependency of LLM Inference Using Lookahead Decoding
title_zh: 使用Lookahead解码打破LLM推理的顺序依赖
authors: "Yichao Fu, Peter Bailis, Ion Stoica, Hao Zhang"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=eDjvSFOkXw"
tags: ["query:edge-llm"]
score: 7.0
evidence: 并行解码打破顺序依赖，硬件感知加速
tldr: 自回归解码受内存带宽限制，浪费加速器并行能力。本文提出Lookahead解码，一种精确并行解码算法，无需草稿模型，通过每步减少解码步数并提高并行度来加速。兼容FlashAttention等内存高效注意力。实验显示显著减少延迟。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 854, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 855, \"height\": 649, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 402, \"height\": 248, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 849, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1780, \"height\": 259, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 847, \"height\": 900, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 844, \"height\": 898, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-edjvsfokxw/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 866, \"height\": 231, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 884, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 835, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 697, \"height\": 349, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 851, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1574, \"height\": 600, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 723, \"height\": 116, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-edjvsfokxw/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1385, \"height\": 207, \"label\": \"Table\"}]"
motivation: 自回归解码内存带宽受限，并行处理能力浪费。
method: 提出Lookahead解码算法，通过并行预测多个token来减少解码步数。
result: 在多个加速器上实现显著延迟降低。
conclusion: Lookahead解码无需辅助模型即可加速LLM推理。
---

## Abstract
Autoregressive decoding of large language models (LLMs) is memory bandwidth bounded, resulting in high latency and significant wastes of the parallel processing power of modern accelerators. Existing methods for accelerating LLM decoding often require a draft model (e.g., speculative decoding), which is nontrivial to obtain and unable to generalize. In this paper, we introduce Lookahead decoding, an exact, parallel decoding algorithm that accelerates LLM decoding without needing auxiliary models or data stores. It allows trading per-step log(FLOPs) to reduce the number of total decoding steps, is more parallelizable on single or multiple modern accelerators, and is compatible with concurrent memory-efficient attention (e.g., FlashAttention). Our implementation of Lookahead decoding can speed up autoregressive decoding by up to 1.8x on MT-bench and 4x with strong scaling on multiple GPUs in code completion tasks. Our code is avialable at https://github.com/hao-ai-lab/LookaheadDecoding

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大型语言模型（LLM）的自回归解码受限于内存带宽，严重浪费现代加速器（如 GPU）的并行计算能力。每步仅生成一个 token，导致高延迟和低资源利用率。
- **现有方法不足**：加速方法如推测解码（Speculative Decoding）依赖额外训练的草稿模型，难以获取且无法泛化到不同模型和数据集。
- **整体含义**：提出 Lookahead Decoding，一种**无需辅助模型**的精确并行解码算法，能通过每步分配更多计算（日志级别的 FLOPs 增加）来线性减少总解码步数，从而降低延迟，且兼容 FlashAttention 等内存高效技术。

### 2. 论文提出的方法论

- **核心思想**：基于 Jacobi 迭代的并行解码框架，利用固定大小的二维窗口（时间轴 x 序列轴）同时生成多个 n-gram 并缓存到 n-gram 池中，再通过验证分支并行验证，保留原始分布。
- **关键技术细节**：
  - **Lookahead Branch**：定义窗口参数 W（前瞻位置数）和 N（n-gram 长度）。每步在 W 个位置上并行生成新 token，并从过去 N-1 步的轨迹中提取 n-gram 存入池中。
  - **Verification Branch**：从 n-gram 池中检索以当前最后 token 开头的候选 n-gram，用 LLM 并行验证。支持贪心采样和随机采样（通过强制贪心生成概率退化，仅存储 token 而非完整分布）。
  - **注意掩码**：设计特殊的注意力掩码允许 token 按生成轨迹可见，兼容 FlashAttention。
  - **Lookahead Parallelism**：将独立的 lookahead 分支和验证分支配到不同 GPU，避免通信，实现多 GPU 强扩展。
- **公式与理论**：推导了步骤压缩比 S 与每步接受 token 期望的关系，表明 S 随每步 log(FLOPs) 线性增加，验证了可扩展性。

### 3. 实验设计

- **使用数据集**：
  - **MT-Bench**（多轮对话，含独特 token）
  - **GSM8K**（数学问答前 1000 题）
  - **HumanEval**（代码补全与填充）
  - **MBPP**（指令式代码生成）
  - **ClassEval**（类级代码补全）
  - **XSum** 和 **CNN/Daily Mail**（摘要任务，用于采样质量验证）
- **Benchmark 设置**：以 HuggingFace 贪心搜索为基线，增强基线包括 FlashAttention；分布式下对比 Tensor Parallelism (TP) 和 Pipeline Parallelism (PP)。
- **对比方法**：推测解码（TinyLLaMA 1B, Vicuna 7B）、Medusa、Parallel Jacobi Decoding 及其变种。

### 4. 资源与算力

- **GPU 型号**：NVIDIA A100 80GB（单 GPU 实验）和 DGX 8×A100 40GB（多 GPU 实验）。
- **模型规模**：LLaMA-2 7B、13B、34B、70B（70B 使用 2×A100 + pipeline parallelism）。
- **精度与批大小**：FP16，批大小为 1。
- **训练要求**：无需额外训练，仅需推理。
- **算力消耗**：未明确给出总训练时长；但指出每步额外 FLOPs 约 (W+G)*(N-1)，文中典型配置（W=15, N=5, G=15）为 7B 模型带来约 120× 额外 FLOPs 开销。

### 5. 实验数量与充分性

- **实验组数**：
  - 端到端性能测试（图5）：涵盖 3 个数据集（MT-Bench、GSM8K、MBPP、HumanEval、Infill）与 3 种模型尺寸（7B、13B、34B 或 70B），共约 15 个子实验。
  - 多 GPU 与 FlashAttention 实验（图6、7）：7B 和 13B 模型在 MT-Bench、HumanEval、ClassEval 上，分别测试 1/4/8 GPU 及 FlashAttention 开关，共 36 组。
  - 采样质量验证（表2）：两个数据集、两种温度，对比 ROUGE 分数与速度。
  - 消融实验（表3）：9 种配置对比 lookahead/verification 分支及 prompt 引用的作用。
  - 理论分析与缩放律（图4）。
- **充分性与公平性**：实验覆盖了对话、数学、代码、摘要等多种任务，对比了主流方法（推测解码、Medusa、Jacobi解码），并控制了 FlashAttention 和分布式并行的影响。消融实验分析了各个组件的贡献，结果客观（如平均压缩比在有无 FlashAttention 时差异 <0.3%）。

### 6. 论文的主要结论与发现

- Lookahead Decoding 可在**无草稿模型**下实现 1.4×–2.3× 端到端加速，结合 FlashAttention 和 Lookahead Parallelism 可达 4×（代码补全任务，8 GPU）。
- **缩放定律**：通过指数级增加每步 FLOPs，可线性减少解码步数，且强扩展到更多 GPU 时加速进一步提升。
- **输出分布不变**：证明在贪心和采样下均保持原始分布（理论 + 实验验证）。
- 小模型加速效果更明显（因为 FLOPs 上限更低），代码任务加速高于文本（因重复 token 更多）。
- 在计算受限环境（如 RTX 3090）仍可实现 30%–50% 的“免费午餐”加速。

### 7. 优点

- **无需辅助模型**：避免了训练草稿模型的开销和泛化问题，即插即用。
- **精确无损**：通过验证机制保证输出分布与自回归解码一致。
- **硬件友好**：兼容 FlashAttention，支持自定义注意力掩码，可有效利用 GPU 空闲计算资源。
- **多 GPU 强扩展**：Lookahead Parallelism 几乎零通信，优于传统模型并行（PP/TP）在推理时的表现。
- **理论支撑**：提供了缩放定律，指导参数选择（W, N, G），具备未来可扩展性。

### 8. 不足与局限

- **额外计算开销**：需要大量 surplus FLOPs，在计算密集环境（如大 batch 服务）中可能引起性能下降。
- **依赖性**：性能受 n-gram 池质量和搜索效率影响，在高度随机的生成任务（如开放对话）中加速比略有下降。
- **实验覆盖有限**：未评估更大模型（70B+）在多 GPU 下的表现；仅测试单 batch 推理，未涉及批量服务场景。
- **数值误差**：FP16 精度下与官方 greedy search 有约 25% 的不一致（但认为在数值误差范围内）。
- **领域泛化**：代码和结构化文本中效果好，但高度非重复文本（如诗歌）的加速可能有限。
- **超参数敏感**：W, N, G 需针对模型和 GPU 调整（文中给出了 A100 上的推荐值，但未提供自动调优方案）。

（完）
