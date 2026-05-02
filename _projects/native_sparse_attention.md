---
title: Native Sparse Attention Reproduction
description: Academic project on large-scale LLM training and long-context sparse attention
img: assets/img/5.jpg
category: work
importance: 2
github: https://github.com/gaspardbd/NativeSparseAttention
redirect: https://github.com/gaspardbd/NativeSparseAttention
---

Reproduced DeepSeek-AI's Native Sparse Attention with compression, selection, and sliding-window branches; implemented a PyTorch reference transformer with RoPE, RMSNorm, SwiGLU, and GQA-style attention.

Benchmarked long-context attention on A100-SXM4-40GB, reaching up to 8.3x forward and 3.36x backward speedup at 64k tokens; designed French Needle-in-a-Haystack experiments where NSA reached 97.6% accuracy.
