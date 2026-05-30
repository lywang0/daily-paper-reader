---
title: Cost-efficient Collaboration between On-device and Cloud Language Models
title_zh: 设备端与云端语言模型的成本高效协作
authors: "Avanika Narayan, Dan Biderman, Sabri Eyuboglu, Avner May, Scott Linderman, James Zou, Christopher Re"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=qGDlzt3dKz"
tags: ["query:edge-llm"]
score: 9.0
evidence: 设备端与云端LLM协作实现高效推理
tldr: "针对设备端小语言模型与云端前沿模型协作降低推理成本的问题，提出MINION协作协议。该协议仅由设备端模型处理完整上下文，云端模型仅参与对话，实现30.4倍云端成本降低并恢复87%性能。进一步分析限制因素并改进，平衡成本与质量。"
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-qgdlzt3dkz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1739, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qgdlzt3dkz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 838, \"height\": 837, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qgdlzt3dkz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 836, \"height\": 407, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qgdlzt3dkz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1759, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qgdlzt3dkz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1560, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qgdlzt3dkz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1052, \"height\": 859, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qgdlzt3dkz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1230, \"height\": 746, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qgdlzt3dkz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1752, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qgdlzt3dkz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1073, \"height\": 635, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qgdlzt3dkz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1724, \"height\": 1381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qgdlzt3dkz/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1588, \"height\": 978, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 473, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 858, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1553, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1314, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 643, \"height\": 329, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 592, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1526, \"height\": 696, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1613, \"height\": 654, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1811, \"height\": 562, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 469, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1578, \"height\": 1523, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1578, \"height\": 1563, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1524, \"height\": 273, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qgdlzt3dkz/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1544, \"height\": 387, \"label\": \"Table\"}]"
motivation: 希望利用设备端模型降低成本，同时保留云端模型的高质量。
method: 提出MINION协议，设备端处理上下文，云端仅通过对话参与推理。
result: "云端成本降低30.4倍，性能恢复87%。"
conclusion: 本地-远程协作可以有效降低推理成本，但需解决指令跟随等挑战。
---

## Abstract
We investigate an emerging setup in which a small, on-device language model (LM) with access to local data collaborates with a frontier, cloud-hosted LM to solve real-world tasks involving financial, medical, and scientific reasoning over long documents. 
*Can a local-remote collaboration reduce cloud inference costs while preserving quality?*
First, we consider a naïve collaboration protocol, coined MINION, where the local and remote models simply chat back and forth. Because only the local model ingests the full context, this protocol reduces cloud costs by 30.4x, but recovers only 87% of the performance of the frontier model.
We identify two key limitations of this protocol: the local model struggles to (1) follow the remote model's multi-step instructions and (2) reason over long contexts. Motivated by these observations, we propose MINIONS, a protocol in which the remote model decomposes the task into easier subtasks over shorter chunks of the document, that are executed locally in parallel. MINIONS reduces costs by 5.7× on average while recovering 97.9% of the remote-only performance. Our analysis reveals several key design choices that influence the trade-off between cost and performance in local-remote systems.

---

## 论文详细总结（自动生成）

# 论文总结：Cost-efficient Collaboration Between On-device and Cloud Language Models

## 1. 核心问题与整体含义

**研究动机与背景**  
云端前沿大语言模型（如GPT-4）能够处理数据密集型的推理任务（如金融、医疗、科学论文），但每次推理成本高昂（处理百万token成本超15美元）。与此同时，小参数模型（1–8B）进步迅速，可在个人电脑或手机上运行，但当前仅用于简单任务。本文研究如何让一个小型设备端LM与云端前沿LM协作，在保持任务质量的前提下，大幅降低云端推理成本。核心问题：**能否通过本地-远程协作协议，在减少云端成本的同时，尽可能恢复远程模型单独运行时的性能？**

## 2. 方法论

**核心思想**  
提出两阶段协议：
- **MINION（Naïve协议）**：设备端模型阅读完整上下文，云端模型仅通过来回对话获取压缩后的信息，减少云端输入token。该协议降低云端成本30.4倍，但性能仅恢复87%。
- **MINIONS（改进协议）**：针对MINION中发现的两大局限（小模型难以同时执行多条指令、长上下文中推理困难），云端模型将任务分解为多个简单子任务，每个子任务对应文档的一个短块，由设备端模型并行执行。具体包括三个步骤：
  1. **分解（Decompose）**：云端模型根据查询生成Python代码，代码在设备端执行，生成作业规范（指令+文本块）。
  2. **执行（Execute）**：设备端模型并行处理所有作业，输出结构化结果（解释、引用、答案），过滤掉无关或不确定的回答。
  3. **聚合（Aggregate）**：云端模型聚合结果，决定是否输出最终答案或进入下一轮迭代。

**关键技术细节**  
- 使用代码生成（code generation）来实现任务分解，无需云端模型读取完整文档。
- 可调节的超参数：本地模型大小、每轮任务数量、每个任务的采样次数、文本块大小、通信轮数等。
- 成本模型：仅统计云端token消耗（输入+输出），本地推理视为免费（忽略硬件固定成本和能耗）。

## 3. 实验设计

**数据集与场景**  
- **FINANCEBENCH**：金融文档理解，含数值推理。
- **LONGHEALTH**：长时间序列医疗记录问答。
- **QASPER**：科学论文摘要问答。
- 每个数据集上下文长度在50K–150K token左右。

**基准方法**  
- 远程模型单独运行（GPT-4 O，全上下文输入）。
- 本地模型单独运行（各种大小的小模型）。
- MINION协议。
- MINIONS协议。
- 对比消融：不同本地模型（LLAMA-3.2-1B/3B/8B、QWEN2.5-3B/7B）、不同远程模型（GPT-4 O、LLAMA-3.3-70B等），以及不同超参数配置。

**评估指标**  
- 准确性（正确/错误二元评分）。
- 平均每次查询的云端成本（美元，基于GPT-4 O API定价）。
- 端到端延迟（秒）和理论延迟分析。

## 4. 资源与算力

**本地硬件**  
- 使用单张消费级GPU：NVIDIA RTX 4090（MSRP $1,599）或RTX 6000 Ada（约$7,000）。
- 本地模型在单GPU上运行（A100也可用于实验，但延迟报告基于RTX 4090）。
- 未明确说明训练时长，因为方法仅涉及推理；微调实验中使用LoRA训练了少量epoch（4轮），使用A100。

**云端模型**  
- GPT-4 O作为默认远程模型（API调用）。
- 未说明云端GPU数量（由云提供商管理）。

## 5. 实验数量与充分性

**实验数量**  
- 主表（Table 1）覆盖3个数据集×4种本地模型×4种协议（远程/本地 alone, MINION, MINIONS），共>40组条件。
- 消融实验：图4（任务数、采样数、块大小）、图5（模型大小、通信轮数）、图6（轮数策略）、附录中关于RAG对比、能量分析、工具使用、多模态扩展等。
- 时间回溯分析（Table 4）：模拟不同时间段模型性能。
- 微调实验（Appendix G.2）：LoRA微调后性能对比。

**充分性与公平性**  
- 实验设计系统：对比了多种本地模型大小、多种远程模型、多种协议超参数，涵盖成本-精度权衡。
- 成本计算基于公开API定价，公平对比。
- 延迟测量使用实际硬件，并给出理论框架（Appendix C）。
- 局限性：实验仅包含三个领域（金融、医疗、科学），未覆盖更多实际应用场景（如代码、法律）。本地模型仅限开源系列（LLAMA、QWEN），未试验其他系列（如Phi、Mistral）。隐私和安全性未深入评估。

## 6. 主要结论与发现

1. **MINIONS高效**：使用LLAMA-8B作为本地模型时，MINIONS平均恢复远程模型性能的97.9%，同时将云端成本降低5.7倍。使用3B模型时，也能恢复93.4%性能，成本降低16.6%。
2. **模型大小很重要**：1B本地模型表现很差（不足远程性能的50%），3B成为有效协作的起点。
3. **并行化提升质量**：增加子任务数量、采样次数、或更细粒度的文本块均可提高准确性，但会增加云端输入token成本（需权衡）。
4. **多轮通信有效**：增加远程-本地对话轮数可提升质量，但成本线性增加；使用“scratchpad”策略比简单重试更优。
5. **随着时间推移**：方法在2024年中期（GPT-4 Turbo + LLAMA-3.1-8B）之后才变得可行，未来小模型进步将进一步提升成本效率。

## 7. 优点

- **清晰的问题定义与分解**：系统识别了小模型的两大弱点（多指令跟随、长上下文推理），并设计了针对性解决方案。
- **巧妙的代码生成机制**：远程模型生成Python代码，在本地执行，无需远程读取文档，实现细粒度任务分解。
- **丰富的可调节性**：提供了多个超参数“旋钮”（任务数、采样、块大小、轮数），方便在不同成本-精度需求下调整。
- **实际可部署**：使用消费级显卡即可运行，延迟增加在可接受范围内（约2–3倍于纯云端）。
- **全面的实验分析**：不仅报告了平均性能，还按问题复杂度、证据跨度数等分层分析；包含能量消耗、延迟、RAG对比等额外维度。

## 8. 不足与局限

- **数据集有限**：仅包含三个领域，且每个数据集的样本量不大（FINANCEBENCH 64条、LONGHEALTH 400条、QASPER 500条），可能不足以全面泛化。
- **本地模型选择单一**：仅使用LLAMA和QWEN系列，未覆盖其他开源模型（如Mistral、Phi）或专有小模型（如Apple Intelligence）。
- **成本模型简化**：假设本地推理免费，但实际涉及硬件折旧、能耗、维护成本，尤其在大量查询时不可忽略。
- **未深入探讨隐私与安全**：虽然提及本地处理可减少数据泄露，但未量化分析或提供保证机制。
- **延迟分析依赖特定硬件**：RTX 4090并非典型服务器GPU，不同设备延迟可能显著变化；理论框架虽好，但未验证所有场景。
- **缺少开放的模型权重或代码**（论文中未提及开源），复现性存疑。
- **MINIONS的代码生成依赖远程模型能力**：如果远程模型生成有缺陷的代码，可能导致作业错误或性能下降。
- **实验未涵盖多模态或工具使用的主流场景**：虽然附录有初步探索，但结论有限。

（完）
