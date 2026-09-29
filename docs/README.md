<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-29
- 运行时间：2026-09-29 23:23:49 UTC
- 运行状态：成功
- 本次总论文数：16
- 精读区：5
- 速读区：11

### 今日简报（AI）
2026-09-29 日报完成16篇论文筛选：精读5篇、速读11篇，主线落在NPU与LLM推理服务优化。  
最值得看的是两项10分精读——NPU混合注意力模型加速，以及移动NPU上用KV Cache复用提升LLM服务效率；速读中KV Cache内存墙、多模态分拆服务与边缘模型并行也值得扫一眼。  
普通读者建议先抓“KV Cache复用/内存墙”和“移动NPU推理”两条线，再回看满分精读的机制与实验。
- 详情：[/202609/29/README](/202609/29/README)

### 精读区论文标签
1. [Empowering Hybrid Attention Models on NPUs](/202609/29/2609.32114v1-empowering-hybrid-attention-models-on-npus)  
   标签：评分：10.0/10、query:edge-llm
   evidence：通过数据流重组在边缘NPU上实现高效混合注意力LLM推理
2. [Dynamic Flow, Static Graph: KV Cache Reuse for Efficient LLM Serving on Mobile NPUs](/202609/29/2609.34727v1-dynamic-flow-static-graph-kv-cache-reuse-for-efficient-llm-serving-on-mobile-npus)  
   标签：评分：10.0/10、query:edge-llm
   evidence：面向移动NPU的LLM服务KV缓存复用
3. [SPIMOE: Exploiting Hybrid Sparsity for Reasoning MoE Inference on Heterogeneous PIM Architectures](/202609/29/2609.34612v1-spimoe-exploiting-hybrid-sparsity-for-reasoning-moe-inference-on-heterogeneous-pim-architectures)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向高效MoE推理的异构计算协同设计
4. [OmniTide: Co-Designing Algorithms and Systems for Efficient On-Device Omni-LLM Streaming](/202609/29/2609.34653v1-omnitide-co-designing-algorithms-and-systems-for-efficient-on-device-omni-llm-streaming)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向端侧LLM推理的算法-系统协同设计
5. [EdgeVLN: Runtime-Aware Deployment Ready Quantized Vision Language Navigation Model](/202609/29/2609.35570v1-edgevln-runtime-aware-deployment-ready-quantized-vision-language-navigation-model)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向内存受限边缘设备的可部署量化VLN

### 速读区论文标签
1. [The KV Cache Is the New Memory Wall](/202609/29/2609.30854v1-the-kv-cache-is-the-new-memory-wall)  
   标签：评分：7.0/10、query:edge-llm
   evidence：以硬件拓扑参数化KV缓存内存带宽墙的解析化综述
2. [Predictive Rolling-Horizon Optimization for Commitment-Aware Model-Parallel Inference under Spatio-Temporal Edge Dynamics](/202609/29/2609.31018v1-predictive-rolling-horizon-optimization-for-commitment-aware-model-parallel-inference-under-spatio-temporal-edge-dynamics)  
   标签：评分：7.0/10、query:edge-llm
   evidence：边缘上承诺感知的模型并行推理调度
3. [EAServe: Encode-Aware Disaggregated Serving for Multimodal Large Language Models](/202609/29/2609.31551v1-easerve-encode-aware-disaggregated-serving-for-multimodal-large-language-models)  
   标签：评分：7.0/10、query:edge-llm
   evidence：分离式编码-预填充-解码的LLM服务框架
4. [MpFA: Hardware-Efficient Train-Free QK4V8 FlashAttention Kernels on Blackwell GPUs](/202609/29/2609.33135v1-mpfa-hardware-efficient-train-free-qk4v8-flashattention-kernels-on-blackwell-gpus)  
   标签：评分：7.0/10、query:edge-llm
   evidence：硬件表征引导的混合精度FlashAttention内核用于LLM推理
5. [Approximating Softmax in Pretrained LLMs: Model Sensitivity and Kernel Acceleration](/202609/29/2609.33586v1-approximating-softmax-in-pretrained-llms-model-sensitivity-and-kernel-acceleration)  
   标签：评分：7.0/10、query:edge-llm
   evidence：在张量核上近似softmax以实现注意力内核加速
6. [DPS: Dual-Mode Precision LLM Serving with Semi-Unified Memory](/202609/29/2609.34380v1-dps-dual-mode-precision-llm-serving-with-semi-unified-memory)  
   标签：评分：7.0/10、query:edge-llm
   evidence：双精度LLM服务系统，权重内存弹性化
7. [Communication-Aware Model Distributed Inference via Latent Representation Compression](/202609/29/2609.30413v1-communication-aware-model-distributed-inference-via-latent-representation-compression)  
   标签：评分：6.0/10、query:edge-llm
   evidence：资源受限边缘上的分布式推理优化
8. [ActKV: Efficient LLM Agents through Action-Guided KV Cache Management](/202609/29/2609.31395v1-actkv-efficient-llm-agents-through-action-guided-kv-cache-management)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向智能体LLM服务的KV缓存压缩提升吞吐
9. [PackServe: SLO-Aware Request Scheduling for Agentic LLM Serving at Scale](/202609/29/2609.33224v1-packserve-slo-aware-request-scheduling-for-agentic-llm-serving-at-scale)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向LLM服务框架的SLO感知请求调度
10. [QuantaSpike: Short-Window Spike-Driven Quantization for Large Language Models](/202609/29/2609.34259v1-quantaspike-short-window-spike-driven-quantization-for-large-language-models)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向低能耗LLM推理的脉冲驱动量化
11. [PulseInfer: I/O-Centric Sparse KV Cache Offloading for Efficient Long-Context LLM Decoding](/202609/29/2609.34555v1-pulseinfer-io-centric-sparse-kv-cache-offloading-for-efficient-long-context-llm-decoding)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向长上下文LLM解码的KV缓存卸载系统


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
