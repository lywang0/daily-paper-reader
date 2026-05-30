---
title: "SpecEdge: Scalable Edge-Assisted Serving Framework for Interactive LLMs"
title_zh: SpecEdge：面向交互式LLM的可扩展边缘辅助服务框架
authors: "Jinwoo Park, Seunggeun Cho, Dongsu Han"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=4QVLKwgg3S"
tags: ["query:edge-llm"]
score: 9.0
evidence: 边缘辅助的LLM服务框架
tldr: 针对现有LLM服务框架忽视边缘GPU的问题，本文提出SpecEdge，利用推测解码将边缘与服务器GPU协同工作，通过主动边缘草稿和流水线感知调度，实现服务器吞吐量提升2.22倍，成本效率提高1.91倍，同时降低令牌间延迟。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 585, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 880, \"height\": 311, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 478, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 687, \"height\": 220, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 675, \"height\": 209, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1394, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 465, \"height\": 271, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 467, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 457, \"height\": 276, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 456, \"height\": 275, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 465, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 455, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1405, \"height\": 223, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 845, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 753, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 613, \"height\": 521, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 1047, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 782, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1160, \"height\": 786, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1442, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1136, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 998, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1178, \"height\": 574, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 489, \"height\": 314, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1441, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 556, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1440, \"height\": 793, \"label\": \"Table\"}]"
motivation: 现有LLM服务系统集中于服务器端，忽视消费者级边缘GPU的潜力。
method: 采用推测解码拆分工作负载，边缘负责草稿生成，服务器验证，结合流水线调度。
result: 服务器吞吐量提升2.22倍，成本效率提高1.91倍，延迟降低。
conclusion: SpecEdge利用边缘GPU显著提升LLM服务效率。
---

## Abstract
Large language models (LLMs) power many modern applications, but serving them at scale remains costly and resource-intensive. Current server-centric systems overlook consumer-grade GPUs at the edge. We introduce SpecEdge, an edge-assisted inference framework that splits LLM workloads between edge and server GPUs using a speculative decoding scheme, exchanging only token outputs over the network. SpecEdge employs proactive edge drafting to overlap edge token creation with server verification and pipeline-aware scheduling that interleaves multiple user requests to increase server-side throughput. Experiments show SpecEdge enhances overall cost efficiency by **1.91×** through achieving **2.22×** server throughput, and reduces inter token latency by **11.24\%** compared to a server-only baseline, introducing a scalable, cost-effective paradigm for LLM serving. The code is available at https://github.com/kaist-ina/specedge

---

## 论文详细总结（自动生成）

# 论文 SpecEdge 详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大规模 LLM 服务成本高昂、资源密集，现有系统完全依赖数据中心级 GPU（如 A100、H100），忽视了网络边缘大量存在的消费级 GPU（如 RTX 4090）。这些边缘 GPU 在计算能力上不逊色，成本却低得多（如 RTX 4090 的 TFLOPS 超过 A100，成本仅为其 1/14）。
- **背景**：传统并行化技术（张量并行、流水线并行）依赖高速内部互联（NVLink、InfiniBand），无法在广域网环境中有效协同边缘与服务器；层拆分方法会引入过高通信延迟且无法缓解内存 I/O 瓶颈。
- **整体含义**：本文首次提出实用的边缘辅助推理框架 SpecEdge，通过推测解码将边缘与服务器 GPU 高效协作，在保持输出质量的同时大幅降低成本、提升吞吐量并降低用户感知延迟。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 采用 **推测解码（Speculative Decoding）** 范式：边缘 GPU 负责生成候选 token（草稿阶段），服务器 GPU 负责批验证（验证阶段），网络仅传输最终的 token 输出，而非中间模型状态。
- 该方式可保证与仅使用服务器模型完全一致的输出分布。

### 关键技术
1. **主动边缘草稿（Proactive Edge Drafting）**
   - 边缘在发送草稿树后不等待验证结果，立即继续生成后续 token（主动扩展）。
   - 仅当服务器验证的 token 与主动草稿完全对齐（Complete Draft Alignment）时，这些预先生成的 token 才被保留，从而有效隐藏网络与验证延迟。
   - 通过选择累积对数概率最高的单一路径作为扩展头（而非扩展所有叶子），最大化预期收益。公式表达为：
     \[
     E(\text{Gain}) = P_{\text{align}} \cdot P_{\text{match}|\text{align}} \cdot \left( \frac{T_{\text{draft}}}{H_{\text{expan}}} - 1 \right)
     \]
     其中 \(P_{\text{align}}\) 为对齐概率，\(T_{\text{draft}}\) 为主动草稿 token 数，\(H_{\text{expan}}\) 为扩展头数量。

2. **流水线感知调度（Pipeline-Aware Scheduling）**
   - 服务器端将来自多个边缘设备的验证请求交错批处理，消除等待空闲气泡。
   - 动态调整草稿深度，使得“边缘草稿时间 + 网络 RTT”约等于“服务器验证时间”，实现流水线完全对齐。
   - 通过自定义注意力掩码和 KV 缓存填充，高效处理长度不一的验证批次。

## 3. 实验设计

### 数据集 / 场景
- **SpecBench**（6 个任务：多轮对话、翻译、摘要、QA、数学、RAG）
- **C4**、**OpenAssistant（OAsst）**、**WikiText-2**、**MTBench**
- 每个查询最多生成 256 个输出 token。

### 基准方法（Baselines）
- **服务器-only 推测解码**（使用树结构推测解码）
- **自回归解码**（仅服务器）
- **层拆分方案**（部分层运行在边缘 GPU）
- 所有配置使用相同的目标模型，保证输出分布一致。

### 模型组合
- 目标模型：Qwen3-14B/32B，Vicuna-33B，Llama2-13B-Chat
- 草稿模型：Qwen3-1.7B/0.6B，Sheared Llama-1.3B，Tiny Llama-1.1B，JackFram-160M

## 4. 资源与算力

- **服务器 GPU**：NVIDIA A100 40GB（部分实验使用 A100 80GB）
- **边缘 GPU**：主要为 NVIDIA RTX 4090（也测试了 RTX 4070 Ti Super、RTX 3090、RTX 2080 Ti、RTX 3060 Ti）
- **网络环境**：实际广域网平均 RTT 为 14.07ms
- **数量**：边缘 GPU 数量与并发请求数成比例（batch size × 2）
- **成本**：A100 40GB 约 $4.05/h，RTX 4090 约 $0.35/h（来自 Vast.ai）
- **未明确说明**：训练时长；论文仅涉及推理阶段，无需训练。

## 5. 实验数量与充分性

- **大量实验覆盖**：
  - 端到端性能对比（表 1 和表 2）：覆盖多个模型组合、6 个 SpecBench 任务，以及 C4/OAsst/WikiText-2/MTBench 等数据集。
  - 消融实验（图 7-9）：分别评估基础解耦、加入主动草稿、加入流水线调度的影响。
  - 网络延迟敏感性（图 11）：RTT 从 15ms 到 65ms。
  - 不同边缘设备（图 12）：4 种消费级 GPU。
  - 替代草稿方法（附录 B.3）：非树结构推测解码。
  - 批处理草稿（附录 B.4）：单边缘 GPU 服务多请求。
  - 推理模式（附录 B.5）：启用/禁用推理 token。
  - 跨云服务商成本分析（附录 C）：多家 GPU 提供商与云服务商。
  - 实际案例研究（附录 D）：展示主动草稿完整生命周期。
- **充分性与公平性**：所有实验使用相同输出分布衡量，采用相同树结构算法（Sequoia/SpecExec），超参数优化充分（服务器-only 穷举最佳草稿深度）。实验设计客观、全面。

## 6. 主要结论与发现

- **成本效率提升 1.91×**：通过 2.22× 的服务器吞吐量提升实现（表 1）。
- **令牌间延迟降低 11.24%**：甚至优于无网络延迟的服务器-only 配置（图 6）。
- **主动草稿有效掩盖网络与验证延迟**：每次验证多生成约 13% 的 token（图 9）。
- **流水线调度消除服务器空闲**：使服务器运行时间减少 40-50%（图 7）。
- **对网络延迟鲁棒**：在 50ms RTT 内仍优于服务器-only，远好于层拆分（图 11）。
- **兼容多种草稿方法**：非树结构同样有效（附录 B.3）。
- **多供应商成本验证**：所有云平台均保持优势（附录 C）。

## 7. 优点

- **创新性**：首次将边缘消费级 GPU 有效融入 LLM 服务，提出“主动边缘草稿+流水线调度”的协同方案。
- **实用性强**：仅需网络传输小量 token，适合真实广域网环境；代码开源，可复现。
- **实验全面**：覆盖多种模型、数据集、硬件、网络条件、云供应商，消融分析完善。
- **性能优越**：同时降低成本、提高吞吐量、降低延迟，三个关键指标均优于基准。
- **不改变输出质量**：通过推测解码保证与纯服务器模型完全相同的分布。

## 8. 不足与局限

- **未充分探索超大规模模型**：实验最大模型为 33B/32B，更大型模型（如 70B+）的适用性尚未验证（但作者认为设计无根本性扩展障碍）。
- **边缘设备可信度与安全性**：论文提及但未深入解决当边缘 GPU 由用户控制时存在的容错、恶意攻击等问题。
- **批处理草稿的权衡**：单边缘 GPU 服务多请求可降低成本，但延迟增加（5.9%–19.0%），适合延迟容忍场景。
- **对网络延迟仍敏感**：当 RTT 超过 50ms 时，延迟优势减弱甚至略高于服务器-only（但仍远好于层拆分）。
- **预填充阶段**：论文说明因可并行处理，预填充延迟与基准相当，但未详细对比时间到首 token（TTFT）指标。
- **未报告训练耗时**：作为推理系统，无需训练，但缺乏长时间运行稳定性评估。

（完）
