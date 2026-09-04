<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-09-04
- 运行时间：2026-09-04 22:51:50 UTC
- 运行状态：成功
- 本次总论文数：15
- 精读区：6
- 速读区：9

### 今日简报（AI）
今日聚焦端侧LLM流式推理与MoE批处理调度，精读两篇高分论文，另速读SoC并行、单GPU压缩及长上下文加速三篇。最值得关注的是《LeanStream》的推测-修正流式框架（10分），以及《DynaNDE》的动态近数据专家调度（9分），分别解决端侧高效推理和批处理MoE瓶颈。建议普通读者优先关注端侧模型部署优化，后续可结合压缩与缓存技术深入探索。
- 详情：[/202609/04/README](/202609/04/README)

### 精读区论文标签
1. [LeanStream: A Speculate-and-Refine Streaming Framework for Efficient on-Device LLM Inference](/202609/04/2609.03079v1-leanstream-a-speculate-and-refine-streaming-framework-for-efficient-on-device-llm-inference)  
   标签：评分：10.0/10、query:edge-llm
   evidence：直接面向移动与嵌入式设备的端侧LLM高效推理框架，契合边缘资源约束优化
2. [DynaNDE: Dynamic Near-Data Expert Scheduling for Batched MoE Inference](/202609/04/2609.00407v1-dynande-dynamic-near-data-expert-scheduling-for-batched-moe-inference)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向NPU异构计算的MoE专家近数据调度加速LLM推理
3. [DRLM: Deep Reinforcement Learning-Based LLM Query Orchestration in Edge Environments](/202609/04/2609.00442v1-drlm-deep-reinforcement-learning-based-llm-query-orchestration-in-edge-environments)  
   标签：评分：9.0/10、query:edge-llm
   evidence：用深度强化学习在边缘异构设备间编排LLM查询，兼顾准确率与延迟。
4. [GrowPage: On-Demand KV Budgeting for Efficient LLM Reasoning Serving](/202609/04/2609.03494v1-growpage-on-demand-kv-budgeting-for-efficient-llm-reasoning-serving)  
   标签：评分：9.0/10、query:edge-llm
   evidence：面向高效LLM推理服务的按需KV缓存预算框架，直接属于LLM serving资源管理技术
5. [HBQ: Hierarchical Scaling Block Quantization with Hardware-Efficiency-Aware Design for Accurate LLM Inference](/202609/04/2609.00450v1-hbq-hierarchical-scaling-block-quantization-with-hardware-efficiency-aware-design-for-accurate-llm-inference)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向LLM推理硬件效率的层级分块量化设计
6. [How Do Prompt Variations Affect Energy Consumption in On-Device LLMs?](/202609/04/2609.01798v1-how-do-prompt-variations-affect-energy-consumption-in-on-device-llms)  
   标签：评分：8.0/10、query:edge-llm
   evidence：针对移动端和端侧LLM能耗的实证研究，直接面向边缘设备上的高效率资源使用

### 速读区论文标签
1. [Para-Pipe: Exploiting Hierarchical Operator Parallelism of ML Computational Graphs on SoCs](/202609/04/2609.04168v1-para-pipe-exploiting-hierarchical-operator-parallelism-of-ml-computational-graphs-on-socs)  
   标签：评分：8.0/10、query:edge-llm
   evidence：面向边缘异构SoC的分层算子并行与调度，属于软硬协同与算子加速方向。
2. [Budget-Aware Compression Pipeline for Single-GPU LLM Inference: Methods, Trade-offs, and Coupling Effects](/202609/04/2608.30076v2-budget-aware-compression-pipeline-for-single-gpu-llm-inference-methods-trade-offs-and-coupling-effects)  
   标签：评分：7.0/10、query:edge-llm
   evidence：在显存与吞吐约束下用剪枝、量化和KV缓存压缩搭建单GPU大模型推理流水线
3. [CateKV: On Sequential Consistency for Long-Context LLM Inference Acceleration](/202609/04/2608.30295v1-catekv-on-sequential-consistency-for-long-context-llm-inference-acceleration)  
   标签：评分：7.0/10、query:edge-llm
   evidence：对序列一致注意力头仅保留关键token的混合KV缓存，降低长上下文LLM推理内存与计算
4. [PCoMoE: Shifting MoE Inference from Monolithic Expert Selection to Fine-Grained Path Composition](/202609/04/2609.01024v1-pcomoe-shifting-moe-inference-from-monolithic-expert-selection-to-fine-grained-path-composition)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向MoE大模型推理的路径组合执行框架，细粒度剪除专家内部冗余
5. [MeanField Surrogate Modeling for Scalable Runtime Scheduling of Concurrent Heterogeneous AI Inference on Shared GPUs](/202609/04/2609.02109v1-meanfield-surrogate-modeling-for-scalable-runtime-scheduling-of-concurrent-heterogeneous-ai-inference-on-shared-gpus)  
   标签：评分：7.0/10、query:edge-llm
   evidence：平均场代理模型支持共享GPU上异构LLM/视觉推理的运行时调度，符合异构运行时效率需求
6. [Closing the Semantic-Edge Gap: Tiny Language Models for 6G Wireless Intelligence](/202609/04/2609.03747v1-closing-the-semantic-edge-gap-tiny-language-models-for-6g-wireless-intelligence)  
   标签：评分：7.0/10、query:edge-llm
   evidence：面向6G边缘设备与IoT的TinyLM综述，将TinyML压缩方法映射到语义通信架构以适配受限硬件。
7. [ContextPipe: Database-Inspired Context Assembly for Long-Horizon Agents](/202609/04/2609.00749v1-contextpipe-database-inspired-context-assembly-for-long-horizon-agents)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向长程LLM智能体的运行时上下文组装框架，与LLM serving中的上下文缓存/预算优化相关
8. [CRISP: Cliff-awaRe Input-adaptive Sparse Prefilling with Structural-Mass-Motivated Routing](/202609/04/2609.01925v1-crisp-cliff-aware-input-adaptive-sparse-prefilling-with-structural-mass-motivated-routing)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向长上下文LLM预填充阶段的输入自适应稀疏注意力路由，属于算子级加速，可纳入边端异构推理栈
9. [HeadWiseKV: Budgeted Per-Head Cache Residency for Hybrid Long-Context Language Models](/202609/04/2609.02029v1-headwisekv-budgeted-per-head-cache-residency-for-hybrid-long-context-language-models)  
   标签：评分：6.0/10、query:edge-llm
   evidence：面向混合长上下文模型的服务端KV缓存预算分配框架，使服务前内存需求可预测


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
