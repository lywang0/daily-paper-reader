<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-03
- 运行时间：2026-09-03 23:08:11 UTC
- 运行状态：成功
- 本次总论文数：18
- 精读区：7
- 速读区：11

### 今日简报（AI）
今日聚焦端侧与多任务场景，精读18篇中2篇满分论文，分别涉及块扩散LLM硬件加速与设备端内存管理。最值得关注的方向是边缘设备上的推理加速与内存复用，建议优先阅读《Hardware Acceleration of Block-Diffusion LLM》和《mzCache》两篇满分工作。下一步可结合速读中的量化与KV复用方法，在单GPU或低资源环境下验证组合效果。
- 详情：[/202609/03/README](/202609/03/README)

### 精读区论文标签
1. [Hardware Acceleration of Block-Diffusion LLM for Edge Devices](/202609/03/2609.01084v1-hardware-acceleration-of-block-diffusion-llm-for-edge-devices)  
   标签：评分：10.0/10、query:edge-llm
   evidence：面向边缘块扩散LLM的软硬协同加速器设计
2. [mzCache: On-Device LLM Memory Management under Multitasking](/202609/03/2609.01338v1-mzcache-on-device-llm-memory-management-under-multitasking)  
   标签：评分：10.0/10、query:edge-llm
   evidence：多任务移动端LLM推理的内存管理
3. [Pro-Router: Token-Aware Progressive Model Routing with Adaptive Edge-Cloud Collaboration for Efficient Multimodal LLM Inference](/202609/03/2608.28726v1-pro-router-token-aware-progressive-model-routing-with-adaptive-edge-cloud-collaboration-for-efficient-multimodal-llm-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：利用token感知渐进路由与自适应边云协作优化边缘端多模态LLM推理
4. [Multi-Access Speculative Inference: Uplink or Downlink?](/202609/03/2608.29618v1-multi-access-speculative-inference-uplink-or-downlink)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向多设备边缘网络，用设备端小模型草稿与边缘大模型并行验证来加速生成，直接优化边缘LLM高效推理
5. [CHIPSMORE: Compute-in-Interconnect and -Memory Chiplets for Multi-Mode Multi-Request LLM Inference Acceleration](/202609/03/2608.30509v1-chipsmore-compute-in-interconnect-and--memory-chiplets-for-multi-mode-multi-request-llm-inference-acceleration)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向LLM推理的多模式多请求硬件加速器，集成互连内计算与存内计算及异构处理单元，直接体现大模型软硬协同设计
6. [LLM Inference on IMC-NoC Architecture with Balanced Dataflow and Fine-Grained Parallelism](/202609/03/2609.00857v1-llm-inference-on-imc-noc-architecture-with-balanced-dataflow-and-fine-grained-parallelism)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向LLM推理的软硬件协同设计，统一分布式计算、存储与通信并构建可扩展IMC-NoC架构
7. [AceSpec: An Asymmetric Edge-Cloud Collaborative Framework for Communication-Efficient LLM Inference](/202609/03/2609.02514v1-acespec-an-asymmetric-edge-cloud-collaborative-framework-for-communication-efficient-llm-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：非对称端云投机解码框架，在波动广域网上提升LLM推理的通信效率与稳定性

### 速读区论文标签
1. [Budget-Aware Compression Pipeline for Single-GPU LLM Inference: Methods, Trade-offs, and Coupling Effects](/202609/03/2608.30076v1-budget-aware-compression-pipeline-for-single-gpu-llm-inference-methods-trade-offs-and-coupling-effects)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向单GPU的预算感知压缩流水线，系统考察剪枝、量化与KV缓存压缩的执行耦合效果
2. [A Universal Context-Reuse Layer for Cross-Model KV Sharing](/202609/03/2608.30963v1-a-universal-context-reuse-layer-for-cross-model-kv-sharing)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向LLM服务框架的跨模型KV共享
3. [REAL-Q: E2E LLM Quantization via Dynamic Gradient Descent](/202609/03/2609.00049v1-real-q-e2e-llm-quantization-via-dynamic-gradient-descent)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向严格资源约束下LLM部署的端到端对齐后训练量化方法，直接提升资源受限场景的推理效率
4. [Faster Than Flash: Exploiting Attention Sparsity for Efficient Long-Context Decoding](/202609/03/2609.00097v1-faster-than-flash-exploiting-attention-sparsity-for-efficient-long-context-decoding)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向长上下文LLM解码的软硬件协同设计框架，融合注意力选择与计算内核并采用低比特扫描和top-delta过滤降低访存开销
5. [LaMoC: Loss-Aware Modular Compression for LLMs](/202609/03/2608.30226v1-lamoc-loss-aware-modular-compression-for-llms)  
   标签：评分：7.0/10、query:edge-llm
   evidence：融合激活统计与经验Fisher信息的损失感知模块压缩，在保持下游精度的同时大幅压缩LLM参数量，有助于内存受限设备部署
6. [Event-Driven Language Models with Sparse Neural Activity for Neuromorphic Hardware](/202609/03/2608.30439v1-event-driven-language-models-with-sparse-neural-activity-for-neuromorphic-hardware)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向神经形态多核多芯片平台，在量化线性注意力语言模型中诱导稀疏神经活动并减少有效运算，属于端侧硬件感知加速
7. [Triple-Bottom-Line Sustainability of Language Models for Edge AI: A Comparison Between SLMs and Quantized LLMs](/202609/03/2609.00665v1-triple-bottom-line-sustainability-of-language-models-for-edge-ai-a-comparison-between-slms-and-quantized-llms)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向边缘部署综合比较小语言模型与量化大语言模型在能力、效率、能耗和安全上的表现
8. [OUTLETS: Output-Length Prediction from Speculative Decoding Backbones](/202609/03/2609.01068v1-outlets-output-length-prediction-from-speculative-decoding-backbones)  
   标签：评分：7.0/10、query:edge-llm
   evidence：针对LLM服务的资源调配问题，利用投机解码隐特征预测输出长度
9. [A rigor-matched audit of periodic-step layer skipping for efficient llm inference: conflayers versus swift, with a supplemental analysis of trained routing alternatives](/202609/03/2608.28846v1-a-rigor-matched-audit-of-periodic-step-layer-skipping-for-efficient-llm-inference-conflayers-versus-swift-with-a-supplemental-analysis-of-trained-routing-alternatives)  
   标签：评分：6.0/10、query:edge-llm
   evidence：针对高效LLM推理的跳层与自投机解码方法的多模型对比研究
10. [SemKV: Semantic Mixed-Precision KV Cache Quantization Guided by the Quality Cliff for Long-Context LLM Inference](/202609/03/2608.28911v1-semkv-semantic-mixed-precision-kv-cache-quantization-guided-by-the-quality-cliff-for-long-context-llm-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：利用质量悬崖引导语义混合精度量化压缩KV缓存，缓解长上下文推理内存瓶颈
11. [A Target-Centric Survey of Quantization-Aware Training](/202609/03/2608.29667v1-a-target-centric-survey-of-quantization-aware-training)  
   标签：评分：6.0/10、query:edge-llm
   evidence：系统梳理量化感知训练，通过低比特模型降低LLM内存与计算开销，是资源受限设备上高效推理的支撑技术


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
