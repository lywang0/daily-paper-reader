<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-04
- 运行时间：2026-06-04 21:59:02 UTC
- 运行状态：成功
- 本次总论文数：12
- 精读区：6
- 速读区：6

### 今日简报（AI）
今日聚焦LLM推理效率优化，精读两篇满分论文分别针对ARM异构SoC和边缘/雾环境部署，速读三篇关注长上下文注意力机制与量化技术。  
最值得关注的方向：边缘端LLM高效部署（精读两篇）和长上下文推理加速（速读《LazyAttention》《SparDA》）。  
建议普通读者优先精读10分论文，把握硬件感知优化思路，再结合速读了解检索增强与稀疏注意力等实用技术。
- 详情：[/202606/04/README](/202606/04/README)

### 精读区论文标签
1. [Fast Transformer Inference on ARM-Based HMPSoCs](/202606/04/2606.02836v1-fast-transformer-inference-on-arm-based-hmpsocs)  
   标签：评分：10.0/10、query:edge-llm
   evidence：通过在ARM-CL中实现自定义transformer内核，加速ARM边缘设备上的变换器推理
2. [E2LLM: Towards Efficient LLM Serving in Heterogeneous Edge/Fog Environments](/202606/04/2606.03770v1-e2llm-towards-efficient-llm-serving-in-heterogeneous-edgefog-environments)  
   标签：评分：10.0/10、query:edge-llm
   evidence：异构边缘/雾环境服务框架
3. [LLM Compression with Jointly Optimizing Architectural and Quantization choices](/202606/04/2606.04063v1-llm-compression-with-jointly-optimizing-architectural-and-quantization-choices)  
   标签：评分：9.0/10、query:edge-llm
   evidence：通过联合优化实现面向边缘设备的LLM压缩
4. [Recover-LoRA for Aggressive Quantization: Reclaiming Accuracy in 2-Bit Language Models via Low-Rank Adaptation with Knowledge Distillation on Synthetic Data](/202606/04/2606.04238v1-recover-lora-for-aggressive-quantization-reclaiming-accuracy-in-2-bit-language-models-via-low-rank-adaptation-with-knowledge-distillation-on-synthetic-data)  
   标签：评分：9.0/10、query:edge-llm
   evidence：明确提到边缘和端侧部署；2位量化用于内存受限推理
5. [FlexNPU: Transparent NPU Virtualization for Dynamic LLM Prefill-Decode Co-location](/202606/04/2606.04415v1-flexnpu-transparent-npu-virtualization-for-dynamic-llm-prefill-decode-co-location)  
   标签：评分：9.0/10、query:edge-llm
   evidence：边缘端NPU虚拟化实现LLM预填充-解码协同部署
6. [Multi-SPIN: Multi-Access Speculative Inference for Cooperative Token Generation at the Edge](/202606/04/2606.04581v1-multi-spin-multi-access-speculative-inference-for-cooperative-token-generation-at-the-edge)  
   标签：评分：9.0/10、query:edge-llm
   evidence：提出在边缘系统中使用设备-服务器协同的分布式推测推理以实现高效令牌生成

### 速读区论文标签
1. [LazyAttention: Efficient Retrieval-Augmented Generation with Deferred Positional Encoding](/202606/04/2606.04302v1-lazyattention-efficient-retrieval-augmented-generation-with-deferred-positional-encoding)  
   标签：评分：8.0/10、query:edge-llm
   evidence：LLM推理中高效的KV缓存
2. [SparDA: Sparse Decoupled Attention for Efficient Long-Context LLM Inference](/202606/04/2606.04511v1-sparda-sparse-decoupled-attention-for-efficient-long-context-llm-inference)  
   标签：评分：8.0/10、query:edge-llm
   evidence：稀疏解耦注意力与硬件感知预取
3. [Qift: Shift-Friendly No-Zero W2 Post-Training Quantization for Rotated W2A4/KV4 LLM Inference](/202606/04/2606.02823v1-qift-shift-friendly-no-zero-w2-post-training-quantization-for-rotated-w2a4kv4-llm-inference)  
   标签：评分：7.0/10、query:edge-llm
   evidence：2比特权重量化实现内存高效LLM推理
4. [Multi-Segment Attention: Enabling Efficient KV-Cache Management for Faster Large Language Model Serving](/202606/04/2606.02964v1-multi-segment-attention-enabling-efficient-kv-cache-management-for-faster-large-language-model-serving)  
   标签：评分：7.0/10、query:edge-llm
   evidence：KV缓存管理系统加速LLM服务
5. [Soft-NBCE: Entropy-Weighted Chunk Fusion for Long-Context](/202606/04/2606.01101v1-soft-nbce-entropy-weighted-chunk-fusion-for-long-context)  
   标签：评分：6.0/10、query:edge-llm
   evidence：通过软块融合实现高效长上下文推理
6. [Ekka: Automated Diagnosis of Silent Errors in LLM Inference](/202606/04/2606.04594v1-ekka-automated-diagnosis-of-silent-errors-in-llm-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：LLM服务框架诊断


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
