---
title: "KeyDiff: Key Similarity-Based KV Cache Eviction for Long-Context LLM Inference in Resource-Constrained Environments"
title_zh: KeyDiff：基于键相似性的KV缓存驱逐方法，用于资源受限环境下的长上下文LLM推理
authors: "Junyoung Park, Dalton Jones, Matthew J Morse, Raghavv Goel, Mingu Lee, Christopher Lott"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=uBaFH7aQnC"
tags: ["query:edge-llm"]
score: 7.0
evidence: 面向资源受限环境的KV缓存驱逐方法
tldr: 本文发现几何独特的键通常获得高注意力分数，据此提出KeyDiff，仅基于键相似性进行无训练KV缓存驱逐，无需依赖注意力分数，兼容FlashAttention，在严格内存限制下高效处理长上下文LLM推理。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1235, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1431, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 602, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1415, \"height\": 316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 504, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1457, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1430, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1419, \"height\": 317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1410, \"height\": 318, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1414, \"height\": 318, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1400, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 722, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1332, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 861, \"height\": 704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1311, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 960, \"height\": 784, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1425, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1418, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ubafh7aqnc/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 740, \"height\": 364, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 947, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 900, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 913, \"height\": 406, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1164, \"height\": 850, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1223, \"height\": 1379, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1163, \"height\": 847, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1222, \"height\": 1374, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1081, \"height\": 668, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 794, \"height\": 949, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1076, \"height\": 2152, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1361, \"height\": 2138, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1042, \"height\": 2133, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1047, \"height\": 2129, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1015, \"height\": 2141, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 514, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 516, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1051, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1223, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ubafh7aqnc/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 627, \"height\": 206, \"label\": \"Table\"}]"
motivation: 长上下文推理中KV缓存消耗大，现有驱逐方法依赖注意力分数导致优化注意力机制受限。
method: 基于键相似性识别重要令牌进行驱逐，无需注意力分数。
result: 在严格内存限制下高效处理长上下文，兼容FlashAttention。
conclusion: KeyDiff是面向资源受限环境的实用KV缓存驱逐技术。
---

## Abstract
We demonstrate that geometrically distinctive keys during LLM inference tend to have high attention scores. Based on the phenomenon we propose KeyDiff, a training-free KV cache eviction method based solely on key similarity. Unlike other KV cache eviction methods, KeyDiff can process arbitrarily long prompts within strict resource constraints and efficiently generate responses.
We provide a theoretical basis for KeyDiff by relating key diversity with attention scores. These results imply  KeyDiff can efficiently identify the most important tokens to retain. Notably KeyDiff does not rely on attention scores, allowing the use of optimized attention mechanisms like FlashAttention. Under a strict memory allowance, we demonstrate the effectiveness of KeyDiff for the Llama and Qwen model families by observing a performance gap of less than 0.04\% with 8K cache budget (~23\% KV cache reduction) from the non-evicting baseline on LongBench for Llama 3.1-8B and Llama 3.2-3B. We also observe near baseline performance for Deepseek-R1-Distill-Llama-8B on the Math500 reasoning benchmark and decrease end-to-end inference latency by up to 30\% compared to the other token-eviction methods.

---

## 论文详细总结（自动生成）

## 论文总结：KeyDiff: 基于键相似性的 KV 缓存驱逐方法

### 1. 核心问题与研究动机
- **问题背景**：大语言模型（LLM）推理中，KV 缓存大小随输入长度线性增长，在资源受限环境（如边缘设备）中成为瓶颈。现有 KV 缓存驱逐方法通常依赖于注意力分数，但存在两个问题：
  1. 需要显式物化注意力权重，无法与 FlashAttention 等高效注意力机制兼容；
  2. 在分块推理（block-wise processing）场景下，注意力分数仅基于当前块而非全局信息，导致驱逐决策不准确。
- **研究目标**：提出一种训练无关、仅依赖键之间相似性的 KV 缓存驱逐方法，能在严格内存约束下处理任意长上下文，并保持高精度与低延迟。

### 2. 方法论
- **核心观察**：通过实验发现，键的成对余弦相似度越低（即几何上越独特），其注意力分数往往越高。这一现象表明键的多样性可以作为令牌重要性的代理。
- **KeyDiff 算法**：
  - 基本版本：对于缓存中的键矩阵 \(K \in \mathbb{R}^{n \times d}\)，计算所有键两两之间的余弦相似度矩阵，然后对每个键求和得到其“相似度分数”，保留分数最小的 \(N\) 个键（即最独特的键）。
  - **高效变体**：为避免 \(O(n^2)\) 计算，使用**锚向量**（anchor vector）近似：计算所有归一化键的平均值 \(\mu(\hat{K})\)，然后计算每个键与锚向量的余弦相似度，保留相似度最小的 \(N\) 个键。复杂度降至 \(O(n)\)。
  - **滑动窗口增强**：对于推理或代码生成等任务中最近令牌重要的情况，可将部分缓存预算用作滑动窗口，其余部分由 KeyDiff 管理。
- **理论依据**：
  - 引理3.1：给定有界范数的键集，高注意力权重 \(w\) 要求新键 \(k^*\) 与查询 \(q\) 具有高余弦相似度。
  - 定理3.2：若 \(k^*\) 与 \(q\) 正相关（\(\beta_q > 0\)），而平均键 \(\bar{k}\) 与 \(q\) 负相关（\(\alpha_q < 0\)），则 \(\text{CosSim}(\bar{k}, k^*)\) 有上界，表明 KeyDiff 选出的键与查询最对齐。
- **流程**：采用分块处理（block-wise），每处理完一个块后执行驱逐，保证始终满足缓存预算。

### 3. 实验设计
- **数据集/基准**：
  - **LongBench**（多任务长上下文基准）：包括单文档 QA、多文档 QA、摘要、少样本学习、合成、代码补全等子集。
  - **Needle-in-a-Haystack**（信息检索压力测试）。
  - **Math-500**（数学推理基准），使用 DeepSeek-R1-Distill-Llama-8B 和 Qwen-7B 蒸馏模型。
- **对比方法**：H2O、TOVA、Sink Attention（StreamingLLM）、SnapKV、KeyL2Norm [9]（L2 范数最小化方法），以及无驱逐的全缓存基线。
- **模型**：Llama 3.1-8B-Instruct、Llama 3.2-3B-Instruct、Qwen 2.5-3B/7B-Instruct、DeepSeek-R1 蒸馏变体。
- **设置**：分块大小 \(B=128\)（默认），缓存预算 2K/4K/6K/8K，贪婪解码。

### 4. 资源与算力
- **硬件**：NVIDIA A100 80GB GPU。
- **未明确说明**：具体 GPU 数量、总运行时长。TTFT 测试使用单 GPU 测量，推理延迟对比在 A100 及 Android 设备（移动端）上进行。

### 5. 实验数量与充分性
- **大量实验**：在 LongBench 的所有子集（20+个任务）上进行系统评估，覆盖不同模型、不同缓存预算、不同分块大小（\(B=64,128,256\)）。
- **消融实验**：验证锚向量选择均值 vs. 中位数 vs. 成对相似度；距离度量（余弦、点积、欧氏距离）；滑动窗口比例。
- **Needle-in-a-Haystack**：不同文档长度和针深度。
- **Math-500**：多个随机种子重复（5次），结果取平均。
- **效率实验**：TTFT 对比，以及 Android 设备上驱逐分数计算延迟。
- **充分性**：实验覆盖了多个模型家族、多种任务类型、不同约束水平，且对比了最先进方法，结论可靠。但缺乏在不同量化级别或更极端资源限制下的测试。

### 6. 主要结论与发现
- KeyDiff 在 LongBench 上以 6K 缓存预算（压缩率 ~33%）仅损失 ≤1.5% 准确率，8K 预算（压缩率 ~23%）损失 ≤0.04%，优于所有对比方法。
- Needle-in-a-Haystack 测试中，KeyDiff 在长文档及深针场景下召回率最高。
- 推理任务（Math-500）中，KeyDiff 接近无驱逐基线，且优于 SnapKV。
- **延迟优势**：由于不依赖注意力权重，KeyDiff 可与 FlashAttention 结合，TTFT 降低高达 30% 相对于 TOVA 和 SnapKV。
- 理论证明：KeyDiff 通过最大化键多样性，选择与查询最对齐的键。

### 7. 优点
- **方法创新**：提出基于键几何的驱逐准则，不再依赖注意力分数，兼容 FlashAttention。
- **高效**：线性复杂度，可实时处理，移动设备上延迟低。
- **理论支持**：提供了键多样性与注意力分数之间关系的数学证明。
- **鲁棒性**：在分块推理场景下表现稳定，不受注意力局部性影响。
- **广泛验证**：在多个模型家族（Llama、Qwen）和任务（通用、推理）上验证。

### 8. 不足与局限
- **架构限制**：主要针对 GQA 注意力（Llama、Qwen），未评估 MLA（如 DeepSeek-V2）等变体。
- **实验覆盖**：未在更低预算（如 1K）或更大模型（>70B）上测试；量化压缩组合效果未探索。
- **推理场景**：Math-500 上 Qwen 蒸馏模型性能下降较明显，可能由高 GQA 压缩率导致。
- **锚向量近似**：使用均值向量代替成对相似度存在轻微精度损失，但消融显示影响很小。
- **未开源代码**：仅提供算法描述，复现需自行实现。

（完）
