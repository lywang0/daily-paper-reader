---
title: "La RoSA: Enhancing LLM Efficiency via Layerwise Rotated Sparse Activation"
title_zh: La RoSA：通过逐层旋转稀疏激活提升LLM效率
authors: "Kai Liu, Bowen Xu, Shaoyu Wu, Xin Chen, Hao Zhou, Yongliang Tao, lulu hu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=1b6NNpFYI4"
tags: ["query:edge-llm"]
score: 7.0
evidence: 无需训练的激活稀疏化方法降低LLM推理成本
tldr: 现有激活稀疏化方法要么需要耗时的恢复训练，要么导致不稳定的加速。La RoSA通过逐层正交旋转将激活变换到更适合稀疏化的形式，无需额外训练即可实现稳定稀疏。实验显示在多种LLM上有效减少计算量并加速推理，且保持模型性能。该方法易部署，实用性强。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-1b6nnpfyi4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 907, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1b6nnpfyi4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1699, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1b6nnpfyi4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1731, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1b6nnpfyi4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 888, \"height\": 996, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-1b6nnpfyi4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 935, \"height\": 709, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1779, \"height\": 544, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 854, \"height\": 612, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1789, \"height\": 564, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 874, \"height\": 646, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 886, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 872, \"height\": 652, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 877, \"height\": 438, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 871, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 869, \"height\": 701, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1063, \"height\": 420, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1099, \"height\": 465, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1661, \"height\": 523, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1658, \"height\": 521, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1660, \"height\": 522, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1661, \"height\": 523, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1659, \"height\": 518, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1658, \"height\": 523, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1660, \"height\": 525, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-1b6nnpfyi4/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1170, \"height\": 563, \"label\": \"Table\"}]"
motivation: 激活稀疏化可以减少LLM推理计算，但现有方法有训练成本高或加速不稳定的问题。
method: 利用逐层正交旋转使激活更适合稀疏化，无需训练或幅值剪枝。
result: 在多个LLM上实现稳定加速和内存节省，且不损失精度。
conclusion: La RoSA提供了一种可即插即用的激活稀疏化方案。
---

## Abstract
Activation sparsity can reduce the computational overhead and memory transfers during the forward pass of Large Language Model (LLM) inference. Existing methods face limitations, either demanding time-consuming recovery training that hinders real-world adoption, or relying on empirical magnitude-based pruning, which causes fluctuating sparsity and unstable inference speed-up. This paper introduces LaRoSA (**La**yerwise **Ro**tated **S**parse **A**ctivation), a novel method for activation sparsification designed to improve LLM efficiency without requiring additional training or magnitude-based pruning. We leverage layerwise orthogonal rotations to transform input activations into rotated forms that are more suitable for sparsification. By employing a Top-K selection approach within the rotated activations, we achieve consistent model-level sparsity and reliable wall-clock time speed-up. LaRoSA is effective across various sizes and types of LLMs, demonstrating minimal performance degradation and robust inference acceleration. Specifically, for LLaMA2-7B at 40\% sparsity, LaRoSA achieves a mere 0.17 perplexity gap with a consistent 1.30× wall-clock time speed-up, and reduces the accuracy gap in zero-shot tasks compared to the dense model to just 0.54\%, while surpassing TEAL by 1.77\% and CATS by 17.14\%.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：激活稀疏化（Activation Sparsity）是减少大语言模型（LLM）推理过程中计算开销和内存传输的有效途径，但现有方法存在两个主要局限：
  - **需要耗时恢复训练**（如ReLU替换后继续预训练），不利于实际部署。
  - **基于经验幅值剪枝的方法**（如CATS、TEAL）依赖离线校准阈值，导致实际稀疏度波动、不一致，进而引起推理加速不稳定。
- **动机**：能否在不需额外训练、不依赖经验阈值的前提下，快速、有效且一致地利用激活稀疏性提升LLM效率？
- **研究含义**：提出一种训练无需、基于旋转变换与Top-K的激活稀疏化方法，旨在实现稳定的模型级稀疏度和可靠的墙钟时间加速。

## 2. 提出的方法论

### 核心思想
- **正交旋转+Top-K稀疏化**：利用层级的正交旋转矩阵将输入激活变换到更适合稀疏化的形式，然后在旋转后的激活上使用Top-K选择（保留绝对值最大的k个元素）实现一致稀疏度。旋转矩阵可被吸收进对应权重矩阵，消除在线计算开销。

### 关键技术细节
1. **层式正交旋转（Layerwise Orthogonal Rotation）**  
   - 对每层输入激活（注意力和MLP块的输入`h1`、`h3`），使用PCA求协方差矩阵的特征向量构成正交矩阵`Q_l`。  
   - 旋转后，激活`x`变为`xQ_l`，再应用Top-K稀疏化。  
   - 旋转的逆变换通过`Q_l^T`实现，且`Q_l^T`可与下游权重合并（如`W·Q_l`），不增加推理计算。  
   - 为支持不同层使用不同旋转，引入残差适配器`Q_l^T Q_{l+1}`连接相邻层，克服残差连接限制。

2. **Top-K稀疏化函数**  
   - 定义：保留旋转激活中绝对值最大的k个元素，其余置零。  
   - k由目标稀疏度`p`和超参数`α`（控制同一块内不同输入激活的稀疏系数）决定：`k = α·(1-p)·D_in`。  
   - 通过网格搜索对每个模型调优α值，确保模型级稀疏度一致。

3. **硬件高效定制核**  
   - 基于Triton实现GEMV核，支持列优先权重存储、融合Top-K与矩阵向量乘法、选择性加载非零激活对应权重列。

### 算法流程（文字说明）
1. **离线阶段**：  
   - 选取校准数据集（如WikiText2），前向传播计算每一层输入激活的协方差矩阵，通过特征分解得到正交旋转矩阵`Q_l`，并提前计算吸收后的权重`W·Q_l`。  
   - 网格搜索确定最优α系数。
2. **推理阶段**：  
   - 对每个输入token，先计算旋转激活`xQ_l`，应用Top-K得到稀疏激活`S_k(xQ_l)`。  
   - 执行矩阵乘法`S_k(xQ_l)·(W·Q_l)^T`，稀疏激活使得对应权重列无需加载/计算，实现加速。

## 3. 实验设计

### 使用的数据集与场景
- **校准数据集**：WikiText2训练集（16条序列，长度2048 token），用于计算旋转矩阵和阈值分布。  
- **基准测试**：  
  - 语言生成：WikiText2测试集上的困惑度（PPL）。  
  - 零样本/少样本任务：ARC-Easy/Challenge、PIQA、BoolQ、HellaSwag、OpenBookQA、WinoGrande（7个零样本任务平均准确率）以及5-shot MMLU。  
  - 复杂推理：MATH500、GPQA-Diamond、AIME’24（在DeepSeek-R1蒸馏模型上测试）。
- **推理加速**：不同输出长度（128~2048 token）下的墙钟加速比。

### 对比方法
- **CATS**（2024）：基于经验分布直方图获取阈值，仅对MLP输出剪枝。  
- **TEAL**（2024a）：扩展至注意力和MLP所有输入激活，仍依赖离线阈值。  
- **Baseline（Dense）**：全密集模型。  
- **消融实验**：对比不同稀疏化函数（TEAL、TopK、TopK+GS、LaRoSA）、不同旋转类型（模型级、块级、层级）、不同校准数据集、与量化（RTN/GPTQ/AWQ/OmniQuant）的兼容性。

### 模型规模与类型
- LLaMA2-7B/70B、LLaMA3-8B/70B、Mistral-7B、Qwen2.5-7B/72B，涵盖7B到72B参数规模。

## 4. 资源与算力

- **GPU型号与数量**：8x80G NVIDIA A100 GPU，用于计算70B模型的旋转矩阵。  
- **耗时**：LLaMA3-70B的旋转矩阵计算约**12分钟**完成（仅需一次）。  
- **推理测试**：单卡A100（7B模型），70B/72B模型使用张量并行（TP2）。另在H20 GPU上测试了速度。  
- 文中未明确给出总训练/测试所用GPU时长，但方法本身训练免费，仅需少量校准计算。

## 5. 实验数量与充分性

- **实验数量丰富**：涵盖7个不同模型×4~5种稀疏度（25%/40%/50%/60%），每个配置报告PPL和零样本准确率。  
- **全面消融**：  
  - 稀疏化函数（Table 5）  
  - 旋转类型（模型级/块级/层级，Table 6）  
  - 校准数据集影响（Table 7, Table 8）  
  - 与量化方法兼容性（Table 9）  
  - 初始token影响分析（Figure 3b）  
  - 复杂推理任务测试（Table 4）  
- **公平性**：与CATS、TEAL在同一模型级稀疏度下比较，全文统一实现了完整序列长度的稀疏化（TEAL原文仅稀疏化99% token，本文重新实现了全稀疏化以公平对比）。  
- **客观性**：给出了多次重复实验的标准差（如Table 5中TEAL的波动），并展示了稀疏度不一致的统计数据（Figure 3c）。  
- **结论**：实验充分、设计合理，支持所提方法在多种设置下的优越性。

## 6. 主要结论与发现

1. **LaRoSA优于SOTA**：在多个模型上均超越CATS和TEAL。例如LLaMA2-7B在40%稀疏度下，PPL仅比密集模型高0.17，零样本准确率下降0.54%，而TEAL下降1.77%，CATS下降17.14%。  
2. **一致加速**：Top-K确保了严格的模型级稀疏度，推理加速波动小（Figure 4），而TEAL的加速因稀疏度不一致而不稳定。  
3. **训练免费且即插即用**：无需模型微调，仅需少量校准数据计算旋转矩阵，且旋转矩阵可被吸收进权重。  
4. **对旋转矩阵来源鲁棒**：不同校准数据集（WikiText2 vs Alpaca）对性能影响极小；协方差矩阵在不同数据集间余弦相似度接近1（Table 8）。  
5. **与量化兼容**：与GPTQ、AWQ等4bit量化结合时，性能退化基本正交（Table 9），有望通过联合优化进一步提升效率。  
6. **可推广到推理模型**：在DeepSeek-R1蒸馏模型上，25%稀疏度下复杂推理任务（MATH/GPQA）准确率下降小于3%。

## 7. 优点

- **无需训练**：不需要昂贵的恢复训练或微调，仅需轻量级校准。  
- **稳定一致稀疏度**：Top-K机制消除了阈值波动，保证了模型级稀疏度的确定性，从而推理加速可预测。  
- **计算开销可忽略**：旋转矩阵吸收进权重后，仅增加极少量残差适配器计算（TFLOPS增加约6-7%，见表19），但稀疏化收益远超此开销。  
- **理论支撑**：提供误差界定理（Theorem A.1），证明旋转后激活近似高斯分布，使Top-K误差可控，且经验误差低于TEAL。  
- **跨模型、跨任务泛化性强**：在多种架构、参数规模、稀疏度、下游任务上表现稳定。  
- **硬件友好**：定制Triton核实现稀疏矩阵乘法加速，实测LLaMA3-70B在75%稀疏度下达到1.90×加速。

## 8. 不足与局限

- **依赖校准数据**：尽管对数据集不敏感，但仍需少量校准数据（16条序列）计算旋转矩阵，无法完全零样本。  
- **额外计算开销**：残差适配器引入约6-7%的额外TFLOPS，在低稀疏度（如25%）时可能抵消部分收益。  
- **仅适用于Transformer架构**：方法基于计算不变性定理（正交旋转不影响RMSNorm），对非Transformer模型（如SSM）可能不适用。  
- **GQA/MLP结构限制**：部分激活（Attention的K/V、MLP的中间激活）因GQA和逐元素乘操作无法应用旋转，限制了稀疏化潜力。  
- **对初始token无特殊处理**：虽然LaRoSA避免了TEAL在初始token上失效的问题，但未明确分析attention sink等导致的潜在退化。  
- **速度测试条件有限**：加速比仅在单batch单GPU上测试，实际部署中多batch、服务场景下的效果未验证。  
- **理论分析假设较强**：定理A.1假设激活与权重独立同高斯分布，实际可能不完全满足。

（完）
