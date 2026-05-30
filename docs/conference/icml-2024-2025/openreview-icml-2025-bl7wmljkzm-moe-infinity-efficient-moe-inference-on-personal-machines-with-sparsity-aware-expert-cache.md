---
title: "MoE-Infinity: Efficient MoE Inference on Personal Machines with Sparsity-Aware Expert Cache"
title_zh: MoE-Infinity：在个人机器上通过稀疏感知专家缓存实现高效MoE推理
authors: "Leyang Xue, Yao Fu, Zhan Lu, Chuanhao Sun, Luo Mai, Mahesh K. Marina"
date: 2025-01-09
pdf: "https://openreview.net/pdf?id=BL7WMLJKZM"
tags: ["query:edge-llm"]
score: 7.0
evidence: 个人机器上MoE推理，内存受限，稀疏感知缓存
tldr: 个人机器GPU内存有限，MoE模型推理困难。本文提出MoE-Infinity，利用单用户场景下专家激活稀疏性，设计稀疏感知专家缓存，跟踪激活模式并指导替换。实验表明在资源受限设备上显著降低内存需求，保持推理速度。
source: ICML-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-bl7wmljkzm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 804, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bl7wmljkzm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 863, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bl7wmljkzm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 702, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bl7wmljkzm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 821, \"height\": 275, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bl7wmljkzm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 834, \"height\": 246, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bl7wmljkzm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 836, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bl7wmljkzm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 853, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bl7wmljkzm/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 781, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bl7wmljkzm/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 777, \"height\": 241, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bl7wmljkzm/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 784, \"height\": 264, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-bl7wmljkzm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 857, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bl7wmljkzm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 837, \"height\": 136, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bl7wmljkzm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 763, \"height\": 247, \"label\": \"Table\"}]"
motivation: 个人机器GPU内存小，难以运行MoE大模型。
method: 利用激活稀疏性，设计稀疏感知专家缓存跟踪和预取专家。
result: 在有限内存下实现高效MoE推理，速度损失小。
conclusion: MoE-Infinity使MoE LLM在个人机器上实用化。
---

## Abstract
This paper presents MoE-Infinity, an efficient MoE inference system designed for personal machines with limited GPU memory capacity. The key idea for MoE-Infinity is that on personal machines, which are often single-user environments, MoE-based LLMs typically operate with a batch size of one. In this setting, MoE models exhibit a high degree of activation sparsity, meaning a small number of experts are frequently reused in generating tokens during the decode phase. Leveraging this idea, we design a sparsity-aware expert cache, which can trace the sparse activation of experts during inference and carefully select the trace that represents the sparsity pattern. By analyzing these selected traces, MoE-Infinity guides the replacement and prefetching of the expert cache, providing 2.7–13.7× per-token latency improvements over numerous state-of-the-art systems, including vLLM, Ollama, DeepSpeed and BrainStorm across various MoE models (DeepSeek and Mixtral) when handling different LLM tasks.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：Mixture-of-Experts（MoE）架构通过稀疏激活大幅降低计算量，因此大型MoE模型（如DeepSeek-MoE、Mixtral）越来越受欢迎。然而，在个人机器上部署这些模型面临GPU显存严重不足（通常仅24–48GB）的挑战，通常需要将专家参数卸载（offloading）到CPU内存，按需取到GPU。
- **问题**：现有推理系统（如DeepSpeed、vLLM、Mixtral-Offloading、BrainStorm）在专家缓存策略上表现不佳，导致高延迟。主要原因包括：① 基于依赖或统计计数的预测无法捕捉MoE的稀疏激活模式；② 跨请求的激活趋于均匀，传统LRU或全局频率方法失效；③ 预取不准确引发PCIe总线争用，加剧GPU空闲时间。
- **核心挑战**：如何在单用户、batch size=1的典型场景下，设计有效的专家缓存策略，利用激活稀疏性实现低延迟推理。

### 2. 论文提出的方法论

- **核心思想**：个人机器上单请求解码时，MoE模型呈现**请求级稀疏激活**：仅少数专家被频繁复用，且这种模式在不同请求间形成可聚类的小规模激活模式。由此设计**稀疏感知专家缓存**（Sparsity-Aware Expert Cache）。
- **关键技术细节**：
  1. **Expert Activation Matrix (EAM)**：记录每个MoE层中每个专家被路由到的token数量，分为迭代级（iEAM）和请求级（rEAM）。
  2. **Expert Activation Matrix Collection (EAMC)**：在线维护一组历史rEAM的集合，容量固定。新请求完成后，将其rEAM与EAMC中已有矩阵计算余弦距离，替换最相似的一个，以快速适应负载变化。
  3. **预测方法（PredictEAM）**：利用当前迭代的iEAM与EAMC中的历史EAM进行匹配（余弦距离最小），将匹配的多个EAM聚合（逐元素求和并行归一化），再引入**层接近度**（Layer Proximity）因子 \((1 - (i-l)/L)\)，生成预测EAM（pEAM），其中每个元素表示专家在未来激活的可能性。
  4. **缓存替换与预取**：根据pEAM计算缓存中每个专家的优先级分数（考虑预测概率和层索引——初始层专家赋予更高缓存优先级），选择分数最低的专家驱逐。同时，利用pEAM对下一层专家进行预取，与计算重叠。
- **算法流程**（以文字说明）：
  - 输入：当前迭代iEAM、请求的专家ID、EAMC、缓存；
  - 若专家已在缓存，直接返回；
  - 若缓存未满，按需取入并返回；
  - 若缓存满，调用PredictEAM生成pEAM；
  - 遍历缓存中专家，计算优先级（\(p = \frac{p\text{eam}[e.layer] + \epsilon}{n_{token}} \cdot (1 - \frac{e.layer}{L})\)），选择p最小的专家驱逐；
  - 按需取入新专家，返回。

### 3. 实验设计

- **使用的数据集/场景**：
  - 三种LLM任务数据集：**BIGBench**（166个任务）、**FLAN**（66个任务）、**MMLU**（58个任务），总共**290个任务**，覆盖推理、问答、翻译、自由回答等。
  - 额外使用**LongBench**进行长上下文测试（最大131072 token）。
- **对比方法**：
  - **DeepSpeed-Inference**（FastGen）
  - **Llama.cpp**
  - **Mixtral-Offloading**
  - **BrainStorm**（作者复现其核心思想）
  - **vLLM**（支持offloading）
- **评估指标**：**Time-Per-Output-Token (TPOT)**，即每个输出token的延迟。

### 4. 资源与算力

- **GPU**：单张 **NVIDIA RTX A5000**（24GB显存），通过 **PCIe 4.0**（32GB/s）连接主机。
- **主机内存**：根据模型大小配置不同：Switch（64GB）、NLLB（256GB）、DeepSeek（32GB）、Mixtral（128GB）、Arctic（1TB）。
- **训练时长**：文中未提及，因为本文聚焦推理系统设计，不涉及模型训练。

### 5. 实验数量与充分性

- **主要实验**：
  1. **端到端延迟**（图7）：在5种MoE模型上对比所有基线，平均延迟统计。
  2. **长上下文性能**（图8）：DeepSeek-V2-Lite在context长度从4K到128K的变化。
  3. **EAMC容量敏感性**（图9）：调整EAMC容量（1~120），观察延迟变化。
  4. **鲁棒性/负载变化**（表3）：同一数据集内任务切换、不同数据集间切换，记录恢复低延迟所需的请求数量。
- **补充实验**：激活模式聚类分析（表2）、Markov链转移概率（图4）等，支持方法设计。
- **充分性评估**：实验覆盖了多种模型规模、多种任务类型、多种上下文长度，并且与多个SOTA系统公平对比（使用相同硬件、相同模型）。不足之处：对Mixtral（8专家/层）改进较小，且未在多batch或高并发场景下验证。整体较为充分，结论可信。

### 6. 论文的主要结论与发现

- **性能提升**：MoE-Infinity在所有对比系统中实现了**2.7–13.7×**的per-token延迟改进（TPOT）。例如在DeepSeek-V2-Lite上，平均TPOT为173ms，而vLLM为485ms，DeepSpeed为737ms。
- **长上下文鲁棒性**：上下文长度达到128K时，由于KV-cache占用了GPU显存，缓存空间缩小，但仍通过按需取回保持较低延迟（比vLLM/Mixtral-Offloading更好）。
- **EAMC容量**：仅需约3%的总请求数（即120左右）即可捕获大多数激活模式，且匹配开销仅21μs（1K EAMs）至226μs（10K EAMs），远低于模型推理延迟。
- **负载适应**：任务切换后约50个请求内即可恢复低延迟，数据集切换后约30个请求。

### 7. 优点

1. **精准的动机分析**：通过大量trace实验证明请求级稀疏激活的存在（图2、表2），为缓存设计提供坚实依据。
2. **创新的缓存策略**：提出请求级EAM追踪和基于余弦匹配的预测，克服了全局统计和LRU的局限。
3. **实用性**：开源且易于部署，支持多种MoE模型和PyTorch/HuggingFace格式，包含预取、层优先缓存等优化。
4. **低开销**：EAMC容量小，搜索效率高，内存和计算开销均低于推理延迟的1%。
5. **长上下文表现**：通过保留全部KV-cache在GPU，避免了VLLM中KV-cache与专家参数的争用。

### 8. 不足与局限

1. **场景局限性**：仅针对单用户、batch size=1的典型个人机器场景，未评估多用户或连续批处理环境。对于服务器端的批量推理可能不适用。
2. **对小型MoE模型效果有限**：在Mixtral-8x7B（仅8个专家/层，激活率约25%）上改进仅1.4×，其他模型改进更大，说明方法对专家数较多、激活更稀疏的模型更有效。
3. **预测方法的泛化性**：依赖EAMC中的历史请求，若遇到全新任务类型且EAMC容量有限，初期可能出现缓存缺失。虽然实验显示恢复快，但极端情况下可能需要更多请求适应。
4. **未讨论多GPU场景的全面性能**：虽然提到支持expert parallelism，但未给出具体加速比或对比。
5. **BrainStorm复现**：由于BrainStorm未开源，作者自行复现可能未完全反映原系统性能，对比可能存在偏差。

（完）
