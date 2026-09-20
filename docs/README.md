<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-20
- 运行时间：2026-09-20 21:46:24 UTC
- 运行状态：成功
- 本次总论文数：3
- 精读区：0
- 速读区：3

### 今日简报（AI）
今天速读 3 篇推理效率论文，全部聚焦大模型加速，无一精读。

最值得看的是两条路线：AdaVSkip 用跨层自适应视觉 token 跳过省算力（6.0），D-Quant 用可漂移熵编码压缩 KV cache（6.0）；若想先建立全局观，可看 Pareto Atlas 梳理哪些优化真正主导成本、质量与延迟的取舍（6.0）。

普通读者建议先花十分钟翻 Pareto Atlas 找准权衡框架，再按自己关心的是多模态还是长上下文推理，挑 AdaVSkip 或 D-Quant 深入。
- 详情：[/202609/20/README](/202609/20/README)

### 精读区论文标签
- 本次无精读推荐。

### 速读区论文标签
1. [AdaVSkip: Adaptive Visual Token Skipping Across Layers For Efficient MLLMs Inference](/202609/20/2609.15131v1-adavskip-adaptive-visual-token-skipping-across-layers-for-efficient-mllms-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：跨层自适应视觉令牌跳过以加速MLLM推理
2. [The Inference Engineering Pareto Atlas: Which Optimizations Dominate the Cost, Quality, and Latency Frontier?](/202609/20/2609.17863v1-the-inference-engineering-pareto-atlas-which-optimizations-dominate-the-cost-quality-and-latency-frontier)  
   标签：评分：6.0/10、query:edge-llm
   evidence：在多种GPU与部署约束下评测大模型推理服务优化
3. [D-Quant: Driftable Entropy Coding for KV Cache Quantization](/202609/20/2609.19880v1-d-quant-driftable-entropy-coding-for-kv-cache-quantization)  
   标签：评分：6.0/10、query:edge-llm
   evidence：通过KV缓存量化降低LLM内存与带宽压力


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
