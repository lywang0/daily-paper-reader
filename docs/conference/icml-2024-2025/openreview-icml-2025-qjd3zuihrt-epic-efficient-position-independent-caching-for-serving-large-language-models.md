---
title: "EPIC: Efficient Position-Independent Caching for Serving Large Language Models"
title_zh: EPIC：面向大语言模型服务的高效位置无关缓存
authors: "Junhao Hu, Wenrui Huang, Weidong Wang, Haoyi Wang, tiancheng hu, zhang qin, Hao Feng, Xusheng Chen, Yizhou Shan, Tao Xie"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=qjd3ZUiHRT"
tags: ["query:edge-llm"]
score: 7.0
evidence: 改进上下文缓存以服务于大语言模型
tldr: 现有上下文缓存要求请求间精确前缀匹配，限制了在少样本学习和检索增强生成等场景中的复用。本文提出位置无关缓存（PIC），允许跨不同前缀的请求模块化复用KV向量，显著提升了大语言模型服务系统的缓存效率和吞吐量。该方法对可变前缀的请求具有鲁棒性，为LLM服务提供了更通用的缓存方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-qjd3zuihrt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 853, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjd3zuihrt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 854, \"height\": 697, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjd3zuihrt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 751, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjd3zuihrt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1748, \"height\": 756, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjd3zuihrt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 853, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjd3zuihrt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 853, \"height\": 1397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjd3zuihrt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 840, \"height\": 127, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjd3zuihrt/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 853, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjd3zuihrt/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 589, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjd3zuihrt/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 863, \"height\": 1351, \"label\": \"Figure\"}]"
motivation: 现有上下文缓存依赖前缀精确匹配，限制了复用场景，导致服务效率低下。
method: 提出位置无关缓存PIC，通过模块化设计使得KV向量可以独立于请求前缀进行复用。
result: 在多种变前缀请求场景下，缓存命中率和服务吞吐量显著提升。
conclusion: PIC通过解耦KV向量与前缀关系，提升了LLM服务缓存的泛用性和效率。
---

## Abstract
Large Language Models (LLMs) show great capabilities in a wide range of applications, but serving them efficiently becomes increasingly challenging as requests (prompts) become more complex. Context caching improves serving performance by reusing Key-Value (KV) vectors, the intermediate representations of tokens that are repeated across requests. However, existing context caching requires exact prefix matches across requests, limiting reuse cases in settings such as few-shot learning and retrieval-augmented generation, where immutable content (e.g., documents) remains unchanged across requests but is preceded by varying prefixes. Position-Independent
Caching (PIC) addresses this issue by enabling modular reuse of the KV vectors regardless of prefixes. We formalize PIC and advance prior work by introducing EPIC, a serving system incorporating our new LegoLink algorithm, which mitigates the inappropriate “attention sink” effect at every document beginning, to maintain accuracy with minimal computation. Experiments show that EPIC achieves up to 8× improvements in Time-To-First-Token (TTFT) and 7× throughput gains over existing systems, with negligible or no accuracy loss.

---

## 论文详细总结（自动生成）

# 论文《EPIC: Efficient Position-Independent Caching for Serving Large Language Models》中文总结

## 1. 核心问题与整体含义（研究动机与背景）
- **问题**：现有上下文缓存（Context Caching）要求请求之间**精确前缀匹配**才能复用KV向量。在少样本学习、检索增强生成（RAG）等场景中，不可变内容（如文档）频繁出现但前缀可变，导致复用机会严重受限。
- **整体含义**：本文提出**位置无关缓存（PIC）**，允许**模块化复用KV向量，不受前缀影响**，从而大幅提升缓存命中率和服务效率。
- **定位**：本文形式化定义了PIC框架，并设计系统EPIC及算法LegoLink，解决现有方法（如CacheBlend）计算复杂度高、动态稀疏性开销大的问题。

## 2. 方法论
### 2.1 核心思想
- **两步框架**：将PIC使用类比为编译-链接过程。
    - **编译步骤**：将每个不可变块单独提交给LLM，生成并存储该块的KV向量（位置ID从0开始）。
    - **链接步骤**：检索并拼接缓存KV向量，再重新计算一部分KV向量以维持精度。
- **关键洞察**：每个块的开头tokens会过度吸收注意力（“attention sink”现象），阻碍后续tokens关注相关上下文。LegoLink通过**重计算每个块（除首个块）的前k个token**，使其认识到自己并非位于起始位置，从而削弱其注意力汇能力，使注意力重新分布到相关位置。

### 2.2 关键技术细节
- **LegoLink算法**：
    - 选择k个token（每个块的前k个 + 用户查询），k≪N（N为总token数）。
    - 对这k'个token，在每一层计算新的Q、K、V矩阵，并从缓存中取出未选中的N−k'个token的KV向量，拼接得到完整的K_exp、V_exp。
    - 执行**掩码自注意力**（只允许关注当前位置之前的token），输出结果传递到下一层。
    - 复杂度：O(kN) ~ O(N)，远优于CacheBlend的O(N²)。
    - **静态稀疏性**：预定义重计算哪些token，避免了CacheBlend中动态选择带来的运行时开销。
- **LegoLink-0变体**：编译时在每个块前添加4个虚拟token（如BOS），然后丢弃其KV向量，在链接步骤中完全跳过重计算，实现零链接开销。

## 3. 实验设计
### 3.1 数据集与场景
- **数据集**：6个数据集
    - 多文档问答：2WikiMQA、MuSiQue、HotpotQA
    - 少样本指令跟随：SAMSum
    - 多文档摘要：MultiNews
    - 长上下文检索：Needle in a Haystack
- **任务类型**：同步负载（单请求串行，评估准确率-延迟权衡）和异步负载（多用户并发，不同请求速率和上下文缓存比例CCR）。

### 3.2 Benchmark
- **基线方法**：
    - Full Recompute (FR)：完全重计算所有KV向量（最高精度，无加速）。
    - Naive：直接使用缓存KV向量，不重计算（最高加速，精度严重下降）。
    - CacheBlend（多种比例r=1%,5%,10%,15%,20%）：动态选择15%的token重计算。
    - LegoLink（多种k=2,4,8,16,32）：重计算每个块前k个token。
- **模型**：Mistral 7B Instruct、Llama 3.1 8B Instruct、Yi Coder 9B Chat（涵盖不同架构和训练方案）。

### 3.3 对比指标
- **TTFT**（首token生成时间，越低越好）
- **F1分数**（用于2WikiMQA、MuSiQue、HotpotQA、Needle）
- **Rouge-L分数**（用于SAMSum、MultiNews）

## 4. 资源与算力
- **硬件**：单台NVIDIA A100服务器，配备1块A100-80GB GPU，128核Intel(R) Xeon(R) Platinum 8358P CPU@2.60GHz，1TB DRAM。
- **软件**：Ubuntu 20.04，Linux kernel 5.16.7，CUDA 12.6。
- **基础设施**：基于vLLM 0.4.1实现，约2000行Python代码。
- **说明**：论文未提及训练过程（仅推理），因此没有训练时长或模型训练算力信息。

## 5. 实验数量与充分性
- **实验数量**：非常充分。
    - 同步负载：6个数据集 × 3种模型 × 多种算法变体（每个点平均200个测试用例），结果以散点图呈现（图6，含大量数据点）。
    - 异步负载：2WikiMQA上测试不同请求率和CCR组合，每个点5次实验取平均和标准差（图8）。
    - 长上下文实验：测试不同上下文长度（0-50000 tokens），固定块大小512 tokens，比较FR、CacheBlend-15、LegoLink-16的TTFT和OOM情况（图9）。
    - 算法分析：消融实验（LegoLink-0，含注意力图可视化，图7）。
    - CacheBlend运行时开销分解（图10）。
- **公平性与客观性**：
    - 与最先进系统CacheBlend直接对比，且包含了多种重计算比例的变体，避免单点比较。
    - 使用了多个模型和数据集，涵盖了主流任务类型，降低偏差。
    - 注意：作者指出所有算法在Yi Coder模型上精度低，但阐述了原因（模型对文档理解差），并不影响算法间相对比较。

## 6. 主要结论与发现
1. **LegoLink建立新的帕累托最优前沿**：在所有数据集和模型上，LegoLink变体在精度-延迟权衡上全面优于CacheBlend变体。
2. **LegoLink-2已足够**：仅重计算每个块前2个token，即可将精度损失控制在0-7%以内，同时TTFT相比CacheBlend-15**降低最多300%**（即3倍加速）。
3. **LegoLink-0可行**：通过编译时丢弃虚拟token，实现了零运行时重计算，精度保持良好（“attention sink”现象在中间层消失），但可能产生过长输出（需未来改进）。
4. **异步负载**：LegoLink-16相比CacheBlend-15，**TTFT降低最多8倍**，**吞吐量提升最多7倍**；随着CCR增大，LegoLink吞吐量持续提升，而CacheBlend保持平稳且无法处理更多请求。
5. **长上下文能力**：LegoLink-16的TTFT呈**近似线性增长**，支持更长的上下文（50k token vs. CacheBlend的35k token OOM），而CacheBlend呈二次增长。

## 7. 优点
- **方法创新性**：首次形式化PIC框架，提出LegoLink算法，利用“attention sink”现象设计简单的静态稀疏重计算方案，思路清晰且有效。
- **效率极高**：将重计算复杂度从O(N²)降至O(kN)，且支持零重计算变体，实际加速显著。
- **充分实验**：涵盖6个数据集、3个模型、多种算法变体、同步/异步负载、长上下文测试，对比基准全面（包含CacheBlend多个比例和Naive/FR），结果可信。
- **消融与解释**：对LegoLink-0的消融实验和注意力图可视化，有力证明了“attention sink”是主要问题，以及LegoLink策略的合理性。
- **系统实现**：基于vLLM构建了完整服务系统，支持显式缓存API，具有实用性。

## 8. 不足与局限
- **精度损失**：虽然LegoLink-2精度损失≤7%，但在某些数据集/模型组合下（如MultiNews + Llama 3.1、Needle + Yi Coder），LegoLink变体的精度分数可能低于CacheBlend的某些配置（图6中部分点LegoLink落在CacheBlend后方）。
- **过长输出问题**：LegoLink-0及其他稀疏算法（如StreamingLLM、H2O、Quest）会产生不必要的过长输出，导致F1/ROUGE-L评分降低，作者承认这是未来工作，但未提供解决方案。
- **模型依赖**：所有算法在Yi Coder模型上精度普遍低，说明PIC方法的有效性受限于底层模型能力。
- **异步负载构造可能不够真实**：作者强调PIC尚无公开trace，因此自建负载（每个用户重复发送相同请求）可能存在偏差，结论需谨慎推广。
- **未探索跨层重计算策略**：LegoLink对所有层均重计算相同的前k个token，但不同层可能对attention sink敏感度不同，可进一步优化。
- **资源限制**：实验仅在单GPU上进行，未验证多GPU或分布式场景下的扩展性。

（完）
