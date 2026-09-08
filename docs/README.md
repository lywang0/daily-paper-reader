<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-08
- 运行时间：2026-09-08 22:55:59 UTC
- 运行状态：成功
- 本次总论文数：5
- 精读区：0
- 速读区：5

### 今日简报（AI）
今日共速读5篇论文，其中3篇公开高价值工作，精读0篇，主攻长上下文与高效推理方向。

最值得关注：KVMem用消费级GPU实现百万token智能体工作区，ACE为MoE模型提供免校准的专家跳过剪枝，均达7.0/10。

下步建议优先精读KVMem与ACE原论文，并关注TopoCompress的图连线语义轨迹压缩思路作为补充。
- 详情：[/202609/08/README](/202609/08/README)

### 精读区论文标签
- 本次无精读推荐。

### 速读区论文标签
1. [KVMem: Virtualizing Million-Token Agent Workspaces on a Consumer GPU](/202609/08/2609.04852v1-kvmem-virtualizing-million-token-agent-workspaces-on-a-consumer-gpu)  
   标签：评分：7.0/10、query:edge-llm
   evidence：在消费级GPU上通过KV上下文跨显存、内存与NVMe分层分页来支撑超长上下文LLM推理
2. [ACE: Adaptive Calibration-Free Expert Skipping for MoE-based LLMs](/202609/08/2609.05228v1-ace-adaptive-calibration-free-expert-skipping-for-moe-based-llms)  
   标签：评分：7.0/10、query:edge-llm
   evidence：免训练的专家跳过降低MoE推理冗余计算，可用于资源受限的边缘推理
3. [TopoCompress: Long Context Compression via Graph-Wired Semantic Trajectories](/202609/08/2608.30811v1-topocompress-long-context-compression-via-graph-wired-semantic-trajectories)  
   标签：评分：6.0/10、query:edge-llm
   evidence：无需训练的长上下文压缩可降低LLM推理成本与延迟，未聚焦边缘/硬件环境
4. [SCULPT: Training Edge Vision Models for Post-Training Quantization Readiness](/202609/08/2609.01743v1-sculpt-training-edge-vision-models-for-post-training-quantization-readiness)  
   标签：评分：6.0/10、query:edge-llm
   evidence：改善边缘模型PTQ就绪性的训练方法，可迁移至大模型量化部署，但目标是视觉模型而非LLM
5. [BeaconKV: Key-Value Cache Compression Guided by Beacon Queries for Efficient Large Reasoning Model Inference](/202609/08/2609.04971v1-beaconkv-key-value-cache-compression-guided-by-beacon-queries-for-efficient-large-reasoning-model-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：通过Beacon查询引导KV缓存压缩，缓解长思维链推理显存瓶颈，可迁移至资源受限的边缘推断场景


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
