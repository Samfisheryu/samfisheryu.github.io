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
        about: About Me
        education: ''
        interests: ''
    design:
      background:
        gradient_mesh:
          enable: false
      name:
        size: sm
      avatar:
        size: small
        shape: circle
  - block: collection
    id: projects
    content:
      title: 'Selected Projects <a class="text-2xl font-medium text-primary-600 hover:text-primary-700 dark:text-primary-400 ml-15 align-middle" href="/publications/">view all →</a>'
      filters:
        folders:
          - projects
        featured_only: true
    design:
      view: article-grid
      columns: 2
---
