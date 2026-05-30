---
title: "Medusa: Simple LLM Inference Acceleration Framework with Multiple Decoding Heads"
title_zh: Medusa：带多个解码头的简单LLM推理加速框架
authors: "Tianle Cai, Yuhong Li, Zhengyang Geng, Hongwu Peng, Jason D. Lee, Deming Chen, Tri Dao"
date: 2024-05-02
pdf: "https://openreview.net/pdf?id=PEpbUobfJv"
tags: ["query:edge-llm"]
score: 6.0
evidence: 多个解码头并行生成token以加速推理
tldr: Medusa通过添加额外的解码头来并行预测多个后续token，并利用树状注意力机制构建多个候选续写，从而在不依赖单独草稿模型的情况下加速LLM推理。该方法简单易用，显著降低了推理延迟，是通用推理加速的有效方案。
source: ICML-2024-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 812, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 810, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1618, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1607, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 814, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1024, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1727, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 802, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1251, \"height\": 779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1253, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1250, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1252, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1253, \"height\": 778, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1252, \"height\": 746, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1252, \"height\": 785, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1251, \"height\": 745, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1252, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1255, \"height\": 756, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1254, \"height\": 747, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1252, \"height\": 745, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1210, \"height\": 743, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 823, \"height\": 783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2024-pepbuobfjv/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 719, \"height\": 774, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 827, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 819, \"height\": 149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 787, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1403, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1566, \"height\": 546, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1679, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1663, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2024-pepbuobfjv/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1707, \"height\": 307, \"label\": \"Table\"}]"
motivation: 自回归解码因顺序计算和全模型参数移动成为瓶颈。
method: 在LLM上添加额外解码头并行预测多个token，使用树注意力筛选候选。
result: Medusa在多个模型上实现了显著的推理加速，且不损失质量。
conclusion: Medusa提供了一种无需草稿模型的简单、高效推理加速方法。
---

## Abstract
Large Language Models (LLMs) employ auto-regressive decoding that requires sequential computation, with each step reliant on the previous one's output. This creates a bottleneck as each step necessitates moving the full model parameters from High-Bandwidth Memory (HBM) to the accelerator's cache. While methods such as speculative decoding have been suggested to address this issue, their implementation is impeded by the challenges associated with acquiring and maintaining a separate draft model. In this paper, we present Medusa, an efficient method that augments LLM inference by adding extra decoding heads to predict multiple subsequent tokens in parallel. Using a tree-based attention mechanism, Medusa constructs multiple candidate continuations and verifies them simultaneously in each decoding step. By leveraging parallel processing, Medusa reduces the number of decoding steps required. We present two levels of fine-tuning procedures for Medusa to meet the needs of different use cases: Medusa-1: Medusa is directly fine-tuned on top of a frozen backbone LLM, enabling lossless inference acceleration. Medusa-2: Medusa is fine-tuned together with the backbone LLM, enabling better prediction accuracy of Medusa heads and higher speedup but needing a special training recipe that preserves the model's capabilities. Moreover, we propose several extensions that improve or expand the utility of Medusa, including a self-distillation to handle situations where no training data is available and a typical acceptance scheme to boost the acceptance rate while maintaining generation quality. We evaluate Medusa on models of various sizes and training procedures. Our experiments demonstrate that Medusa-1 can achieve over 2.2$\times$ speedup without compromising generation quality, while Medusa-2 further improves the speedup to 2.3-2.8$\times$.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）采用自回归解码，每一步都需要将整个模型参数从高带宽内存（HBM）加载到加速器缓存，生成一个token，导致推理延迟严重受限于内存带宽。现有加速方法（如推测解码）依赖单独的草稿模型，但获取和维护草稿模型困难、存在分布偏移、多模型集成复杂。
- **研究动机**：设计一种无需草稿模型、易于集成、参数高效的推理加速方法，在不降低生成质量的前提下显著减少解码步数。
- **整体含义**：提出Medusa框架，通过添加多个解码头并行预测后续token，并利用树注意力同时验证多个候选，实现2.2–2.8倍的速度提升，同时保持输出质量。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：在LLM的最后隐层之上添加K个额外解码头（每个头是一个带残差连接的前馈网络），每个头预测（t+k+1）位置的token分布；利用这些头的top预测构造多个候选序列，并使用树注意力机制一次性验证所有候选，从而在每一步解码中接受一个长度≥1的连续序列。
- **关键技术细节**：
  - **Medusa Heads**：定义第k个头输出 \(p_t^{(k)} = \text{softmax}\left(W_2^{(k)} \cdot \left(\text{SiLU}(W_1^{(k)} \cdot h_t) + h_t\right)\right)\)。初始化时 \(W_2^{(k)}\) 复制原LM head，\(W_1^{(k)}\) 设为零，保证初始预测与原始模型一致。
  - **Tree Attention**：将各头的top预测通过笛卡尔积构造树结构候选，修改注意力掩码使每个token只能看到其前驱token（保持因果性），从而一次性并行处理所有候选。
  - **训练策略**：
    - **Medusa-1**：冻结骨干模型，仅训练Medusa heads，损失为各头交叉熵的加权和（权重 \(\lambda_k = 0.8^k\)），可配合量化（如4-bit）在单GPU上训练。
    - **Medusa-2**：联合训练骨干和heads，加入骨干的交叉熵损失 \(L_{LM}\)，使用差异化学习率、heads预热（先训练heads再联合训练），并采用LoRA/Qlora进行参数高效微调。
  - **典型接受方案（Typical Acceptance）**：替代推测解码中的拒绝采样，基于原始模型概率 \(p_{\text{original}}(x_{n+k}|\dots)\) 与熵阈值 \( \min(\epsilon, \delta e^{-H})\) 判断是否接受候选token，在保证质量前提下获得更高加速比。
  - **自蒸馏**：当训练数据不可得时，使用原始模型本身生成响应（seed prompt + 自生成数据）构建训练集；对Medusa-2，用KL散度蒸馏原始模型分布，并配合LoRA避免额外显存开销。
  - **优化树结构**：基于校准集计算各头top预测的准确率，贪心添加节点构建稀疏树，最大化期望接受长度。

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - 训练：ShareGPT（Vicuna-7B/13B），UltraChat（Zephyr-7B/33B自蒸馏），以及自生成数据集。
  - 评估：MT-Bench（多轮对话基准），AlpacaEval（附加实验）。
- **基准（Benchmark）**：MT-Bench的8个类别（Humanities, Reasoning, Roleplay, Writing, Stem, Math, Coding, Extraction），使用GPT-4作为裁判评分（0-10）。
- **对比方法**：
  - 基线：默认Huggingface实现（无加速）。
  - 推测解码（Speculative Decoding）：使用不同大小的草稿模型（Llama-68M/160M/1B, Tiny-Vicuna-1B）。
  - Medusa自身变体：Medusa-1 vs Medusa-2，不同树配置、不同接受阈值。

### 4. 资源与算力

- **Medusa-1**：Vicuna-7B模型在单张NVIDIA A100 PCIE GPU上训练5小时（60k ShareGPT样本，batch size 64，双精度+4-bit量化）。
- **Medusa-2**：使用8-bit AdamW优化器、LoRA（rank=32, alpha=16），骨干学习率5e-4、Medusa heads学习率2e-3（4倍差异），训练2个epoch。具体GPU数量未明确，但提到可使用单卡（通过量化）。
- **推测解码对比**：采用开源草稿模型，报告中未给出训练时间，但指出需要额外275 A100 GPU小时（如SpecInfer）。
- 总体资源需求较低，且支持单卡部署。

### 5. 实验数量与充分性

- **实验数量**：主要包含3组实验：
  1. Medusa-1 vs Medusa-2在Vicuna-7B/13B（图3、表2）。
  2. 自蒸馏场景：Vicuna-33B、Zephyr-7B（表1、图8）。
  3. 消融实验：树注意力候选数影响（图4）、典型接受阈值（图5）、两阶段微调效果（表3）、稀疏树优化（图6）、不同batch/seq长度模拟（附录G）。
- **充分性评估**：
  - 覆盖了不同模型大小（7B,13B,33B）、不同训练范式（公开SFT、私有数据、RLHF）。
  - 对比了推测解码，并公开了其最佳结果。
  - 消融实验系统探究了各组件贡献（表3：无树注意力≈1.5x，加树≈1.9x，优化树≈2.2x，Medusa-2可达2.8x）。
  - 使用MT-Bench和GPT-4评分，有客观量化指标。
- **客观公平性**：推测解码的选择可能存在偏差（仅使用开源小模型），但作者给出了具体设置并展示了其低于Medusa的最高速度。基线为默认实现，对比公平。

### 6. 论文的主要结论与发现

- Medusa-1可在不降低生成质量前提下实现≥2.2倍加速，Medusa-2则进一步达到2.3–2.8倍。
- 典型接受方案在保持与原始模型相似质量的同时，比拒绝采样获得更高加速比（图5）。
- 自蒸馏有效解决了训练数据不可得的问题，但联合训练时需用KL散度蒸馏以保持质量。
- 树注意力候选节点数存在最优值（约64节点），超过后因计算开销导致速度下降。
- 方法在编码、抽取等任务上加速效果最好（3.29–3.62倍），在数学、推理等任务上稍低。
- 相比于推测解码，Medusa更简单、集成成本更低、加速更显著。

### 7. 优点：方法或实验设计上的亮点

- **方法优点**：
  - 无需额外草稿模型，直接复用骨干模型特征，训练参数极少（仅若干线性层）。
  - 支持量化训练（Qlora），可在单消费级GPU上实现。
  - 树注意力设计巧妙，一次性处理多候选而无需扩展batch维度。
  - 典型接受方案理论清晰，实际效果好，且能通过\(\epsilon\)调节速度-质量权衡。
  - 自蒸馏方案自动生成匹配分布的训练数据，且蒸馏时无需额外模型（借助LoRA开关）。
- **实验设计亮点**：
  - 多维度消融（树结构、接受策略、训练策略）系统验证各组件贡献。
  - 模拟了不同batch size和序列长度下的吞吐，揭示边际收益递减规律（附录G）。
  - 公开了优化稀疏树的可视化（图6）和贪心构造算法（附录C）。

### 8. 不足与局限

- **实验覆盖**：主要针对batch size=1的本地部署场景，未充分验证batch≥2时的加速效果（虽然在附录G有模拟，但缺乏实际系统实现对比）。
- **偏差风险**：
  - 典型接受方案等价于一个非标准采样，可能改变生成分布（尽管质量评分显示持平）；对于严格要求分布一致的应用（如某些概率计算），仍需使用拒绝采样。
  - 自蒸馏生成的训练数据可能无法完全覆盖原始模型能力，导致Medusa-2在某些领域加速/质量低于Medusa-1（如Vicuna-33B加速比2.35x低于7B的2.83x）。
- **应用限制**：
  - 树注意力节点增多时，计算开销增长快于加速收益，需针对具体模型和硬件调优候选数。
  - 方法假设骨干模型具有较好的representation，对极小型模型（<1B）效果可能有限（未测试）。
- **其他**：未讨论与KV cache压缩、FlashAttention等工程优化的集成效果；未在多GPU分布式推理环境下测试（虽然声称易集成）。

（完）
