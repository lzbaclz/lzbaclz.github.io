---
permalink: /
title: "Ziqing Li"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

I am a Ph.D. student in Computer Science at the [School of Computer Science and Technology](http://www.cs.hust.edu.cn/index.htm), [Huazhong University of Science and Technology (HUST)](https://www.hust.edu.cn/), advised by Associate Professor [Jianxi Chen](http://faculty.hust.edu.cn/chenjianxi/zh_CN/index.htm). I am a member of the Key Laboratory of Information Storage System, Ministry of Education, led by Professor [Dan Feng](http://faculty.hust.edu.cn/dfeng/zh_CN/index.htm).

My research is in **memory systems for long-context LLM inference**. I study how to manage the **KV-cache** (the key/value tensors cached during Transformer decoding) when contexts become too large for **HBM** (GPU high-bandwidth memory). My work connects storage systems, computer architecture, MLSys, and real-time serving.

## Research question

> How can long-context LLM serving remain memory-efficient, latency-predictable, and semantically safe when the KV-cache becomes larger than GPU memory?

I approach this question by treating KV-cache as a first-class managed memory object rather than an opaque tensor buffer.

## Research stack

My current projects form a coherent stack for long-context LLM memory systems:

| Layer | Question | System |
| --- | --- | --- |
| Tiered substrate | How should KV blocks move across HBM, DRAM, NVM, and SSD? | [OrchKvCache](https://github.com/lzbaclz/OrchKvCache) |
| Semantic safety | Can offloading preserve full-attention semantics? | [HALO](https://github.com/lzbaclz/HALO) |
| SLO control | Can KV placement satisfy P99 / P99.9 serving targets? | [SEER](https://github.com/lzbaclz/SEER) |
| Saliency measurement | Which signals actually predict future important KV blocks? | [XQP](https://github.com/lzbaclz/xqp) |
| Hardware-aware memory | What is a memory “tier” on unified-memory systems? | [PeerKV / UMA-LLM](https://github.com/lzbaclz/PeerKV) |

More details are collected on the [Systems](/systems/) page.

## Technical themes

- **Tiered KV-cache management**: placing KV blocks across GPU HBM, host DRAM, NVM, and SSD according to access hotness and IO cost.
- **Identity-preserving offloading**: moving cold KV blocks out of GPU memory while preserving full-attention semantics through chunked attention and log-sum-exp merging.
- **SLO-aware scheduling**: treating KV-cache eviction and prefetch as a soft real-time scheduling problem under P99 / P99.9 latency targets.
- **Attention-dynamics prediction**: using measured attention traces to predict future salient KV blocks with small, calibrated models.
- **Unified-memory inference**: rethinking KV-cache placement on Apple Silicon and Grace-Hopper systems where CPU and GPU memory are coherent or physically shared.

## Broader interests

Beyond long-context LLM inference, I am interested in storage systems, heterogeneous IO paths, CXL and memory disaggregation, GPU memory management, and OS/runtime support for ML workloads.

## Contact

I am happy to discuss systems research, long-context LLM inference, storage systems, and research collaboration. Please feel free to [email me](mailto:d202381502@hust.edu.cn).

{% include visitor-flagcounter.html %}
