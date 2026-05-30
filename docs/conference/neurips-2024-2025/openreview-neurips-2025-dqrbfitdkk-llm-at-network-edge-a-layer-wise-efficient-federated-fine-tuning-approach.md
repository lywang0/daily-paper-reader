---
title: "LLM at Network Edge: A Layer-wise Efficient Federated Fine-tuning Approach"
title_zh: 网络边缘的LLM：一种分层高效联邦微调方法
authors: "Jinglong Shen, Nan Cheng, Wenchao Xu, Haozhao Wang, Yifan Guo, Jiajie Xu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=DqRbfiTdKK"
tags: ["query:edge-llm"]
score: 4.0
evidence: 边缘设备上的分层高效联邦微调
tldr: LEFF针对联邦学习微调LLM时边缘客户端计算能力异构导致拖后腿的问题，提出分层高效微调方法，根据客户端计算容量选择可微调层，并用重要性采样优先选择影响大的层。理论证明收敛速率，实验表明在减少客户端计算量的同时保持模型性能，适合网络边缘设备。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dqrbfitdkk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1455, \"height\": 810, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dqrbfitdkk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 592, \"height\": 323, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dqrbfitdkk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 593, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dqrbfitdkk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 470, \"height\": 271, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dqrbfitdkk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 468, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dqrbfitdkk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 570, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dqrbfitdkk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 472, \"height\": 269, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dqrbfitdkk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 988, \"height\": 649, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dqrbfitdkk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dqrbfitdkk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 516, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dqrbfitdkk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 586, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dqrbfitdkk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 885, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dqrbfitdkk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1048, \"height\": 1004, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dqrbfitdkk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 879, \"height\": 189, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dqrbfitdkk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1451, \"height\": 265, \"label\": \"Table\"}]"
motivation: 联邦微调中客户端异构导致计算负担不均和拖后腿效应。
method: 按客户端计算能力分层选择微调层，并结合重要性采样。
result: 减少客户端计算开销，保持模型性能。
conclusion: 分层选择可有效适应异构边缘环境。
---

## Abstract
Fine-tuning large language models (LLMs) poses significant computational burdens, especially in federated learning (FL) settings. We introduce Layer-wise Efficient Federated Fine-tuning (LEFF), a novel method designed to enhance the efficiency of FL fine-tuning while preserving model performance and minimizing client-side computational overhead. LEFF strategically selects layers for fine-tuning based on client computational capacity, thereby mitigating the straggler effect prevalent in heterogeneous environments. Furthermore, LEFF incorporates an importance-driven layer sampling mechanism, prioritizing layers with greater influence on model performance. Theoretical analysis demonstrates that LEFF achieves a convergence rate of $\mathcal{O}(1/\sqrt{T})$. Extensive experiments on diverse datasets demonstrate that LEFF attains superior computational efficiency and model performance compared to existing federated fine-tuning methods, particularly under heterogeneous conditions.

---

## 论文详细总结（自动生成）

# 论文总结：《LLM at Network Edge: A Layer-wise Efficient Federated Fine-tuning Approach》

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：在联邦学习（FL）环境中微调大语言模型（LLM）面临两大挑战：一是客户端计算资源异构，慢客户端拖累整体进度（“拖后腿”效应）；二是非独立同分布（Non-IID）数据导致现有参数高效微调（PEFT）方法（如LoRA、Adapter）性能显著下降。
- **目标**：设计一种联邦微调框架，既能保留全参数微调的优势（适应异构数据），又能大幅降低客户端计算开销，并适配不同设备的计算能力，缓解拖后腿问题。

## 2. 方法论
### 2.1 核心思想
- **分层选择微调**：每个客户端根据自身计算能力（可微调层数 $L_i$），仅微调模型的一部分连续层（称为“块”），其余层通过知识蒸馏压缩后冻结，从而减少客户端内存和计算需求。
- **重要性驱动的层采样**：在各轮通信开始时，服务器基于参数重要性（用梯度-参数乘积平方近似）计算每个块的重要性分数，经Softmax归一化为采样概率，优先选择对模型性能影响更大的层块进行微调。

### 2.2 关键技术细节
- **重要性计算**：每个参数 $m$ 的重要性 $I_m^{(1)} = (g_m \theta_m)^2$，层重要性为该层所有参数重要性之和，块重要性为连续 $L_i$ 层的重要性之和。
- **模型压缩**：对未选中的层，服务器使用代理数据集进行知识蒸馏，学生模型层数由压缩率 $r$ 决定。蒸馏损失包括隐藏状态的均方误差（MSE）和注意力矩阵的KL散度，避免学习任务特定信息。
- **客户端训练**：仅更新选中的层，其余压缩层冻结，提供上下文。
- **服务器聚合**：按层进行加权平均（权重为各客户端数据量占比），重建全局模型。

## 3. 实验设计
### 3.1 数据集和任务
- **自然语言理解（NLU）**：GLUE基准（含CoLA、SST-2、MRPC、STS-B、QQP、MNLI、QNLI、RTE）。
- **自然语言生成（NLG）**：E2E NLG Challenge（基于结构化意义表示生成文本）。

### 3.2 模型和baseline
- **模型**：GPT-2 Medium（NLG），DeBERTaV3 Base（NLU）。附录中还使用了Llama-3.1-8B在MMLU上测试。
- **对比方法**：FedAvg、FedBitFit、FedLoRA、SLoRA。附录中额外对比了FLoRA和FlexLoRA。

### 3.3 实验设置
- 异构数据：Dirichlet分布（$\alpha \in \{0.05,0.1,0.5,1.0,5.0,10.0,50.0\}$）。
- 客户端数量：8～40（主实验默认）。
- 通信轮数：20，每轮本地训练1个epoch，学习率 $1\times 10^{-5}$，优化器AdamW。

## 4. 资源与算力
- 文中明确说明：所有实验在 **八块 NVIDIA H100 GPU** 上完成。
- **未明确给出训练总时长**，但提及了GPT-2 Medium和DeBERTaV3 Base等中等规模模型，所需资源相对可控。

## 5. 实验数量与充分性
- **主要实验组数**：
  - 主对比实验（图4、表1）：在不同 $\alpha$ 下比较6种方法，覆盖GLUE的8个子任务和E2E的5个指标。
  - 压缩率影响（图5）：设置 $r=0.2,0.5,0.8$。
  - 客户端规模影响（表2、表3）：从8到40个客户端。
  - 采样方法对比（图6、图7）：重要性采样 vs 轮询 vs 随机。
  - 附录实验：代理数据集消融（表6）、标准差稳定性（表7）、Llama-3.1-8B在MMLU上的扩展实验（表4）、训练收敛曲线（图8）。
- **充分性评价**：实验覆盖数据异构、系统异构、压缩率、采样策略、客户端数量等关键维度，且报告了多次运行的均值和标准差（表7），对比方法为当前主流FL微调方法，实验设计较为全面、客观、公平。但仅测试了两个中等规模模型（GPT-2 Medium、DeBERTaV3 Base），附录虽补充了8B模型但baseline较少。

## 6. 主要结论与发现
- LEFF在NLU和NLG任务上的性能 **接近全参数微调（FedAvg）**，显著优于FedBitFit、FedLoRA、SLoRA等PEFT方法，尤其在高度异构数据（低 $\alpha$）下优势明显。
- LEFF大幅度 **降低客户端峰值内存占用**（例如GPT-2 Large降低79% vs FedAvg），同时内存使用低于所有PEFT基线（因为无需加载整个冻结模型）。
- **重要性采样** 优于轮询和随机采样，在困难任务（如CoLA、MRPC）上提升更显著。
- **压缩率越高（r越大）**，性能越好，因为保留更多参数以更好模拟教师模型。
- 客户端数量增加时性能总体下降（数据更分散），但LEFF仍优于其他PEFT方法。
- 理论保证：收敛速率为 $\mathcal{O}(1/\sqrt{T})$，受数据异构、梯度噪声和模型近似误差影响。

## 7. 优点
- **方法创新**：将全参数微调的思想与分层选择性更新结合，同时利用重要性采样优先更新关键层，通过知识蒸馏压缩非选中层，兼顾性能与效率。
- **理论分析完整**：给出了收敛性定理和误差界，揭示了精度与效率之间的权衡。
- **实验全面**：覆盖多种异构程度、客户端规模、压缩率和采样策略，并报告了多次运行的标准差，结果可靠。
- **资源效率高**：显著降低客户端内存和计算开销，使LLM微调在资源受限的边缘设备上成为可能。

## 8. 不足与局限
- **近似误差**：层选择和压缩引入了模型近似误差 $\bar{\Delta}^2$，理论表明这会限制最终精度，实践中需要平衡压缩率与性能。
- **服务器端负担增加**：需计算层重要性、进行知识蒸馏和逐层聚合，服务器计算和通信成本较高；客户端数量大时可能成为瓶颈。
- **通信开销**：每个客户端接收定制的压缩模型（包含未选层的蒸馏版本），可能增加服务器到客户端的传输量（尤其在压缩率较低时）。
- **实验覆盖有限**：仅使用了GPT-2 Medium和DeBERTaV3 Base（及附录中的8B模型），未在更大规模模型（如70B级别）或更多任务（如代码生成、多模态）上验证。
- **连续块假设**：层采样仅选择连续的一段层，可能不如非连续层组合灵活，尽管实验显示基于连续块的抽样已有效。
- **代理数据集依赖**：蒸馏依赖公开代理数据集，虽实验表明鲁棒，但在极不匹配的领域下可能存在风险。

（完）
