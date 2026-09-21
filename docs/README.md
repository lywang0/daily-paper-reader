<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-21
- 运行时间：2026-09-21 22:44:37 UTC
- 运行状态：成功
- 本次总论文数：6
- 精读区：1
- 速读区：5

### 今日简报（AI）
今天筛出 6 篇 LLM 推理优化论文，精读 1 篇、速读 5 篇，重点集中在 KV 缓存、量化和注意力调度。

最值得看的是 9.0 分的《TierKV》提出的多级 KV 缓存思路，以及速读中 SpecQuant 的多父量化与 On-Demand Attention 的按需回忆机制。

普通读者可优先了解端侧长上下文如何靠缓存分层省显存，再按兴趣跟进量化与注意力优化方向。
- 详情：[/202609/21/README](/202609/21/README)

### 精读区论文标签
1. [TierKV: Long-Context On-Device LLMs via Predictive Multi-Tier KV Caching](/202609/21/2609.21172v1-tierkv-long-context-on-device-llms-via-predictive-multi-tier-kv-caching)  
   标签：评分：9.0/10、query:edge-llm
   evidence：移动端设备端LLM推理框架与多级KV缓存

### 速读区论文标签
1. [SpecQuant: Speculative Decoding with Multi-Parent Quantization for Adaptive LLM Inference](/202609/21/2609.21704v1-specquant-speculative-decoding-with-multi-parent-quantization-for-adaptive-llm-inference)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向消费级硬件的量化与推测解码本地推理
2. [rMuscle: Robotic Muscle Memory for Efficient Vision-Language-Action Model Inference](/202609/21/2609.19104v1-rmuscle-robotic-muscle-memory-for-efficient-vision-language-action-model-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：利用具身负载相似性的高效VLA模型推理
3. [On-Demand Attention: Language Models Know When to Recall](/202609/21/2609.20734v1-on-demand-attention-language-models-know-when-to-recall)  
   标签：评分：6.0/10、query:edge-llm
   evidence：按需注意力与vLLM条件执行，提升长上下文推理效率
4. [An Approximate Queueing Model of LLM Inference Serving for SLO-Driven Autoscaling](/202609/21/2609.20957v1-an-approximate-queueing-model-of-llm-inference-serving-for-slo-driven-autoscaling)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向SLO自动扩缩的LLM推理服务排队模型
5. [Samsone: A Family of Open Small Audio Language Models for On-Device Inference](/202609/21/2609.21666v1-samsone-a-family-of-open-small-audio-language-models-for-on-device-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向边缘计算与端侧推理的小型音频语言模型


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
