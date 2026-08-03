<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-03
- 运行时间：2026-08-03 21:56:27 UTC
- 运行状态：成功
- 本次总论文数：8
- 精读区：4
- 速读区：4

### 今日简报（AI）
今日研读8篇论文，精读聚焦模拟存内计算系统的KV缓存保护与LLM服务性能建模。  
最值得关注的两大方向：面向噪声鲁棒性的选择性KV缓存保护（9.0分），以及感知饱和度的轻量级服务性能建模（9.0分）。  
建议普通读者优先了解KV缓存优化对推理效率与稳定性的实际收益，再结合动态退出与级联方案探索成本-精度平衡。
- 详情：[/202608/03/README](/202608/03/README)

### 精读区论文标签
1. [Selective KV Cache Protection for Noise-Resilient LLM Inference on Analog Compute-In-Memory Systems](/202608/03/2607.29076v1-selective-kv-cache-protection-for-noise-resilient-llm-inference-on-analog-compute-in-memory-systems)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向模拟存算一体LLM推理的抗噪算法-硬件协同设计
2. [SLIM: Saturation-Aware Lightweight Performance Modeling for LLM Serving](/202608/03/2607.29575v1-slim-saturation-aware-lightweight-performance-modeling-for-llm-serving)  
   标签：评分：9.0/10、query:edge-llm
   evidence：SLIM为LLM服务提供饱和度感知的轻量性能建模，并通过硬件剖析定位解码阶段注意力内核。
3. [Characterizing LLM Kernel Access and Memory Interaction in Multi-Partition NUMA GPUs](/202608/03/2607.28824v1-characterizing-llm-kernel-access-and-memory-interaction-in-multi-partition-numa-gpus)  
   标签：评分：8.0/10、query:edge-llm
   evidence：刻画多分区NUMA GPU上LLM内核访存与局部性，服务硬件感知优化
4. [DeltaServe: Host-Agnostic Co-Serving of Inference and Fine-Tuning for LLMs](/202608/03/2607.28848v1-deltaserve-host-agnostic-co-serving-of-inference-and-fine-tuning-for-llms)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向LLM的服务框架，支持推理与微调协同调度

### 速读区论文标签
1. [BLADE: Boundary-Expanded and Layer-Adaptive Dynamic Exit for Efficient LLM Reasoning](/202608/03/2607.28966v1-blade-boundary-expanded-and-layer-adaptive-dynamic-exit-for-efficient-llm-reasoning)  
   标签：评分：7.0/10、query:edge-llm
   evidence：通过动态早退降低计算量，实现高效LLM推理
2. [Conformal Cascade: Distribution-Free Accuracy Guarantees for Multi-Tier LLM Inference](/202608/03/2607.25018v3-conformal-cascade-distribution-free-accuracy-guarantees-for-multi-tier-llm-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：多级级联通过路由降低推理开销，适合资源受限场景
3. [Mixture-of-Translators: Translating KV Caches Across Heterogeneous Large Language Models](/202608/03/2607.28979v1-mixture-of-translators-translating-kv-caches-across-heterogeneous-large-language-models)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向异构LLM的KV缓存翻译，提升多模型推理可扩展性。
4. [Studying quantization trade-offs for efficient inference deployment in machine translation](/202608/03/2607.29397v1-studying-quantization-trade-offs-for-efficient-inference-deployment-in-machine-translation)  
   标签：评分：6.0/10、query:edge-llm
   evidence：GPU上量化权衡用于高效推理部署


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
