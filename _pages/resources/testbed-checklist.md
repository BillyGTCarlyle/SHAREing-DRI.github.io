---
layout: splash
title: Hardware Testbed Checklist
permalink: /resources/testbed-checklist
classes: wide
---

# Hardware Testbed Checklist

## Purpose

## Checklist

### Hardware name

Detailed description, including:
- [ ] Background (if any)
- [ ] Primary purpose / intended use-case

### Specifications
- [ ] Detailed specs
    - Host:
        - [ ] Number of nodes available
        - [ ] Number of processors/accelerators per node
        - [ ] RAM per node
        - [ ] Network fabric used
    - Hardware:
        - [ ] Accelerator memory
        - [ ] Chip architecture (CPU and accelerator if applicable)
        - [ ] Accelerator cores (CUs, CUDA cores, Tensix cores, etc.)
        - [ ] Cache topology
            - [ ] Diagram

- [ ] Benchmarks
    - [ ] Memory bandwidth (Stream or BabelStream)

- [ ] Link to SHAREing testbed site

### Usage
- [ ] Instructions for creating an account and gaining access
- [ ] Scheduler partition to use
- [ ] Direct SSH (if available)
- [ ] Recommended compiler
- [ ] Other compatible compilers
- [ ] Recommended libraries or SDKs

### Known issues
- [ ] Compilers known not to work
- [ ] Support for OpenMP or MPI

### Hints and tips
- [ ] Scheduler notes (useful sbatch options)
