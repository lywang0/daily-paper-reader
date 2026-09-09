# 日报 · 2026-09-09

- 生成时间：2026-09-09 22:07:49 UTC
- 当次推荐总数：14
- 精读区：6
- 速读区：8

## 今日简报（AI）
今日14篇论文聚焦LLM推理优化，精读6篇、速读8篇，重点在KV缓存与调度效率。  
最值得看两个方向：面向长上下文的NVM感知KV缓存量化（9.0分）与统一模型路由/缓存管理框架（9.0分），直击存储带宽和延迟瓶颈。  
建议普通读者从KV缓存压缩入手，可结合“MetaKV自适应压缩”和“截止时间感知分块预填充”加速理解。

## 精读区
1. [Interface-Aware KV Cache Quantization for Dense On-Chip NVM in Long-Context LLM Decoding](/202609/09/2609.05764v1-interface-aware-kv-cache-quantization-for-dense-on-chip-nvm-in-long-context-llm-decoding) （9.0/10）
2. [Unified AI Gateway: A Framework for Joint Model Routing and KV Cache Management](/202609/09/2609.06940v1-unified-ai-gateway-a-framework-for-joint-model-routing-and-kv-cache-management) （9.0/10）
3. [Hardware-Aware FP4 FlashAttention-4](/202609/09/2609.04105v1-hardware-aware-fp4-flashattention-4) （8.0/10）
4. [Toward Sustainable Distributed LLM Inference: A Systems Synthesis and Research Agenda for an Energy-, Carbon-, and Cache-Aware llm-d Control Plane](/202609/09/2609.05565v1-toward-sustainable-distributed-llm-inference-a-systems-synthesis-and-research-agenda-for-an-energy--carbon--and-cache-aware-llm-d-control-plane) （8.0/10）
5. [All for 1-Bit: Towards Genuine 1-Bit Post-Training Quantization for LLMs](/202609/09/2609.06161v1-all-for-1-bit-towards-genuine-1-bit-post-training-quantization-for-llms) （8.0/10）
6. [AutoUVM: Automated Prefetching Framework for LLMs under UVM Oversubscription](/202609/09/2609.06172v1-autouvm-automated-prefetching-framework-for-llms-under-uvm-oversubscription) （8.0/10）

## 速读区
1. [Accuracy is Not Enough: A Divergence-Based Approach to Evaluate Fidelity Loss in Quantized LLMs](/202609/09/2609.07664v1-accuracy-is-not-enough-a-divergence-based-approach-to-evaluate-fidelity-loss-in-quantized-llms) （8.0/10）
2. [Deadline-Aware Adaptive Prefill Chunking for Efficient Large Language Model Serving](/202609/09/2609.07883v1-deadline-aware-adaptive-prefill-chunking-for-efficient-large-language-model-serving) （8.0/10）
3. [MetaKV: Adaptive KV Cache Compression for Constrained LLM Inference](/202609/09/2609.07966v1-metakv-adaptive-kv-cache-compression-for-constrained-llm-inference) （8.0/10）
4. [A Measurement Study of LLM Inference Trade-offs Across Edge Continuum Hardware](/202609/09/2609.08307v1-a-measurement-study-of-llm-inference-trade-offs-across-edge-continuum-hardware) （8.0/10）
5. [Signed Rescue Routing: Harm-Aware Cascades for Efficient LLM Inference](/202609/09/2609.07786v1-signed-rescue-routing-harm-aware-cascades-for-efficient-llm-inference) （7.0/10）
6. [Do Dynamic Routers Need Memory? HeRo: History-Aware Routing for Efficient LLM Inference](/202609/09/2609.08189v1-do-dynamic-routers-need-memory-hero-history-aware-routing-for-efficient-llm-inference) （7.0/10）
7. [Train Overcomplete, Deploy Compact: Scaling Recovery Capacity for Structured LLM Pruning](/202609/09/2609.06974v1-train-overcomplete-deploy-compact-scaling-recovery-capacity-for-structured-llm-pruning) （6.0/10）
8. [FastE: Readout-Triggered Token Compression for LLM Embedding Inference](/202609/09/2609.08407v1-faste-readout-triggered-token-compression-for-llm-embedding-inference) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
