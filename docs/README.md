<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-16
- 运行时间：2026-09-16 21:55:37 UTC
- 运行状态：成功
- 本次总论文数：7
- 精读区：1
- 速读区：6

### 今日简报（AI）
今日筛选7篇LLM推理与边缘部署论文，AMD gfx90a上的DeepSeek-V4-Flash正确性恢复与推理性能工程以8.0分领跑精读。  
最值得先看这条DeepSeek-V4-Flash的性能工程结论，其次关注LayerRoute用自适应层跳过加LoRA保质量提效LLM推理。  
普通读者可先读精读篇的方法与复现要点，再按需扫LayerRoute、BIO-MEMART和MANE中的KV缓存与边缘卸载思路。
- 详情：[/202609/16/README](/202609/16/README)

### 精读区论文标签
1. [DeepSeek-V4-Flash on AMD gfx90a: Correctness Recovery and Inference Performance Engineering](/202609/16/2609.15627v1-deepseek-v4-flash-on-amd-gfx90a-correctness-recovery-and-inference-performance-engineering)  
   标签：评分：8.0/10、query:edge-llm
   evidence：AMD GPU上FP4/FP8与并行的硬件感知推理性能工程

### 速读区论文标签
1. [LayerRoute: Adaptive Layer-Skipping with LoRA-Preserved Quality for Efficient LLM Inference](/202609/16/2609.13682v1-layerroute-adaptive-layer-skipping-with-lora-preserved-quality-for-efficient-llm-inference)  
   标签：评分：7.0/10、query:edge-llm
   evidence：自适应跳层实现高效LLM推理
2. [BIO-MEMART: Biometric-Aware KV Cache Memory for Multi-User LLM Agents](/202609/16/2609.08566v1-bio-memart-biometric-aware-kv-cache-memory-for-multi-user-llm-agents)  
   标签：评分：6.0/10、query:edge-llm
   evidence：多用户LLM代理的KV缓存服务优化
3. [MANE: A Multi-Path Adaptive Network for Edge Onloading of Deep Neural Networks](/202609/16/2609.14660v1-mane-a-multi-path-adaptive-network-for-edge-onloading-of-deep-neural-networks)  
   标签：评分：6.0/10、query:edge-llm
   evidence：边缘卸载与共享推理资源管理以保障时延SLO
4. [SpliTEE: Improving LLM Inference on Trusted Hardware with Differentially Private GPU Outsourcing](/202609/16/2609.15039v1-splitee-improving-llm-inference-on-trusted-hardware-with-differentially-private-gpu-outsourcing)  
   标签：评分：6.0/10、query:edge-llm
   evidence：在CPU可信执行环境与不可信GPU间拆分LLM推理
5. [A 25-$μ$s/inf Event-driven Graph Neural Network Processor with Spatiotemporal Caching and Spline Convolution for Ultra-low-latency AI at the Edge](/202609/16/2609.15241v1-a-25-sinf-event-driven-graph-neural-network-processor-with-spatiotemporal-caching-and-spline-convolution-for-ultra-low-latency-ai-at-the-edge)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向边缘超低延迟AI的算法-硬件协同设计加速器
6. [Dynamic Semantic Compression for Efficient Latent-Space Inference in Large Language Models](/202609/16/2609.15338v1-dynamic-semantic-compression-for-efficient-latent-space-inference-in-large-language-models)  
   标签：评分：6.0/10、query:edge-llm
   evidence：通过段级潜在空间推理降低LLM内存与计算开销


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
