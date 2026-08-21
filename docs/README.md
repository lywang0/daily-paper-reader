<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-21
- 运行时间：2026-08-21 20:51:34 UTC
- 运行状态：成功
- 本次总论文数：8
- 精读区：3
- 速读区：5

### 今日简报（AI）
今日论文涉及异构芯片设计与视觉语言模型加速，重点在动态负载与推理优化。  
精读推荐：HYDRA框架针对异构芯粒设计，聚类与token去噪方法提升VLM速度与鲁棒性。  
下一步可优先了解HYDRA的架构思路，并关注PTXBench以追踪GPU内核优化方向。
- 详情：[/202608/21/README](/202608/21/README)

### 精读区论文标签
1. [HYDRA: A Heterogeneous Chiplet DSE Framework for Serving Dynamic Hybrid LLM Workloads](/202608/21/2608.19395v1-hydra-a-heterogeneous-chiplet-dse-framework-for-serving-dynamic-hybrid-llm-workloads)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向混合LLM服务的异构chiplet软硬协同设计框架
2. [Clustering and Token Denoising for Faster and More Robust VLMs](/202608/21/2608.19285v1-clustering-and-token-denoising-for-faster-and-more-robust-vlms)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向端侧部署的免训练Token剪枝方法，降低VLM计算负担
3. [From Retrieved Context to Runtime Control: Adaptive Compression for Edge-based RAG](/202608/21/2608.19535v1-from-retrieved-context-to-runtime-control-adaptive-compression-for-edge-based-rag)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向边缘RAG的自适应上下文压缩，在边缘SoC上根据设备实时状态降低时延与能耗

### 速读区论文标签
1. [PTXBench: Benchmark and Adapt LLMs for GPU Kernel Optimization with Architecture-specific PTX](/202608/21/2608.17379v2-ptxbench-benchmark-and-adapt-llms-for-gpu-kernel-optimization-with-architecture-specific-ptx)  
   标签：评分：7.0/10、query:edge-llm
   evidence：评估并微调LLM生成面向H100/B200架构的PTX核，用于GEMM和注意力计算的硬件感知GPU算子优化
2. [FlashPrefill V2: Block-Sparse Prefill Attention for Long-Context LLM Serving](/202608/21/2608.19758v1-flashprefill-v2-block-sparse-prefill-attention-for-long-context-llm-serving)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向长上下文LLM服务实用化的块稀疏预填充注意力优化
3. [Nexus: Structured Synergy for Efficient Text-to-Image Generation using Rectified Flow Model](/202608/21/2608.16104v1-nexus-structured-synergy-for-efficient-text-to-image-generation-using-rectified-flow-model)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向边缘部署的生成模型效率优化，其方法可迁移到LLM推理
4. [ReCache: Efficient KV Cache Reuse and Compression for Tool-Augmented LLM Agents](/202608/21/2608.19662v1-recache-efficient-kv-cache-reuse-and-compression-for-tool-augmented-llm-agents)  
   标签：评分：6.0/10、query:edge-llm
   evidence：通过KV缓存复用与压缩降低推理资源开销
5. [Learning how to Forget: Fine-tuning for Long-Context Sparse Attention](/202608/21/2608.19920v1-learning-how-to-forget-fine-tuning-for-long-context-sparse-attention)  
   标签：评分：6.0/10、query:edge-llm
   evidence：针对长上下文LLM推理的高效稀疏注意力微调与算子内核实现，可迁移用于降低推理显存与计算开销，但并非面向边缘场景。


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
