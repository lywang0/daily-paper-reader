<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-08
- 运行时间：2026-06-08 21:47:14 UTC
- 运行状态：成功
- 本次总论文数：8
- 精读区：2
- 速读区：6

### 今日简报（AI）
今日聚焦LLM内部几何保持蒸馏与预测调度缓解阻塞，两篇高分精读揭示核心突破。  
最值得看《Beyond Output Matching》证明保留中间层几何结构优于纯输出匹配，《Clairvoyant》提出预测式SJF调度有效克服串行LLM后端头阻塞问题。  
建议普通读者优先关注速读中的OffQ和SigmaScale——结构化异常值偏移与SVD低秩分解，在量化压缩场景最具实操价值。
- 详情：[/202606/08/README](/202606/08/README)

### 精读区论文标签
1. [Beyond Output Matching: Preserving Internal Geometry in NVFP4 LLM Distillation](/202606/08/2606.05682v2-beyond-output-matching-preserving-internal-geometry-in-nvfp4-llm-distillation)  
   标签：评分：8.0/10、query:edge-llm
   evidence：基于NVFP4的低精度推理，硬件感知蒸馏
2. [Clairvoyant: Predictive SJF Scheduling to Mitigate Head-of-Line Blocking in Serial LLM Backends](/202606/08/2606.07248v1-clairvoyant-predictive-sjf-scheduling-to-mitigate-head-of-line-blocking-in-serial-llm-backends)  
   标签：评分：8.0/10、query:edge-llm
   evidence：为边缘设备上的串行LLM后端提供预测调度

### 速读区论文标签
1. [Skip a Layer or Loop It? Learning Program-of-Layers in LLMs](/202606/08/2606.06574v1-skip-a-layer-or-loop-it-learning-program-of-layers-in-llms)  
   标签：评分：7.0/10、query:edge-llm
   evidence：动态层跳过实现高效LLM推理
2. [SigmaScale: LLM Compression with SVD-based Low-Rank Decomposition and Learned Scaling Matrices](/202606/08/2606.07098v1-sigmascale-llm-compression-with-svd-based-low-rank-decomposition-and-learned-scaling-matrices)  
   标签：评分：7.0/10、query:edge-llm
   evidence：基于SVD的LLM压缩用于资源高效推理
3. [OffQ: Taming Structured Outliers in LLM Quantization by Offsetting](/202606/08/2606.07116v1-offq-taming-structured-outliers-in-llm-quantization-by-offsetting)  
   标签：评分：7.0/10、query:edge-llm
   evidence：低比特量化加速LLM推理
4. [Toward Multi-Domain and Long-Tailed Quantization via Feature Alignment and Scaling](/202606/08/2606.04920v1-toward-multi-domain-and-long-tailed-quantization-via-feature-alignment-and-scaling)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向资源受限设备的多域量化方法，可迁移至LLM模型
5. [Depth-Attention: Cross-Layer Value Mixing for Language Models](/202606/08/2606.05014v1-depth-attention-cross-layer-value-mixing-for-language-models)  
   标签：评分：6.0/10、query:edge-llm
   evidence：跨层值混合提升语言模型推理效率
6. [Tangram: Unlocking Non-Uniform KV Cache for Efficient Multi-turn LLM Serving](/202606/08/2606.06302v1-tangram-unlocking-non-uniform-kv-cache-for-efficient-multi-turn-llm-serving)  
   标签：评分：6.0/10、query:edge-llm
   evidence：针对非均匀KV缓存的服务系统，提升多轮LLM效率


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
