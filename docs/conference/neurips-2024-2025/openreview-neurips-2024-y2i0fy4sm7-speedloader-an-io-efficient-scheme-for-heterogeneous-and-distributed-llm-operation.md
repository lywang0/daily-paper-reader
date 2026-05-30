---
title: "SpeedLoader: An I/O efficient scheme for heterogeneous and distributed LLM operation"
title_zh: SpeedLoader：面向异构分布式LLM操作的I/O高效方案
authors: "Yiqi Zhang, Yang You"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=Y2I0Fy4sm7"
tags: ["query:edge-llm"]
score: 6.0
evidence: 面向异构分布式LLM操作的I/O优化方案
tldr: 本文提出SpeedLoader，针对异构分布式LLM操作中的I/O瓶颈，通过智能分布和卸载模型状态到主机DRAM和块设备，降低加速器内存压力和张量通信开销，提升整体效率，适用于资源受限环境。
source: NeurIPS-2024-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2024-y2i0fy4sm7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1141, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-y2i0fy4sm7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1349, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-y2i0fy4sm7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1264, \"height\": 179, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-y2i0fy4sm7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 739, \"height\": 790, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-y2i0fy4sm7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-y2i0fy4sm7/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1413, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-y2i0fy4sm7/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 991, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-y2i0fy4sm7/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 414, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-y2i0fy4sm7/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 833, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-y2i0fy4sm7/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 625, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2024-y2i0fy4sm7/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 807, \"height\": 442, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2024-y2i0fy4sm7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 739, \"height\": 790, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-y2i0fy4sm7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1457, \"height\": 403, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-y2i0fy4sm7/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1024, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-y2i0fy4sm7/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 744, \"height\": 450, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2024-y2i0fy4sm7/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 832, \"height\": 785, \"label\": \"Table\"}]"
motivation: 大模型部署受限于加速器内存，现有分布和卸载方案存在高昂通信成本。
method: 优化模型状态在加速器、主机DRAM和块设备间的分布与卸载策略。
result: 降低了I/O开销，提升了异构分布式LLM操作的效率。
conclusion: SpeedLoader为异构分布式LLM提供了I/O高效的解决方案。
---

## Abstract
With the surging growth of model parameters, foundation models pose unprecedented challenges to traditional computational infrastructures. These large models inherently require substantial accelerator memory to accommodate massive tensors during pre-training, fine-tuning, and even inference stages, making it even more challenging to deploy a model with restricted computational resources. Given this challenge, distribution and offloading the model states are two major solutions. Partitioning the required states to participating workers, and storing them in lower speed media, such as host DRAM and block devices, largely alleviate the accelerator memory pressure. However, the prohibitive costs of tensor communication render it a theoretically plausible yet practically inefficient solution. Previous efforts to improve efficiency include maximizing rematerialization and employing chunk-based tensor management to reduce host-device communication. Despite these efforts, the reported training throughput only achieves 36.54% of model FLOPs utilization (MFUs), still not comparable to full on-device training. In this work, we redesign the data flow of heterogeneous hardware and sharded model training to minimize the excessive communication overhead. Our proposed scheme significantly enhances training and inference throughput of large language models under restrictive computational resources. We confirmed a large leap in effective compute time by looking into the kernel-level runtime behavior of our trials, where the MFUs can achieve up to 51%. Compared to the state-of-the-art approach, our framework robustly achieves remarkable speedups from 3x to 30x in multiple distributed heterogeneous training setups and inference speedups of 1.5x to 2.35x without compromising arithmetic precision.

---

## 论文详细总结（自动生成）

# 论文《SpeedLoader: An I/O efficient scheme for heterogeneous and distributed LLM operation》详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：大模型（如GPT-3、LLaMA-3）参数规模急剧增长，对加速器高带宽内存（HBM）的需求远超单卡容量。现有分布式和卸载方案（如ZeRO-Offload、FSDP）虽然将模型状态分布到主机DRAM或NVMe，但张量通信（peer-to-peer和device-host I/O）开销巨大，导致训练吞吐量仅达到36.54%的模型FLOPs利用率（MFU），远低于全设备内训练。
- **整体含义**：本文旨在通过重新设计异构硬件和数据流的调度策略，最小化冗余I/O，从而在不牺牲精度的情况下显著提升资源受限环境下大语言模型（LLM）的训练和推理效率。SpeedLoader在多种分布式异构训练设置下实现了3~30倍加速，推理加速1.5~2.35倍。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程（文字说明）
### 核心思想
- 通过“有效批次”（effective batch）机制，将多个小批次（sub-batch）合并处理，每个模型层仅需加载两次（一次前向、一次反向）即可完成多个子批次的梯度累积，大幅减少模型参数的加载和同步次数。
- 重新设计计算图，利用no-op函数连接同一层不同子批次的激活，使自动微分机制能够正确反向传播并累积梯度，避免逐子批次加载模型。

### 关键技术细节
- **Tensor Exchange Manager**：
  - **透明数据交换**：在每层前向/反向之前，异步预取下一子批次的输入/激活，同时卸载上一子批次的激活/梯度，并与计算重叠（使用独立CUDA流）。
  - **无碎片化内存池**：根据模型超参数预分配固定大小的页锁定内存（pinned memory），避免动态分配导致的内存碎片和阻塞。对推理的KV Cache，按(n_sub_batches, layer, sequence_length, -1)排列以支持连续异步批量拷贝。
- **超参数调优策略**：
  - 新维度包括子批次大小（sub-batch size）、子批次数量（number of sub-batches）、设备内层数（number of on-device layers）。
  - 通过两次脚本运行（不同批次大小）记录峰值设备/主机内存，利用线性关系（R² > 0.999）外推出最优配置，最大化HBM和主机内存利用。
- **通信量定量分析**（附录A.3，表4）：
  - SpeedLoader总本地通信：5NA + 3P，远程通信：3P（A=激活大小，P=参数大小，N=子批次数）。
  - 对比ZeRO-Offload（本地3NP，远程3NP），SpeedLoader的I/O优势随N增大而渐近增强（5n/(36Lh) + 1/N 和 1/N 量级）。

### 算法流程（伪代码概述）
- **前向**：对每个子批次，将当前激活卸载到pinned_mem[lid][i-1]，预取上一个层的下一子批次激活，然后执行该层计算。
- **反向**：通过backward_hook将梯度卸载到pinned_mem[lid-1][i-1]，预取所需激活和梯度，然后执行反向传播。

## 3. 实验设计：数据集/场景、基准、对比方法
- **数据集**：
  - 预训练实验：Wikipedia、OpenWebText、C4数据集（截断处理）。
  - 推理/吞吐量测试：使用LLaMA-2和OPT系列模型（含OPT-175B）。
- **基准模型**：LLaMA-2-7B/13B/70B，OPT-6.7B/30B/175B。
- **场景**：
  - 单设备（offloading）
  - 分布式（offloading，64 GPU）
  - 分布式（无offloading，仅peer通信）
  - 弱可扩展性测试（4/16/64 GPU）
  - 推理吞吐量（单设备，与FlexGen、vLLM、DeepSpeed对比）
  - 兼容性测试（V100S、A6000、H100）
- **对比方法**：DeepSpeed（ZeRO++，含offloading）、FlexGen、vLLM。

## 4. 资源与算力
- **主要实验平台**：
  - 云VM：16× NVIDIA A100-40GB GPU，96 vCPU，1360GB RAM，100Gbps以太网互联。
  - HPC集群：NVIDIA A100-40GB，HPE Slingshot互联（Dragonfly拓扑）。
- **其他平台**：NVIDIA H100-96GB, V100S-32GB, A6000（PCIe Gen 3/4/5）。
- **训练时长**：未明确给出具体小时数。预训练实验采用“截止时间”（cutoff time）比较处理的token数量（例如7B模型在Wikipedia上跑26.2M tokens vs 113.2M tokens），未说明具体时长。

## 5. 实验数量与充分性
- **实验组数**：
  - 训练MFU对比：3个场景（单设备、分布式、无卸载）× 各模型大小（7B/13B/70B），共约7个柱状图。
  - 推理吞吐量：OPT三个大小，对比4种方法，共12个数据点。
  - 预训练：2个模型 × 3个数据集 = 6组有效实验，报告了loss和处理token数。
  - 弱扩展测试：3种模型 × 3个GPU数量（4/16/64），共9条曲线。
  - 超参数分析：单次实验展示线性关系。
  - FlashAttention-2消融：2个场景（分布式offload和无卸载）× 各模型，共约6组。
  - 兼容性测试：V100S/A6000/H100各一次。
- **充分性与公平性**：
  - 实验覆盖了主流训练和推理场景，包括单卡、多卡、跨节点分布式、有无卸载、不同总线速度等，较为全面。
  - 对比方法均为最新SOTA（DeepSpeed ZeRO++, FlexGen, vLLM），且在同一平台上运行。
  - **不足**：未提供误差棒（作者解释为计算成本过高），且未与张量/流水线并行联合测试。

## 6. 论文的主要结论与发现
- **训练效率**：SpeedLoader在单设备offloading中达到51% MFU（DeepSpeed仅约30%）；分布式offloading下可达36%+（Baseline~10%）；无卸载分布式下可达55%+（Baseline~5%）。
- **推理效率**：比FlexGen快1.52~2.35倍，远优于vLLM和DeepSpeed（尤其在大模型OPT-175B时优势明显）。
- **超参数影响**：子批次大小应与HBM容量对齐最大化；子批次数受主机DRAM限制；设备内层数影响较小。
- **线性资源使用**：GPU内存和主机内存与输入token数呈极强线性关系（R²>0.999），使得一次性超参数调优可行。
- **可扩展性**：弱扩展中每设备吞吐量随GPU数量增加而超线性提升（得益于带宽释放）。

## 7. 优点：方法或实验设计上的亮点
- **方法创新**：
  - 提出“有效批次”概念，将多次模型加载减少到两次，从根源上降低了I/O量。
  - 计算图重路由（no-op连接）确保自动微分正确性，无需手动拦截梯度。
  - 透明数据交换与计算重叠，减少空闲等待。
  - 预分配无碎片内存池，避免PyTorch默认分配的次幂对齐浪费。
- **实验设计**：
  - 覆盖多模型、多规模、多场景（训练/推理/offload/无offload），对比方法全面。
  - 进行预训练实际验证，展示了收敛性和吞吐量双重提升。
  - 弱扩展测试证实了带宽瓶颈缓解的潜力。

## 8. 不足与局限
- **未与其他并行策略集成**：未与张量并行、流水线并行等联合测试，限制了在大规模混合并行场景的应用验证。
- **内存浪费风险**：PyTorch的CPU内存分配只能为2的幂次，导致实际可用内存可能低于理论值，引发OOM。
- **主机内存成为新瓶颈**：有效批次规模受主机DRAM容量限制，对于超大模型或长序列可能无法充分发挥优势。
- **实验统计性不足**：未提供误差棒和多次重复结果，对结果稳定性存疑（但计算成本高是客观原因）。
- **模型类型局限**：仅验证了Transformer架构（OPT/LLaMA），其他非Transformer大模型（如Mamba、RWKV）未测试。
- **推理场景只测试单卡**：分布式推理场景未涉及，且对大模型（175B）需采用NVMe卸载，导致KV Cache引起额外I/O，SpeedLoader在禁用KV cache时反而受益。

（完）
