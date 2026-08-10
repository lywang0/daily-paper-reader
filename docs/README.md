<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-10
- 运行时间：2026-08-10 21:07:13 UTC
- 运行状态：成功
- 本次总论文数：14
- 精读区：6
- 速读区：8

### 今日简报（AI）
今日聚焦 LLM 推理优化与路由，14 篇论文中精读 2 篇、速读 3 篇。最值得关注 SLO 感知的延迟预算调度（Cascade）与 NPU-PIM 双视图内存设计，均获 9.0 高分。速读可关注稀疏注意力 KV 缓存管理；建议优先精读两篇高分论文，把握推理性能与内存架构前沿。
- 详情：[/202608/10/README](/202608/10/README)

### 精读区论文标签
1. [Cascade: Exploiting SLO-Aware latency budget for fair and high goodput LLM inference serving](/202608/10/2608.06557v1-cascade-exploiting-slo-aware-latency-budget-for-fair-and-high-goodput-llm-inference-serving)  
   标签：评分：9.0/10、query:edge-llm
   evidence：利用延迟余量的SLO感知调度，提升LLM服务的公平性与有效吞吐
2. [Rethinking Unified Memory for NPU-PIM Systems: Dual-View Memory for Dynamic Inference of LLM](/202608/10/2608.06989v1-rethinking-unified-memory-for-npu-pim-systems-dual-view-memory-for-dynamic-inference-of-llm)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向NPU-PIM异构系统的双视图内存，适应LLM推理相位和MoE路由的动态张量放置
3. [Output-Aware Rotation for INT2 KV-Cache Quantization](/202608/10/2608.02691v1-output-aware-rotation-for-int2-kv-cache-quantization)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向高效LLM推理的INT2 KV缓存量化方法，用于降低内存和带宽
4. [Multi-Level Modeling of Large Language Model Inference Latency and Energy via Hybrid Analytical--Machine-Learning Predictors](/202608/10/2608.06723v1-multi-level-modeling-of-large-language-model-inference-latency-and-energy-via-hybrid-analytical--machine-learning-predictors)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向硬件感知设计的LLM推理延迟与能耗混合建模
5. [CubicQuant: Parametric Non-Uniform Codebooks for High-Throughput LLM Inference with 1-8-Bit Weights](/202608/10/2608.06763v1-cubicquant-parametric-non-uniform-codebooks-for-high-throughput-llm-inference-with-1-8-bit-weights)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向高吞吐LLM推理的量化方法，硬件感知的码本设计
6. [MiCoPro: End-to-End Mixed Precision HW/SW Co-design with HW-aware Proxy Model](/202608/10/2608.06916v1-micopro-end-to-end-mixed-precision-hwsw-co-design-with-hw-aware-proxy-model)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向边缘设备部署的端到端混合精度软硬件协同设计与硬件感知代理模型

### 速读区论文标签
1. [HiSparse: Scaling Sparse-Attention Decoding with Hierarchical KV Cache Management](/202608/10/2608.07009v1-hisparse-scaling-sparse-attention-decoding-with-hierarchical-kv-cache-management)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向稀疏注意力LLM服务的分层KV缓存管理，使长上下文解码突破GPU显存限制
2. [MACRO: Markov Chain Routing of Transformer Layers](/202608/10/2608.05872v1-macro-markov-chain-routing-of-transformer-layers)  
   标签：评分：7.0/10、query:edge-llm
   evidence：通过动态层路由和计算预算控制减少推理资源消耗
3. [LLMRouter: Unified Infrastructure for Developing, Evaluating, and Deploying LLM Routers](/202608/10/2608.06867v1-llmrouter-unified-infrastructure-for-developing-evaluating-and-deploying-llm-routers)  
   标签：评分：7.0/10、query:edge-llm
   evidence：统一的LLM路由开发与部署基础设施，用于成本高效的服务
4. [Every Cache Entry Earns Its Place: Global Allocation of Resolution and Coverage for KV Cache Compression](/202608/10/2608.07001v1-every-cache-entry-earns-its-place-global-allocation-of-resolution-and-coverage-for-kv-cache-compression)  
   标签：评分：7.0/10、query:edge-llm
   evidence：KV缓存压缩降低LLM推理内存占用，有利于资源受限端侧部署
5. [A Picture is Worth a Thousand Tokens: How Vision Language Models Cut AI Energy Costs While Improving Accuracy](/202608/10/2608.07427v1-a-picture-is-worth-a-thousand-tokens-how-vision-language-models-cut-ai-energy-costs-while-improving-accuracy)  
   标签：评分：7.0/10、query:edge-llm
   evidence：基于VLM的时序编码减少输入token和推理能耗，并在电信边缘与CloudRAN场景验证
6. [LiveMem: Maintaining Memory State Continuity in Long-Running LLM Inference](/202608/10/2608.02515v1-livemem-maintaining-memory-state-continuity-in-long-running-llm-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：通过持久内存状态与有界KV窗口降低推理内存占用
7. [Retrofitting Linear Attention into Diffusion Language Models](/202608/10/2608.06628v1-retrofitting-linear-attention-into-diffusion-language-models)  
   标签：评分：6.0/10、query:edge-llm
   evidence：线性化注意力以加速扩散LLM推理
8. [Autonomy-of-Heads: Data-Free Sparse Attention from Frozen Query-Key Geometry](/202608/10/2608.06849v1-autonomy-of-heads-data-free-sparse-attention-from-frozen-query-key-geometry)  
   标签：评分：6.0/10、query:edge-llm
   evidence：无数据稀疏注意力降低长上下文LLM推理开销，可用于高效边缘部署


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
