<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-20
- 运行时间：2026-08-20 20:03:19 UTC
- 运行状态：成功
- 本次总论文数：6
- 精读区：3
- 速读区：3

### 今日简报（AI）
今日聚焦大模型高效推理，6篇论文中精读3篇，重点覆盖MoE边缘部署与注意力加速。
最值得看两个方向：S2-MoE实现边缘设备自推测解码，FlashAttention针对可扩展向量架构优化。
建议普通读者优先关注边缘端MoE推理的能效提升，以及注意力机制在非GPU硬件上的加速思路。
- 详情：[/202608/20/README](/202608/20/README)

### 精读区论文标签
1. [S2-MoE: Enabling Efficient Self-Speculative Decoding for Mixture-of-Experts on Edge Devices](/202608/20/2608.15018v2-s2-moe-enabling-efficient-self-speculative-decoding-for-mixture-of-experts-on-edge-devices)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向边缘设备MoE推理的自推测解码，直接应对内存与带宽约束。
2. [FlashAttention for Scalable Vector Architectures](/202608/20/2608.18656v1-flashattention-for-scalable-vector-architectures)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向CPU向量架构的硬件感知FlashAttention，加速SLM推理
3. [Pre-Compiled Pipeline Shards for Distributed LLM Inference on Intel AI PC Fleets](/202608/20/2608.19147v1-pre-compiled-pipeline-shards-for-distributed-llm-inference-on-intel-ai-pc-fleets)  
   标签：评分：9.0/10、query:edge-llm
   evidence：在边缘AI PC上通过预编译OpenVINO分片实现流水线并行的LLM分布式推理

### 速读区论文标签
1. [Collective Communication for Distributed LLM Systems: Planning, Runtime Adaptation, and Computation Coordination](/202608/20/2608.15118v1-collective-communication-for-distributed-llm-systems-planning-runtime-adaptation-and-computation-coordination)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向分布式LLM系统的拓扑感知集合通信与运行时自适应
2. [Cacheable by Design? Training Mixture-of-Experts Routers for Locality Against the Edge Memory-Bandwidth Wall: A Pre-Registered Negative Result with a Systems Measurement Study](/202608/20/2608.18261v1-cacheable-by-design-training-mixture-of-experts-routers-for-locality-against-the-edge-memory-bandwidth-wall-a-pre-registered-negative-result-with-a-systems-measurement-study)  
   标签：评分：7.0/10、query:edge-llm
   evidence：针对边缘MoE服务的内存带宽墙测量研究
3. [Efficient INT8 Inference of Small NLP Models on Server CPUs with PyTorch Native Stack](/202608/20/2608.18182v1-efficient-int8-inference-of-small-nlp-models-on-server-cpus-with-pytorch-native-stack)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向CPU的NLP模型推理INT8量化与硬件感知内核优化


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
