<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-07
- 运行时间：2026-08-07 20:38:29 UTC
- 运行状态：成功
- 本次总论文数：19
- 精读区：8
- 速读区：11

### 今日简报（AI）
今日精读8篇、速读11篇，聚焦LLM推理优化与边缘部署。最值得关注EdgeXpert（MoE+投机解码）与Opt.Gear技术报告，均获高分；速读中预填充-解码分离及量化压缩方向也有新见解。建议普通读者优先浏览精读两篇的摘要与结论，再按需深入速读列表中的系统设计类论文。
- 详情：[/202608/07/README](/202608/07/README)

### 精读区论文标签
1. [EdgeXpert: An Edge Device for Memory-Efficient LLM Inference with Mixture-of-Experts and Speculative Decoding](/202608/07/2608.05303v1-edgexpert-an-edge-device-for-memory-efficient-llm-inference-with-mixture-of-experts-and-speculative-decoding)  
   标签：评分：10.0/10、query:edge-llm
   evidence：软硬件协同的边缘LLM加速器，结合MoE与推测解码
2. [Opt.Gear Technical Report](/202608/07/2608.01034v2-optgear-technical-report)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向端侧部署的基座模型，在NPU上加速prefill和解码
3. [LLM Serving in the Wild: An Empirical Study of Frameworks, Methods, and System Designs](/202608/07/2608.03036v1-llm-serving-in-the-wild-an-empirical-study-of-frameworks-methods-and-system-designs)  
   标签：评分：9.0/10、query:edge-llm
   evidence：研究五个LLM服务框架在实际系统中的使用
4. [Heterogeneous LLM Serving with General-Purpose Processing-Near-Memory for Retrieval-Based Sparse Attention](/202608/07/2608.03555v1-heterogeneous-llm-serving-with-general-purpose-processing-near-memory-for-retrieval-based-sparse-attention)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向检索式稀疏注意力的异构解码服务系统，结合近内存处理
5. [Heterogeneity-Aware Microscaling for Efficient Low-Bit LLM Inference](/202608/07/2608.03867v1-heterogeneity-aware-microscaling-for-efficient-low-bit-llm-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向高效LLM推断的异构感知低比特格式与加速器
6. [On Design Principles for Efficient Heterogeneous DRAM-PIM-GPU Systems](/202608/07/2608.04169v1-on-design-principles-for-efficient-heterogeneous-dram-pim-gpu-systems)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向LLM解码阶段的高效异构DRAM-PIM-GPU系统设计原理
7. [Deltoris: Enabling Real-time VLA Inference in Embodied AI via Bit-level Sparsity and Speculative Inference](/202608/07/2608.04428v1-deltoris-enabling-real-time-vla-inference-in-embodied-ai-via-bit-level-sparsity-and-speculative-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向边缘VLA推理的软硬件协同设计框架，结合位级稀疏与推测推理
8. [BALANCE: Hybrid Autoregressive-Speculative LLM Inference in Wireless Edge Networks](/202608/07/2608.05926v1-balance-hybrid-autoregressive-speculative-llm-inference-in-wireless-edge-networks)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向边缘LLM推理的混合自回归-投机解码框架，权衡时延与内存

### 速读区论文标签
1. [When Does Disaggregation Pay? Simulating Prefill--Decode--Attention--FFN Specialization for Agentic LLM Inference](/202608/07/2608.03741v1-when-does-disaggregation-pay-simulating-prefill--decode--attention--ffn-specialization-for-agentic-llm-inference)  
   标签：评分：8.0/10、query:edge-llm
   evidence：模拟异构GPU/LPU上代理式LLM推理的预填充-解码与注意力-FFN专业化
2. [Recurrent Residual Quantization: A Progressive Multi-Precision Representation for LLMs](/202608/07/2608.04048v1-recurrent-residual-quantization-a-progressive-multi-precision-representation-for-llms)  
   标签：评分：8.0/10、query:edge-llm
   evidence：多精度后训练量化框架，用单个检查点支持灵活精度-内存权衡，助力LLM高效部署
3. [RAC: Reference-Aware Activation Compression for Communication-Efficient Split LLM Inference](/202608/07/2608.04991v1-rac-reference-aware-activation-compression-for-communication-efficient-split-llm-inference)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向本地-云端边缘部署的通信高效拆分LLM推断
4. [From Chains to Trees: Parent-Conditioned Drafting for Semi-Autoregressive Speculative Decoding](/202608/07/2608.02123v1-from-chains-to-trees-parent-conditioned-drafting-for-semi-autoregressive-speculative-decoding)  
   标签：评分：7.0/10、query:edge-llm
   evidence：用于推测解码的父条件草稿树
5. [ARCHead: Activation-Metric Residual Correction for Large Language Model Output Heads](/202608/07/2608.02703v1-archead-activation-metric-residual-correction-for-large-language-model-output-heads)  
   标签：评分：7.0/10、query:edge-llm
   evidence：量化语言模型头压缩，降低LLM存储占用
6. [AnchorKV: Anchor-Residual KV Cache Compression](/202608/07/2608.02901v1-anchorkv-anchor-residual-kv-cache-compression)  
   标签：评分：7.0/10、query:edge-llm
   evidence：KV缓存压缩实现20倍内存缩减
7. [Pruning-Aware Multi-Cluster Co-Inference for Large AI Models in AI-RANs](/202608/07/2608.03026v1-pruning-aware-multi-cluster-co-inference-for-large-ai-models-in-ai-rans)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向边缘AI-RAN的大AI模型剪枝感知多簇协同推理
8. [Lightweight Chunk Selection for Mobile Retrieval-Augmented Generation](/202608/07/2608.03148v1-lightweight-chunk-selection-for-mobile-retrieval-augmented-generation)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向移动RAG的轻量级分块选择，降低计算与内存开销，契合资源受限边缘LLM推理需求。
9. [Unified Lookup-Table Inference with Signed-Digit K/V Caches for Ternary LLMs](/202608/07/2608.03229v1-unified-lookup-table-inference-with-signed-digit-kv-caches-for-ternary-llms)  
   标签：评分：7.0/10、query:edge-llm
   evidence：基于查找表的三值LLM推理，使注意力与三值投影统一
10. [SlimVLM: Sensitivity-aware Dynamic Structured Pruning with Adaptive Visual Token Selection for Efficient Vision-Language Models](/202608/07/2608.03580v1-slimvlm-sensitivity-aware-dynamic-structured-pruning-with-adaptive-visual-token-selection-for-efficient-vision-language-models)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向资源受限设备VLM的敏感度感知结构化剪枝
11. [ATFlash: Per-RoPE-Wavelength Attention Windows for Compute/Memory-Efficient LLM Inference](/202608/07/2608.02947v1-atflash-per-rope-wavelength-attention-windows-for-computememory-efficient-llm-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向LLM推理的计算/内存高效注意力窗口，可与稀疏方法叠加


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
