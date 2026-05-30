---
title: "AegisGuard: RL-Guided Adapter Tuning for TEE-Based Efficient & Secure On-Device Inference"
title_zh: AegisGuard：基于RL引导的适配器调优实现TEE安全高效的设备上推理
authors: "CHE WANG, Ziqi Zhang, Yinggui Wang, Tiantong Wang, Yurong Hao, Jianbo Gao, Tao Wei, YANG CAO, Zhong Chen, Wei Yang Bryan Lim"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=i99ZhFw6GN"
tags: ["query:edge-llm"]
score: 7.0
evidence: 基于RL引导的适配器调优实现安全高效的设备上LLM推理
tldr: AegisGuard针对设备上LLM推理中模型权重易被白盒窃取的问题，提出RL引导的适配器调优框架，仅将安全敏感的LoRA适配器置于TEE，其余部分卸载到GPU，平衡安全与效率。通过RL敏感性测量筛选关键层，实验证明在防御模型窃取的同时显著降低设备上推理延迟，为边缘LLM部署提供软硬协同方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-i99zhfw6gn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1424, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-i99zhfw6gn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1355, \"height\": 644, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-i99zhfw6gn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 624, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-i99zhfw6gn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 625, \"height\": 616, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-i99zhfw6gn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1148, \"height\": 661, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-i99zhfw6gn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1448, \"height\": 968, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-i99zhfw6gn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1441, \"height\": 414, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-i99zhfw6gn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1454, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-i99zhfw6gn/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1453, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-i99zhfw6gn/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 512, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-i99zhfw6gn/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1452, \"height\": 499, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-i99zhfw6gn/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1450, \"height\": 483, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-i99zhfw6gn/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1440, \"height\": 273, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-i99zhfw6gn/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1443, \"height\": 772, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-i99zhfw6gn/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1453, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-i99zhfw6gn/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1441, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-i99zhfw6gn/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1454, \"height\": 209, \"label\": \"Table\"}]"
motivation: 设备上LM推理暴露模型权重，易受模型窃取攻击，全TEE方案通信延迟高。
method: RL选择性屏蔽敏感适配器，非敏感部分卸载到GPU。
result: 防御模型窃取，降低延迟。
conclusion: 选择性保护可实现安全高效的设备上推理。
---

## Abstract
On-device large models (LMs) reduce cloud dependency but expose proprietary model weights to the end-user, making them vulnerable to white-box model stealing (MS) attacks. A common defense is TEE-Shielded DNN Partition (TSDP), which places all trainable LoRA adapters (fine tuned on private data) inside a trusted execution environment (TEE). However, this design suffers from excessive host-to-TEE communication latency. We propose AegisGuard, a fine tuning and deployment framework that selectively shields the MS sensitive adapters while offloading the rest to the GPU, balancing security and efficiency. AegisGuard integrates two key components: i) RL-based Sensitivity Measurement (RSM), which injects Gaussian noise during training and applies a lightweight reinforcement learning to rank adapters based on their impact on model stealing; and (ii) Shielded-Adapter Compression (SAC), which structurally prunes the selected adapters to reduce both parameter size and intermediate feature maps, further lowering TEE computation and data transfer costs. Extensive experiments demonstrate that AegisGuard achieves black-box level MS resilience (surrogate accuracy around 39%, matching fully shielded baselines), while reducing end-to-end inference latency by 2–3× and cutting TEE memory usage by 4× compared to state-of-the-art TSDP methods.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：设备端部署的大型模型（LM）将专有权重暴露给终端用户，易遭受白盒模型窃取（MS）攻击。现有防御方案TEE-Shielded DNN Partition（TSDP）将所有LoRA适配器置于可信执行环境（TEE）中，但导致严重的宿主与TEE间通信延迟（实验中达总延迟的60%以上）。
- **背景**：TEE（如Intel SGX）提供硬件隔离，但计算能力受限；GPU加速高效但不可信。TSDP方案将模型划分到TEE和GPU，但通信成为新瓶颈。现有TSDP工作主要关注选择关键权重或混淆卸载权重，未解决LM场景下的通信开销问题。
- **目标**：在保持强安全性的同时，显著降低端到端推理延迟，实现安全与效率的平衡。

### 2. 论文提出的方法论：核心思想、关键技术细节

#### 核心思想
并非所有LoRA适配器对隐私泄露贡献相同，只有部分适配器对模型窃取攻击敏感。因此选择性屏蔽敏感适配器于TEE，其余卸载到GPU，从而减少通信和数据传输。

#### 关键技术细节

**① RL-based Sensitivity Measurement（RSM）**
- 将敏感度测量建模为上下文多臂赌博机问题，通过强化学习更新各层敏感度分数。
- **敏感层选择**：基于均匀分布结合敏感度分数采样候选层，每轮选择N_t个高分层次作为可训练层。
- **层敏感度估计**：对每层LoRA矩阵A注入高斯噪声，计算噪声前后损失变化ΔL，作为敏感度信号。
- **奖励计算**：R_t = sgn(ΔL) * [exp(ΔL) - mean(exp(ΔL))]，正ΔL表示更敏感，给予奖励。
- **分数更新**：仅更新当前可训练层的分数，公式：s_i = s_i + r_t * μ * sigmoid(s_i) * (1 - sigmoid(s_i))。

**② Shielded Adapter Compression（SAC）**
- 对RSM选中的敏感适配器进行结构性剪枝，减少参数数量和中间特征图尺寸。
- 重要性估计：基于一阶泰勒展开近似LoRA参数重要性。
- 动态剪枝率：ratio_i(t) = (R_total - R_t) / ((T - t + δ) * sigmoid(s_i)) * (1 - α + α * t/T)，随训练逐步增加。
- 以注意力头为单位剪枝，保留高重要性头，屏蔽低重要性头。

**整体流程**：微调阶段定期执行RSM和SAC，动态调整敏感层选择和剪枝比例。推理阶段仅将高敏感适配器部署在TEE，其余在GPU上运行。

### 3. 实验设计

#### 使用数据集/场景
- **NLP任务**：CommonSenseQA微调，评估用ARC-Challenge、ARC-Easy、HellaSwag、OBQA、PIQA、WinoGrande。
- **视觉任务**：CIFAR-10、CIFAR-100、UTKFace、MNIST、GTSRB、SUN397。

#### benchmark
- **模型**：OPT-2.7B、LLaMA-7B（生成模型），ViT-Base、ViT-Large-14（视觉Transformer）。
- **对比方法**：
  - 上界（最高安全）：Shield-LoRA（所有适配器在TEE）。
  - 下界（最高效率）：No-Shield（全部在GPU）。
  - SOTA TSDP方案：TEESlice（SP 2024）、Phantom（USENIX Security 2025）。
- **评估指标**：推理延迟（GPU/TEE/数据传输/端到端）、TEE内存占用、攻击后替代模型准确率、下游任务准确率。

### 4. 资源与算力

- **微调**：在单块NVIDIA A6000 GPU上运行，PyTorch 2.5.1实现。
- **推理评估**：PC搭载Intel SGX enclave（SDK 2.6, GCC 7.5）和NVIDIA RTX4090D 24GB GPU。
- **训练时长**：未明确给出具体训练时间，但提到NLP任务训练2-5个epoch，视觉任务6-20个epoch，批量大小8/32，梯度累积步数8/1。

### 5. 实验数量与充分性

- **多模型多任务**：覆盖4种模型（OPT, LLaMA, ViT-Base, ViT-Large），NLP和视觉共12个数据集。
- **消融实验**：分别评估RSM和SAC模块的单独贡献（如Shield-LoRA+RL sens, Shield-LoRA+SAC(30%)）。
- **对比完备**：与4种基线（Shield-LoRA, No-Shield, TEESlice, Phantom）在效率、安全、准确率三方面对比。
- **统计显著性**：提供了标准误差（表6）。
- **公平性**：攻击设置与基线相同（查询率1%数据集），超参数搜索范围明确。
- **客观性**：结果清晰展示AegisGuard在效率和安全间取得最佳平衡，随机选择层与AegisGuard对比表明后者更优。

**充分性评价**：实验设计较为全面，覆盖主流模型和任务，消融实验验证各模块作用，统计指标完整，对比方法均为近两年顶级会议工作，足以支撑结论。

### 6. 论文的主要结论与发现

- **效率**：AegisGuard在端到端延迟上比Shield-LoRA加速2-3倍（LLaMA-7B达3.33×，ViT-Base达2.16×），优于TEESlice和Phantom约1.6倍。
- **安全**：防御模型窃取攻击后，替代模型准确率约39.1%，接近黑盒基线（38.9%），与完全屏蔽的Shield-LoRA相当。
- **准确率**：下游任务准确率仅降低0.12%，可忽略不计。
- **内存**：TEE内参数减少约4×（LLaMA-7B: 54.96MB vs 基线224.4MB）。
- **层敏感度分布**：不同模型和数据集下敏感层分布不同，需动态选择而非固定策略。

### 7. 优点

- **创新性**：首次将强化学习用于LoRA适配器的敏感度测量与选择性屏蔽，解决TSDP通信瓶颈。
- **方法设计精巧**：RSM利用噪声扰动与RL更新，轻量高效；SAC动态剪枝适配器，适配TEE资源受限特性。
- **实验充分**：覆盖多种模型规模、任务类型、安全与效率指标，与多个SOTA对比，消融验证。
- **实用性**：在真实硬件（SGX+RTX4090D）上评估，结果具有说服力。

### 8. 不足与局限

- **威胁模型局限**：仅针对参数提取和功能模仿的模型窃取攻击，未考虑输入重建、训练数据反演等正交威胁，需集成差分隐私等补充技术。
- **基线适配性**：Phantom和TEESlice原为卷积神经网络设计，虽经适配但可能未达最优性能，存在不公平比较风险。
- **可扩展性**：实验仅涉及7B参数模型，更大规模模型（如130B+）下的通信开销与TEE内存限制未验证。
- **硬件依赖**：依赖Intel SGX等TEE，不同TEE实现（如ARM TrustZone）性能差异未探讨。
- **超参数敏感性**：RSM中噪声方差、RL学习率等需调优，未提供自动调参策略。
- **训练开销**：RL步骤每次需额外前向传播计算噪声损失，微调总时间可能增加，但论文未量化训练开销。

（完）
