---
title: "Implementing Ci in Ansible"
date: 2020-04-08T18:35:27+07:00
draft: true
toc: false
images:
tags: 
  - ansible
  - devops
---
Today we're going to take the abstract concept of "Flow" and find out a way to make it happen in the implementation. Like mentioned in the previous article, the main value of Flow is shortening the development lead time. We shorten the development lead time by following the DevOps ideal.

> In the DevOps ideal, developers receive fast, constant feedback on their work, which enables them to quickly and independently implement, integrate, and validate their code, and have the code deployed into the production environment (either by deploying the code themselves or by others). (DevOps Handbook, part I)

> We achieve this by continually checking small code changes into our version control repository, performing automated and exploratory testing against it, and deploying it into production. This enables us to have a high degree of confidence that our changes will operate as designed in production and that any problems can be quickly detected and corrected. (DevOps Handbook, part I)

> This is most easily achieved when we have architecture that is modular, well encapsulated, and loosely-coupled so that small teams are able to work with high degrees of autonomy, with failures being small and contained, and without causing global disruptions. (DevOps Handbook, part I)

