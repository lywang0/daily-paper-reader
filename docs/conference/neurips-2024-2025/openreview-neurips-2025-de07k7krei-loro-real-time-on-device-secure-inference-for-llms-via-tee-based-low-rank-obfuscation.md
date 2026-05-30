---
title: "LoRO: Real-Time on-Device Secure Inference for LLMs via TEE-Based Low Rank Obfuscation"
title_zh: LoRO：通过TEE低秩混淆实现实时设备端LLM安全推理
authors: "Gaojian Xiong, Yu Sun, Jianhua Liu, Jian Cui, Jianwei Liu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=de07K7kreI"
tags: ["query:edge-llm"]
score: 7.0
evidence: 通过TEE实现实时设备端LLM安全推理
tldr: LoRO针对边缘设备上LLM模型被盗风险，提出基于可信执行环境(TEE)的低秩混淆方法，通过密集掩码完全混淆参数，同时利用低秩分解减少TEE内计算复杂度，实现实时设备端安全推理，保障模型隐私。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-de07k7krei/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1306, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-de07k7krei/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1334, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-de07k7krei/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1243, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-de07k7krei/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1433, \"height\": 309, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-de07k7krei/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1431, \"height\": 301, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-de07k7krei/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1307, \"height\": 565, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-de07k7krei/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1302, \"height\": 422, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-de07k7krei/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1157, \"height\": 568, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-de07k7krei/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1440, \"height\": 269, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-de07k7krei/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1085, \"height\": 179, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-de07k7krei/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1437, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-de07k7krei/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 539, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-de07k7krei/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 656, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-de07k7krei/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1116, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-de07k7krei/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1270, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-de07k7krei/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1290, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-de07k7krei/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1002, \"height\": 221, \"label\": \"Table\"}]"
motivation: 边缘设备上的LLM易被窃取，现有TEE保护存在统计漏洞。
method: 使用低秩因子生成密集掩码，在TEE内高效混淆模型参数。
result: 在保证安全性的同时，实现了实时推理。
conclusion: 低秩混淆是边缘设备上高效安全的LLM推理方案。
---

## Abstract
While Large Language Models (LLMs) have gained remarkable success, they are consistently at risk of being stolen when deployed on untrusted edge devices. As a solution, TEE-based secure inference has been proposed to protect valuable model property. However, we identify a statistical vulnerability in existing protection methods, and furtherly compromise their security guarantees by proposed Model Stealing Attack with Prior. To eliminate this vulnerability, LoRO is presented in this paper, which leverages dense mask to completely obfuscate parameters. LoRO includes two innovations: (1) Low Rank Mask, which uses low-rank factors to generate dense masks efficiently. The computing complexity in TEE is hence reduced by an exponential amount to achieve inference speed up, while providing robust model confidentiality. (2) Factors Multiplexing, which reuses several cornerstone factors to generate masks for all layers. Compared to one-mask-per-layer, the secure memory requirement is reduced from GB-level to tens of MB, hence avoiding the hundred-fold latency introduced by secure memory paging. Experimental results indicate that LoRO achieve a $0.94\times$ Model Stealing (MS) accuracy, while SOTA methods presents $3.37\times$ at least. The averaged inference latency of LoRO is only $1.49\times$, compared to the $112\times$ of TEE-shielded inference. Moreover, LoRO results no accuracy loss, and requires no re-training and structure modification. LoRO can solve the concerns regarding model thefts on edge devices in an efficient and secure manner, facilitating the wide edge application of LLMs.

---

## 论文详细总结（自动生成）

# 论文总结：LoRO: 通过TEE低秩混淆实现实时设备端LLM安全推理

## 1. 核心问题与整体含义（研究动机与背景）

- **研究背景**：大语言模型（LLM）在边缘设备部署时面临严重的模型窃取风险。尽管基于可信执行环境（TEE）的安全推理方案已被提出，但现有方法存在统计性漏洞，无法有效保护模型隐私。
- **核心问题**：作者发现现有TEE保护方法（如置换、加法掩码、乘法噪声）无法隐藏模型参数与公开预训练模型之间的统计相关性，导致攻击者可利用先验知识发起模型窃取攻击（Model Stealing Attack with Prior, MSP），几乎恢复原始模型。
- **整体含义**：LoRO旨在提供一种**实时、无精度损失、无需重训练**的TEE安全推理框架，将设备端LLM的保护水平提升至黑盒级别，同时保持推理效率。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：使用**密集加法掩码**完全混淆模型参数，但通过**低秩分解**和**因子复用**解决密集掩码带来的TEE计算复杂度和安全内存瓶颈。
- **关键技术细节**：
  - **Low Rank Mask（低秩掩码）**：用两个低秩因子 \(B_{n \times d}\) 和 \(A_{d \times n}\) 生成密集掩码 \(D = BA\)。推理时，TEE内仅需计算轻量级的 \(xBA\)（复杂度由 \(O(n^3)\) 降至 \(O(n^2)\)），而大部分计算在REE（富执行环境）中完成。
  - **Factor Multiplexing（因子复用）**：复用若干“基石因子”（cornerstone factors），通过随机线性组合生成各层的掩码，避免每层独立存储一对因子，将安全内存需求从GB级降至MB级（如7B模型从1.02GB降至26MB）。
  - **中间结果保护**：对普通线性层使用一次性密码本（OTP）保护输入；对注意力模块的Q/K/V使用置换矩阵保护（因为OTP在点积注意力中不适用）。
  - **公式流程**：
    - 部署阶段：在TEE内用低秩因子生成密集掩码并混淆参数 \(W' = W + D\)，将密钥和因子安全存储。
    - 推理阶段：REE计算 \(y_{\text{REE}} = xW'\)，TEE计算 \(y_{\text{TEE}} = xD\)，结果恢复 \(y = y_{\text{REE}} - y_{\text{TEE}} = xW\)。

- **无需修改模型结构或重训练**，即插即用。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - NLP：SQuAD（阅读理解）、GSM8K（数学）、Spider（代码生成）、GLUE（MRPC、SST-2、MNLI等）。
  - CV：CIFAR100、Food101。
  - 额外：MATH（数学推理）。
- **模型**：
  - RoBERTa-Base/Large, BART-Large, Qwen2 (1.5B/3B/7B), LLaMA3 (1.5B/3B/8B), ViT-Base, ResNet18。
- **对比方法**：
  - 全遮蔽方法：MLCapsule, Penetralium。
  - 部分遮蔽方法：AegisDNN, TEESlice。
  - 解混淆遮蔽方法：TLG（置换）、Magnitude（稀疏加法掩码）、SOTER（乘法噪声）、ShadowNet（加法和乘法组合）、NNSplitter。
- **基准**：黑盒模型（无任何保护，仅提供推理接口）。

## 4. 资源与算力

- **文中明确说明**：
  - 模型安全性和精度实验在**两台NVIDIA RTX 4090 GPU**的服务器上进行。
  - 推理效率实验在两种TEE平台：
    - **Intel SGX**：笔记本电脑，Intel Core i9-10885H CPU + Quadro T2000 GPU，Gramine-SGX作为TEE OS。
    - **ARM TrustZone**：NVIDIA Jetson Orin NX开发板，6核ARM Cortex-A78AE CPU + 1024核Ampere GPU，OP-TEE作为TEE OS。
- 未给出具体训练时长或GPU总耗时，仅提到攻击微调使用少量epoch（2～5轮）。

## 5. 实验数量与充分性

- **大量实验**：涵盖6种模型规模（从125M到8B）、10余个数据集、多种攻击和防御对比。主要实验包括：
  - **模型窃取（MS）精度评估**：对每种方法在多个模型+数据集上报告攻击成功率（表1）。
  - **推理延迟比较**：在SGX和TrustZone两个平台，对比所有对比方法（图4、图5）。
  - **模型精度评估**：原始模型 vs LoRO vs 混淆模型（表3）。
  - **消融分析**：延迟分解（表6）、安全内存需求（表9）、低辅助数据攻击（表11）、CV场景（表12）等。
- **充分性评价**：实验覆盖了主流的LLM架构、多种TEE平台、不同攻击策略，对比方法全面，结果具有说服力。攻击实验取5次最高结果，体现最强敌手假设，公平性较好。

## 6. 主要结论与发现

- **安全性**：LoRO将模型窃取精度降至黑盒水平（平均0.94×，即攻击者仅获得与黑盒相近的性能），而现有最佳方法至少为3.37×。
- **效率**：平均推理延迟仅为REE推理的1.49×，远低于现有方法的112×以上。
- **精度**：无精度损失（浮点误差可忽略），混淆后的模型在REE中性能退化至随机猜测。
- **即插即用**：无需重训练或修改模型结构。

## 7. 优点（方法或实验设计的亮点）

- **创新性**：首次揭示现有TEE保护方法的统计漏洞，并设计出可完全掩盖统计分布的密集低秩掩码。
- **高效性**：低秩分解将TEE内复杂度从三次方降为二次方，因子复用将内存需求压缩到MB级，真正实现实时推理。
- **通用性**：兼容主流Transformer架构，支持CV和NLP任务；无需重训练，易于部署。
- **实验严谨**：在两个主流TEE平台上验证，对比方法包含最新SOTA，攻击假设强（10%训练数据），结果可信。

## 8. 不足与局限

- **实验覆盖**：
  - 仅测试了Intel SGX和ARM TrustZone，未涉及最新Confidential GPU（如NVIDIA H100），作者在讨论中指出成本原因暂未纳入。
  - 侧信道攻击超出范围，但该领域仍存在实际威胁。
- **偏差风险**：
  - 攻击实验采用5次最好结果，可能高估攻击能力，但作为安全评估合理。
  - 辅助数据比例设为10%，实际中攻击者可能拥有更少数据，结果已补充低数据实验（表11）证明LoRO仍有效。
- **应用限制**：
  - 需要TEE支持，目前并非所有边缘设备都配备。
  - OTP在注意力模块不适用，改用置换保护，但置换可能暴露列分布（作者声称因掩码独立而风险规避，但未严格证明）。
  - 对卷积层仅提及兼容，但未深入实验（仅在ResNet18上测试了攻击）。

（完）
