---
title: "FLAME GPU Benchmarking and Profiling for AMD"
layout: champions
 # set date when task has been approved by consortium. Remove once completed. Will then go into history
image: https://images.pexels.com/photos/7293756/pexels-photo-7293756.jpeg?auto=compress&cs=tinysrgb&fm=webp&w=600
status: progress
added: new
workpackage: "wp1.1"
person:
  name: Paul Richmond
  institution: University of Sheffield
  image: /assets/profilepics/generic.jpg
---

## Fit to programme

This was a proposed solution answering Task 036: Community GPU codes [WP 1.1](/workpackages/workpackage-1/).


<!-- I need some pictures and links -->


## Summary

FLAME GPU is a widely used platform for large-scale agent-based modelling (ABM), enabling researchers to simulate millions of interacting agents on modern graphics processors (GPUs). There were 786 users over the last year performing upwards of 1.5M simulations. 

Recent work, undertaken through a collaboration with the UKRI Living Benchmarks project, has introduced experimental support for AMD GPUs [1] alongside an initial synthetic benchmark for evaluating performance [2]. This project will build on that foundation by developing a comprehensive benchmark suite that better reflects the diverse ways researchers use FLAME GPU. New benchmarks will include a spatial Boids model, grid-based models representative of NetLogo-style simulations, ensemble workloads that capture repeated stochastic simulations, and realistic data input/output patterns. 

Alongside benchmark development, we will undertake detailed performance analysis and profiling of AMD hardware, comparing results with equivalent NVIDIA GPU systems. The project will also produce practical documentation describing profiling tools and workflows for AMD hardware, helping researchers and research software engineers transition from the more established NVIDIA ecosystem. 

[1] https://github.com/FLAMEGPU/FLAMEGPU2/pull/1379 
[2] https://github.com/ukri-bench/benchmark-flamegpu/issues

