---
title: 'DMI: Performant and Flexible LLM Internal Observability'
summary: 'Treating model-internal observability as a first-class systems primitive for high-performance LLM inference.'

date: '2025-09-01T00:00:00Z'

tags:
  - LLM Inference
  - Observability
  - Systems for ML

featured: true

links:
  - type: pdf
    url: /uploads/dmi-arxiv.pdf
    label: arXiv preprint
  - type: poster
    url: /uploads/dmi-poster.pdf
    label: Poster
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
  CUDA graphs and a dedicated GPU-side ring buffer, drained asynchronously
  on the host.
- A **runtime policy manager** with complete or best-effort export policies,
  adapting data rate and fidelity to interconnect and memory budgets.

Integrated with Hugging Face and vLLM in ~11K lines of CUDA / C++ / Python.
Across offline batch inference DMI introduces only **0.4 % – 6.8 %**
overhead and ~**6 %** in moderate online serving — **2× – 15×** lower
than baselines with comparable observability features.

📄 [Enabling Performant and Flexible Model-Internal Observability for LLM
Inference]({{< ref "/publications/dmi-arxiv" >}}) (arXiv preprint, with
[poster](/uploads/dmi-poster.pdf)).
