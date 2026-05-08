---
title: 'Reliable & Resilient Collective Communication for Distributed ML'
summary: 'Closing the gap between fail-stop CCLs and the realities of large-scale GPU training/serving — through resilient communication and bandwidth-optimal AllReduce under failures.'

date: '2025-05-01T00:00:00Z'

tags:
  - Collective Communication
  - Fault Tolerance
  - LLM Training
  - LLM Serving

featured: true

links:
  - type: preprint
    provider: arxiv
    id: '2512.25059'
    label: R2CC arXiv
---

## Overview

Modern ML training and inference span tens to tens of thousands of GPUs,
where network failures (NIC, cable, port faults) can waste **10–15 %** of
GPU hours due to slow recovery. Today's collective communication libraries
(NCCL, etc.) are *fail-stop*: any network error crashes the communicator
and forces a job restart. This project closes the gap with two complementary
threads:

### 1. R2CC — Failure-resilient collective communication

A drop-in extension for NCCL that turns the CCL layer from fail-stop to
**fail-operational** under inter-node NIC/link failures. Detects faults
mid-collective, migrates in-flight transfers losslessly to healthy
connections, and adapts collective schedules to the degraded topology —
with no framework changes required.

**Results** (4×8 H100 InfiniBand cluster + simulated up to 1024 GPUs):

- **< 1.1 %** training overhead and **< 3 %** inference overhead under
  active failure scenarios
- Compared to existing fault-tolerant approaches, R2CC reduces failure-
  induced overhead by **up to 92 % for training** and **98 % for inference**

### 2. Bandwidth-optimal AllReduce under bandwidth-asymmetric topologies

Extends the resilience story by asking: once a NIC fails and a server
becomes a *straggler*, what is the unavoidable AllReduce overhead, and how
do we approach it? We give the **first information-theoretic lower bound**
on AllReduce completion time under asymmetric network bandwidth, and design
a four-stage pipelined AllReduce that closes the gap to within **2–6 %** of
NCCL's fault-free ring under up to 50 % bandwidth loss (whereas
state-of-the-art still incurs up to 57 % overhead).

*Manuscript under review — details available on request.*

## Papers

- **[Reliable and Resilient Collective Communication Library for LLM
  Training and Serving]({{< ref "/publications/r2cc-2025-arxiv" >}})** —
  arXiv preprint (R2CC).
