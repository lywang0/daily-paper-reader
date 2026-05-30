---
title: "HiFC: High-efficiency Flash-based KV Cache Swapping for Scaling LLM Inference"
title_zh: HiFC：基于闪存的高效KV缓存交换以扩展LLM推理
authors: "Inho Jeong, Sunghyeon Woo, Sol Namkung, Dongsuk Jeon"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=onhjdWCxZY"
tags: ["query:edge-llm"]
score: 4.0
evidence: 基于闪存的KV缓存交换实现成本效益扩展
tldr: HiFC提出一种无DRAM的KV缓存交换方案，利用SSD直接访问GPU，降低大模型推理的内存成本，但主要面向服务器端扩展，对边缘设备场景适用性有限，方法具有启发性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-onhjdwcxzy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 826, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-onhjdwcxzy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 603, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-onhjdwcxzy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1407, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-onhjdwcxzy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1449, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-onhjdwcxzy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-onhjdwcxzy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 723, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-onhjdwcxzy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1451, \"height\": 441, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1070, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1296, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1356, \"height\": 408, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 663, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1186, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1356, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1456, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1462, \"height\": 432, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1460, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1463, \"height\": 451, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1283, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1199, \"height\": 490, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1449, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1277, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 610, \"height\": 449, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1008, \"height\": 565, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 916, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 871, \"height\": 452, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1057, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1185, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-onhjdwcxzy/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 800, \"height\": 473, \"label\": \"Table\"}]"
motivation: 长上下文推理中KV缓存超出GPU内存，现有DRAM扩展成本高。
method: 设计DRAM-free方案，通过SSD直接与GPU交换KV缓存，绕过CPU带宽瓶颈。
result: 在低成本下实现了与DRAM方案相当的性能。
conclusion: 闪存交换是扩展推理内存的经济方案。
---

## Abstract
Large‑language‑model inference with long contexts often produces key–value (KV) caches whose footprint exceeds the capacity of high‑bandwidth memory on a GPU. Prior LLM inference frameworks such as vLLM mitigate this pressure by swapping KV cache pages to host DRAM. However, the high cost of large DRAM pools makes this solution economically unattractive. Although offloading to SSDs can be a cost-effective way to expand memory capacity relative to DRAM, conventional frameworks such as FlexGen experience a substantial throughput drop since the data path that routes SSD traffic through CPU to GPU is severely bandwidth-constrained. To overcome these limitations, we introduce HiFC, a novel DRAM‑free swapping scheme that enables direct access to SSD-resident memory with low latency and high effective bandwidth. HiFC stores KV pages in pseudo-SLC (pSLC) regions of commodity NVMe SSDs, sustaining high throughput under sequential I/O and improving write endurance by up to 8$\times$. Leveraging GPU Direct Storage, HiFC enables direct transfers between SSD and GPU, bypassing host DRAM and alleviating PCIe bottlenecks. HiFC employs fine-grained block mapping to confine writes to high-performance pSLC zones, stabilizing latency and throughput under load. HiFC achieves inference throughput comparable to DRAM-based swapping under diverse long-context workloads, such as NarrativeQA, while significantly lowering the memory expansion cost of a GPU server system by 4.5$\times$ over three years.

---

## 论文详细总结（自动生成）

# HiFC 论文详细中文总结

## 1. 核心问题与整体含义
- **研究背景**：大语言模型（LLM）在长上下文推理时，KV Cache 的占用会远超 GPU 显存（HBM）容量。现有方案（如 vLLM）通过将 KV Cache 交换到主机 DRAM 来缓解压力，但大容量 DRAM 成本高昂、功耗大，经济性差。使用 SSD 虽可降低成本，但传统路径需经 CPU 和 DRAM 中转，形成严重带宽瓶颈，导致吞吐量大幅下降。
- **核心问题**：如何在不依赖 DRAM 的前提下，实现低成本、高吞吐的 KV Cache 扩展？
- **整体意义**：提出 HiFC（High-efficiency Flash Cache），一种无 DRAM 的交换方案，利用商用 NVMe SSD 的 pSLC（伪单层单元）区域和 GPU Direct Storage（GDS）技术，实现 GPU 与 SSD 之间的直接数据传输，在达到与 DRAM 交换相当吞吐量的同时，将三年内存扩展成本降低 4.5 倍。

## 2. 方法论
- **核心思想**：构建 DRAM-free 的存储层级——将 KV Cache 直接交换到 SSD，绕过主机 DRAM 中转。
- **关键技术细节**：
    1. **pSLC 区域利用**：在商用 NVMe SSD 中划分伪 SLC 区域（约占 20% 容量），该区域支持更高顺序 I/O 吞吐量，并将写入寿命提升 8 倍（P/E 循环从 3000 提升至 30000）。
    2. **GPU Direct Storage（GDS）**：启用 GPU 与 SSD 之间的直接 DMA 传输，完全绕过主机 CPU 和 DRAM，消除 PCIe 瓶颈。
    3. **闪存块分配与写放大控制**：采用 **追加分配策略** 和 **块级顺序写入**，使 KV 块物理上连续排列。实验测得写放大因子（WAF）仅为 1.02，远低于典型 SSD 的 1.4。
    4. **Flash Cache 块分配器**：在 vLLM 的 Block Manager 中加入 FC（Flash Cache）块分配器，与 GPU/CPU 块共存。当 GPU 内存不足时，将受害者序列的 KV 块交换到 FC 块。
    5. **缓存引擎**：基于 CUDA 和 GDS 实现多线程 I/O 调度，直接使用 4KB 对齐的 tensor 作为 GDS 缓冲区，在 pSLC 区域达到 >4.7 GiB/s 的吞吐量。
- **流程**（见图 1a）：解码阶段 GPU 显存不足 → 调度器选择受害者序列 → 通过 GDS 将 KV 块异步交换到 SSD（FC）→ 释放的 GPU 块立即被其他序列使用 → 后续计算与 I/O 重叠，隐藏延迟。

## 3. 实验设计
- **主要模型**：DeepSeek-R1-Distill-Qwen-32B（DS-Qwen-32B），另扩展验证了 DS-Llama-8B、DS-Qwen-14B、Mistral-7B。
- **数据集与场景**：
    - 长上下文：Qasper（平均 3.6k tokens）、GovReport（平均 8.7k tokens）、NarrativeQA（平均 18.4k tokens）。
    - 固定输入/输出长度测试（图 3）、多序列并发测试（图 4）。
- **基准（Baseline）**：vLLM 中的 DRAM 交换方案（同为 vLLM 框架下的 block-level 交换）。
- **对比指标**：吞吐量（tokens/s）、交换次数、端到端吞吐、初始化时间等。
- **硬件拓扑实验**：1:1（GPU:SSD）、2:1（多 GPU 共享单 SSD）、2:2（多 GPU 多 SSD 并行）。
- **消融与分析**：
    - 不同 block size 对吞吐的影响（图 6）。
    - 顺序 vs 随机 I/O 的吞吐对比（表 5）。
    - 写放大因子（WAF）验证（表 4）。
    - SSD 寿命预测（附录 D）。

## 4. 资源与算力
- **GPU**：2× NVIDIA A100 80GB（单机多卡）。
- **CPU**：2× Intel Xeon Silver 4310。
- **内存**：256GB DDR4。
- **SSD**：1TB NVMe Gen4（pSLC 缓存区 200 GiB）。
- **软件**：vLLM v0.6.6、CUDA 12.3、PyTorch 2.5.1、GDS 1.8.1.2。
- **备注**：论文未明确给出完整训练或推理的总时长，仅报告了单次测试的耗时（如最长测试约 1097 秒），但未统计总 GPU 机时。

## 5. 实验数量与充分性
- **实验数量**：丰富。包括：
    - 输入/输出长度变化（5 个长度点）；
    - 不同批量大小（10, 20, 200 等）；
    - 3 种硬件拓扑；
    - 4 种大模型 × 3 种长上下文数据集；
    - 块大小分析（4 种设置）；
    - I/O 吞吐基准（顺序/随机、不同 LBA 范围）；
    - 初始化时间对比（10 种 cache 大小）；
    - WAF 与寿命分析。
- **充分性**：实验设计较全面，覆盖了典型长上下文推理场景，并与 DRAM 基线在相同框架下公平对比。结果一致表明 HiFC 吞吐与 DRAM 相差在 1–2% 以内。
- **客观性**：论文公开了全部配置和部分代码，并声明了使用 checkpoint，对比基线为标准 vLLM，结论可靠。

## 6. 主要结论与发现
1. **性能相当**：HiFC 在多种长上下文数据集上达到与 DRAM 交换几乎相同的吞吐量，差异不超过 2%。
2. **成本大幅降低**：三年内存扩展成本从 DRAM 的 $614 降至 $136（降价 78%，即 4.5 倍）；若按更新市场数据（H2 2025）则达 6.1 倍。
3. **写放大极低**：WAF = 1.02，有效延长 SSD 寿命，预测在持续负载下 SSD 寿命约 8.3 年。
4. **初始化更快**：HiFC 的 session 初始化时间恒定为 32–34s，而 DRAM 随缓存大小增加至 90s，最大加速 2.81 倍。
5. **硬件可扩展**：多 GPU 模式下 HiFC 可线性扩展吞吐（2:1 和 2:2 拓扑均未出现 I/O 瓶颈）。

## 7. 优点
- **创新性**：首次提出 DRAM-free 的 LLM 推理交换方案，完全消除对主机 DRAM 的依赖。
- **工程实用性**：基于 vLLM 框架改造，无需改变模型架构，易于集成到现有推理服务。
- **性能优化充分**：通过 pSLC 区域、顺序写入、GDS 多线程等多级优化，将 SSD 延迟隐藏在流水线调度下。
- **成本模型严谨**：提供了完整的 TCO 分析，包含资本支出和 3 年运营成本，数据来源于公开市场价格。
- **实验覆盖广**：验证了多种模型、数据集、硬件拓扑，并分析了写放大、寿命、初始化等实际问题。

## 8. 不足与局限
- **短上下文/延迟敏感场景**：在极短上下文或对首 token 延迟要求高的场景中，Flash 访问可能引入额外延迟，不如纯 DRAM 方案。
- **多 GPU 共享带宽**：多 GPU 共享单 SSD 时若调度不当可能引起 I/O 争用，论文中虽测试了 2:1 拓扑但未进行高并发下的压力测试。
- **系统配置门槛**：需针对 SSD 进行 pSLC 分区、GDS 驱动配置和文件系统调优，可能增加部署复杂性。
- **模型规模有限**：最大测试模型为 32B 参数，未在 100B+ 超大规模模型上验证，可扩展性推断存在风险。
- **仅测试推理阶段**：论文未涉及训练或微调场景，仅在推理阶段使用。
- **公开数据有限**：虽声称提供代码，但未在会议材料中给出完整仓库链接，复现需额外沟通。

（完）
