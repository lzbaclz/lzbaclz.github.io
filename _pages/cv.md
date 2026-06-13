---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

<div class="cv-download-links">
  <a href="{{ base_path }}/files/cv.pdf" class="btn btn--primary">CV (PDF)</a>
</div>

Contact
======
* **Email:** d202381502@hust.edu.cn
* **Affiliations:** <br>
    - School of Computer Science and Technology, Huazhong University of Science and Technology<br>
    - Key Laboratory of Information Storage System, Ministry of Education

Education
======
* **2023–present:** Ph.D. student in Computer Architecture, Huazhong University of Science and Technology
* **2019–2023:** B.S. in Computer Science and Technology, Beijing Jiaotong University

Research interests
======
* Memory systems for long-context LLM inference
* KV-cache management, offloading, compression, and scheduling
* Storage systems and heterogeneous IO paths
* CXL and memory disaggregation
* GPU memory management and MLSys runtime support

Research experience
======
* **Long-context LLM memory systems** (2025–present)  
  *Advisors:* Assoc. Prof. Jianxi Chen and Prof. Dan Feng, HUST  
  * Study KV-cache as a managed memory object for long-context LLM inference, including tiered placement, offloading, prefetch, and scheduling.
  * Built research systems around GPU HBM, host DRAM, NVM, SSD, and unified-memory platforms.
  * Explored exact placement, lossy eviction, calibrated saliency prediction, and SLO-aware scheduling as separate design modes.

* **LLM inference acceleration with PCIe 5.0 SSD arrays** (Apr 2025–present)  
  *Advisors:* Assoc. Prof. Jianxi Chen and Prof. Dan Feng, HUST  
  * Designed a hot/cold separation scheme using attention EMA, temporal decay, and access frequency for online KV-block classification.
  * Integrated heterogeneous storage ideas from OrchFS to build a GPU–DRAM–NVM–SSD hierarchy for KV-cache management.
  * Studied overlapping compute, prefetch, and preload pipelines to reduce storage migration latency.

* **GPUDirect Storage for GPU–SSD collaborative systems** (Mar 2025–present)  
  *Advisors:* Assoc. Prof. Jianxi Chen and Prof. Dan Feng, HUST  
  * Explored GPUDirect Storage (GDS) for direct GPU–SSD data paths, bypassing unnecessary CPU-side copies.
  * Analyzed GPU–SSD bottlenecks and storage/runtime co-design opportunities for LLM serving.

* **Stock prediction with traditional and non-traditional financial data** (Jul 2022–Oct 2022)  
  *Advisor:* Researcher Guangnan Ye, Fudan University  
  * Built prediction models with TOPNet, LSTM, and LightGBM; used NLP and graph models for financial text and user-behavior signals.
  * Studied federated learning for cross-institution privacy-preserving settings and compared FedAvg and FedProx under non-IID conditions.

Work experience
======
* **Software engineering intern — Data Platform, OLAP engine team** (Nov 2023–Feb 2024)  
  * **Xiaomi Group**  
  *Mentor:* Yaodong Zhang, Senior Software Engineer; Apache Spark committer  
  * Implemented column-level encryption for Parquet files in Apache Spark and Trino, so sensitive columns in internal OLAP pipelines could be protected independently.

Selected systems
======
* **OrchKvCache:** tiered KV-cache management across GPU HBM, host DRAM, NVM, and SSD.
* **HALO:** identity-preserving KV offloading through chunked attention and log-sum-exp merge.
* **SEER:** SLO-aware KV-cache eviction and prefetch under P99 / P99.9 latency targets.
* **XQP:** measurement-driven KV-block saliency prediction.
* **PeerKV / UMA-LLM:** KV-cache residency and compression on unified-memory systems.

Skills
======
* **Programming:** C/C++, Java, Python, Scala, MATLAB
* **Systems & tools:** Git, GDB, SPDK, GPUDirect Storage, HDFS, Linux systems programming
* **Research areas:** storage systems, LLM inference systems, GPU memory systems, memory disaggregation, MLSys

Awards
======
* **2023–2025:** First-class Academic Scholarship, HUST
* **2020–2021:** Merit Student and Outstanding Academic Scholarship, Beijing Jiaotong University
* **Nov 2020:** China Undergraduate Mathematical Contest in Modeling (CUMCM), second prize

Publication record
======
A concise publication and manuscript list is maintained on the [Publications](/publications/) page to avoid duplicating the same records in multiple places.
