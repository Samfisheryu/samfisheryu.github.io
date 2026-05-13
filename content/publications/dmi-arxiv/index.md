---
title: 'Enabling Performant and Flexible Model-Internal Observability for LLM Inference'

authors:
  - me
  - Sixian Xiong
  - Yibo Zhao
  - Wei Wang
  - Zaoxing Liu

date: '2026-05-11T00:00:00Z'
publishDate: '2026-05-11T00:00:00Z'

publication_types: ['article']
publication: '*arXiv preprint arXiv:2605.11093*'
publication_short: 'arXiv'

abstract: |
  Today's inference-time workloads increasingly depend on timely access to a
  model's internal states. We present DMI, a high-speed deep model inspector
  that treats internal observability as a first-class systems primitive,
  decoupling it from the inference hot path via an asynchronous observability
  substrate built from Ring², a GPU–CPU memory abstraction for capturing and
  staging tensors, and a policy-controlled host backend that exports them. DMI
  enables the placement of observation points across a rich space of internal
  signals and diverse inference backends while preserving serving optimizations
  and adhering to tight GPU memory budgets. Our experiments demonstrate that
  DMI incurs only 0.4%–6.8% overhead in offline batch inference and an average
  of 6% in moderate online serving, reducing latency overhead by 2×–15×
  compared to existing baselines with similar observability features.

summary: 'A performant, flexible deep model inspector that turns internal LLM observability into a first-class systems primitive — only 0.4%–6.8% offline / ~6% online overhead, 2×–15× lower latency than baselines.'

tags:
  - Systems for ML
  - LLM

featured: true

links:
  - type: preprint
    provider: arxiv
    id: '2605.11093'
  - type: pdf
    url: https://arxiv.org/pdf/2605.11093
  - type: poster
    url: /uploads/dmi-poster.pdf
---
