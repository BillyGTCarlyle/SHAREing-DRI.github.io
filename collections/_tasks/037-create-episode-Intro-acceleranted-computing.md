---
title: "Using GPUs to accelerate scientific workflows in python"
layout: champions
 # set date when task has been approved by consortium. Remove once completed. Will then go into history
image: https://images.pexels.com/photos/1604025/pexels-photo-1604025.jpeg?auto=compress&cs=tinysrgb&fm=webp&w=600
workpackage: "wp2.3"
added: new
status: progress
person:
  name: Ben Thorpe
  institution: University of York
  image: /assets/profilepics/generic.jpg
---


## Fit to programme

<!-- I need some pictures and links -->

This was a proposed solution answering Task 037: "Create “Introduction to Accelerated Computing” episode for existing training courses on software performance, behind [WP 2.3](/workpackages/workpackage-2/).


## Summary
We propose to create a standalone episode for submission to the software carpentries course: Performance Profiling & Optimisation (Python) course. It will cover the basics of how GPUs work at a high level alongside examples of the types of workloads that they are good at, and bad at, accelerating. 
It will also briefly cover some simple “drop-in” replacements for common python packages with some example use cases and demonstrations of the potential performance increase. 

These will include: 
- CuPy (GPU “drop in” replacement for Numpy) 
- DPNP (an Intel replacement for numpy optimised for use with multi-core cpus and GPUs) 
- Modlin and CUDF (large scale mpi CPU and GPU version of pandas) 

Finally it will cover just in time (jit) compilation, a common technique for relatively easy performance gains requiring only minor changes to existing python code.


