---
title: 'DMI: Performant and Flexible LLM Internal Observability'
summary: 'Treating model-internal observability as a first-class systems primitive for high-performance LLM inference.'

date: '2025-09-01T00:00:00Z'

tags:
  - Systems for ML
  - LLM

featured: true

image:
  preview_only: true

links:
  - type: github
    url: https://github.com/ProjectDMX/DMI
    label: ProjectDMX/DMI
---

## Motivation

Today's inference-time workloads increasingly depend on **timely access to a
model's internal states** — for interpretability, test-time alignment,
speculative decoding, hallucination detection, and real-time safety
monitoring. But existing approaches retrofit observation either through
PyTorch hooks (limited and slow) or engine-specific APIs (not portable),
treating observability as an afterthought rather than a systems concern.
This project pursues internal observability as a *first-class systems
primitive*, asking: what does it take for a serving stack to expose
arbitrary internal states without paying for it on the inference hot path?

### DMI — Deep Model Inspector

DMI is the first system in this line of work. It decouples observability
from the inference hot path through three pieces:

- **HookPoint** — a CUDA-graph-compatible collection primitive that can be
  placed at arbitrary locations in PyTorch models, exposing diverse internal
  states without engine-specific changes.
- **Ring²** — a GPU–CPU staging abstraction that keeps tensor capture inside
  CUDA graphs and a dedicated GPU-side ring buffer.
- A **data exporter** that drains the staged tensors asynchronously on the
  host, governed by complete or best-effort policies that adapt data rate
  and fidelity to interconnect and memory budgets.

Integrated with Hugging Face and vLLM in ~11K lines of CUDA / C++ / Python.
Across offline batch inference DMI introduces only **0.4 % – 6.8 %**
overhead and ~**6 %** in moderate online serving — **2× – 15×** lower
than baselines with comparable observability features.

📄 [Enabling Performant and Flexible Model-Internal Observability for LLM
Inference]({{< ref "/publications/dmi-arxiv" >}}) (arXiv preprint, with NSDI'26
[poster](/uploads/dmi-poster.pdf)).

💻 Code is open-sourced at **[github.com/ProjectDMX/DMI](https://github.com/ProjectDMX/DMI)** —
contributions, issues, and benchmark reports very welcome.
