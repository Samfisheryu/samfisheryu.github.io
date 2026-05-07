---
# Leave the homepage title empty to use the site title
title: ''
summary: ''
date: 2022-10-24
type: landing

sections:
  - block: resume-biography-3
    content:
      username: me
      text: ''
      button:
        text: Download CV
        url: uploads/resume.pdf
      headings:
        about: ''
        education: ''
        interests: ''
    design:
      background:
        gradient_mesh:
          enable: true
      name:
        size: md
      avatar:
        size: medium
        shape: circle
  - block: markdown
    content:
      title: '📚 Research'
      subtitle: ''
      text: |-
        My research primarily centers on two directions:

        - **(1) ML systems** — from ML-for-systems to systems-for-ML, with a current focus on **telemetry and observability for LLM platforms**, distributed and fault-tolerant LLM training/serving, and collective communication.
        - **(2) Data-driven machine learning** — algorithms for learning from complex, real-world (often small, multi-cohort, high-dimensional) data, with applications in computational biology.

        I bridge algorithm design and systems engineering to deliver reliable, measurable, and scalable platforms.
    design:
      columns: '1'
  - block: collection
    id: papers
    content:
      title: Featured Publications
      filters:
        folders:
          - publications
        featured_only: true
    design:
      view: article-grid
      columns: 2
  - block: collection
    content:
      title: All Publications
      text: ''
      filters:
        folders:
          - publications
        exclude_featured: false
    design:
      view: citation
---
