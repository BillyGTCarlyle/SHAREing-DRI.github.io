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

- [ ] Resource links
    - [ ] **Manufacturer's website**
    - [ ] Training materials
    - [ ] SHAREing testbed site

### Usage
- [ ] **Instructions for creating an account and gaining access**
- [ ] **Scheduler partition to use**
- [ ] **Direct SSH (if available)**
- [ ] **Recommended compiler**
- [ ] Recommended profiler and debugger
- [ ] Other compatible compilers
- [ ] Recommended libraries or SDKs

### Known issues
- [ ] Compilers known not to work
- [ ] Support for OpenMP or MPI

### Hints and tips
- [ ] Scheduler notes (useful sbatch options)

## Example cache diagram

Below is an example cache topology diagram for the AMD MI300X
Feel free to copy and adapt as you see fit.

```
|--------------|     |--------------|
|              |     |              |
|    HBM3      |     |    HBM3      |   (8 stacks of 24GB = 192GB total HBM3)
|    24GB      |     |    24GB      |
|--------------|     |--------------|
       |                    |
|-----------------------------------|
|       AMD INFINITY CACHE          |   (Global buffer for all XCDs)
|              256 MB               |
|-----------------------------------|
  |                               |
  |    --------        -------    |
  |    |      |        |     |    |
|---------|----|     |----|---------|
|   XCD   | L2 |     | L2 |   XCD   |
|         |    |     |    |         |   (4MB L2 per XCD)
|         |4MB |     |4MB |         |
|---------|----|     |----|---------|
      |
      |
 Detailed view
      |
      |
      V
|-----------------------------------|
|              L2 4MB               |   
|-----------------------------------|
|               XCD      |          |
|      |-------------------------|  |
|      | Compute Unit            |  |
|      ||---------------------|  |  |
|      || L1 instruction 64KB |  |  |
| 38 x ||---------------------|  |  |   (38 CUs per XCD.  L1 instruction cache
|      || L1 Constant 16KB    |  |  |   shared between pairs of CUs)
|      ||---------------------|  |  |
|      || L1 Data 32KB        |  |  |
|      ||---------------------|  |  |
|      || L1 Scalar 16KB      |  |  |
|      ||---------------------|  |  |
|      || LDS 64KB            |  |  |
|      ||---------------------|  |  |
|      |-------------------------|  |
|                                   |
|-----------------------------------|

```
