# 日报 · 2026-09-04

- 生成时间：2026-09-04 22:51:50 UTC
- 当次推荐总数：15
- 精读区：6
- 速读区：9

## 今日简报（AI）
今日聚焦端侧与批处理推理效率，15篇论文中6篇精读，核心覆盖流式推测框架与MoE动态调度。最值得关注LeanStream的10分 speculate-and-refine 流式方案，以及DynaNDE对批量MoE专家调度的优化，二者均面向实际部署瓶颈。若时间有限，建议先看这两篇精读摘要，再按需浏览速读中SoC算子并行与KV缓存一致性主题。

## 精读区
1. [LeanStream: A Speculate-and-Refine Streaming Framework for Efficient on-Device LLM Inference](/202609/04/2609.03079v1-leanstream-a-speculate-and-refine-streaming-framework-for-efficient-on-device-llm-inference) （10.0/10）
2. [DynaNDE: Dynamic Near-Data Expert Scheduling for Batched MoE Inference](/202609/04/2609.00407v1-dynande-dynamic-near-data-expert-scheduling-for-batched-moe-inference) （9.0/10）
3. [DRLM: Deep Reinforcement Learning-Based LLM Query Orchestration in Edge Environments](/202609/04/2609.00442v1-drlm-deep-reinforcement-learning-based-llm-query-orchestration-in-edge-environments) （9.0/10）
4. [GrowPage: On-Demand KV Budgeting for Efficient LLM Reasoning Serving](/202609/04/2609.03494v1-growpage-on-demand-kv-budgeting-for-efficient-llm-reasoning-serving) （9.0/10）
5. [HBQ: Hierarchical Scaling Block Quantization with Hardware-Efficiency-Aware Design for Accurate LLM Inference](/202609/04/2609.00450v1-hbq-hierarchical-scaling-block-quantization-with-hardware-efficiency-aware-design-for-accurate-llm-inference) （8.0/10）
6. [How Do Prompt Variations Affect Energy Consumption in On-Device LLMs?](/202609/04/2609.01798v1-how-do-prompt-variations-affect-energy-consumption-in-on-device-llms) （8.0/10）

## 速读区
1. [Para-Pipe: Exploiting Hierarchical Operator Parallelism of ML Computational Graphs on SoCs](/202609/04/2609.04168v1-para-pipe-exploiting-hierarchical-operator-parallelism-of-ml-computational-graphs-on-socs) （8.0/10）
2. [Budget-Aware Compression Pipeline for Single-GPU LLM Inference: Methods, Trade-offs, and Coupling Effects](/202609/04/2608.30076v2-budget-aware-compression-pipeline-for-single-gpu-llm-inference-methods-trade-offs-and-coupling-effects) （7.0/10）
3. [CateKV: On Sequential Consistency for Long-Context LLM Inference Acceleration](/202609/04/2608.30295v1-catekv-on-sequential-consistency-for-long-context-llm-inference-acceleration) （7.0/10）
4. [PCoMoE: Shifting MoE Inference from Monolithic Expert Selection to Fine-Grained Path Composition](/202609/04/2609.01024v1-pcomoe-shifting-moe-inference-from-monolithic-expert-selection-to-fine-grained-path-composition) （7.0/10）
5. [MeanField Surrogate Modeling for Scalable Runtime Scheduling of Concurrent Heterogeneous AI Inference on Shared GPUs](/202609/04/2609.02109v1-meanfield-surrogate-modeling-for-scalable-runtime-scheduling-of-concurrent-heterogeneous-ai-inference-on-shared-gpus) （7.0/10）
6. [Closing the Semantic-Edge Gap: Tiny Language Models for 6G Wireless Intelligence](/202609/04/2609.03747v1-closing-the-semantic-edge-gap-tiny-language-models-for-6g-wireless-intelligence) （7.0/10）
7. [ContextPipe: Database-Inspired Context Assembly for Long-Horizon Agents](/202609/04/2609.00749v1-contextpipe-database-inspired-context-assembly-for-long-horizon-agents) （6.0/10）
8. [CRISP: Cliff-awaRe Input-adaptive Sparse Prefilling with Structural-Mass-Motivated Routing](/202609/04/2609.01925v1-crisp-cliff-aware-input-adaptive-sparse-prefilling-with-structural-mass-motivated-routing) （6.0/10）
9. [HeadWiseKV: Budgeted Per-Head Cache Residency for Hybrid Long-Context Language Models](/202609/04/2609.02029v1-headwisekv-budgeted-per-head-cache-residency-for-hybrid-long-context-language-models) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
