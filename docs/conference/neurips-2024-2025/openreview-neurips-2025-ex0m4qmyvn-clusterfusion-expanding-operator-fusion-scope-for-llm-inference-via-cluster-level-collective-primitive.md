---
title: "ClusterFusion: Expanding Operator Fusion Scope for LLM Inference via Cluster-Level Collective Primitive"
title_zh: ClusterFusion：通过集群级集体原语扩展LLM推理的算子融合范围
authors: "Xinhao Luo, Zihan Liu, Yangjie Zhou, Shihan Fang, Ziyu Huang, Yu Feng, Chen Zhang, Shixuan Sun, Zhenzhe Zheng, Jingwen Leng, Minyi Guo"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=eX0m4qMYVN"
tags: ["query:edge-llm"]
score: 8.0
evidence: 集群级集体原语实现硬件感知融合
tldr: ClusterFusion为LLM推理提出集群级集体通信原语ClusterReduce和ClusterGather，利用NVIDIA Hopper架构的片上互连，将碎片化算子融合为高效集群级操作，减少内存流量和内核启动开销，实现硬件感知的加速，是软硬协同设计的典范。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 808, \"height\": 243, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 558, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1455, \"height\": 595, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 388, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 978, \"height\": 259, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 231, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1452, \"height\": 572, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 692, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 517, \"height\": 320, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 691, \"height\": 287, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 407, \"height\": 267, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 813, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 559, \"height\": 322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1441, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1457, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1452, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 705, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 810, \"height\": 306, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 704, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 548, \"height\": 303, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ex0m4qmyvn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 845, \"height\": 305, \"label\": \"Table\"}]"
motivation: LLM解码中算子碎片化导致高延迟和内存开销，现有硬件缺乏高层抽象。
method: 引入ClusterReduce和ClusterGather原语，抽象片上通信模式，扩大融合范围。
result: 显著降低了内存流量和延迟，提升了推理速度。
conclusion: 集群级原语有效弥合了软件硬件差距，提升推理效率。
---

## Abstract
Large language model (LLM) decoding suffers from high latency due to fragmented execution across operators and heavy reliance on off-chip memory for data exchange and reduction. 
This execution model limits opportunities for fusion and incurs significant memory traffic and kernel launch overhead.
While modern architectures such as NVIDIA Hopper provide distributed shared memory and low-latency intra-cluster interconnects, they expose only low-level data movement instructions, lacking structured abstractions for collective on-chip communication.
To bridge this software-hardware gap, we introduce two cluster-level communication primitives, ClusterReduce and ClusterGather, which abstract common communication patterns and enable structured, high-speed data exchange and reduction between thread blocks within a cluster, allowing intermediate results to be on-chip without involving off-chip memory.
Building on these abstractions, we design ClusterFusion, an execution framework that schedules communication and computation jointly to expand operator fusion scope by composing decoding stages such as QKV Projection, Attention, and Output Projection into a single fused kernels.
Evaluations on H100 GPUs show that ClusterFusion outperforms state-of-the-art inference frameworks by $1.61\times$ on average in end-to-end latency across different models and configurations.

---

## 论文详细总结（自动生成）

# 论文 ClusterFusion 中文总结

## 1. 核心问题与研究动机
- **问题**：LLM 解码阶段因算子碎片化（如 QKV Projection、Attention、Output Projection 分多个 kernel 执行）导致高延迟，中间结果频繁读写全局内存，且存在大量 kernel 启动开销。
- **硬件机遇**：NVIDIA Hopper 架构提供分布式共享内存（DSMEM）和线程块集群（Cluster），可实现片上低延迟通信，但仅暴露底层指令，缺乏高层集体通信抽象。
- **目标**：设计集群级集体原语，将算子融合范围扩大，使整个解码流水线（QKV 投影→注意力→输出投影）在一个 fused kernel 内完成，消除片外数据交换。

## 2. 方法论
### 2.1 核心思想
- 将线程块集群视为协作执行单元，利用 **ClusterReduce**（归约）和 **ClusterGather**（聚集）两个原语，在 DSMEM 上实现结构化片上集体通信，避免全局内存同步。

### 2.2 关键技术细节
- **ClusterReduce**：采用二叉树模式，每轮通信步长加倍，各 block 与偏移量为当前步长的 peer 交换并归约数据，消息大小不变。
- **ClusterGather**：同样二叉树结构，但消息大小每轮翻倍，最终每个 block 持有所有其他 block 的局部数据。
- **集群中心数据流**：每个注意力头对应一个集群，集群内不同 block 分别划分 head 维度（投影）、KV 缓存 token 维度（注意力）、输出维度（输出投影）。算法伪代码见 Algorithm 3（正文）。
- **扩展性**：该数据流设计原则可推广到 DeepSeek MLA 等变体（Algorithm 4，附录 B）。
- **DSMEM 流量模型**：给出归约和聚集操作的片上流量公式，用于优选数据流变体（SplitToken 优于 SplitHead）。

## 3. 实验设计
- **硬件平台**：NVIDIA H100 SXM5 80GB GPU（CUDA 12.4，PyTorch 2.5.1）。
- **模型**：Llama2-7B（标准 MHA）、DeepSeek-V2-Lite（MLA）。
- **对比基线**：SGLang 0.4.3、vLLM 0.6.4、TensorRT-LLM 0.18.0、MLC-LLM 0.20.dev0，均启用 CUDA Graph 优化。
- **评估场景**：
  - 序列长度：1K、2K、4K、8K、16K。
  - 批量大小：主实验 batch=1，附录 C 补充 batch=16。
  - 核心模块延迟（QKV Proj + Attn + Out Proj）。
  - 不同集群大小（2~16）和注意力头数（32/64/128）。
  - 消融实验：有无 DSMEM 对比、片上 vs 片外原语延迟。

## 4. 资源与算力
- 仅使用单张 NVIDIA H100 GPU 进行推理评估，未披露训练或其他计算资源投入。
- 论文未说明具体运行时总时长或 GPU 小时数。

## 5. 实验数量与充分性
- **实验数量**：涵盖端到端 TPOT、核心模块延迟、多 batch、集群配置扫描、消融、流量分析等多组实验，图、表共 20 余幅。
- **充分性**：
  - 与 4 个 SOTA 框架对比，结果统计了多次运行的平均值。
  - 消融实验验证了 DSMEM 的必要性（开启 DSMEM 比关闭加速达 33%）。
  - 分析了不同集群尺寸对性能的影响，并给出理论流量模型支撑。
- **公平性**：所有基线采用官方推荐配置及同等优化（CUDA Graph、Torch.compile），对比客观。
- **局限性**：仅测试两个模型（Llama2-7B 和 DeepSeek-V2-Lite），未覆盖更大规模（如 70B、MoE）或不同硬件（如 AMD、Intel）环境。

## 6. 主要结论
- ClusterFusion 实现平均 **1.61×** 端到端加速（最高 3.19× 核心模块加速），优于 SOTA 框架。
- 加速主要源于：减少全局内存传输（中间结果片上保留）以及大幅降低 kernel 启动开销（近一个数量级）。
- 最优集群大小取决于工作负载（一般为 4），过大（8/16）因片上带宽竞争和活跃 SM 减少而性能下降。

## 7. 优点
- **硬件感知**：充分利用 Hopper DSMEM 和集群特性，设计高层原语弥合软硬件鸿沟。
- **原语可复用**：ClusterReduce/Gather 抽象了常见的归约/聚集模式，易于嵌入不同数据流。
- **数据流可推广**：设计原则适用于 MHA 和 MLA 等多种注意力机制，附录还给出 SplitHead 变体分析。
- **工程实现完整**：开源代码，实验细节透明，消融分析严谨。

## 8. 不足与局限
- **融合范围受限**：受 Hopper 集群大小上限（16 个 block）限制，未来更大头数或算子可能无法在单个集群内完成，需回退到全局内存，引入碎片。
- **模型覆盖不足**：仅评估 7B 级模型，未测试更大规模、MoE 或稀疏注意力等新型架构。
- **多 batch 加速较弱**：batch=16 时加速比降至 1.1× 左右，因计算强度变大，DSMEM 优化边际收益减少。
- **硬件依赖**：当前设计完全绑定 Hopper 架构的 DSMEM，无法直接迁移到其他 GPU（如 Ampere）。
- **未讨论预处理（Prefill）阶段**：聚焦解码，预填充阶段未评估。

（完）
