---
permalink: /
title: "Ziqing Li — Memory Systems for Long-Context LLM Inference"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

I am a Ph.D. student in Computer Science at the [School of Computer Science and Technology](http://www.cs.hust.edu.cn/index.htm), [Huazhong University of Science and Technology (HUST)](https://www.hust.edu.cn/), advised by Associate Professor [Jianxi Chen](http://faculty.hust.edu.cn/chenjianxi/zh_CN/index.htm). I am a member of the Key Laboratory of Information Storage System, Ministry of Education, led by Professor [Dan Feng](http://faculty.hust.edu.cn/dfeng/zh_CN/index.htm).

My research is in **computer systems for machine learning**, with a focus on **memory and storage systems for long-context LLM inference**. I study how to manage the **KV-cache** (the cached key/value tensors used during Transformer decoding) when contexts grow beyond the practical capacity of **HBM** (GPU high-bandwidth memory). My recent work connects storage systems, computer architecture, real-time systems, and MLSys.

## Research focus

The central question I am working on is:

> How can long-context LLM serving remain memory-efficient, latency-predictable, and semantically safe when the KV-cache becomes larger than GPU memory?

I approach this problem from several layers of the system stack:

- **Tiered KV-cache management** (placing KV blocks across GPU HBM, host DRAM, NVM, and SSD according to access hotness).
- **Identity-preserving offloading** (moving cold KV blocks out of GPU memory while preserving full-attention semantics through chunked attention and log-sum-exp merging).
- **SLO-aware scheduling** (treating KV-cache eviction and prefetch as a soft real-time scheduling problem under P99 / P99.9 latency targets).
- **Attention-dynamics prediction** (using measured attention traces to predict future salient KV blocks with small, calibrated models).
- **Unified-memory inference** (rethinking KV-cache tiers on Apple Silicon and Grace-Hopper systems where CPU and GPU memory are coherent or physically shared).

## Current systems and artifacts

### [OrchKvCache](https://github.com/lzbaclz/OrchKvCache)

A tiered KV-cache substrate for long-context LLM inference. OrchKvCache explores a four-level storage hierarchy: **GPU HBM** (fastest GPU memory), **host DRAM** (CPU memory used as a larger warm tier), **NVM** (non-volatile memory used for low-latency cold storage), and **SSD** (large-capacity cold storage). It manages KV blocks with hot/cold classification, eviction, migration, and prefetch scheduling.

The main idea is to treat KV-cache as a storage-system object rather than a passive tensor buffer. KV blocks are tracked, scored, demoted, promoted, and prefetched according to attention-derived hotness and tier-specific IO costs.

### [HALO](https://github.com/lzbaclz/HALO)

A system for **identity-preserving tier-paged KV offloading** (offloading KV-cache without discarding information needed by full attention). HALO keeps recent KV blocks on GPU and moves older cold KV blocks to host DRAM. During decoding, cold blocks are streamed back chunk by chunk and merged with the hot GPU-resident blocks using **online softmax / log-sum-exp merge** (a numerically stable way to combine partial attention results).

HALO is motivated by a simple systems principle: if eviction risks quality loss, make offloading a placement problem first. The cold data may be slow, but it should still be available to the attention computation when needed.

### [SEER](https://github.com/lzbaclz/SEER)

A soft real-time framework for KV-cache eviction and prefetch under serving objectives. SEER models long-context decoding as a sequence of jobs with deadlines and studies whether a KV policy can satisfy an **SLO** (service-level objective, such as P99 TPOT below 50 ms). It focuses on **deadline-miss probability** (the chance that a decode step exceeds its latency deadline) rather than only average quality or throughput.

SEER combines a learned attention predictor with an IO-aware scheduling policy. The policy scores each candidate block by predicted usefulness minus a tier-dependent IO penalty, while a controller adjusts the IO penalty according to observed latency slack.

### [Csp-llm / XQP](https://github.com/lzbaclz/Csp-llm)

A measurement-driven study of KV-block saliency prediction. XQP asks which cheap signals actually predict whether a KV block will be important in future attention. The investigated signals include **within-layer attention EMA** (recent attention magnitude in the same layer), **cross-layer hotness** (whether the previous layer already marked a block as important), **query-key affinity** (similarity between the current query and stored keys), and **recency** (how recently a block was used).

The main research direction is minimal sufficient modeling: prefer the smallest calibrated predictor that matches heavier baselines on real attention traces. This line of work is useful for deciding when learned KV-cache policies are genuinely better than simple attention-based heuristics, and when they are not.

### [PeerKV / UMA-LLM](https://github.com/lzbaclz/PeerKV)

A project on KV-cache management for **UMA** (unified memory architecture, where CPU and GPU share or coherently access one memory space). On Apple Silicon and NVIDIA Grace-Hopper, the old PCIe offloading model changes: the key cost is no longer always explicit data movement, but cache-line residency, compression, page migration, and memory pressure.

PeerKV studies KV-cache placement under residency states such as GPU-active, CPU-active, compressed, and swapped. It also explores selective low-bit KV compression, MLX-based inference on Apple Silicon, and cost-model-based active-memory sizing.

## Technical themes

My recent projects share several recurring technical themes:

- **KV-cache as a managed memory object**: expose KV blocks to scheduling, placement, and IO policies rather than treating them as opaque tensors.
- **Prediction with accountability**: use predictors only when their calibration, tail latency, and deployment behavior are measured.
- **Semantic safety first**: separate lossless placement from lossy eviction so that the system can reason explicitly about quality risk.
- **Tail latency over averages**: optimize and bound P99 / P99.9 behavior because interactive LLM serving is dominated by tail latency.
- **Hardware-aware memory models**: adapt the definition of a “tier” to the hardware, from PCIe-attached GPUs to coherent unified-memory platforms.

## Background interests

Beyond LLM inference, I am broadly interested in:

- storage systems and heterogeneous IO paths,
- CXL and memory disaggregation,
- GPU memory management,
- operating-system and runtime support for ML workloads,
- computer architecture for data-intensive systems.

## Contact

I am always happy to discuss systems research, long-context LLM inference, storage systems, and research collaboration. Please feel free to [email me](mailto:d202381502@hust.edu.cn).

{% include visitor-flagcounter.html %}
