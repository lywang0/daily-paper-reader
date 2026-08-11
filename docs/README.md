<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-11
- 运行时间：2026-08-11 21:19:37 UTC
- 运行状态：成功
- 本次总论文数：9
- 精读区：5
- 速读区：4

### 今日简报（AI）
今日共处理9篇论文，精读5篇、速读4篇，核心聚焦大模型推理的效率优化。

最值得关注的两项高分研究分别针对WebGPU调度开销与低比特稀疏推理框架，均获9.0/10评分。

建议普通读者优先了解KV-Cache与内存管理相关速读文章，在此基础上可快速把握推理性能瓶颈。
- 详情：[/202608/11/README](/202608/11/README)

### 精读区论文标签
1. [Measuring and Reducing WebGPU Dispatch Overhead for LLM Inference](/202608/11/2608.08730v1-measuring-and-reducing-webgpu-dispatch-overhead-for-llm-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：测量并降低浏览器与边缘设备上LLM推理的WebGPU调度开销
2. [UnionSparse: An Index-Efficient Sparsity Framework for Low-Bit Sparse LLM Inference on Edge](/202608/11/2608.09291v1-unionsparse-an-index-efficient-sparsity-framework-for-low-bit-sparse-llm-inference-on-edge)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向边缘低比特稀疏LLM推理的索引高效稀疏性框架
3. [RotaryQuant: Fitting 120B MoE Models on Consumer Hardware via Fused Compressed-Space Attention](/202608/11/2608.08081v1-rotaryquant-fitting-120b-moe-models-on-consumer-hardware-via-fused-compressed-space-attention)  
   标签：评分：8.0/10、query:edge-llm
   evidence：通过混合精度量化与存储外置实现消费级硬件上的资源高效MoE LLM推理
4. [OasisKV: Scaling In-Decode KV Cache Beyond HBM with Lookahead Sparse Prefetching](/202608/11/2608.08097v1-oasiskv-scaling-in-decode-kv-cache-beyond-hbm-with-lookahead-sparse-prefetching)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向HBM容量瓶颈的KV缓存系统设计，体现硬件感知的内存管理
5. [LLMVisor: A Real-Time Latency Attribution Model for Multi-Tenant LLM Serving](/202608/11/2608.08382v1-llmvisor-a-real-time-latency-attribution-model-for-multi-tenant-llm-serving)  
   标签：评分：8.0/10、query:edge-llm
   evidence：用于多租户LLM服务调度的实时延迟归属

### 速读区论文标签
1. [SwiftQK: Fast and Communication-Efficient Tensor Parallelism for Query-Key Normalization](/202608/11/2608.09160v1-swiftqk-fast-and-communication-efficient-tensor-parallelism-for-query-key-normalization)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向QK-Norm的多GPU低通信算子内核，属于硬件感知的LLM推理加速
2. [LiveMem: Maintaining Memory State Continuity in Long-Running LLM Inference](/202608/11/2608.02515v2-livemem-maintaining-memory-state-continuity-in-long-running-llm-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：用有界KV窗口和内在记忆实现资源高效的长时间LLM推理
3. [DistillCache: KL-Guided Adaptive KV-Cache Eviction for Memory-Efficient LLM Inference](/202608/11/2608.08878v1-distillcache-kl-guided-adaptive-kv-cache-eviction-for-memory-efficient-llm-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：通过强化学习进行KV缓存驱逐以节省内存，适用于资源受限推理
4. [Depth-adaptive Inference of Looped Language Models via Continuous Depth Batching](/202608/11/2608.09444v1-depth-adaptive-inference-of-looped-language-models-via-continuous-depth-batching)  
   标签：评分：6.0/10、query:edge-llm
   evidence：通过连续深度批处理调度变深度推理，提升回环语言模型推理效率


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
