<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-19
- 运行时间：2026-08-19 20:39:57 UTC
- 运行状态：成功
- 本次总论文数：6
- 精读区：2
- 速读区：4

### 今日简报（AI）
今日6篇论文聚焦LLM推理加速，重点精读TileMix混合精度注意力与PTXBench GPU内核优化。最值得关注TileMix的tile级混合精度调优，以及PTXBench对架构specific PTX的基准与适配，均获8.0高分。建议普通读者优先了解混合精度推理如何降低显存占用，并留意PTX级优化对国产GPU生态的潜力。
- 详情：[/202608/19/README](/202608/19/README)

### 精读区论文标签
1. [TileMix: Tile-Centric Mixed-Precision Attention for LLM Inference Acceleration](/202608/19/2608.17336v1-tilemix-tile-centric-mixed-precision-attention-for-llm-inference-acceleration)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向LLM预填充加速的硬件对齐混合精度注意力内核
2. [PTXBench: Benchmark and Adapt LLMs for GPU Kernel Optimization with Architecture-specific PTX](/202608/19/2608.17379v1-ptxbench-benchmark-and-adapt-llms-for-gpu-kernel-optimization-with-architecture-specific-ptx)  
   标签：评分：8.0/10、query:edge-llm
   evidence：基于架构特定PTX的LLM驱动GPU内核优化基准

### 速读区论文标签
1. [The Integer Alibi: Localizing Cross-Kernel Divergence in INT8-Quantized LLM Inference](/202608/19/2608.13756v2-the-integer-alibi-localizing-cross-kernel-divergence-in-int8-quantized-llm-inference)  
   标签：评分：7.0/10、query:edge-llm
   evidence：研究INT8量化LLM推理中GPU内核差异，关注内核级硬件相关行为
2. [P2Skill: Privacy Preserving Skill Distillation for Cloud-Local LLM Inference Systems](/202608/19/2608.14094v1-p2skill-privacy-preserving-skill-distillation-for-cloud-local-llm-inference-systems)  
   标签：评分：7.0/10、query:edge-llm
   evidence：云-端LLM推理系统中本地小模型进行隐私感知路由与技能蒸馏
3. [MoNe: Modular Neural Memory for Efficient Long Context Inference](/202608/19/2608.17616v1-mone-modular-neural-memory-for-efficient-long-context-inference)  
   标签：评分：7.0/10、query:edge-llm
   evidence：解耦上下文长度与推理开销并降低GPU内存的高效长上下文LLM推理
4. [Beyond FLOPs: Energy-Aware Knowledge Distillation for Sustainable LLMs on Code-Related Task](/202608/19/2608.17515v1-beyond-flops-energy-aware-knowledge-distillation-for-sustainable-llms-on-code-related-task)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向资源受限平台的能量感知知识蒸馏以降低LLM计算需求


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
