<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-23
- 运行时间：2026-09-23 22:31:34 UTC
- 运行状态：成功
- 本次总论文数：10
- 精读区：1
- 速读区：9

### 今日简报（AI）
今日精读1篇、速读9篇，重点落在 Agentic LLM 服务的资源调度与长上下文推理优化。最值得看的是 SARA 提出的 SLO 感知资源分配（8.0分），以及速读中长上下文解码、HBM 与高带宽闪存分层、扩散 LLM 的 KV 缓存与并行解码三个方向。普通读者可优先从 SARA 入手，理解服务质量约束下如何分配算力与存储。
- 详情：[/202609/23/README](/202609/23/README)

### 精读区论文标签
1. [SARA: SLO-Aware Resource Allocation for Disaggregated Agentic LLM Services](/202609/23/2609.26763v1-sara-slo-aware-resource-allocation-for-disaggregated-agentic-llm-services)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向云边LLM服务的SLO感知资源分配与调度

### 速读区论文标签
1. [Elastic Threshold Attention: Learned Contextual Sparsity for Long-Context Decoding](/202609/23/2609.20888v1-elastic-threshold-attention-learned-contextual-sparsity-for-long-context-decoding)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向硬件的稀疏注意力加速解码
2. [Hot-Cold Tiering of HBM and High Bandwidth Flash for Agentic LLM Serving](/202609/23/2609.25782v1-hot-cold-tiering-of-hbm-and-high-bandwidth-flash-for-agentic-llm-serving)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向LLM服务的KV缓存硬件内存分层
3. [Flash-dLLM: IO-Aware KV Caching and Parallel Decoding for Fast, Memory-Efficient Diffusion LLMs](/202609/23/2609.26796v1-flash-dllm-io-aware-kv-caching-and-parallel-decoding-for-fast-memory-efficient-diffusion-llms)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向快速内存高效推理的IO感知KV缓存与并行解码
4. [Accelerating Dense LLMs via L0-regularized Mixture-of-Experts](/202609/23/2609.21672v1-accelerating-dense-llms-via-l0-regularized-mixture-of-experts)  
   标签：评分：6.0/10、query:edge-llm
   evidence：L0正则轻量MoE加速稠密LLM推理
5. [KerColle: Unlocking Fine-Grained GPU Concurrency in Vision-Language-Action Models](/202609/23/2609.22335v1-kercolle-unlocking-fine-grained-gpu-concurrency-in-vision-language-action-models)  
   标签：评分：6.0/10、query:edge-llm
   evidence：GPU线程块调度器阻塞限制推理吞吐
6. [Analytical Power-Aware Provisioning for Prefill-Decode Disaggregated AI Inference](/202609/23/2609.24639v1-analytical-power-aware-provisioning-for-prefill-decode-disaggregated-ai-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向PD分离LLM服务的功耗感知配置
7. [Compressing Long Context into Answer-Aligned Memory Embeddings for LLM Inference](/202609/23/2609.25537v1-compressing-long-context-into-answer-aligned-memory-embeddings-for-llm-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：将长上下文压缩为记忆嵌入以降低LLM推理开销
8. [Accelerating the Mitigation of LLM Inference Nondeterminism Across GPU Architectures](/202609/23/2609.25624v1-accelerating-the-mitigation-of-llm-inference-nondeterminism-across-gpu-architectures)  
   标签：评分：6.0/10、query:edge-llm
   evidence：针对不同GPU架构选择GEMM内核以加速LLM推理
9. [Disaggregated Quantization: Specializing LLM Prefill and Decode](/202609/23/2609.26333v1-disaggregated-quantization-specializing-llm-prefill-and-decode)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向LLM预填充与解码的量化特化，降低访存并加速推理


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
