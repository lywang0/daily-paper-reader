<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-18
- 运行时间：2026-08-18 21:04:41 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：7
- 速读区：10

### 今日简报（AI）
今日聚焦边缘设备端MoE推理优化，共17篇论文，精读7篇、速读10篇。  
最值得看的是两篇满分工作：S2-MoE实现高效自推测解码，FreeToken提出带宽自适应执行机制。  
建议优先精读这两篇，并速读ExactMoE的W4A16内存优化与EcoVLA的实时能耗协同方案。
- 详情：[/202608/18/README](/202608/18/README)

### 精读区论文标签
1. [S2-MoE: Enabling Efficient Self-Speculative Decoding for Mixture-of-Experts on Edge Devices](/202608/18/2608.15018v1-s2-moe-enabling-efficient-self-speculative-decoding-for-mixture-of-experts-on-edge-devices)  
   标签：评分：10.0/10、query:edge-llm
   evidence：面向边缘设备MoE推理的高效自推测解码，解决内存与带宽约束
2. [FreeToken: Efficient Edge-Native MoE Serving with Bandwidth-Adaptive Execution](/202608/18/2608.16157v1-freetoken-efficient-edge-native-moe-serving-with-bandwidth-adaptive-execution)  
   标签：评分：10.0/10、query:edge-llm
   evidence：边缘原生MoE服务系统，协同设计模型布局、专家驻留、CPU-GPU执行与内存管理
3. [P-PAS: Prefill-Pressure Adaptive Scheduling for Long-Context LLM Serving](/202608/18/2608.15171v1-p-pas-prefill-pressure-adaptive-scheduling-for-long-context-llm-serving)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向长上下文LLM服务的自适应调度策略，基于预填充压力调整调度预算
4. [FluxBin: Flexible LUT-based Ultra-low-bit LLM Inference by Algorithm-Kernel Synergy](/202608/18/2608.15602v1-fluxbin-flexible-lut-based-ultra-low-bit-llm-inference-by-algorithm-kernel-synergy)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向超低比特LLM推理的算法-内核协同设计，结合LUT与CUDA内核
5. [Large Models for Small Devices: Recent Advances and Empirical Analysis of Edge AI Deployment](/202608/18/2608.15693v1-large-models-for-small-devices-recent-advances-and-empirical-analysis-of-edge-ai-deployment)  
   标签：评分：9.0/10、query:edge-llm
   evidence：在树莓派等边缘平台上实证部署压缩后的语言与图像模型
6. [Beyond Binary Priorities: Multi-Tier SLA Scheduling for Large Language Model Serving](/202608/18/2608.16336v1-beyond-binary-priorities-multi-tier-sla-scheduling-for-large-language-model-serving)  
   标签：评分：9.0/10、query:edge-llm
   evidence：直接面向大语言模型服务框架，扩展Llumnix调度器以支持多优先级SLA分级调度。
7. [Pallas: A Proactive KV Cache Migration Framework for LLM Inference in AI-RAN](/202608/18/2608.16477v1-pallas-a-proactive-kv-cache-migration-framework-for-llm-inference-in-ai-ran)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向AI-RAN边缘场景的LLM推理KV缓存主动迁移框架，提升服务连续性与时延表现

### 速读区论文标签
1. [LOCAL: Enabling Learning On-device Contiguously for Agent LLMs](/202608/18/2608.15241v1-local-enabling-learning-on-device-contiguously-for-agent-llms)  
   标签：评分：8.0/10、query:edge-llm
   evidence：设备端单GPU运行时，管理适配器与KV缓存
2. [Every Expert Counts: ExactMoE for Memory-Efficient W4A16 Inference](/202608/18/2608.15383v1-every-expert-counts-exactmoe-for-memory-efficient-w4a16-inference)  
   标签：评分：8.0/10、query:edge-llm
   evidence：通过4比特量化、MARLIN内核和GPU缓存实现W4A16 MoE推理的内存高效硬件感知推理
3. [EcoVLA: Energy-Efficient Device-Edge Co-Inference for Vision-Language-Action Models under Real-Time Constraints](/202608/18/2608.15502v1-ecovla-energy-efficient-device-edge-co-inference-for-vision-language-action-models-under-real-time-constraints)  
   标签：评分：8.0/10、query:edge-llm
   evidence：设备-边缘协同推理框架，实现能效优化的边缘模型部署
4. [FlashQuant: Sparse-Dense Fusion for Memory-Efficient Outlier-Aware LLM Inference](/202608/18/2608.15531v1-flashquant-sparse-dense-fusion-for-memory-efficient-outlier-aware-llm-inference)  
   标签：评分：8.0/10、query:edge-llm
   evidence：提出稀疏-稠密融合的内核实现低比特异常感知LLM推理，属于硬件感知的推理加速方法。
5. [SchurQuant: Groupwise Discrete Optimization for Layer-Wise LLM Quantization](/202608/18/2608.15567v1-schurquant-groupwise-discrete-optimization-for-layer-wise-llm-quantization)  
   标签：评分：8.0/10、query:edge-llm
   evidence：量化方法支持在资源受限设备上高效部署LLM
6. [Achieving Near-Zero-Overhead Multi-Model Hierarchical Classification in Real-Time Detection Pipelines](/202608/18/2608.11770v1-achieving-near-zero-overhead-multi-model-hierarchical-classification-in-real-time-detection-pipelines)  
   标签：评分：7.0/10、query:edge-llm
   evidence：边缘SoC上GPU与NPU/DLA并发执行，异构计算用于多模型推理
7. [From LLM Inference to Agentic Workloads: Characterization and Implications for Serving Systems](/202608/18/2608.15127v1-from-llm-inference-to-agentic-workloads-characterization-and-implications-for-serving-systems)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向智能体负载的LLM服务系统特征分析与启示
8. [When Entropy Is Not Enough: Reclaiming Lost Semantics in LLM Output Length Prediction](/202608/18/2608.15592v1-when-entropy-is-not-enough-reclaiming-lost-semantics-in-llm-output-length-prediction)  
   标签：评分：7.0/10、query:edge-llm
   evidence：通过考虑语义的输出长度预测来减少padding浪费，支撑长度感知调度，属于服务框架优化。
9. [Dynamic Multi-Byte Prediction With Hierarchical Language Models](/202608/18/2608.15454v1-dynamic-multi-byte-prediction-with-hierarchical-language-models)  
   标签：评分：6.0/10、query:edge-llm
   evidence：并行字节预测，加速LLM推理
10. [Algorithm-Architecture Co-Design for Efficient VLA Inference via Speculative Inference and Verification](/202608/18/2608.15636v1-algorithm-architecture-co-design-for-efficient-vla-inference-via-speculative-inference-and-verification)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向大模型推理的算法-架构协同设计，通过推测推理与验证提升效率


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
