---
title: ''
date: 2022-10-24
type: landing
sections:
  - block: about.biography
    id: about
    content:
      title: About
      username: admin
  - block: collection
    id: posts
    content:
      title: Recent Posts
      count: 5
      filters:
        folders:
          - post
      order: desc
    design:
      view: compact
      columns: '2'
  - block: contact
    id: contact
    content:
      title: Contact
      email: xiangyushun@sjtu.edu.cn
      autolink: true
    design:
      columns: '2'
---
