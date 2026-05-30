---
title: "70% Size, 100% Accuracy: Lossless LLM Compression for Efficient GPU Inference via Dynamic-Length Float (DFloat11)"
title_zh: "70%大小，100%精度：通过动态长度浮点数（DFloat11）实现高效GPU推理的无损LLM压缩"
authors: "Tianyi Zhang, Mohsen Hariri, Shaochen Zhong, Vipin Chaudhary, Yang Sui, Xia Hu, Anshumali Shrivastava"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=xdNAVP7TGy"
tags: ["query:edge-llm"]
score: 6.0
evidence: 无损压缩减小模型大小，适配资源受限设备
tldr: "本文提出DFloat11无损压缩框架，利用BFloat16权重表示的熵冗余，通过熵编码分配动态长度编码，将LLM大小减少30%且输出比特一致。该方法为资源受限硬件上的高效推理提供了通用压缩技术，尤其适合边缘设备部署。"
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1424, \"height\": 654, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1447, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1434, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1430, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1431, \"height\": 696, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1422, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1443, \"height\": 791, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1439, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1433, \"height\": 860, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1442, \"height\": 828, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1133, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xdnavp7tgy/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1453, \"height\": 626, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-xdnavp7tgy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xdnavp7tgy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1433, \"height\": 654, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xdnavp7tgy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1296, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xdnavp7tgy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1387, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xdnavp7tgy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1155, \"height\": 219, \"label\": \"Table\"}]"
motivation: 大型LLM在资源受限硬件上部署困难，现有存储格式存在效率浪费。
method: 基于熵编码的DFloat11格式，对BFloat16权重按频率分配动态长度编码。
result: "压缩后模型大小减少30%，输出与原模型比特级一致。"
conclusion: DFloat11是一种高效的无损压缩方法，可显著降低LLM存储需求。
---

## Abstract
Large-scale AI models, such as Large Language Models (LLMs) and Diffusion Models (DMs), have grown rapidly in size, creating significant challenges for efficient deployment on resource-constrained hardware. In this paper, we introduce Dynamic-Length Float (DFloat11), a lossless compression framework that reduces LLM and DM size by 30\% while preserving outputs that are bit-for-bit identical to the original model. DFloat11 is motivated by the low entropy in the BFloat16 weight representation of LLMs, which reveals significant inefficiency in the existing storage format. By applying entropy coding, DFloat11 assigns dynamic-length encodings to weights based on frequency, achieving near information-optimal compression without any loss of precision. To facilitate efficient inference with dynamic-length encodings, we develop a custom GPU kernel for fast online decompression. Our design incorporates the following: (i) compact, hierarchical lookup tables (LUTs) that fit within GPU SRAM for efficient decoding, (ii) a two-phase GPU kernel for coordinating thread read/write positions using lightweight auxiliary variables, and (iii) transformer-block-level decompression to minimize latency. Experiments on Llama 3.3, Qwen 3, Mistral 3, FLUX.1, and others validate our hypothesis that DFloat11 achieves around 30\% model size reduction while preserving bit-for-bit identical outputs. Compared to a potential alternative of offloading parts of an uncompressed model to the CPU to meet memory constraints, DFloat11 achieves 2.3--46.2$\times$ higher throughput in token generation. With a fixed GPU memory budget, DFloat11 enables 5.7--14.9$\times$ longer generation lengths than uncompressed models. Notably, our method enables lossless inference of Llama 3.1 405B, an 810GB model, on a single node equipped with 8$\times$80GB GPUs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大型语言模型（LLM）和扩散模型（DM）规模快速增长，例如Llama 3.1 405B需约810GB内存，远超单块高端GPU（如80GB），导致多节点部署成本高昂。现有方案如**有损量化**引入精度下降、行为翻转（flips）及合规风险；**无损压缩**方法（如Deep Compression、ZipNN）仅适用于存储或FPGA，无法支持高效GPU推理。
- **目标**：提出一种**无损、支持GPU高效推理**的压缩框架，将模型大小减少约30%，同时保持输出与原模型比特级一致。

## 2. 方法论

### 核心思想
- **关键洞察**：BFloat16权重中，**指数位（8位）的实际信息熵仅约2.6位**，存在大量冗余；符号位和尾数位熵接近其位宽，冗余小。
- **压缩策略**：对指数部分应用**霍夫曼编码**（动态长度编码），符号和尾数保持不变。压缩后平均约11位（DFloat11）。

### 关键技术细节
1. **熵编码的适用性**：BFloat16权重的指数分布高度偏斜（仅约40个指数值被使用），频率衰减快。
2. **高效GPU解码挑战**：霍夫曼码是变长的，传统树遍历在GPU上并行性差。
3. **层次化查找表（LUTs）**：将整个霍夫曼树分解为高度为8的非重叠子树，每个LUT大小为2^8=256。利用指数值稀疏性，将未出现的指数值（240-255）作为指向下层LUT的指针。总LUT数量4-8个，占用(8+1)×256字节，可放入GPU SRAM。
4. **两阶段GPU内核**：
   - **阶段1**：每个线程解码其分配的字节块（n=8），只计数元素个数，不写结果。使用`Gaps`数组（5位偏移量）指定每个线程的起始位偏移。
   - **同步**：线程块内Blelloch前缀和计算每个线程的输出位置。
   - **阶段2**：重新解码同一块，将结果写入SRAM缓冲区，最后合并写入HBM。
   - 使用轻量级辅助变量：`Gaps`和`BlockOutputPos`（每个块一个输出起始位置）。
5. **Transformer块级批处理解压**：将每个transformer块内所有权重矩阵一次性解压，利用更大矩阵尺寸提高GPU利用率。嵌入层和语言模型头单独解压。

### 公式与算法
- BFloat16数值：\((-1)^{\text{sign}} \times 2^{\text{exponent}-127} \times (1.\text{mantissa})\)
- 熵公式：\(H(X) = -\sum_{x} p(x) \log_2 p(x)\)
- 算法伪代码（Algorithm 1）见附录D：详细描述两阶段过程。

## 3. 实验设计

### 数据集/场景
- **模型**：Llama 3.1/3.3（8B/70B/405B）、Qwen 3（14B）、QwQ（32B）、Mistral Nemo/Small、Phi 4、DeepSeek R1 Distill（8B）、Stable Diffusion 3.5、FLUX.1。
- **评估基准**：MMLU、TruthfulQA、WikiText、C4（同困惑度或准确率）。
- **任务**：文本生成吞吐量/延迟、图像生成（扩散模型）、长生成长度（KV cache占用）。

### Benchmark与对比方法
- **对比方案**：
  - BF16模型 + CPU offloading（通过HuggingFace Accelerate框架）
  - NVIDIA nvCOMP ANS解压（GPU-only）
  - CPU-to-GPU传输（BF16权重从CPU拷贝到GPU）
- **指标**：压缩率、准确率/困惑度、吞吐量（tokens/s）、延迟（s/token）、峰值GPU内存。

## 4. 资源与算力

- 使用三台服务器（附录表4）：
  - Server1：RTX A5000（24GB）、AMD EPYC 7513、504GB内存
  - Server2：A100（40GB）、AMD EPYC 7742、1.48TB内存
  - Server3：RTX 8000（48GB）、AMD EPYC 7742、1.48TB内存
- **压缩时间**（单线程CPU）：Llama 3.1 8B每个transformer块约191秒；70B约547秒；405B约2133秒。压缩是一次性预处理，可并行。
- 未提供训练资源，仅推理压缩。

## 5. 实验数量与充分性

- **主要实验**：
  - 压缩率表（表1）：覆盖9个LLM和3个扩散模型，均显示~68%压缩率。
  - 准确性验证（表2）：Llama 3.1 8B在MMLU、TruthfulQA、WikiText、C4上DF11与BF16完全一致。
  - 推理性能对比（图4）：3种GPU+3个模型，多种batch size，证明DF11吞吐量和延迟均优于CPU offloading（2.3-46.2×）。
  - 扩散模型内存与时间（表3）：SD3.5和FLUX.1内存减少28%，时间仅增加4-5%。
  - 长生成长度（图5）：DF11允许生成5.7-14.9×更多token。
  - 消融实验（图6）：延迟分解展示解压开销，大batch下被摊销。
  - 解压吞吐量对比（图7）：与nvCOMP ANS和CPU传输对比，DF11吞吐量高34.95×，延迟低。
- **充分性**：覆盖不同规模模型、不同GPU、不同batch size、多种任务。实验设计客观，与主流基准对比，且提供误差条。但仅对比了CPU offloading，未与全BF16 GPU-only场景（若设备内存足够）对比，因为受限于内存限制。

## 6. 主要结论与发现

- DFloat11可实现**约30%模型大小减少**（平均11bits/权重），**输出与原模型比特级相同**。
- 在内存受限的单GPU上，DF11相比BF16+CPU offloading，吞吐量**提升2.3-46.2×**，延迟显著降低。
- 在固定GPU内存预算下，DF11支持**5.7-14.9×更长的生成长度**。
- 使**Llama 3.1 405B**（810GB）可在单节点8×80GB GPU上无损推理，降低硬件需求一半。
- 解压内核在GPU上高效运行，解压开销随batch size增加可被摊销。

## 7. 优点

- **无损性**：保证模型行为完全不变，避免量化引入的精度损失、行为翻转和合规问题。
- **硬件感知设计**：层次化LUT适应GPU SRAM；两阶段内核最小化内存访问；块级合并写，充分利用GPU并行性。
- **实用性强**：支持多种主流LLM和扩散模型，压缩比稳定，推理效率高。
- **开源友好**：代码和模型在GitHub和HuggingFace发布（代码链接、模型链接）。

## 8. 不足与局限

- **仅限BFloat16**：不适用于FP32、FP16、FP8等格式，可能需不同压缩策略。
- **引入额外延迟**：解压带来微小延迟，小batch下可能显著；需大batch摊销。
- **仅评估GPU**：未在CPU、TPU或专用加速器上验证，平台可移植性未知。
- **压缩时间较长**：单线程处理每个transformer块耗时数分钟至半小时，但可并行。
- **推理对比范围有限**：未与全BF16 GPU-only场景（若设备内存允许）对比，只对比了CPU offloading。未对比其他无损GPU推理方法（如NeuZip，由于nvCOMP闭源且效率差）。
- **无新模型训练**：仅做压缩后推理，不涉及训练或微调，对模型原始能力无提升。

（完）
