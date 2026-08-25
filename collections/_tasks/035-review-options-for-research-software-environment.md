---
title: "Python–Fortran Interoperability for Scientific Computing"
layout: champions
 # set date when task has been approved by consortium. Remove once completed. Will then go into history
image: https://images.pexels.com/photos/5408005/pexels-photo-5408005.jpeg?auto=compress&cs=tinysrgb&fm=webp&w=600
summary: 
workpackage: "wp1.2"
added: new
status: progress
person:
  name: You Lu
  institution: STFC Scientific Computing
  image: /assets/profilepics/generic.jpg
---


## Fit to programme

This was a proposed solution answering Task 035: Research software env in HPC, behind [WP 1.2](/workpackages/workpackage-1/).



## Summary
Many important scientific software packages are built on long-established Fortran code. This is valuable: the methods are trusted, the implementations have been tested for years, and many research communities depend on them. At the same time, new scientific workflows increasingly use Python for automation, analysis, high-throughput studies and AI/ML methods. Connecting these two worlds reliably and efficiently is not straightforward, especially on large high-performance computing (HPC) services, where different compilers, Python environments, parallel libraries and GPUs must all work together.

This project will produce practical SHAREing guidance for teams that need to provide and support Python–Fortran scientific software on HPC services. It will use CASTEP, a large materials-modelling Fortran application, as the main case study. Existing interoperability work based on f2py/f90wrap will be compared with the DL_PY2F approach, using CASTEP to identify which lessons transfer to other codes, where common build, portability and runtime issues arise, and which issues are specific to a particular code, library, compiler, GPU route or HPC environment. Public outputs will include guidance, build notes, a shareable example and a short SHAREing webpage contribution, helping code teams avoid one-off solutions and make mature scientific software easier to reuse.


