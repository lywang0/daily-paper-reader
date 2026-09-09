<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-09
- 运行时间：2026-09-09 22:07:49 UTC
- 运行状态：成功
- 本次总论文数：14
- 精读区：6
- 速读区：8

### 今日简报（AI）
今日14篇论文聚焦大模型推理效率，精读6篇重点围绕KV缓存量化与调度。最值得关注两项高分工作：面向NVM的接口感知KV量化，以及统一模型路由与缓存管理的AI网关框架。建议下一步深入对比MetaKV等压缩方案，评估不同长上下文场景下的精度与成本权衡。
- 详情：[/202609/09/README](/202609/09/README)

### 精读区论文标签
1. [Interface-Aware KV Cache Quantization for Dense On-Chip NVM in Long-Context LLM Decoding](/202609/09/2609.05764v1-interface-aware-kv-cache-quantization-for-dense-on-chip-nvm-in-long-context-llm-decoding)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向片上NVM接口设计KV量化方案，是大语言模型基础设施的软硬协同方法
2. [Unified AI Gateway: A Framework for Joint Model Routing and KV Cache Management](/202609/09/2609.06940v1-unified-ai-gateway-a-framework-for-joint-model-routing-and-kv-cache-management)  
   标签：评分：9.0/10、query:edge-llm
   evidence：提出边缘部署的LLM统一网关，联合模型路由、KV缓存与执行位置调度。
3. [Hardware-Aware FP4 FlashAttention-4](/202609/09/2609.04105v1-hardware-aware-fp4-flashattention-4)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向LLM推理的硬件感知FP4注意力算子加速
4. [Toward Sustainable Distributed LLM Inference: A Systems Synthesis and Research Agenda for an Energy-, Carbon-, and Cache-Aware llm-d Control Plane](/202609/09/2609.05565v1-toward-sustainable-distributed-llm-inference-a-systems-synthesis-and-research-agenda-for-an-energy--carbon--and-cache-aware-llm-d-control-plane)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向分布式大模型推理控制平面的系统综述与研究议程，聚焦服务系统的能效与缓存效率
5. [All for 1-Bit: Towards Genuine 1-Bit Post-Training Quantization for LLMs](/202609/09/2609.06161v1-all-for-1-bit-towards-genuine-1-bit-post-training-quantization-for-llms)  
   标签：评分：8.0/10、query:edge-llm
   evidence：真正1比特后训练量化大幅降低存储与内存带宽开销，是资源受限边缘LLM部署的核心支撑技术。
6. [AutoUVM: Automated Prefetching Framework for LLMs under UVM Oversubscription](/202609/09/2609.06172v1-autouvm-automated-prefetching-framework-for-llms-under-uvm-oversubscription)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向LLM GPU内存超订的UVM自动预取框架，优化页迁移与CPU-GPU数据传输。

### 速读区论文标签
1. [Accuracy is Not Enough: A Divergence-Based Approach to Evaluate Fidelity Loss in Quantized LLMs](/202609/09/2609.07664v1-accuracy-is-not-enough-a-divergence-based-approach-to-evaluate-fidelity-loss-in-quantized-llms)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向内存受限边缘设备量化LLM部署的保真度评估方法
2. [Deadline-Aware Adaptive Prefill Chunking for Efficient Large Language Model Serving](/202609/09/2609.07883v1-deadline-aware-adaptive-prefill-chunking-for-efficient-large-language-model-serving)  
   标签：评分：8.0/10、query:edge-llm
   evidence：截止时间感知的自适应预填充分块调度方法，直接面向连续批处理的LLM服务效率与时延目标。
3. [MetaKV: Adaptive KV Cache Compression for Constrained LLM Inference](/202609/09/2609.07966v1-metakv-adaptive-kv-cache-compression-for-constrained-llm-inference)  
   标签：评分：8.0/10、query:edge-llm
   evidence：基于用户指定延迟与峰值内存预算选择KV压缩配置，面向受资源约束的推理场景
4. [A Measurement Study of LLM Inference Trade-offs Across Edge Continuum Hardware](/202609/09/2609.08307v1-a-measurement-study-of-llm-inference-trade-offs-across-edge-continuum-hardware)  
   标签：评分：8.0/10、query:edge-llm
   evidence：对Jetson等边缘设备上的LLM延迟、能耗与模型体积进行受控测量。
5. [Signed Rescue Routing: Harm-Aware Cascades for Efficient LLM Inference](/202609/09/2609.07786v1-signed-rescue-routing-harm-aware-cascades-for-efficient-llm-inference)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向高效LLM推理的有预算小-大模型路由方法，可集成到服务系统
6. [Do Dynamic Routers Need Memory? HeRo: History-Aware Routing for Efficient LLM Inference](/202609/09/2609.08189v1-do-dynamic-routers-need-memory-hero-history-aware-routing-for-efficient-llm-inference)  
   标签：评分：7.0/10、query:edge-llm
   evidence：通过历史感知动态层路由减少LLM推理开销，可提升资源受限端的推理效率。
7. [Train Overcomplete, Deploy Compact: Scaling Recovery Capacity for Structured LLM Pruning](/202609/09/2609.06974v1-train-overcomplete-deploy-compact-scaling-recovery-capacity-for-structured-llm-pruning)  
   标签：评分：6.0/10、query:edge-llm
   evidence：通过结构化剪枝与过参数化恢复降低LLM部署资源开销
8. [FastE: Readout-Triggered Token Compression for LLM Embedding Inference](/202609/09/2609.08407v1-faste-readout-triggered-token-compression-for-llm-embedding-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向LLM嵌入模型的无训练令牌压缩，显著降低推理计算负担，适合移植到资源受限的边缘场景


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
