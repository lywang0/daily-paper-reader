<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-12
- 运行时间：2026-08-12 20:18:36 UTC
- 运行状态：成功
- 本次总论文数：8
- 精读区：4
- 速读区：4

### 今日简报（AI）
今日聚焦 LLM 推理优化，精读 WebGPU 调度开销与稀疏加速器生成两篇高分论文，并速读 KV 缓存、视觉 token 剪枝及 RAG 运行时等方向。最值得关注的是 WebGPU 开销测量与稀疏加速器生成，均获 9.0/10 高分。建议普通读者优先关注 LLM 推理效率提升，可结合 KV 缓存分配与视觉 token 剪枝等轻量方案。
- 详情：[/202608/12/README](/202608/12/README)

### 精读区论文标签
1. [Measuring and Reducing WebGPU Dispatch Overhead for LLM Inference](/202608/12/2608.08730v2-measuring-and-reducing-webgpu-dispatch-overhead-for-llm-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：针对浏览器与边缘设备上的LLM推理，测量并降低WebGPU调度开销
2. [FSGen: Agile Fused and Sparse Accelerator Generator with Accurate Power Model for LLM Applications](/202608/12/2608.09252v1-fsgen-agile-fused-and-sparse-accelerator-generator-with-accurate-power-model-for-llm-applications)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向LLM的敏捷加速器生成器，支持融合数据流和稀疏性，用于软硬件协同设计的空间探索
3. [MemSpec: Memory-Aware Runtime for Adaptive Draft Scheduling in Speculative Decoding on Edge Devices](/202608/12/2608.10362v1-memspec-memory-aware-runtime-for-adaptive-draft-scheduling-in-speculative-decoding-on-edge-devices)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向边缘设备的自适应草稿调度的内存感知运行时，匹配边缘LLM服务的硬件感知调度
4. [ImpactHO: Importance-Aware KV Cache Transfer for Multi-User Edge LLM Handover](/202608/12/2608.10545v1-impactho-importance-aware-kv-cache-transfer-for-multi-user-edge-llm-handover)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向多用户边缘LLM切换的KV缓存重要性传输，直接面向边缘LLM服务

### 速读区论文标签
1. [RippleKV: Cross-Layer KV Cache Allocation via Perturbation Propagation](/202608/12/2608.08684v1-ripplekv-cross-layer-kv-cache-allocation-via-perturbation-propagation)  
   标签：评分：7.0/10、query:edge-llm
   evidence：跨层KV缓存分配以减少长上下文LLM推理的内存占用
2. [RoRA: Role-Oriented Regional Allocation for Visual Token Pruning in MLLMs](/202608/12/2608.07088v1-rora-role-oriented-regional-allocation-for-visual-token-pruning-in-mllms)  
   标签：评分：6.0/10、query:edge-llm
   evidence：免训练的视觉令牌剪枝降低多模态LLM预填充和KV缓存存储开销
3. [OpRAG: A Resource-Deterministic Runtime for GPU-Backed Multi-Stage RAG Workflows](/202608/12/2608.08340v1-oprag-a-resource-deterministic-runtime-for-gpu-backed-multi-stage-rag-workflows)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向多阶段RAG工作流的资源确定性分布式运行时，与LLM服务框架相关
4. [Continuous Interaction Diffusion: A Diffusion-Native Runtime for Asynchronous Tool-Augmented Reasoning](/202608/12/2608.10438v1-continuous-interaction-diffusion-a-diffusion-native-runtime-for-asynchronous-tool-augmented-reasoning)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向异步工具增强推理的扩散原生运行时，属于扩散LLM的serving框架


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
