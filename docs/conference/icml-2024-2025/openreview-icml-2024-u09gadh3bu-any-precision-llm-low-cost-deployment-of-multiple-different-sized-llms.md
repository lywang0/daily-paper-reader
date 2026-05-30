---
title: "Any-Precision LLM: Low-Cost Deployment of Multiple, Different-Sized LLMs"
title_zh: 任意精度LLM：低成本部署多个不同大小的LLM
authors: "Yeonhong Park, Jake Hyun, SangLyul Cho, Bonggeun Sim, Jae W. Lee"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=u09gadH3BU"
tags: ["query:edge-llm"]
score: 6.0
evidence: 任意精度量化支持低成本部署多个不同大小的LLM
tldr: 该论文将任意精度（any-precision）概念扩展到LLM，提出轻量级后训练量化方法和专用服务引擎，支持以低开销同时部署多个不同大小的LLM。这种方法降低了多模型部署的成本，对于资源受限场景下的服务灵活性和效率具有重要意义。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 855, \"height\": 322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 866, \"height\": 232, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 864, \"height\": 290, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 850, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1768, \"height\": 367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 870, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 864, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 865, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 865, \"height\": 309, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 870, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 866, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 866, \"height\": 1421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 866, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 858, \"height\": 1079, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-u09gadh3bu/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 864, \"height\": 374, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-u09gadh3bu/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-u09gadh3bu/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 865, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-u09gadh3bu/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1780, \"height\": 410, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-u09gadh3bu/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 873, \"height\": 480, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-u09gadh3bu/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 858, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-u09gadh3bu/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1776, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-u09gadh3bu/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 871, \"height\": 575, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-u09gadh3bu/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 982, \"height\": 2343, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-u09gadh3bu/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 908, \"height\": 2352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-u09gadh3bu/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1765, \"height\": 1735, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-u09gadh3bu/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1772, \"height\": 716, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-u09gadh3bu/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1776, \"height\": 1819, \"label\": \"Table\"}]"
motivation: 部署多个不同大小的LLM成本高昂，现有研究较少关注。
method: 提出任意精度量化方法，基于后训练量化框架，并开发专用服务引擎。
result: 方法实现了多个不同大小LLM的高效部署，减少了存储和切换开销。
conclusion: 任意精度量化是多模型部署中降低成本的有效策略。
---

## Abstract
Recently, considerable efforts have been directed towards compressing Large Language Models (LLMs), which showcase groundbreaking capabilities across diverse applications but entail significant deployment costs due to their large sizes. Meanwhile, much less attention has been given to mitigating the costs associated with deploying multiple LLMs of varying sizes despite its practical significance. Thus, this paper introduces any-precision LLM, extending the concept of any-precision DNN to LLMs. Addressing challenges in any-precision LLM, we propose a lightweight method for any-precision quantization of LLMs, leveraging a post-training quantization framework, and develop a specialized software engine for its efficient serving. As a result, our solution significantly reduces the high costs of deploying multiple, different-sized LLMs by overlaying LLMs quantized to varying bit-widths, such as 3, 4, ..., $n$ bits, into a memory footprint comparable to a single $n$-bit LLM. All the supported LLMs with varying bit-widths demonstrate state-of-the-art model quality and inference throughput, proving itself to be a compelling option for deployment of multiple, different-sized LLMs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大规模语言模型（LLMs）部署成本高昂，尤其是当需要同时部署多个不同大小（不同位宽）的模型时，内存开销和训练成本会显著增加。实际场景中（如不同延迟要求的查询、推测解码等）往往需要动态切换多个不同精度/大小的LLM，但现有工作主要关注单个模型的压缩，忽视了多模型部署的代价。
- **核心问题**：如何在不显著增加内存和训练成本的前提下，支持以任意精度（3、4、…、n位）同时部署多个不同大小的LLM，并保证模型质量和推理效率。
- **整体含义**：提出“任意精度LLM”（any-precision LLM）概念，将任意精度DNN的思想扩展到LLM，通过后训练量化（PTQ）和专用软件引擎实现多模型低开销部署，降低存储和切换开销。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过**增量式升尺度（Incremental Upscaling）** 方法，先量化出最低位宽的种子模型（如3位），然后逐位增加高比特权重，最终得到一个n位父模型。所有低位模型只需通过截取父模型权重的高位比特即可得到，无需单独存储或训练。
- **关键技术细节**：
  - **基于非均匀量化的增量升尺度**：采用SqueezeLLM的聚类式非均匀量化作为基础。升尺度时，将每个聚类（bin）进一步划分为两个子聚类，并基于敏感度（二阶导数近似）进行加权K-means。该方法天然支持非均匀量化，且与均匀量化方法（如GPTQ、AWQ）相比，不会导致严重性能退化（实验证实）。
  - **专用软件引擎**：采用**位平面（bitplane）表示**而非传统的位打包（bitpacking）表示，以便只加载所需比特数，实现低比特推理的线性加速。优化包括：
    - **权重位平面布局优化**：通过字节置换实现线程束内激活值的连续访问（合并内存访问）。
    - **高效位转置算法**：将32位向量视为多个子向量，利用SIMD思想减少位操作次数（从76次降至40次）。
    - **合并表查找**：对小位宽（如3位）合并两个索引查找，减少位操作和共享内存访问。
- **算法流程**（文字说明）：
  1. 生成种子模型（最低位宽，如3位）：使用SqueezeLLM对FP16模型进行后训练量化。
  2. 逐位升尺度：对当前k位模型的每个聚类，使用加权K-means将其划分为两个子聚类，得到k+1位模型。所有步骤无需重新训练，仅需少量校准数据。

## 3. 实验设计：数据集、基准与对比方法

- **数据集**：
  - 困惑度评估：WikiText2、Penn Treebank（PTB）、C4（验证集）。
  - 零样本准确率：ARC-easy、ARC-challenge、HellaSwag、PIQA、WinoGrande（5个任务）。
- **基准**：FP16全精度模型，以及独立量化的SqueezeLLM模型（每个位宽分别量化）。
- **对比方法**：
  - 量化方法对比：SqueezeLLM（论文骨干），并提供与GPTQ、AWQ等均匀量化方法的兼容性分析（附录E）。
  - 核性能对比：与SqueezeLLM原始核、ExLlamaV2、LUT-GEMM、TensorRT-LLM等现有量化推理内核对比。
  - 平台：RTX 4090（桌面）、RTX 4070 Laptop（笔记本）、Jetson AGX Orin（移动端）。

## 4. 资源与算力

- **训练/量化开销**：论文采用后训练量化（PTQ），无需大规模训练。量化过程在Intel i9-13900K CPU（24核）上完成，耗时如表5所示：
  - Llama-2-7B：种子生成36.2秒 + 增量升尺度15.6秒 = 51.8秒。
  - 其他模型（Mistral-7B、OPT-6.7B等）均在1分钟内完成。
- **推理硬件**：实验在RTX 4090、RTX 4070 Laptop、Jetson AGX Orin上进行，均为单GPU测试。未说明使用多GPU或分布式环境。
- **算力规模**：相对较低，适合个人设备或边缘部署场景。

## 5. 实验数量与充分性

- **实验数量**：充分且系统化。
  - 困惑度：覆盖5个模型（Llama-2-7B、Mistral-7B、OPT-6.7B/2.7B/1.3B），3个数据集，位宽从3到8位，共约5×3×6=90个数据点（表3）。
  - 零样本准确率：相同模型和位宽，5个任务，表8给出完整结果。
  - 核微基准测试：3种矩阵尺寸，3种GPU，与SqueezeLLM核对比（表6），以及与其他通用量化核对比（附录C）。
  - 端到端吞吐量：Llama-2-7B及多个模型，128和1024 token生成长度（图12、附录D）。
  - 消融实验：3种优化技术（WLO、IBT、TLM）在不同位宽和平台上的贡献（图10）。
- **充分性与公平性**：
  - 对比方法均为现有最优，且作者提供了代码开源，可复现。
  - 但未与最新的一些量化方法（如QuIP、SpQR）在全套实验上对比（仅提及但未直接比较）。不过论文聚焦于任意精度特性，与独立量化方法公平比较了模型质量。
  - 核性能对比中，与不支持任意精度的内核对比存在不对等，但作者明确指出这是非公平比较（non-apples-to-apples），并展示了自己内核的竞争力。

## 6. 论文的主要结论与发现

- 通过增量式升尺度，可以生成一系列位宽从3到8的量化LLM，其困惑度和零样本准确率与独立量化的SqueezeLLM模型几乎一致（差距<0.1 perplexity，准确率波动≤0.2%）。
- 专用引擎实现了低比特推理的近乎线性加速，在RTX 4090上3位比FP16快约4倍，且与SqueezeLLM核性能相当或更优（尤其在Jetson上显著提升）。
- 整体内存节省：支持3-8位所有模型时，内存占用仅为独立部署的1/3.56（表1）。
- 量化过程极快（<1分钟），适合个人开发者和边缘设备。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：将任意精度概念扩展到LLM，填补了多模型部署低成本的空白。
- **轻量化**：完全基于PTQ，无需训练，且量化时间极短，实用性强。
- **工程优化**：位平面布局优化、高效位转置、合并表查找等技巧显著提升内核性能，并在多种GPU上验证。
- **实验全面**：覆盖不同规模模型（1.3B~7B）、不同平台（桌面、笔记本、移动端），以及常见量化评价指标。
- **开源可复现**：代码已公开（GitHub）。

## 8. 不足与局限

- **实验覆盖的偏差风险**：
  - 对比方法仅选取了SqueezeLLM作为骨干，并证明与GPTQ/AWQ不兼容，但未尝试其他可能更适合增量升尺度的均匀量化改进（如自适应分桶）。
  - 零样本任务仅5个，未涵盖更多语言理解/生成基准（如MMLU、BIG-Bench）。
  - 端到端吞吐量测试仅使用TensorRT-LLM作为后端，未与其他推理框架（如vLLM、TGI）对比。
- **应用限制**：
  - 当前引擎不支持张量核心（Tensor Cores），导致预填充阶段（大批处理）性能下降，需要回退到cuBLAS+反量化，增加额外延迟。
  - 仅支持非均匀量化（SqueezeLLM风格），不支持均匀量化，限制了通用性。
  - 未考虑动态选择策略（如运行时自动选择位宽）的实现与开销。
- **资源说明**：
  - 仅使用单GPU测试，未评估多GPU/分布式部署情况。
  - 未测量能效（功耗）指标，而这是边缘设备的重要考量。
- **潜在偏差**：作者来自首尔大学，实验软件依赖NVIDIA工具链（Nsight、TensorRT-LLM），可能对NVIDIA GPU有优化偏向，对其他硬件（如AMD、Apple Silicon）未验证。

（完）
