<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-08-13
- 运行时间：2026-08-13 21:16:37 UTC
- 运行状态：成功
- 本次总论文数：6
- 精读区：2
- 速读区：4

### 今日简报（AI）
今日精读聚焦稀疏混合专家模型，揭示计算最优不等于集群最优，并推出边缘MoE的自适应专家预取方案APEX；速读覆盖LLM云芯片互连、实时分层分类与边缘推理调度。

最值得关注的是MoE系统级优化：从集群扩展到边缘推理，均需考虑硬件感知与内存带宽瓶颈，而非单纯追求计算效率。

建议普通读者优先回顾两篇9分论文，理解MoE在真实系统中的资源权衡，速读可暂缓。
- 详情：[/202608/13/README](/202608/13/README)

### 精读区论文标签
1. [Compute-Optimal Is Not Cluster-Optimal: Systems-Aware Scaling for Sparse Mixture-of-Experts](/202608/13/2608.10605v1-compute-optimal-is-not-cluster-optimal-systems-aware-scaling-for-sparse-mixture-of-experts)  
   标签：评分：9.0/10、query:edge-llm
   evidence：将模型架构与系统软硬协同设计建模为优化问题
2. [APEX: Adaptive Expert Prefetching for Memory-Efficient Edge MoE Inference](/202608/13/2608.11688v1-apex-adaptive-expert-prefetching-for-memory-efficient-edge-moe-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向边缘MoE推理的自适应专家预取框架，直接解决内存受限下的LLM部署问题

### 速读区论文标签
1. [C2C-Explorer: An Exploration Framework for Chip-to-Chip Interconnect Architectures in LLM Cloud Computing Systems](/202608/13/2608.08611v1-c2c-explorer-an-exploration-framework-for-chip-to-chip-interconnect-architectures-in-llm-cloud-computing-systems)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向LLM工作负载的芯片间互连设计空间探索，实现工作负载到硬件的协同优化
2. [Achieving Near-Zero-Overhead Multi-Model Hierarchical Classification in Real-Time Detection Pipelines](/202608/13/2608.11770v1-achieving-near-zero-overhead-multi-model-hierarchical-classification-in-real-time-detection-pipelines)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向边缘GPU+NPU异构流水线，解决算子约束和量化不兼容，贴合边缘软硬协同与NPU异构计算主题
3. [Split-Gate Pooled-Evidence Stochastic-Rollout Scheduling for Timely Progressive Edge Inference](/202608/13/2608.08338v1-split-gate-pooled-evidence-stochastic-rollout-scheduling-for-timely-progressive-edge-inference)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向渐进式边缘推理的GPU调度；与边缘硬件感知调度相关
4. [AI Query Compilation for Unified and Optimized Execution](/202608/13/2608.10139v1-ai-query-compilation-for-unified-and-optimized-execution)  
   标签：评分：6.0/10、query:edge-llm
   evidence：将LLM推理层与SQL统一编译为张量计算图，实现全局编译器优化与自动切分，加速硬件执行


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
