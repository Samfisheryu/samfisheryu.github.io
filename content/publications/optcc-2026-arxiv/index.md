---
title: "Don't Let a Few Network Failures Slow the Entire AllReduce"

authors:
  - Peiqing Chen
  - Jiedong Jiang
  - me
  - Yuefeng Wang
  - Sixian Xiong
  - Wei Wang
  - Zaoxing Liu

date: '2026-06-01T00:00:00Z'
publishDate: '2026-06-01T00:00:00Z'

publication_types: ['article']
publication: '*arXiv preprint arXiv:2606.01680*'
publication_short: 'arXiv'

abstract: |
  Network failures are common in large GPU clusters and can force collective
  communication libraries to route around degraded NICs, leaving the affected
  server on the critical path of standard ring AllReduce. We derive an
  information-theoretic lower bound for AllReduce completion time under
  asymmetric network bandwidth, showing that a straggler with at least half of
  its original bandwidth need only impose small unavoidable overhead. We then
  design OptCC, a four-stage pipelined AllReduce algorithm that approaches
  this bound. In SimAI experiments, OptCC completes AllReduce within 2%–6% of
  NCCL's fault-free ring performance under practical failures with up to 50%
  bandwidth loss, while prior fault-tolerant schemes can incur up to 57%
  overhead.

summary: "OptCC gives an information-theoretic lower bound and a four-stage pipelined AllReduce algorithm for bandwidth-asymmetric failures, staying within 2%–6% of NCCL's fault-free ring under up to 50% bandwidth loss."

tags:
  - Systems for ML
  - LLM
  - Distributed Systems

featured: true

links:
  - type: preprint
    provider: arxiv
    id: '2606.01680'
  - type: pdf
    url: https://arxiv.org/pdf/2606.01680
---
