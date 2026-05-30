<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-05-01 ~ 2026-05-30
- 运行时间：2026-05-30 04:03:25 UTC
- 运行状态：成功
- 本次总论文数：19
- 精读区：0
- 速读区：19

### 今日简报（AI）
本期速读19篇论文，重点关注3篇高分工作：边缘设备混合精度LLM加速器、移动端混合专家模型及Versal AI Edge的GEMM流式框架。  
最值得关注的是两篇10分论文——边缘LLM推理加速器VitaLLM和移动端MoE框架MobileMoE，后者对端侧大模型部署有重要启示。  
建议优先精读上述两篇满分论文，关注其面向资源受限场景的混合精度与稀疏计算设计，可直接用于边缘AI部署实践。
- 详情：[/20260501-20260530/README](/20260501-20260530/README)

### 精读区论文标签
- 本次无精读推荐。

### 速读区论文标签
1. [VitaLLM: A Versatile and Tiny Accelerator for Mixed-Precision LLM Inference on Edge Devices](/20260501-20260530/2605.00320v1-vitallm-a-versatile-and-tiny-accelerator-for-mixed-precision-llm-inference-on-edge-devices)  
   标签：评分：10.0/10、query:edge-llm
   evidence：面向边缘LLM推理的混合精度加速器
2. [MobileMoE: Scaling On-Device Mixture of Experts](/20260501-20260530/2605.27358v1-mobilemoe-scaling-on-device-mixture-of-experts)  
   标签：评分：10.0/10、query:edge-llm
   evidence：移动端约束下的设备上MoE语言模型
3. [Tempus: A Temporally Scalable Resource-Invariant GEMM Streaming Framework for Versal AI Edge](/20260501-20260530/2605.00536v1-tempus-a-temporally-scalable-resource-invariant-gemm-streaming-framework-for-versal-ai-edge)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向Versal AI Edge的LLM推理GEMM流式加速框架
4. [Tempus: A Temporally Scalable Resource-Invariant GEMM Streaming Framework for Versal AI Edge](/20260501-20260530/2605.00536v2-tempus-a-temporally-scalable-resource-invariant-gemm-streaming-framework-for-versal-ai-edge)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向边缘AI加速器（Versal）的GEMM流式框架
5. [HCInfer: An Efficient Inference System via Error Compensation for Resource-Constrained Devices](/20260501-20260530/2605.05819v1-hcinfer-an-efficient-inference-system-via-error-compensation-for-resource-constrained-devices)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向资源受限设备的异构推理系统，含误差补偿
6. [DSPE: An Energy-Efficient Edge Processor for DeepSeek Inference with MerkleTree-based Incremental Pruning, Multi-Stage Boothing Lookup and Dynamic Adaptive Posit Processing](/20260501-20260530/2605.08615v1-dspe-an-energy-efficient-edge-processor-for-deepseek-inference-with-merkletree-based-incremental-pruning-multi-stage-boothing-lookup-and-dynamic-adaptive-posit-processing)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向LLM推理的边缘处理器协同设计
7. [GELATO: Generative Entropy- and Lyapunov-based Adaptive Token Offloading for Device-Edge Speculative LLM Inference](/20260501-20260530/2605.10124v1-gelato-generative-entropy--and-lyapunov-based-adaptive-token-offloading-for-device-edge-speculative-llm-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：设备-边缘协同推测式LLM推理的自适应token卸载
8. [CATS: Cascaded Adaptive Tree Speculation for Memory-Limited LLM Inference Acceleration](/20260501-20260530/2605.11186v1-cats-cascaded-adaptive-tree-speculation-for-memory-limited-llm-inference-acceleration)  
   标签：评分：9.0/10、query:edge-llm
   evidence：边缘平台上的内存受限LLM推理加速
9. [CR^2: Cost-Aware Risk-Controlled Routing for Wireless Device-Edge LLM Inference](/20260501-20260530/2605.12001v1-cr2-cost-aware-risk-controlled-routing-for-wireless-device-edge-llm-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：无线设备-边缘LLM推理的成本感知路由框架
10. [Multi-Scale Dequant: Eliminating Dequantization Bottleneck via Activation Decomposition for Efficient LLM Inference](/20260501-20260530/2605.13915v1-multi-scale-dequant-eliminating-dequantization-bottleneck-via-activation-decomposition-for-efficient-llm-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：消除NPU加速器上的反量化瓶颈
11. [Lever: Speculative LLM Inference on Smartphones](/20260501-20260530/2605.16786v1-lever-speculative-llm-inference-on-smartphones)  
   标签：评分：9.0/10、query:edge-llm
   evidence：在智能手机上利用闪存进行推测性LLM推理
12. [LLMForge: Multi-Backend Hardware-Aware Neural Architecture Search with Infinite-Head Attention for Edge Language Models](/20260501-20260530/2605.17653v1-llmforge-multi-backend-hardware-aware-neural-architecture-search-with-infinite-head-attention-for-edge-language-models)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向边缘语言模型的硬件感知神经架构搜索，支持多后端
13. [C2CServe: Leveraging NVLink-C2C for Elastic Serverless LLM Serving on MIG](/20260501-20260530/2605.19481v1-c2cserve-leveraging-nvlink-c2c-for-elastic-serverless-llm-serving-on-mig)  
   标签：评分：9.0/10、query:edge-llm
   evidence：基于NVLink-C2C和MIG的LLM服务框架
14. [Quant.npu: Enabling Efficient Mobile NPU Inference for on-device LLMs via Fully Static Quantization](/20260501-20260530/2605.20295v1-quantnpu-enabling-efficient-mobile-npu-inference-for-on-device-llms-via-fully-static-quantization)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向移动NPU的全静态量化框架，支持设备端LLM高效推理
15. [AlignedServe: Orchestrating Prefix-aware Batching to Build a High-throughput and Computing-efficient LLM Serving System](/20260501-20260530/2605.23389v1-alignedserve-orchestrating-prefix-aware-batching-to-build-a-high-throughput-and-computing-efficient-llm-serving-system)  
   标签：评分：9.0/10、query:edge-llm
   evidence：LLM服务框架，采用前缀感知批处理
16. [Dense2MoE: Pushing the Pareto Frontier of On-Device LLMs via Unified Pruning and Upcycling](/20260501-20260530/2605.26496v1-dense2moe-pushing-the-pareto-frontier-of-on-device-llms-via-unified-pruning-and-upcycling)  
   标签：评分：9.0/10、query:edge-llm
   evidence：统一的剪枝与升级回收用于设备端LLM
17. [When NPUs Are Not Always Faster: A Stage-Level Analysis of Mobile LLM Inference](/20260501-20260530/2605.27435v1-when-npus-are-not-always-faster-a-stage-level-analysis-of-mobile-llm-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：移动端CPU-NPU异构SoC上的LLM推理分析
18. [Sieve: Dynamic Expert-Aware PIM Acceleration for Evolving Mixture-of-Experts Models](/20260501-20260530/2605.11277v1-sieve-dynamic-expert-aware-pim-acceleration-for-evolving-mixture-of-experts-models)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向进化中的MoE LLM推理的动态专家感知PIM加速
19. [Llamas on the Web: Memory-Efficient, Performance-Portable, and Multi-Precision LLM Inference with WebGPU](/20260501-20260530/2605.20706v1-llamas-on-the-web-memory-efficient-performance-portable-and-multi-precision-llm-inference-with-webgpu)  
   标签：评分：8.0/10、query:edge-llm
   evidence：基于WebGPU的浏览器中内存高效LLM推理


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
