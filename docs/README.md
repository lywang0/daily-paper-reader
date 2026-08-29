<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-29
- 运行时间：2026-08-29 03:36:59 UTC
- 运行状态：成功
- 本次总论文数：5
- 精读区：1
- 速读区：4

### 今日简报（AI）
今日聚焦长上下文LLM推理优化，精读VPP虚拟流水线并行方案，另有数据库查询与推理干预等速读。  
最值得关注VPP对分块预填充的效率提升，以及LLM在GPU数据库查询优化中的潜力。  
建议优先精读VPP论文，并关注推理阶段token效率的后续研究。
- 详情：[/202608/29/README](/202608/29/README)

### 精读区论文标签
1. [VPP: Virtual Pipeline Parallelism for Efficient Chunked Prefill in Long-Context LLM Inference](/202608/29/2608.26523v1-vpp-virtual-pipeline-parallelism-for-efficient-chunked-prefill-in-long-context-llm-inference)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向LLM服务的分块预填充流水线并行，优化流水线布局

### 速读区论文标签
1. [DataKernelBench: Can LLMs Optimize Database Queries on GPUs?](/202608/29/2608.25061v2-datakernelbench-can-llms-optimize-database-queries-on-gpus)  
   标签：评分：7.0/10、query:edge-llm
   evidence：基于LLM的CUDA/Triton内核优化基准，其方法可迁移至LLM推理算子的硬件感知加速
2. [Selective Regenerative Decoding: Trajectory-Level Intervention for Inference-Time Reasoning](/202608/29/2608.24338v1-selective-regenerative-decoding-trajectory-level-intervention-for-inference-time-reasoning)  
   标签：评分：6.0/10、query:edge-llm
   evidence：推理时解码优化减少了无效计算，是一种算法级推理效率技术。
3. [Reflection Steering: Disentangling Reflection from Reasoning in Activation Space for Token-Efficient Inference](/202608/29/2608.25542v1-reflection-steering-disentangling-reflection-from-reasoning-in-activation-space-for-token-efficient-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：通过激活引导实现令牌高效推理，降低延迟，可迁移至边缘
4. [Dependency-Aware Revocable Decoding for Efficient Diffusion Large Language Model Inference](/202608/29/2608.26574v1-dependency-aware-revocable-decoding-for-efficient-diffusion-large-language-model-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向扩散LLM的高效解码，仅对不可靠token重新计算，降低推理计算量。


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
