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
* **Phone:** (+86) 139-5553-7233
* **Email:** d202381502@hust.edu.cn
* **Affiliations:** <br>
    - Wuhan National Laboratory for Optoelectronics; Key Laboratory of Information Storage Systems<br>
    - School of Computer Science and Technology, Huazhong University of Science and Technology

Education
======
* **2023–present:** Ph.D. student in Computer Architecture, Huazhong University of Science and Technology
* **2019–2023:** B.S. in Computer Science and Technology, Beijing Jiaotong University

Research experience
======
* **LLM inference acceleration with PCIe 5.0 SSD arrays** (Apr 2025–present)  
  *Advisors:* Assoc. Prof. Jianxi Chen and Prof. Dan Feng, HUST  
  * Designed a cold/hot separation scheme combining Attention EMA, temporal decay, and access frequency for three-tier online classification of KV blocks; scheduling latency P99 &lt; 60 μs.  
  * Integrated **OrchFS (FAST ’25)** to build a GPU–DRAM–NVM–SSD four-tier hierarchy: warm data on NVM 4 KB pages, cold data aggregated into 32 KB blocks for SSD writes; raised SSD write bandwidth utilization from ~4% to 41%+.  
  * Implemented a three-stage overlapping pipeline (compute–prefetch–preload) to hide storage migration latency; bit-exact vs. a GPU-only baseline with throughput overhead &lt; 0.5%.

* **GPUDirect Storage for GPU–SSD collaborative systems** (Mar 2025–present)  
  *Advisors:* Assoc. Prof. Jianxi Chen and Prof. Dan Feng, HUST  
  * Explored **GPUDirect Storage (GDS)** for direct GPU–SSD transfers, bypassing CPU and host memory.  
  * Analyzed GPU–SSD data-path bottlenecks and storage/runtime co-design opportunities for LLM serving.

* **Stock prediction with traditional and non-traditional financial data** (Jul 2022–Oct 2022)  
  *Advisor:* Researcher Guangnan Ye, Fudan University (School of Computer Science and Financial Technology Research Institute)  
  * Built prediction models with TOPNet, LSTM, and LightGBM; used NLP and graph models for financial text and user-behavior signals.  
  * Studied federated learning for cross-institution privacy-preserving settings (e.g., bank credit scoring, medical imaging); compared **FedAvg** and **FedProx** under non-IID conditions.

Work experience
======
* **Software engineering intern — Data Platform, OLAP engine team** (Nov 2023–Feb 2024)  
  * **Xiaomi Group**  
  *Mentor:* Yaodong Zhang (Senior Software Engineer; Apache Spark committer)  
  * Implemented column-level encryption for **Parquet** files in **Apache Spark and Trino**, so sensitive columns in internal OLAP pipelines could be protected independently.

Skills
======
* **Programming:** C/C++, Java, Python, Scala, MATLAB  
* **Systems & tools:** Git, GDB, SPDK, GDS, HDFS  
* **Research interests:** Next-generation storage systems, LLM inference acceleration and optimization, RDMA

Awards
======
* **2023–2025:** First-class Academic Scholarship, HUST  
* **2020–2021:** Merit Student and Outstanding Academic Scholarship, Beijing Jiaotong University  
* **Nov 2020:** China Undergraduate Mathematical Contest in Modeling (CUMCM), second prize

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
  
<!-- Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul>
  
Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul> -->
