# 日报 · 2026-06-11

- 生成时间：2026-06-11 22:21:56 UTC
- 当次推荐总数：7
- 精读区：1
- 速读区：6

## 今日简报（AI）
今日聚焦AMD NPU上量化LLM推理的混合精度库TileFuse，并速读KV缓存压缩、上下文压缩及GEMM模拟三篇论文。  
最值得精读的是TileFuse（10分）——它针对AMD NPU设计融合混合精度内核，显著提升量化LLM推理效率；速读中可关注KV缓存压缩与端到端上下文压缩两个方向。  
建议优先精读TileFuse以获取NPU优化实战思路，再根据兴趣浏览压缩与模拟方法。

## 精读区
1. [TileFuse: A Fused Mixed-Precision Kernel Library for Efficient Quantized LLM Inference on AMD NPUs](/202606/11/2606.11357v1-tilefuse-a-fused-mixed-precision-kernel-library-for-efficient-quantized-llm-inference-on-amd-npus) （10.0/10）

## 速读区
1. [Still: Amortized KV Cache Compaction in a Single Forward Pass](/202606/11/2606.07878v1-still-amortized-kv-cache-compaction-in-a-single-forward-pass) （7.0/10）
2. [End-to-End Context Compression at Scale](/202606/11/2606.09659v1-end-to-end-context-compression-at-scale) （7.0/10）
3. [A Fast Locality Simulator for GEMM Design-Space Exploration on Multi-Chiplet GPUs](/202606/11/2606.11716v1-a-fast-locality-simulator-for-gemm-design-space-exploration-on-multi-chiplet-gpus) （7.0/10）
4. [Making Locality-aware GEMM Compatible with Page-Granularity Placement on Chiplet GPUs](/202606/11/2606.11718v1-making-locality-aware-gemm-compatible-with-page-granularity-placement-on-chiplet-gpus) （7.0/10）
5. [Domain-Adapted Small Language Models with Hybrid Post-Processing: Achieving Cost-Efficient, Low-Latency Multi-Label Structured Prediction via LoRA Fine-Tuning on Scarce Data](/202606/11/2606.05781v2-domain-adapted-small-language-models-with-hybrid-post-processing-achieving-cost-efficient-low-latency-multi-label-structured-prediction-via-lora-fine-tuning-on-scarce-data) （6.0/10）
6. [Task-Aware Structured Memory for Dynamic Multi-modal In-Context Learning](/202606/11/2606.11853v1-task-aware-structured-memory-for-dynamic-multi-modal-in-context-learning) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
