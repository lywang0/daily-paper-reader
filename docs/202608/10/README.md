# 日报 · 2026-08-10

- 生成时间：2026-08-10 21:07:13 UTC
- 当次推荐总数：14
- 精读区：6
- 速读区：8

## 今日简报（AI）
今日聚焦LLM推理系统优化，精读2篇高分论文，速读3篇，共覆盖14篇文献，核心热点在延迟预算调度与统一内存设计。最值得关注：SLO感知的延迟预算分配（Cascade）可实现公平且高吞吐的推理服务，NPU-PIM系统的双视角内存设计则显著提升动态LLM推理效率。建议结合分层KV缓存管理（HiSparse）与路由工具（LLMRouter），从系统层和调度层同时优化实际部署。

## 精读区
1. [Cascade: Exploiting SLO-Aware latency budget for fair and high goodput LLM inference serving](/202608/10/2608.06557v1-cascade-exploiting-slo-aware-latency-budget-for-fair-and-high-goodput-llm-inference-serving) （9.0/10）
2. [Rethinking Unified Memory for NPU-PIM Systems: Dual-View Memory for Dynamic Inference of LLM](/202608/10/2608.06989v1-rethinking-unified-memory-for-npu-pim-systems-dual-view-memory-for-dynamic-inference-of-llm) （9.0/10）
3. [Output-Aware Rotation for INT2 KV-Cache Quantization](/202608/10/2608.02691v1-output-aware-rotation-for-int2-kv-cache-quantization) （8.0/10）
4. [Multi-Level Modeling of Large Language Model Inference Latency and Energy via Hybrid Analytical--Machine-Learning Predictors](/202608/10/2608.06723v1-multi-level-modeling-of-large-language-model-inference-latency-and-energy-via-hybrid-analytical--machine-learning-predictors) （8.0/10）
5. [CubicQuant: Parametric Non-Uniform Codebooks for High-Throughput LLM Inference with 1-8-Bit Weights](/202608/10/2608.06763v1-cubicquant-parametric-non-uniform-codebooks-for-high-throughput-llm-inference-with-1-8-bit-weights) （8.0/10）
6. [MiCoPro: End-to-End Mixed Precision HW/SW Co-design with HW-aware Proxy Model](/202608/10/2608.06916v1-micopro-end-to-end-mixed-precision-hwsw-co-design-with-hw-aware-proxy-model) （8.0/10）

## 速读区
1. [HiSparse: Scaling Sparse-Attention Decoding with Hierarchical KV Cache Management](/202608/10/2608.07009v1-hisparse-scaling-sparse-attention-decoding-with-hierarchical-kv-cache-management) （8.0/10）
2. [MACRO: Markov Chain Routing of Transformer Layers](/202608/10/2608.05872v1-macro-markov-chain-routing-of-transformer-layers) （7.0/10）
3. [LLMRouter: Unified Infrastructure for Developing, Evaluating, and Deploying LLM Routers](/202608/10/2608.06867v1-llmrouter-unified-infrastructure-for-developing-evaluating-and-deploying-llm-routers) （7.0/10）
4. [Every Cache Entry Earns Its Place: Global Allocation of Resolution and Coverage for KV Cache Compression](/202608/10/2608.07001v1-every-cache-entry-earns-its-place-global-allocation-of-resolution-and-coverage-for-kv-cache-compression) （7.0/10）
5. [A Picture is Worth a Thousand Tokens: How Vision Language Models Cut AI Energy Costs While Improving Accuracy](/202608/10/2608.07427v1-a-picture-is-worth-a-thousand-tokens-how-vision-language-models-cut-ai-energy-costs-while-improving-accuracy) （7.0/10）
6. [LiveMem: Maintaining Memory State Continuity in Long-Running LLM Inference](/202608/10/2608.02515v1-livemem-maintaining-memory-state-continuity-in-long-running-llm-inference) （6.0/10）
7. [Retrofitting Linear Attention into Diffusion Language Models](/202608/10/2608.06628v1-retrofitting-linear-attention-into-diffusion-language-models) （6.0/10）
8. [Autonomy-of-Heads: Data-Free Sparse Attention from Frozen Query-Key Geometry](/202608/10/2608.06849v1-autonomy-of-heads-data-free-sparse-attention-from-frozen-query-key-geometry) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
