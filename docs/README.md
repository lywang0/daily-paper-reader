<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-31
- 运行时间：2026-07-31 21:45:57 UTC
- 运行状态：成功
- 本次总论文数：14
- 精读区：6
- 速读区：8

### 今日简报（AI）
今日精读6篇、速读8篇，重点聚焦低比特LLM推理中的旋转与量化协同技术。  
最值得关注两篇9分工作：GyRot揭示旋转与细粒度分组量化的协同效应，LightRot提出轻量旋转方案及架构，均显著提升低比特推理精度。  
建议优先精读这两篇论文，深入理解旋转矩阵与量化误差的交互机制，再结合CONQuEr等混合精度方法验证实际部署效果。
- 详情：[/202607/31/README](/202607/31/README)

### 精读区论文标签
1. [GyRot: Leveraging Hidden Synergy between Rotation and Fine-grained Group Quantization for Low-bit LLM Inference](/202607/31/2607.27694v1-gyrot-leveraging-hidden-synergy-between-rotation-and-fine-grained-group-quantization-for-low-bit-llm-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：低比特LLM推理的量化框架与硬件加速器，算法-硬件协同设计
2. [LightRot: A Light-Weighted Rotation Scheme and Architecture for Accurate Low-Bit Large Language Model Inference](/202607/31/2607.27704v1-lightrot-a-light-weighted-rotation-scheme-and-architecture-for-accurate-low-bit-large-language-model-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：用于低比特LLM推理的专用硬件加速器与轻量旋转方案
3. [LAST: The Last Query Token Guides Visual Token Pruning for Edge-Cloud Collaborative MLLM Inference](/202607/31/2607.27952v1-last-the-last-query-token-guides-visual-token-pruning-for-edge-cloud-collaborative-mllm-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：边缘-云协同MLLM推理中的查询引导token剪枝
4. [SmartGen: Seamless Disaggregated LLM Inference with Selective KV Cache Transfer](/202607/31/2607.28150v1-smartgen-seamless-disaggregated-llm-inference-with-selective-kv-cache-transfer)  
   标签：评分：9.0/10、query:edge-llm
   evidence：提出解耦式LLM服务框架，通过选择性KV缓存传输缓解网络瓶颈
5. [SpecBox: Speculative Sandbox Scheduling for Efficient LLM Agent Serving](/202607/31/2607.23933v1-specbox-speculative-sandbox-scheduling-for-efficient-llm-agent-serving)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向LLM代理服务的运行时系统，通过推测性沙箱预分配提升资源利用
6. [WIDE: Boosting Adaptive LLM Inference via Token-level Dynamic Width Pruning](/202607/31/2607.28418v1-wide-boosting-adaptive-llm-inference-via-token-level-dynamic-width-pruning)  
   标签：评分：8.0/10、query:edge-llm
   evidence：通过词元级动态宽度剪枝提升大语言模型推理效率，适用于预填充和解码阶段

### 速读区论文标签
1. [OrchNAS: Orchestrated Neural Architecture Search Service for Personalised Federated Edge Intelligence](/202607/31/2607.22805v1-orchnas-orchestrated-neural-architecture-search-service-for-personalised-federated-edge-intelligence)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向异构边缘环境的能量感知个性化模型设计
2. [KAP: Bridging the Knowledge Selection-Runtime Consumption Gap in LLM Systems](/202607/31/2607.24260v1-kap-bridging-the-knowledge-selection-runtime-consumption-gap-in-llm-systems)  
   标签：评分：7.0/10、query:edge-llm
   evidence：针对结构化先验知识导致的KV缓存内存流量问题，优化LLM服务
3. [CONQuER: Hardware-Aware Mixed-Precision Quantisation with Online-Calibrated Surrogates](/202607/31/2607.25884v1-conquer-hardware-aware-mixed-precision-quantisation-with-online-calibrated-surrogates)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向资源受限异构硬件的硬件感知混合精度量化，是硬件感知加速的核心方法
4. [A Photonic-CXL Memory Appliance for Scalable KV Cache Management in LLM Inference](/202607/31/2607.27187v1-a-photonic-cxl-memory-appliance-for-scalable-kv-cache-management-in-llm-inference)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向LLM推理KV缓存管理的光子-CXL内存架构
5. [Prox: Training-Free FFN Activation Sparsity via Approximate Intermediate-Channel Salience in LLMs](/202607/31/2607.27591v1-prox-training-free-ffn-activation-sparsity-via-approximate-intermediate-channel-salience-in-llms)  
   标签：评分：7.0/10、query:edge-llm
   evidence：免训练激活稀疏化降低LLM推理资源消耗，可用于边缘部署
6. [A Sparse Glimpse of the Whole: Train-Free Self-Speculative Decoding](/202607/31/2607.27735v1-a-sparse-glimpse-of-the-whole-train-free-self-speculative-decoding)  
   标签：评分：7.0/10、query:edge-llm
   evidence：基于稀疏可召回KV缓存的免训练自推测解码，提升LLM高效推理
7. [Conformal Cascade: Distribution-Free Accuracy Guarantees for Multi-Tier LLM Inference](/202607/31/2607.25018v2-conformal-cascade-distribution-free-accuracy-guarantees-for-multi-tier-llm-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：基于保形预测的多级LLM级联，实现资源高效的推理
8. [Rethinking Inference-Time Scaling in Local Computer-Use Agents: Failure Modes and Compute Tradeoffs](/202607/31/2607.28573v1-rethinking-inference-time-scaling-in-local-computer-use-agents-failure-modes-and-compute-tradeoffs)  
   标签：评分：6.0/10、query:edge-llm
   evidence：本地部署场景下推理时扩展的实证研究，涉及资源受限设备优化


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
