---
title: Fast Inference for Augmented Large Language Models
title_zh: 增强型大语言模型的快速推理
authors: "Rana Shahout, Cong Liang, Shiji Xin, Qianru Lao, Yong Cui, Minlan Yu, Michael Mitzenmacher"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=uNqTxj5brQ"
tags: ["query:edge-llm"]
score: 5.0
evidence: 优化增强型LLM调度的推理框架
tldr: 增强型LLM通过API调用集成外部数据，但引入调度挑战：请求令牌大小与执行时间不再相关。MARS框架显式结合系统和应用级信息优化调度，降低请求完成时间，提升用户体验。实验显示MARS在增强型LLM场景下显著优于传统调度算法。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1410, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1233, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1411, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1415, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1486, \"height\": 698, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1459, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1410, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1418, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1438, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1332, \"height\": 1065, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1331, \"height\": 1063, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1332, \"height\": 1066, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 921, \"height\": 1515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1436, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-unqtxj5brq/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1543, \"height\": 1191, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-unqtxj5brq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 843, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-unqtxj5brq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1459, \"height\": 145, \"label\": \"Table\"}]"
motivation: 增强型LLM的调度面临请求大小与执行时间不相关的挑战。
method: 设计MARS框架，结合系统和应用级信息优化调度。
result: 在增强型LLM场景下显著优于传统调度算法。
conclusion: MARS通过感知上下文的调度实现了增强型LLM的快速推理。
---

## Abstract
Augmented Large Language Models (LLMs) enhance standalone LLMs by integrating external data sources through API calls. In interactive applications, efficient scheduling is crucial for maintaining low request completion times, directly impacting user engagement. However, these augmentations introduce new scheduling challenges: the size of augmented requests (in tokens) no longer correlates proportionally with execution time, making traditional size-based scheduling algorithms like Shortest Job First less effective. Additionally, requests may require different handling during API calls, which must be incorporated into scheduling.
This paper presents MARS, a novel inference framework that optimizes augmented LLM latency by explicitly incorporating system- and application-level considerations into scheduling. MARS introduces a predictive, memory-aware scheduling approach that integrates API handling and request prioritization to minimize completion time. We implement MARS on top of vLLM and evaluate its performance against baseline LLM inference systems, demonstrating improvements in end-to-end latency by 27%-85% and reductions in TTFT by 4%-96% compared to the existing augmented-LLM system, with even greater gains over vLLM. Our implementation is available online.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题背景**：增强型大语言模型（Augmented LLMs）通过 API 调用集成外部数据源（如计算器、图像生成、搜索引擎等），在交互式应用中至关重要。然而，这种增强带来了新的调度挑战：传统大小优先调度（如 Shortest Job First）假设请求的执行时间与输出 token 数成正比，但在 API 增强场景中，请求的 token 大小不再可靠地反映总执行时间（因为 API 调用耗时可能远长于解码阶段，反之亦然）。此外，API 调用期间的内存管理策略（保留/丢弃/交换）需要根据请求特征动态选择，且影响后续请求的调度。
- **研究动机**：现有 LLM 推理系统（如 vLLM）和增强型 LLM 系统（如 INFERCEPT）未能有效解决以上问题，导致队头阻塞（HoL）、内存浪费和高延迟。因此需要一种统一考虑系统级（内存占用）和应用级（API 特征）的调度框架，以最小化请求完成时间，提升用户体验。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：MARS（Memory- and API- Rooted Scheduler）通过两步协同优化实现低延迟推理：
  - **步骤一：API 处理策略预分配**。利用轻量级预测器（基于 OPT-125M 模型的 embedding 和线性分类器）提前预测每个请求的“前 API 输出长度”和“API 调用时长”。基于这些预测，计算三种策略（Preserve、Discard、Swap）各自的内存浪费（对时间积分的内存占用），选择浪费最小的策略。
  - **步骤二：基于预测总内存的调度**。将每个请求的“预测总内存消耗”（即内存使用量随时间积分的面积）作为排序依据，优先调度总内存需求较小的请求。同时引入饥饿预防机制：每个请求设置计数器，当在等待队列中停留超过阈值（设为 100 次迭代）时，提升其优先级至队列头部。
- **关键技术细节**：
  - 内存浪费计算：Preserve 策略浪费为 `T_api * C_i * M`（API 时长 × 上下文大小 × 每 token 内存）；Discard 策略浪费为 `T_fwd(C_i) * C_i * M + T_fwd(C_i) * C_other * M`；Swap 策略浪费为 `2 * T_swap(C_i) * C_batch * M`。选择最小化浪费的策略。
  - 多 API 请求：每个 API 调用被视为一个中断点，将请求划分为多个片段，每个片段独立分类。
  - 预测器：OPT-125M 提取 prompt 的最终 token embedding，输入线性分类器（50 个 bin，每个 bin 10 个 token），使用交叉熵损失训练。
  - 调度算法伪代码：见附录 Algorithm 1（循环处理请求池、更新等待队列、计算排名、执行运行批次、处理 API 事件）。
  - 混合工作负载（API 请求 + 非 API 请求）：非 API 请求按其估计内存消耗（相当于执行时间）排名，与 API 请求统一调度。

## 3. 实验设计
- **数据集**：
  - **Single-API 数据集**：INFERCEPT 的子集，每个请求仅包含单个 API 调用。
  - **Multi-API 数据集**：INFERCEPT 的完整数据集，包含多个 API 调用类型（Math, QA, VE, Chatbot, Image, TTS）。
  - **ToolBench 数据集**：包含 16,000+ 真实世界 API，49 个类别，用于评估预测和泛化能力。
- **基准方法**：
  - **vanilla vLLM**（基线推理系统，无 API 感知）。
  - **INFERCEPT**（当前最先进的增强型 LLM 推理系统，动态选择 API 处理策略但使用 FCFS 调度）。
  - **MARS w/o scheduling**（仅使用预测 API 处理策略，但调度仍为 FCFS）用于消融。
- **评估指标**：端到端延迟（mean 和 P99）、Time-to-First-Token（TTFT，mean 和 P99）、吞吐量。
- **实验场景**：在不同请求到达率（qps = 3,4,5,6）下进行，覆盖三种数据集和多个模型尺寸。

## 4. 资源与算力
- **硬件平台**：双路 AMD EPYC 7313 CPU（各 16 核，共 64 线程）、503 GB RAM、两块 NVIDIA A100 (80 GB) GPU，通过 NVLink 连接。
- **模型推理**：GPT-J 6B 和 Vicuna 13B 时 GPU 内存限制为 40 GB（为与 INFERCEPT 公平比较）；Llama 70B 使用 vLLM 默认张量并行（2 路）。
- **预测模型**：OPT-125M，在单个 A100 GPU 上运行，平均每个输入预测耗时 13.7 ms。
- **训练**：未明确说明训练时长，但提到使用 80/20 分割训练 OPT-125M 轻量分类器，训练数据来自 ToolBench。

## 5. 实验数量与充分性
- **实验数量**：论文进行了大量的系统性实验：
  - 在三个数据集（Single-API、Multi-API、ToolBench）上分别对四种模型（TinyLlama 1.1B、GPT-J 6B、Vicuna 13B、Llama 70B）在不同请求率下进行了端到端性能对比。
  - 消融实验（图6）：比较 MARS、MARS w/o scheduling、INFERCEPT 在多 API 数据集上的性能，验证调度组件和预测组件各自的贡献。
  - 预测误差影响实验（图7）：在 API 时长和输出大小上注入高斯噪声（5%–60%），评估性能退化。
  - 饥饿阈值实验（图16）：比较不同阈值（10,100,1000,10000,off）下的尾延迟和吞吐量。
  - 混合工作负载实验（附录 C.2）：50% API + 50% 非 API 请求。
  - 内存占用分析（附录 C.7）：记录 GPU/CPU cache 随时间变化。
- **充分性与公平性**：实验设计较为全面，覆盖了不同模型规模、不同请求负载、多种数据来源，并进行了消融和鲁棒性分析。基准方法 vLLM 和 INFERCEPT 的复现设置与论文一致，比较公平。但缺乏与更近期系统（如 Sarathi-Serve、FastServe）的直接对比，可能影响完整性。

## 6. 主要结论与发现
- **主要结论**：MARS 在所有测试数据集和模型上均显著优于 vLLM 和 INFERCEPT：
  - 端到端延迟改进 27%–85%（与 INFERCEPT 相比），对 vLLM 改进更大。
  - TTFT 降低 4%–96%（与 INFERCEPT 相比）。
  - 在较高请求率下（qps=5,6），改进最为显著（TTFT 降低超 90%，延迟降低 60%–80%）。
  - 预测误差实验表明，即使误差达 60%，MARS 性能退化仍有限，鲁棒性较好。
  - 饥饿预防阈值设为 100 在尾延迟和吞吐量之间取得良好平衡。
  - 预测组件（单独加入）带来的收益较小，必须与调度组件结合才能达到最优性能。

## 7. 优点
- **方法创新性**：首次将 API 处理策略的预分配与基于内存总消耗的调度紧密结合，超越了 INFERCEPT 的动态决策 + FCFS 范式。
- **实用性**：基于 vLLM 实现，可集成到现有系统；预测器轻量（OPT-125M），开销小（13.7ms/请求）。
- **实验全面性**：测试多种模型（1.1B~70B）、多种数据集、多种负载，并进行了消融、噪声注入和饥饿阈值分析，验证了方法的鲁棒性。
- **结构清晰**：问题定义明确，示例论证直观（图1），算法流程（Algorithm 1）详细。
- **开源**：代码已公开，便于复现和扩展。

## 8. 不足与局限
- **预测精度依赖**：API 时长和输出大小的预测采用简单平均值，未针对复杂变化建模；预测误差较大时（如 60%）仍可能影响系统性能（尽管实验显示影响有限）。作者承认这是未来改进方向。
- **多 API 处理简化**：多 API 请求被分割成独立片段，未考虑多个 API 调用的累积内存开销和依赖性，可能导致次优策略。
- **实验覆盖不足**：未与同样针对 LLM 推理调度的系统（如 Sarathi-Serve、FastServe、Splitwise）进行比较；仅对比了 vLLM 和 INFERCEPT。
- **饥饿预防阈值固定**：阈值设置为 100 是基于实验数据，未提供自适应或理论分析，可能在不同负载下需要调整。
- **缩放性验证有限**：仅测试了 Llama 70B 在 2 个 GPU 上的情况，未评估更大规模集群或多 GPU 间的通信开销。
- **缺少统计显著性分析**：未提供误差条或置信区间，尽管作者声称由于稳态系统和大数据集，误差很小。

（完）
