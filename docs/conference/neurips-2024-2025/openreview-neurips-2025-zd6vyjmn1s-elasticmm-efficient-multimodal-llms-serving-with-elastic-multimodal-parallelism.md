---
title: "ElasticMM: Efficient Multimodal LLMs Serving with Elastic Multimodal Parallelism"
title_zh: ElasticMM：通过弹性多模态并行高效服务多模态LLM
authors: "Zedong Liu, Shenggan Cheng, Guangming Tan, Yang You, Dingwen Tao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Zd6VyjmN1S"
tags: ["query:edge-llm"]
score: 5.0
evidence: 弹性并行实现高效多模态LLM服务
tldr: 多模态大语言模型（MLLM）因额外组件和异构工作负载导致推理开销大，现有紧耦合服务架构无法灵活适应。本文提出弹性多模态并行（EMP）范式，根据资源异构性和推理阶段动态调整并行策略，优化时间至首令牌（TTFT）和资源利用率。该方法可视为对LLM服务框架的扩展，虽不特指边缘，但其中的弹性并行思想对边缘异构计算有参考价值。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1224, \"height\": 676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1238, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1161, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 640, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1450, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1445, \"height\": 317, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zd6vyjmn1s/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1453, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zd6vyjmn1s/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1228, \"height\": 182, \"label\": \"Table\"}]"
motivation: MLLM服务面临推理管线复杂和资源异构挑战，需要弹性并行策略。
method: 提出弹性多模态并行，动态调整不同模态和推理阶段的并行度。
result: 显著降低TTFT，提高资源利用率。
conclusion: 弹性并行是高效服务多模态LLM的有效方法，可推广至边缘异构环境。
---

## Abstract
Multimodal large language models (MLLMs) extend LLMs to handle images, videos, and audio by incorporating feature extractors and projection modules. However, these additional components—combined with complex inference pipelines and heterogeneous workloads—introduce significant inference overhead. Therefore, efficiently serving MLLMs remains a major challenge. Current tightly coupled serving architectures struggle to distinguish between mixed request types or adapt parallelism strategies to different inference stages, leading to increased time-to-first-token (TTFT) and poor resource utilization. To address this, we introduce Elastic Multimodal Parallelism (EMP), a new serving paradigm that elastically adapts to resource heterogeneity across request types and inference stages. Building upon EMP, we develop ElasticMM, an MLLM serving system that (1) separates requests into independent modality groups with dynamic resource allocation via a modality-aware load balancer; (2) decouples inference stages and enables parallelism adjustment and adaptive scaling via elastic partition scheduling; and (3) improves inference efficiency through unified multimodal prefix caching and non-blocking encoding. Experiments on diverse real-world datasets show that ElasticMM outperforms state-of-the-art (SOTA) serving systems, reducing TTFT by up to 4.2$\times$ and achieving 3.2–4.5$\times$ higher throughput while meeting service-level objectives (SLOs).

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：多模态大语言模型（MLLM）在服务时引入了特征提取器、投影模块等额外组件，导致推理管线复杂、计算开销大。现有服务系统采用紧耦合架构，无法区分纯文本请求与多模态请求的资源需求差异，也无法在不同推理阶段（编码、预填充、解码）灵活调整并行策略。
- **后果**：时间至首令牌（TTFT）显著增加，资源利用率低下，难以满足服务等级目标（SLO）。
- **整体含义**：需要一种**解耦且弹性**的服务范式，能根据请求类型和推理阶段动态优化资源分配与并行度，从而提高MLLM推理效率。

## 2. 方法论：核心思想、关键技术细节
### 核心思想
- 提出**弹性多模态并行（Elastic Multimodal Parallelism, EMP）** 新范式，通过两级调度框架实现：
  1. **模态级**：将纯文本请求与多模态请求分离为独立组，动态分配资源。
  2. **阶段级**：将推理管线解耦为编码、预填充、解码阶段，每个阶段独立调整并行度并支持弹性伸缩。

### 关键技术细节
- **模态感知负载均衡（Modality-Aware Load Balancing）**：
  - 结合**主动机制**和**反应式伸缩**主动机制通过贪婪策略最大化各组的最小突发容忍度：`bt(i) = N_peak_i / N_avg_i`。
  - 反应式伸缩在检测到资源不足时，根据收益-成本模型从其他组抢占实例。
- **弹性分区调度（Elastic Partition Scheduling）**：
  - **请求调度**：采用FCFS策略，同时考虑GPU内存和吞吐约束。
  - **阶段分配**：将空闲实例优先分配给预填充阶段，必要时可从解码阶段抢占实例。使用收益-成本模型决定是否抢占（加速收益 vs 迁移开销 + 性能损失）。
  - **弹性自动伸缩**：监控解码阶段瓶颈，通过离线profiling设定阈值，触发伸缩时比较组内与组间抢占的净收益。
- **统一多模态前缀缓存（Unified Multimodal Prefix Cache）**：
  - 将视觉编码缓存和文本KV缓存统一管理，通过LRU策略淘汰，减少冗余计算。
- **非阻塞编码（Non-blocking Encoding）**：
  - 将图像编码与后续推理解耦为异步执行，消除编码阶段对预填充/解码的阻塞。

## 3. 实验设计
- **数据集**：
  - **VisualWebInstruct**：来自70万+URL的多模态指令数据，文本较长。
  - **ShareGPT-4o**：5万张高分辨率图像及其文本提示，图像密集。
- **模型**：
  - **LLaMA3.2-Vision-11B**（编码器-解码器架构）
  - **Qwen2.5-VL-7B**（解码器-仅架构）
- **基准方法**：
  - **vLLM**（v0.6.6）：紧耦合SOTA系统。
  - **DistServe**：解耦预填充与解码，静态资源分配。
- **对比指标**：
  - **输入延迟（TTFT）**：归一化平均预填充时间。
  - **输出延迟**：归一化平均解码时间。
  - **吞吐量**：在满足SLO约束下的最大请求处理率。
  - 使用泊松分布生成可变请求到达率（QPS），并融入真实生产跟踪。

## 4. 资源与算力
- **硬件环境**：
  - 8块 NVIDIA A800 80GB GPU
  - 2颗64核 Intel Xeon 8358P CPU
  - 2 TB DDR4 内存
  - NVLink 带宽 400 GB/s
- **说明**：仅进行了单节点实验；论文明确将多节点分布式研究留作未来工作，因此训练时长无关（本工作聚焦推理服务，不涉及训练）。

## 5. 实验数量与充分性
- **核心实验**：
  - **端到端性能**（图5）：在两个数据集、两个模型上对比输入/输出延迟，覆盖多种请求速率。
  - **吞吐量对比**（图6）：在SLO缩放因子1×~5×下测量最大吞吐量。
  - **消融实验**（图7）：评估弹性多模态并行（EMP）的有效性，对比三种静态资源分配策略。
  - **消融实验**（图8）：评估统一前缀缓存和非阻塞编码的单独与联合效果。
- **充分性与公平性**：
  - 覆盖两种主流架构（DecOnly与EncDec）和互补性数据集（长文本 vs 高分辨率）。
  - 基线均为现有SOTA系统，且进行了公平的代码扩展（如为DistServe添加多模态支持）。
  - 消融实验逐步剥离组件，结论清晰。
- **附录**：还提供了推理等值性的数学证明及1000次prompt输出一致性验证（表2），进一步支持无精度损失。

## 6. 主要结论与发现
- ElasticMM 在**TTFT**上比vLLM降低最高 **4.2×**（ShareGPT-4o, Qwen2.5-VL），比DistServe也有显著优势。
- **吞吐量**提升 **3.2–4.5×**（vLLM），相比DistServe提升最高 **2.3×**。
- **解码延迟**稳定，不受编码和预填充干扰。
- 弹性调度（EMP）比任何静态分配方案吞吐量高 **1.8–2.3×**。
- 统一前缀缓存和非阻塞编码均有效降低输入延迟，两者叠加效果最好。

## 7. 优点
1. **创新性**：提出模态级+阶段级两级解耦与弹性并行，是首个系统性解决MLLM服务异构性的工作。
2. **无精度损失**：所有优化均保持推理等价性（附录提供了数学证明和实验验证）。
3. **兼容性**：支持Decoder-only和Encoder-Decoder两种主流架构，不依赖特定模型修改。
4. **实用优化**：统一前缀缓存和非阻塞编码直接减少计算冗余和流水线阻塞，工程实现扎实。
5. **实验全面**：覆盖多种负载、模型架构和SLO条件，消融明确。

## 8. 不足与局限
1. **单节点实验**：仅在8 GPU节点上测试，未涉及多节点分布场景。论文指出未来将扩展，但当前结论的泛化性受限于单集群。
2. **未与模型级优化对比**：如视觉token剪枝、KV缓存压缩等方法（如Dynamic-LLaVA、Elastic Cache）虽可能带来精度下降，但论文未进行公平对比（作者说明这些工作正交）。
3. **仅考虑图像模态**：未涉及视频、音频等其他模态，实际多模态场景可能更复杂。
4. **资源开销假设**：依赖NVLink高速互联和充足GPU显存；在带宽受限或显存较小的环境，弹性迁移的开销可能抵消收益。
5. **实现基于vLLM**：虽然构建在成熟框架上，但未评估与其他框架（如SGLang、TensorRT-LLM）集成的效果。

（完）
