---
title: "DuoGPT: Training-free Dual Sparsity through Activation-aware Pruning in LLMs"
title_zh: DuoGPT：通过激活感知剪枝实现免训练双稀疏化的大语言模型
authors: "Ruokai Yin, Yuhang Li, Donghyun Lee, Priyadarshini Panda"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=PjbpL4brUb"
tags: ["query:edge-llm"]
score: 7.0
evidence: 激活感知剪枝以减少内存和计算
tldr: 针对大语言模型部署中高内存和计算成本的问题，DuoGPT提出一种免训练的双稀疏化框架，将非结构化权重剪枝与运行时激活稀疏性结合，生成双稀疏计算负载。通过扩展最优脑压缩框架并引入激活感知校准和输出残差校正，该方法在保持精度的同时大幅降低推理开销，并在十亿参数模型上验证了可扩展性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-pjbpl4brub/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1096, \"height\": 409, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-pjbpl4brub/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1433, \"height\": 537, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-pjbpl4brub/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 572, \"height\": 276, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-pjbpl4brub/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1434, \"height\": 624, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-pjbpl4brub/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1130, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-pjbpl4brub/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1290, \"height\": 805, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1423, \"height\": 752, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1458, \"height\": 895, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1453, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 553, \"height\": 161, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 791, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 736, \"height\": 160, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 596, \"height\": 200, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1452, \"height\": 188, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1459, \"height\": 1611, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1128, \"height\": 188, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1192, \"height\": 189, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1242, \"height\": 289, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pjbpl4brub/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1278, \"height\": 225, \"label\": \"Table\"}]"
motivation: 大语言模型部署成本高，现有剪枝方法忽略运行时激活稀疏性。
method: 提出DuoGPT框架，将非结构化权重剪枝与激活稀疏性结合，生成双稀疏工作负载，并采用激活感知校准和残差校正保持精度。
result: 在多个基准上实现显著的内存和计算减少，同时保持模型精度。
conclusion: DuoGPT通过激活感知双稀疏化，为LLM高效部署提供了一种免训练的解决方案。
---

## Abstract
Large language models (LLMs) deliver strong performance but are difficult to deploy due to high memory and compute costs. While pruning reduces these demands, most methods ignore activation sparsity observed at runtime. We reinterpret activation sparsity as dynamic structured weight sparsity and propose DuoGPT, a unified framework that constructs dual-sparse (spMspV) workloads by combining unstructured weight pruning with activation sparsity. To preserve accuracy, we extend the Optimal Brain Compression (OBC) framework with activation-aware calibration and introduce output residuals from the dense model as correction terms. We further optimize the solution for efficient GPU execution, enabling scalability to billion-parameter LLMs. Evaluations on LLaMA-2 and LLaMA-3 show that DuoGPT outperforms state-of-the-art structured pruning methods by up to 9.17\% accuracy at an iso-speedup of 1.39$\times$ compared to the baseline dense model. Code is available at GitHub.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

大语言模型（LLM）虽然性能优异，但部署时面临高内存和计算成本的问题。现有的剪枝方法大多忽略了运行时观测到的激活稀疏性。论文的核心动机是：**如何同时利用激活稀疏性和权重稀疏性，在保持模型精度的前提下显著降低推理开销**。作者重新将激活稀疏性解释为动态的结构化权重稀疏性，提出一个统一的双稀疏框架 DuoGPT，通过结合非结构化权重剪枝与运行时激活稀疏性，生成稀疏矩阵-稀疏向量（spMspV）工作负载，从而在不增加训练成本的前提下实现高效推理。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将激活稀疏性视为一种动态的结构化权重稀疏性，并与非结构化权重剪枝结合，实现“双稀疏”（权重和激活同时稀疏）。在解码阶段，仅需加载和计算非零激活对应的权重行，且权重本身已压缩存储，进一步减少 HBM 到 SRAM 的数据搬运和计算量。
- **关键技术细节**：
  - 在最优脑压缩（OBC）剪枝框架基础上，引入激活感知校准：使用经过激活稀疏化后的校准输入 \(\hat{X}\) 进行剪枝，同时利用原始密集模型的输出 \(\tilde{X}\) 构建残差项 \(r = W(\hat{X} - \tilde{X})\)，修正因激活稀疏导致的信息损失。
  - 推导出包含残差项的新损失函数和权重更新公式（式 3），使剪枝过程能自适应补偿激活稀疏误差。
  - **高效实现**：通过分解残差矩阵、利用 Cholesky 分解、向量化预计算等技巧，避免逐列计算的高复杂度，将单层复杂度从 \(O(nmk^2 + nk^3)\) 降至 \(O(mk^2)\)，使得 70B 模型可在单张 A100 GPU 上约 2.3 小时内完成校准（Algorithm 1）。
  - 理论分析（Theorem 1）证明 DuoGPT 相比 SparseGPT 的损失改进下界与激活稀疏度 \(p_x\) 呈正比。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - 校准数据：C4 训练集随机选取 128 个 2048-token 样本。
  - 评估：WikiText2 困惑度（PPL）；零样本任务分类（PIQA, HellaSwag, WinoGrande, ARC-easy, ARC-challenge, OpenBookQA, BoolQ）使用 LM Eval Harness；GSM8K 5-shot 推理基准。
- **基准方法**：
  - 非结构化剪枝基线：SparseGPT、Wanda 及其 2:4 半结构化变体。
  - 结构化剪枝基线：ShortGPT、2SSP、BlockPruner、SliceGPT。
  - 激活稀疏方法：TEAL、R-Sparse、CATS（对比部分）。
- **实验设置**：模型包括 LLaMA-2 (7B/13B/70B)、LLaMA-3 (8B/70B)，以及 Mistral-7B、Qwen2-7B/1.5B、OPT-125M/1.3B 等架构，验证泛化性。主要对比指标为 PPL 和零样本平均准确率，并报告模型大小、端到端加速比。

## 4. 资源与算力

- 文中明确说明：所有校准和实验在 **80GB NVIDIA A100 GPU** 上进行（70B 模型评估时使用两块 GPU 进行零样本评估）。
- 校准时长：LLaMA-3-70B 在单卡 A100 上约 **2.28 GPU 小时**；LLaMA-3-8B 约 0.27 小时；LLaMA-2-7B 约 0.22 小时。对比方法 SparseGPT 和 Wanda 同样在相同 GPU 上运行，时长相近或更短（但 DuoGPT 额外引入残差计算，稍慢仍可接受）。
- 未说明具体集群或云环境，但指出所有实验均基于 PyTorch 和 HuggingFace Transformers，可复现。

## 5. 实验数量与充分性

- **实验数量充足**：覆盖多个模型系列（LLaMA-2/3, Mistral, Qwen, OPT）、多种稀疏水平（30%~70%）、多种任务（PPL + 7 个零样本任务 + GSM8K）。主要对比表（Table 1）共报告 5 个模型 × 4 种方法（含变体）的结果，约 40 余行数据。
- **消融实验**：包含不同双稀疏度水平（Table 3a）、与阈值激活稀疏法的兼容性（Table 3b）、与量化结合（Table 4）、校准集大小和序列长度敏感性（Appendix C.3）、不同架构泛化（Appendix C.7）等。
- **公平性**：所有对比方法使用相同校准数据、相同批次和序列长度设定；结构化剪枝基线按各自原文最佳设置运行。但未报告误差棒或多次运行的标准差（作者解释因随机种子固定）。
- 总体实验设计较为充分，覆盖了主流场景和消融需求，结论可信。

## 6. 论文的主要结论与发现

- DuoGPT 在所有测试模型上均取得最低困惑度和最高零样本平均准确率，尤其是在高稀疏度（50%+）下优势显著。
- 在 50% 双稀疏条件下，相比 SparseGPT/Wanda 的同等稀疏变体，DuoGPT 平均准确率提升 2~5 个百分点；相比 2:4 半结构化剪枝，提升更大（如 LLaMA-3-8B 提升 5.45%）。
- 与结构化剪枝方法（如 ShortGPT）相比，在相近端到端加速比（1.39× vs 1.44×）下，DuoGPT 的准确率高出 9.17%，且模型体积更小。
- 理论分析证明 DuoGPT 的损失改进随激活稀疏度线性增长，与实验结果一致。
- 该框架与量化、阈值激活稀疏法（如 TEAL）兼容，且泛化到其他架构（Mistral, Qwen, OPT）。

## 7. 优点

- **创新性**：首次将激活稀疏性显式融入 OBC 框架，提出不对称残差校正形式，实现双稀疏的无训练校准。
- **高效性**：通过数学推导和向量化实现，使 70B 模型校准仅需 2.3 小时，达到实用级别。
- **兼容性**：可与其他压缩方法（量化、阈值激活稀疏）无缝集成。
- **理论支撑**：提供了损失改进的数学下界，解释性能提升的原因。

## 8. 不足与局限

- **未实现专用 GPU Kernel**：目前仅使用通用 sparse matrix-vector 操作（基于 TEAL 的 Triton kernel），并未编写优化的 spMspV kernel，因此实际加速比仅是下界，尚未充分发挥双稀疏潜力。
- **仅在线性层应用**：注意力层的 KV 缓存稀疏性未包含，未来可结合 KV 缓存剪枝技术。
- **校准数据固定**：统一使用 128 个 C4 样本，未探讨不同校准数据分布的影响。
- **无统计显著性报告**：未给出多次运行的平均值和标准差，虽然固定种子，但可能掩盖随机性影响。
- **仅考虑单批解码**：不适用于大 batch 推理场景（如服务端批量推理），但作者明确说明工作重点在单批解码。

（完）
