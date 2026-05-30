<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-05-30
- 运行时间：2026-05-30 20:53:04 UTC
- 运行状态：成功
- 本次总论文数：17
- 精读区：6
- 速读区：11

### 今日简报（AI）
1) 今日聚焦边缘端LLM推理优化，精读两篇高分论文分别提出自适应分布式推理与3D NAND存算一体架构，速读关注弹性解码与深度剪枝。  
2) 最值得看的方向是面向资源受限设备的加速：Profiling驱动的动态分配与CAM多比特CIM硬件协同，满分论文可重点精读。  
3) 建议读者优先精读《Profiling-Driven Adaptive Distributed Transformer Inference》，掌握边缘部署中计算与内存调度的自适应策略。
- 详情：[/202605/30/README](/202605/30/README)

### 精读区论文标签
1. [Profiling-Driven Adaptive Distributed Transformer Inference on Embedded Edge Deployment](/202605/30/2605.25682v1-profiling-driven-adaptive-distributed-transformer-inference-on-embedded-edge-deployment)  
   标签：评分：10.0/10、query:edge-llm
   evidence：在嵌入式边缘设备上分布式Transformer推理，使用Jetson硬件原型
2. [NASiC: 3D NAND-based CAM-Selected Multibit CIM Architecture for Efficient On-Device Mixture-of-Experts LLM Inference](/202605/30/2605.23294v1-nasic-3d-nand-based-cam-selected-multibit-cim-architecture-for-efficient-on-device-mixture-of-experts-llm-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向设备上MoE的3D NAND存内计算软硬协同设计
3. [Stateful Inference for Low-Latency Multi-Agent Tool Calling](/202605/30/2605.26289v1-stateful-inference-for-low-latency-multi-agent-tool-calling)  
   标签：评分：9.0/10、query:edge-llm
   evidence：提出有状态推理架构，降低LLM服务每轮开销
4. [How Far Can Disaggregation Go? A Design-Space Exploration of Attention-FFN Disaggregation for Efficient MoE LLM Serving](/202605/30/2605.28302v1-how-far-can-disaggregation-go-a-design-space-exploration-of-attention-ffn-disaggregation-for-efficient-moe-llm-serving)  
   标签：评分：9.0/10、query:edge-llm
   evidence：注意力-FFN分离的设计空间探索，用于高效MoE LLM服务
5. [Adaptive Mass-Segmented KV Compression for Long-Context Reasoning](/202605/30/2605.23200v1-adaptive-mass-segmented-kv-compression-for-long-context-reasoning)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向长上下文的KV缓存压缩，采用区域感知配额分配
6. [CONF-KV: Confidence-Aware KV Cache Eviction with Mixed-Precision Storage for Long-Horizon LLM](/202605/30/2605.24786v1-conf-kv-confidence-aware-kv-cache-eviction-with-mixed-precision-storage-for-long-horizon-llm)  
   标签：评分：8.0/10、query:edge-llm
   evidence：基于置信度的KV缓存逐出与混合精度存储

### 速读区论文标签
1. [Optimus: Elastic Decoding for Efficient Diffusion LLM Serving](/202605/30/2605.24832v1-optimus-elastic-decoding-for-efficient-diffusion-llm-serving)  
   标签：评分：8.0/10、query:edge-llm
   evidence：扩散LLM服务的弹性解码，提升硬件利用率
2. [Bandwidth-Aware LLM Inference on Heterogeneous Many-Core Supercomputers](/202605/30/2605.25655v1-bandwidth-aware-llm-inference-on-heterogeneous-many-core-supercomputers)  
   标签：评分：8.0/10、query:edge-llm
   evidence：异构众核超级计算机上的带宽感知LLM推理，软硬件协同设计
3. [Locality-Aware Redundancy Pruning for LLM Depth Compression](/202605/30/2605.27786v1-locality-aware-redundancy-pruning-for-llm-depth-compression)  
   标签：评分：8.0/10、query:edge-llm
   evidence：免训练深度剪枝，提升LLM推理效率
4. [ModeSwitch-LLM: A Lightweight Phase-Aware Controller for Cross-Mode LLM Inference on a Single GPU](/202605/30/2605.23057v1-modeswitch-llm-a-lightweight-phase-aware-controller-for-cross-mode-llm-inference-on-a-single-gpu)  
   标签：评分：7.0/10、query:edge-llm
   evidence：基于工作负载特征选择推理模式的相位感知控制器
5. [Interdomain Attention: Beyond Token-Level Key-Value Memory](/202605/30/2605.24330v1-interdomain-attention-beyond-token-level-key-value-memory)  
   标签：评分：7.0/10、query:edge-llm
   evidence：提出域间注意力机制，集成SSM实现定长KV缓存，降低内存
6. [H$^{2}$MT: Semantic Hierarchy-Aware Hierarchical Memory Transformer](/202605/30/2605.24930v1-h2mt-semantic-hierarchy-aware-hierarchical-memory-transformer)  
   标签：评分：7.0/10、query:edge-llm
   evidence：层次内存Transformer降低长上下文推理的预填充成本
7. [A general tensor-structured compression scheme for efficient large language models](/202605/30/2605.25344v1-a-general-tensor-structured-compression-scheme-for-efficient-large-language-models)  
   标签：评分：7.0/10、query:edge-llm
   evidence：张量结构压缩减少LLM的内存和计算
8. [ReMoE: Boosting Expert Reuse through Router Fine-Tuning in Memory-Constrained MoE LLM Inference](/202605/30/2605.27081v1-remoe-boosting-expert-reuse-through-router-fine-tuning-in-memory-constrained-moe-llm-inference)  
   标签：评分：7.0/10、query:edge-llm
   evidence：通过改进专家重用提升MoE资源效率
9. [GEMQ: Global Expert-Level Mixed-Precision Quantization for MoE LLMs](/202605/30/2605.23078v1-gemq-global-expert-level-mixed-precision-quantization-for-moe-llms)  
   标签：评分：6.0/10、query:edge-llm
   evidence：混合精度量化减少MoE LLM内存占用，与硬件感知加速相关
10. [FD-RAG: Federated Dual-System Retrieval-Augmented Generation](/202605/30/2605.27432v1-fd-rag-federated-dual-system-retrieval-augmented-generation)  
   标签：评分：6.0/10、query:edge-llm
   evidence：边缘环境中的联邦RAG，资源高效LLM推理
11. [SiDP: Memory-Efficient Data Parallelism for Offline LLM Inference](/202605/30/2605.28095v1-sidp-memory-efficient-data-parallelism-for-offline-llm-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向LLM服务的内存高效数据并行


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
