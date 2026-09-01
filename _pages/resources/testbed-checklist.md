---
layout: splash
title: Hardware Testbed Checklist
permalink: /resources/testbed-checklist
classes: wide
---

# Hardware Testbed Checklist

Many universities in the UK host HPC testbeds and test nodes within their organisation.
System descriptions are not currently standardised, leading to varying levels of detail in testbed documentation.

This page provides a checklist of information to be provided, where possible, such that users may clearly understand: 
- What the hardware is
- What it's for
- How to use it

When writing documentation for a hardware testbed, use the checklist as a guide.
All items should be added if possible, items in bold are considered essential.

## Checklist

### Hardware name

Detailed description, including:
- [ ] **Primary purpose / intended use-case**
- [ ] Background (if any)

### Specifications
- [ ] **Detailed specs**
    - Host:
        - [ ] **Number of nodes available**
        - [ ] **Number of processors/accelerators per node**
        - [ ] **RAM per node**
        - [ ] Network fabric used
    - Hardware:
        - [ ] **Total memory**
        - [ ] **Accelerator cores (CUs, CUDA cores, Tensix cores, etc.)**
        - [ ] Chip architecture (CPU and accelerator if applicable)
        - [ ] Cache topology
            - [ ] Diagram

- [ ] Benchmarks
    - [ ] Memory bandwidth (Stream or BabelStream)

- [ ] Link to SHAREing testbed site

### Usage
- [ ] **Instructions for creating an account and gaining access**
- [ ] **Scheduler partition to use**
- [ ] **Direct SSH (if available)**
- [ ] **Recommended compiler**
- [ ] Other compatible compilers
- [ ] Recommended libraries or SDKs

### Known issues
- [ ] Compilers known not to work
- [ ] Support for OpenMP or MPI

### Hints and tips
- [ ] Scheduler notes (useful sbatch options)
