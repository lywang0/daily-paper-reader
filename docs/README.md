<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-08
- 运行时间：2026-08-08 20:36:19 UTC
- 运行状态：成功
- 本次总论文数：7
- 精读区：0
- 速读区：7

### 今日简报（AI）
今日聚焦长上下文问答的隐藏状态内存压缩，速读7篇相关研究，其中3篇获7.0分。最值得关注的方向是选择性解压（SeDeM）与稀疏采样重构（S$^4$R），均旨在压缩KV缓存同时保留查询关键信息。建议普通读者先了解KV缓存量化的注意力保持变换，再深入比较这三类方法的精度与效率权衡。
- 详情：[/202608/08/README](/202608/08/README)

### 精读区论文标签
- 本次无精读推荐。

### 速读区论文标签
1. [SeDeM: Selective Decompression of Hidden-State Memories for Long-Context Question Answering](/202608/08/2608.00311v1-sedem-selective-decompression-of-hidden-state-memories-for-long-context-question-answering)  
   标签：评分：7.0/10、query:edge-llm
   evidence：通过选择性解压隐藏状态记忆，减少长上下文问答中的KV缓存与计算开销。
2. [S$^4$R: Selective Sampling, Subspaces, and Sparse Reconstruction for Compressed Long-Context KV Caching](/202608/08/2608.00528v1-s4r-selective-sampling-subspaces-and-sparse-reconstruction-for-compressed-long-context-kv-caching)  
   标签：评分：7.0/10、query:edge-llm
   evidence：基于选择性采样与稀疏重构的低秩KV缓存压缩，降低长上下文推理的内存开销，促进资源高效部署。
3. [Spend Bits Where Queries Look: KV Cache Vector Quantization with Attention-Preserving Transforms](/202608/08/2608.04074v1-spend-bits-where-queries-look-kv-cache-vector-quantization-with-attention-preserving-transforms)  
   标签：评分：7.0/10、query:edge-llm
   evidence：通过注意力保持的向量量化压缩KV缓存，降低解码带宽需求，是可用于边缘端的资源高效推理技术。
4. [TensorCast: The Missing Tensor Management Layer in Large Language Model Infrastructure](/202608/08/2608.06007v1-tensorcast-the-missing-tensor-management-layer-in-large-language-model-infrastructure)  
   标签：评分：7.0/10、query:edge-llm
   evidence：提出LLM基础设施中张量生命周期管理抽象层，解决服务框架中张量管理策略的复用与组合问题。
5. [CascadeLUT: Information-Ordered Streaming Inference for Bandwidth-Constrained FPGAs](/202608/08/2608.00720v1-cascadelut-information-ordered-streaming-inference-for-bandwidth-constrained-fpgas)  
   标签：评分：6.0/10、query:edge-llm
   evidence：提出面向带宽受限FPGA的信息有序流式推理，属硬件感知加速方法，可迁移至边缘推理。
6. [Design-Time Optimization of Deep Neural Networks for Intermittent Learning on Microcontrollers](/202608/08/2608.03589v1-design-time-optimization-of-deep-neural-networks-for-intermittent-learning-on-microcontrollers)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向MCU设备端DNN推理的硬件感知能量预测与多目标优化
7. [LLM Inference Under Bursty Workload Distribution: Modifying the WAIT Algorithm](/202608/08/2608.06135v1-llm-inference-under-bursty-workload-distribution-modifying-the-wait-algorithm)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向突发流量的LLM服务调度算法扩展，优化吞吐与延迟


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
