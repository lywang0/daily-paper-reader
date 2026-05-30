---
title: On-Device Collaborative Language Modeling via a Mixture of Generalists and Specialists
title_zh: 设备端协作语言建模：通用与专用专家的混合
authors: "Dongyang Fan, Bettina Messmer, Nikita Doikov, Martin Jaggi"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Eog0kXX7hW"
tags: ["query:edge-llm"]
score: 9.0
evidence: 设备端协作LLM推理，应对计算资源异构性
tldr: 设备端LLM面临计算资源和数据分布的异构挑战。CoMiGS提出包含通用专家和专用专家的混合专家模型，通过双层优化联合训练路由器，实现设备间高效协作。实验表明在异构场景下优于现有联邦学习方法，同时保护隐私。该方法直接面向边缘设备上的LLM推理优化和软硬协同。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 786, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 866, \"height\": 323, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 869, \"height\": 187, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1303, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 842, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 850, \"height\": 197, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 852, \"height\": 198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 851, \"height\": 204, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1728, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1572, \"height\": 975, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1728, \"height\": 719, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1741, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1740, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1742, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1743, \"height\": 1362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1743, \"height\": 1362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1743, \"height\": 1362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1744, \"height\": 1366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1744, \"height\": 1367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-eog0kxx7hw/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1744, \"height\": 1367, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-eog0kxx7hw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 852, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-eog0kxx7hw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 849, \"height\": 472, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-eog0kxx7hw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 680, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-eog0kxx7hw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1413, \"height\": 682, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-eog0kxx7hw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1416, \"height\": 1036, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-eog0kxx7hw/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1131, \"height\": 316, \"label\": \"Table\"}]"
motivation: 设备端LLM训练面临计算和数据异构性，现有联邦学习难以应对。
method: 提出混合通用和专用专家的MoE架构，通过双层优化训练路由器。
result: 在异构设备场景下，模型性能和数据效率均显著提升。
conclusion: CoMiGS实现了适应异构环境的设备端协作LLM学习。
---

## Abstract
On-device LLMs have gained increasing attention for their ability to enhance privacy and provide a personalized user experience. To facilitate private learning with scarce data, Federated Learning has become a standard approach. However, it faces challenges such as computational resource heterogeneity and data heterogeneity among end users. We propose CoMiGS ($\textbf{Co}$llaborative learning  with a $\textbf{Mi}$xture of $\textbf{G}$eneralists and $\textbf{S}$pecialists), the first approach to address both challenges. A key innovation of our method is the bi-level optimization formulation of the Mixture-of-Experts learning objective, where the router is optimized using a separate validation set to ensure alignment with the target distribution. We solve our objective with alternating minimization, for which we provide a theoretical analysis. Our method shares generalist experts across users while localizing a varying number of specialist experts, thereby adapting to users’ computational resources and preserving privacy. Through extensive experiments, we show CoMiGS effectively balances general and personalized knowledge for each token generation. We demonstrate that CoMiGS remains robust against overfitting—due to the generalists' regularizing effect—while adapting to local data through specialist expertise. We open source our codebase for collaborative LLMs.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：设备端大语言模型（LLM）因低延迟、隐私保护和个性化体验而受到关注。但是，联邦学习（Federated Learning）在设备端微调时面临两大挑战：**计算资源异构性**（不同设备能力不同，如支持的 LoRA 模块数量或秩不同）和**数据异构性**（不同用户的数据分布差异大，如语言偏好、主题偏好）。现有方法只能处理其中一种异构性，没有统一解决方案。
- **整体含义**：本文提出 CoMiGS（Collaborative learning with a Mixture of Generalists and Specialists），首次同时处理两种异构性，实现设备端个性化协作语言模型微调。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程（文字说明）

- **核心思想**：采用 Mixture-of-Experts（MoE）架构，将专家分为**通用专家（Generalists）**和**专用专家（Specialists）**。通用专家在所有用户间共享并聚合（服务器端），专用专家保留在本地（用户特定）。路由器根据输入 token 动态分配权重，将 token 路由到合适的专家组合。
- **关键技术细节**：
  1. **双层优化公式（Bi-level Optimization）**：上层优化路由器参数 $\Phi$，使用小规模验证集损失，使其对齐目标分布；下层优化专家参数 $\Theta$（包括通用和专用），使用训练集损失。这避免了路由器与专家同时更新可能导致的过拟合和分布偏移问题。
  2. **交替最小化算法（Alternating Minimization）**：交替更新 $\Theta$ 和 $\Phi$。更新专家参数时，每个用户先本地优化，然后服务器聚合通用专家（取平均），专用专家保留。如 Algorithm 1 所示。
  3. **理论分析**：在收缩假设下证明了线性收敛速率；在线性专家情况下给出全局收敛证明（Theorem 3.1, 3.2）。
- **算法流程简述**：
  1. 服务器聚合通用专家参数 $\theta_G$。
  2. 每个用户下载通用参数、本地专用参数和路由器，在训练集上梯度更新（含负载均衡损失）。
  3. 每隔 $\tau$ 轮，使用验证集梯度更新路由器参数。
  4. 用户上传更新后的通用专家参数到服务器。

## 3. 实验设计：数据集 / 场景、基准方法、对比方法

- **数据集与场景**：
  - **Multilingual Wikipedia**：四种语言（德语、法语、意大利语、荷兰语），用户各一种语言（数据异构）。
  - **SlimPajama**：四个类别（StackExchange、Github Codes、ArXiv、Book）。
  - **AG News**：四个新闻类别（World、Sports、Business、Sci/Tech）。
  - **Common Corpus**：三个类别（YouTube-Commons、Public Domain Books、EU Tenders）外加 Harvard US Patent。
  - **场景**：包括**同分布任务**（验证/测试集与训练分布相同）和**分布外任务**（验证/测试集为所有类别的均匀混合）。
- **基准与对比方法**：
  - **上下界**：Pretrained（预训练权重）、Centralized（集中训练，不可行基线）。
  - **基线**：Local（仅本地训练）、FedAvg、PCL（客户端级协作图）、pFedMoE（同时更新路由和专家）、FDLoRA（全局/局部双 LoRA + 学习融合权重）。
  - **消融**：CoMiGS-2S（两个专用专家）、CoMiGS-2G（两个通用专家）、CoMiGS-1G1S（一个通用一个专用，即完整方法）。此外还有 FFA-LoRA、FedSA-LoRA 等扩展对比。
- **异构模型实验**：与 HetLoRA、FlexLoRA 对比，通过调整专家数量或 LoRA 秩匹配参数量。

## 4. 资源与算力

- 论文提及：**所有实验（除集中式基线外）在单张 A100-SXM4-40GB GPU 上运行**；集中式基线在单张 A100-SXM4-80GB GPU 上运行。
- 未明确给出训练总时长、总 GPU 小时数。仅描述迭代次数和通信轮数（如 GPT-2 实验 20 或 50 轮，每轮 10 次 local iteration）。因此算力消耗属于中等规模，但未提供精确统计。

## 5. 实验数量与充分性

- **实验数量**：涵盖 4 个数据集，至少 3 种场景（同分布、分布外、异构），每个条件运行 3 个随机种子取平均和标准差。消融实验包括：不同专家配置、不同路由更新频率、负载平衡对性能的影响。异构模型实验匹配激活/全部参数量。此外还有用户数据分析（数据量大小与模型规模的关系）。
- **充分性评价**：**实验较为充分**。对比了多个 SOTA 基线（FedAvg、PCL、pFedMoE、FDLoRA、HetLoRA、FlexLoRA），覆盖了同质和异质模型设置，进行了消融研究和超参数调优（图 8 展示路由更新周期和步数的选择）。但未在更大规模模型（如 7B+）上进行验证，且仅使用英文和多语言数据，未覆盖其他语言/任务类型（如问答、摘要）。

## 6. 论文的主要结论与发现

- CoMiGS 在**同分布任务**上接近甚至超过最优基准（如中央式或局部最佳），在**分布外任务**上表现更稳定且优于大多数基线。
- token 级路由比客户端级协作更灵活，路由器能有效区分通用与专用知识（第一层倾向于路由功能词给通用专家，最后一层路由领域特定词给专用专家）。
- 同时拥有通用专家和专用专家是必要的：仅使用通用（CoMiGS-2G）或仅使用专用（CoMiGS-2S）都不能在所有场景下稳定最优，而 CoMiGS-1G1S 能自动接近最优。
- **计算资源异构性**：CoMiGS 通过调整每个设备的专用专家数量适应不同设备能力，优于 HetLoRA 和 FlexLoRA。
- **数据量分析**：高数据量用户从更多专用专家中获益；低数据量用户受通用专家的正则化作用，增加专用专家不导致过拟合。甚至仅有一个通用专家的低资源用户也能从其他用户拥有更多专用专家中受益（通用专家因角色分化而更强）。
- 资源开销小：相比 FedAvg，计算和内存开销仅增加 1.25%，通信成本降低 50%（仅传输通用专家参数）。

## 7. 优点

- **创新性**：首次同时处理计算资源异构性和数据异构性，使用双层优化分离路由和专家更新，理论保证收敛。
- **实用性**：对资源受限设备友好，额外开销极低，通信减半。开源代码促进后续研究。
- **鲁棒性**：通用专家提供正则化，防止低数据量用户过拟合；专用专家提供个性化，在高数据量下进一步提升。
- **灵活性**：支持不同设备拥有不同数量的专用专家，自动适配计算能力。

## 8. 不足与局限

- **实验规模**：仅测试了 GPT-2 (124M) 和 Llama 3.2 (1B) 两个较小模型，未在更大模型（如 7B）或更大用户群体（超过 4 用户）上验证。通信延迟和实际设备部署的细节未涉及。
- **隐私与安全**：论文仅在摘要提及“隐私可进一步通过差分隐私增强”，未考虑对抗性攻击（如恶意用户上传恶意通用参数）下的鲁棒性。路由参数保留在本地，但通用参数聚合仍有安全隐患。
- **依赖验证集**：方法需要每个用户有一个小规模验证集用于更新路由器；若验证集不独立或训练分布与目标分布差异过大，可能影响表现。论文虽提供可通过训练集采样替代的方案（如 CoMiGS-tr），但性能略降。
- **负载均衡**：标准负载均衡损失的效果与修改版无显著差异，说明对通用专家的偏向性路由并不总是必需，可能因数据集而异，未深入探讨。
- **理论假设较强**：线性收敛证明基于 Contractive 假设或线性专家假设，在实际深度非线性网络中仅局部成立，泛化至所有情况仍需更多验证。

（完）
