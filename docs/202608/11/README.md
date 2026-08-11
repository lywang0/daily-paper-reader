# 日报 · 2026-08-11

- 生成时间：2026-08-11 21:19:37 UTC
- 当次推荐总数：9
- 精读区：5
- 速读区：4

## 今日简报（AI）
今日聚焦 LLM 推理优化，重点覆盖 WebGPU 调度、低比特稀疏推理与 KV 缓存管理。  
最值得关注的是《Measuring and Reducing WebGPU Dispatch Overhead for LLM Inference》与《UnionSparse》两项 9 分工作，分别从调度开销和索引效率切入。  
下一步可顺着 KV 缓存淘汰与张量并行通信优化方向延伸阅读。

## 精读区
1. [Measuring and Reducing WebGPU Dispatch Overhead for LLM Inference](/202608/11/2608.08730v1-measuring-and-reducing-webgpu-dispatch-overhead-for-llm-inference) （9.0/10）
2. [UnionSparse: An Index-Efficient Sparsity Framework for Low-Bit Sparse LLM Inference on Edge](/202608/11/2608.09291v1-unionsparse-an-index-efficient-sparsity-framework-for-low-bit-sparse-llm-inference-on-edge) （9.0/10）
3. [RotaryQuant: Fitting 120B MoE Models on Consumer Hardware via Fused Compressed-Space Attention](/202608/11/2608.08081v1-rotaryquant-fitting-120b-moe-models-on-consumer-hardware-via-fused-compressed-space-attention) （8.0/10）
4. [OasisKV: Scaling In-Decode KV Cache Beyond HBM with Lookahead Sparse Prefetching](/202608/11/2608.08097v1-oasiskv-scaling-in-decode-kv-cache-beyond-hbm-with-lookahead-sparse-prefetching) （8.0/10）
5. [LLMVisor: A Real-Time Latency Attribution Model for Multi-Tenant LLM Serving](/202608/11/2608.08382v1-llmvisor-a-real-time-latency-attribution-model-for-multi-tenant-llm-serving) （8.0/10）

## 速读区
1. [SwiftQK: Fast and Communication-Efficient Tensor Parallelism for Query-Key Normalization](/202608/11/2608.09160v1-swiftqk-fast-and-communication-efficient-tensor-parallelism-for-query-key-normalization) （7.0/10）
2. [LiveMem: Maintaining Memory State Continuity in Long-Running LLM Inference](/202608/11/2608.02515v2-livemem-maintaining-memory-state-continuity-in-long-running-llm-inference) （6.0/10）
3. [DistillCache: KL-Guided Adaptive KV-Cache Eviction for Memory-Efficient LLM Inference](/202608/11/2608.08878v1-distillcache-kl-guided-adaptive-kv-cache-eviction-for-memory-efficient-llm-inference) （6.0/10）
4. [Depth-adaptive Inference of Looped Language Models via Continuous Depth Batching](/202608/11/2608.09444v1-depth-adaptive-inference-of-looped-language-models-via-continuous-depth-batching) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
