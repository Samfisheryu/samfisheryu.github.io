---
title: 'Reliable & Resilient Collective Communication for Distributed ML'
summary: 'Closing the gap between fail-stop CCLs and the realities of large-scale GPU training/serving — through resilient communication and bandwidth-optimal AllReduce under failures.'

date: '2025-05-01T00:00:00Z'

tags:
  - Systems for ML
  - LLM
  - Distributed Systems

featured: true

links:
  - type: preprint
    provider: arxiv
    id: '2512.25059'
    label: R2CC arXiv
---

## Motivation

Modern ML training and inference span tens to tens of thousands of GPUs,
where network failures (NIC, cable, port faults) can waste **10–15 %** of
GPU hours due to slow recovery. Today's collective communication libraries
(NCCL, etc.) are *fail-stop*: any network error crashes the communicator
and forces a job restart. This project closes the gap with two complementary
threads — failure-resilient collectives, and a tighter performance lower
bound once a server has degraded.

### R2CC — Failure-resilient collective communication

A drop-in extension for NCCL that turns the CCL layer from fail-stop to
**fail-operational** under inter-node NIC/link failures. Detects faults
mid-collective, migrates in-flight transfers losslessly to healthy
connections, and adapts collective schedules to the degraded topology —
with no framework changes required.

Evaluated on a 4×8 H100 InfiniBand cluster and large-scale ML simulators
modeling up to 1024 GPUs: R2CC incurs **< 1.1 %** training overhead and
**< 3 %** inference overhead under active failure scenarios, and reduces
failure-induced overhead by **up to 92 % for training** and **98 % for
inference** versus existing fault-tolerant approaches.

📄 [Reliable and Resilient Collective Communication Library for LLM
Training and Serving]({{< ref "/publications/r2cc-2025-arxiv" >}}) (arXiv
preprint).

### Bandwidth-optimal AllReduce under bandwidth-asymmetric topologies

Once a NIC fails and a server becomes a *straggler*, what is the
unavoidable AllReduce overhead, and how do we approach it? This thread
gives the **first information-theoretic lower bound** on AllReduce
completion time under asymmetric network bandwidth, and designs a
four-stage pipelined AllReduce that closes the gap to within **2 – 6 %**
of NCCL's fault-free ring under up to 50 % bandwidth loss — whereas
state-of-the-art still incurs up to 57 % overhead.

*Manuscript under review — details available on request.*
