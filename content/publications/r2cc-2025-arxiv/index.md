---
title: 'Reliable and Resilient Collective Communication Library for LLM Training and Serving'

authors:
  - Wei Wang
  - me
  - Sixian Xiong
  - Zaoxing Liu

date: '2025-12-01T00:00:00Z'
publishDate: '2025-12-01T00:00:00Z'

publication_types: ['article']
publication: '*arXiv preprint arXiv:2512.25059*'
publication_short: 'arXiv'

abstract: |
  Modern LLM training and inference can waste 10–15% of GPU hours due to slow
  recovery from network failures. We present R2CC, an NCCL-compatible
  collective communication library that maintains job progress under NIC and
  link failures via seamless RDMA connection migration, multi-NIC GPU-memory
  preregistration, NIC-affinity scheduling, and an adaptive split-AllReduce
  strategy. Evaluated on SimAI and a 2x8 H100 cluster, R2CC outperforms
  recovery-based approaches such as checkpoint/restart and existing
  fault-tolerant frameworks in end-to-end LLM training and serving under
  injected failures.

summary: 'A fault-tolerant, NCCL-compatible collective communication library that keeps LLM training and serving alive under NIC/link failures.'

tags:
  - Collective Communication
  - Fault Tolerance
  - LLM Training
  - LLM Serving
  - RDMA

featured: true

links:
  - type: preprint
    provider: arxiv
    id: '2512.25059'
  - type: pdf
    url: https://arxiv.org/pdf/2512.25059
---
