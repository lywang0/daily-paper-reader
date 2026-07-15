<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-15
- 运行时间：2026-07-15 21:34:31 UTC
- 运行状态：成功
- 本次总论文数：9
- 精读区：4
- 速读区：5

### 今日简报（AI）
今日聚焦边缘和消费设备上的LLM推理优化，精读两篇高分论文：HeteroMosaic通过异构执行机会提升端侧能效（10分），Automated Tensor Scheduling实现消费级CPU-GPU混合推理（8分）。最值得关注方向为异构计算与自动化调度，建议优先阅读这两篇论文，了解如何在不牺牲性能的前提下降低功耗。下一步可关注速读列表中SiFAR的低延迟同步方案和N:M稀疏Transformer的实用化设计。
- 详情：[/202607/15/README](/202607/15/README)

### 精读区论文标签
1. [HeteroMosaic: Exposing and Exploiting Heterogeneous Execution Opportunities for Energy-Efficient Edge LLM Inference](/202607/15/2607.12839v1-heteromosaic-exposing-and-exploiting-heterogeneous-execution-opportunities-for-energy-efficient-edge-llm-inference)  
   标签：评分：10.0/10、query:edge-llm
   evidence：面向边缘LLM推理的异构调度框架，结合iGPU和NPU
2. [Automated Tensor Scheduling for Hybrid CPU-GPU LLM Inference on Consumer Devices](/202607/15/2607.10183v2-automated-tensor-scheduling-for-hybrid-cpu-gpu-llm-inference-on-consumer-devices)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向消费设备的CPU-GPU混合LLM推理自动张量调度
3. [IRONSmith: A Visual Dataflow Design Environment for AMD Ryzen AI NPUs](/202607/15/2607.10944v1-ironsmith-a-visual-dataflow-design-environment-for-amd-ryzen-ai-npus)  
   标签：评分：8.0/10、query:edge-llm
   evidence：NPU可视化数据流设计环境支持软硬件协同设计
4. [HCRMap: Pressure-Aware Hot-Expert Residency Mapping for 3.5D MoE Chiplet Inference](/202607/15/2607.11586v1-hcrmap-pressure-aware-hot-expert-residency-mapping-for-35d-moe-chiplet-inference)  
   标签：评分：8.0/10、query:edge-llm
   evidence：3.5D多芯片系统上MoE LLM推理的软硬协同设计

### 速读区论文标签
1. [SiFAR: Synchronization-Free All-Reduce for Low-Latency LLM Inference](/202607/15/2607.08973v1-sifar-synchronization-free-all-reduce-for-low-latency-llm-inference)  
   标签：评分：7.0/10、query:edge-llm
   evidence：无同步全归约实现低延迟LLM推理
2. [Realizable N:M Sparse Transformer Inference via Search-Kernel Co-Design](/202607/15/2607.12505v1-realizable-nm-sparse-transformer-inference-via-search-kernel-co-design)  
   标签：评分：7.0/10、query:edge-llm
   evidence：N:M稀疏ViT推理的软硬协同设计，含自定义CUDA内核
3. [[AAFLOW+] Stateful Operator Abstraction with Zero-Copy Distributed KV Cache Orchestration for Multi-Agent Workflows](/202607/15/2607.10987v1-aaflow-stateful-operator-abstraction-with-zero-copy-distributed-kv-cache-orchestration-for-multi-agent-workflows)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向多智能体工作流的状态化算子抽象与零拷贝分布式KV缓存编排
4. [Extending LLM Context via Associative Recurrent Memory](/202607/15/2607.11614v1-extending-llm-context-via-associative-recurrent-memory)  
   标签：评分：6.0/10、query:edge-llm
   evidence：常量内存缩放使边缘设备支持更长上下文
5. [Transforming LLMs into Efficient Cross-Encoders via Knowledge Distillation for RAG Reranking](/202607/15/2607.11933v1-transforming-llms-into-efficient-cross-encoders-via-knowledge-distillation-for-rag-reranking)  
   标签：评分：6.0/10、query:edge-llm
   evidence：知识蒸馏和量化减小LLM大小以实现高效推理


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
