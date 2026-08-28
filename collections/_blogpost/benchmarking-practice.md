---
layout: blog
# Unique URL for this post
permalink: /blogpost/benchmarking-practice/
# Main title of the post
title: "A 'how-to-guide' to benchmarking"
# E.g., Retreat, Workshop, Update
category: 
# Optional but recommended
subtitle: ""
# Full name of the author
author: "Thomas Flynn"
author_image: "/assets/profilepics/thomas.jpg"
# Main post image
hero_image: "/assets/images/stopwatch.jpg"
# Date of the post, please use the format: YYYY/MM/DD
date: 2026-08-28 # CHANGE!
social_links:
  - title: LinkedIn
    url: "https://www.linkedin.com/company/shareing/"
  - title: Bluesky
    url: "https://bsky.app/profile/shareing.bsky.social"
  - title: Email
    url: "mailto:shareing@durham.ac.uk"
---

Benchmarking can sound simple: run a code, measure how long it takes. However,
this approach hides a lot of nuance. It can be very easy to report benchmarking
results which are unreliable or sell a narrative. We want our benchmarking to
run like clean, reproducible experiments wherever possible.

In this blog we run through some basic steps to get started with benchmarking,
and signpost some resources to consider in future benchmarking.

# Getting started

The aim of getting started with benchmarking is essentially choosing the
software to benchmark with the hardware to benchmark on, and then document in
detail the steps needed to get the benchmark built and running. This is
particularly important as there are many variables in these steps which can
impact performance. We must remember: **documentation is key!**

## 1. The code

To get started, we need a **benchmark**. If you are working on a code that does
not currently ship with any benchmarks, SHAREing has written up some basic
guidelines on how to write a representative benchmark which we link
[here](/assets/pdfs/shareing-benchmark-guide.pdf).

There are different types of benchmarks such as microbenchmarks, synthetic and
application benchmarks. Microbenchmarks are typically very small code blocks
that can be used to measure low-level performance...

## 2. Hardware

Hardware is a vital part of benchmarking. When beginning, pick hardware that
you are interested in. This might be a system that you often use, or you might
have in mind a hardware comparison. For example, you may be using a local
institutional cluster but have in mind using a regional or national cluster.
Hardware details can often be found on cluster documentation, so make a note of
what you plan to use. If you are interested in trying hardware that you
currently do not have access to, look into whether this is available through
testbeds. For more information on available testbeds, please see the testbeds
portal on the SHAREing webpages [here](/hpc-testbeds).

This can be a deep rabbit hole, but to begin with we just note down the
hardware that we are running on. The easiest option is to just note down what
is listed on the documentation. For more information we can use tools such as
```bash
likwid-topology
``` 
and MAQAO, or files such as 
```bash
less /proc/cpuinfo
``` 
on Linux systems.  However, these outputs are typically very detailed and go
far beyond the data often used in simple hardware comparisons for benchmarking.
Some example values, given by `likwid-topology` are core counts, cache sizes
and NUMA domains.

## 3. Software dependencies

As with hardware a code's software dependencies can impact performance, and so
what we recommend with all of this is document. We want our benchmarking to be
as reproducible as possible, so we document on a specific system any specific
software. For example, note down compilers, libraries and version numbers.

On a cluster we can just note down the dependencies using the 
```bash
module list
```
and note down the output. An alternative and more granular method for noting
the hardware and software environment of your benchmarking work is to use the
[MachineState](https://github.com/RRZE-HPC/MachineState) tool, though we do not
go into detail on this tool here.

## 4. Build

We just simply follow and document the build steps. This may include typical
compiler flags used in the production code. Build steps are a classic example
of a step where the configuration can change code performance, so we just
simply note down what we begin with. Then, once we have begun to collate
results, we can see about whether there are different compilation options we
can use, and then compare software performance.

## 5. Run

For a first run, we recommend running naively; do not worry too much how you
are configuring the job, we just want an indicative run of the code. We can
play around with parallel resources, etc. in the future, but to begin with we
just pick a certain setup and run. This is to verify that the code runs, and
check some basic resource usage such as total runtime and memory footprint.

On a SLURM based system we can use 
```bash
sacct -j <job-number> --format=elapsed,maxRSS
```
to give the total runtime (`elapsed`) and the memory footprint (`maxRSS`). 

Alternatively, we can time an application using `/usr/bin/time` which is a
standardised tool on Linux (it is recommended to avoid just using `time`), and
then reading off the `real` time from this output. Then for total memory usage,
on most Linux systems we have access to the `valgrind` tool which is used in
detecting memory leaks, etc.
```bash
valgrind --tool=massif ./code
```

We note these results for future reference, but we now have some representative
results for how our code performs. We can use this in different ways:
1. Hardware comparisons - we can repeat this across different hardware
   platforms
2. Tweak resource allocations - how do we configure the parallel resources, or
   change our job scripts
3. Software engineering and optimisation - what if we change something in the
   code
4. Varying dependencies - we might change compiler and libraries
5. Many more...

We will touch on some of these ideas below.

# Further things to consider

Now that we have documented our hardware, software and basic workflows for
building and running the benchmark, we can then consider what other controls we
have at our disposal.

## 6. Compiler optimisations

As mentioned above, build steps are an aspect of benchmarking that can have
significant effects on performance. Some hardware may have advanced
instructions that can be exploited via compiler flags. 

There is vast documentation online for compilers and their flags, often with
pages dedicated to optimisation flags. Similarly, tools like
[MAQAO](https://www.maqao.org/) can suggest compiler flags that can exploit
hardware features. As with all aspects of benchmarking, comparison is key.

One feature of MAQAO which can help here is its **compare reports** feature. We
can create a simple workflow of running an individual benchmark for each
compiler optimisation we may be exploring with MAQAO. Then, we can collect
these different runs together to explore how the different compiler
optimisations vary the runtime and more detail performance features of the
code. This can become a very detailed form of analysis, so we leave it to the
reader to explore MAQAO in further detail.

## 7. Affinity

As we have discussed, restricting any variables that we have control over is
always desirable. For parallel applications we have the common issue of
affinity: OpenMP threads and MPI ranks can wander, i.e., they can change the
physical core that they are assigned to which can then create performance
inefficiencies as data then needs to be moved in memory.

There are different ways of **pinning** our processes and we will look at a few
examples here.

### OpenMP

With the OpenMP library we can set environment variables to control out thread
affinity. The two primaru environment variables are `OMP_PLACES` and
`OMP_PROC_BIND`. The `OMP_PLACES` specifies the location of the threads, whilst
`OMP_PROC_BIND` specifies how these threads are bound to these locations. This
is easier to see in practice
```bash
export OMP_PLACES=core
export OMP_PROC_BIND=close
```
will bind threads to physical cores, and will ensure that these are cores are
close to one another, i.e., typically filling them out in logical order. So for
a four thread application this will likely bind to cores labelled 0-3. We will
look at this further below, but often when specifying thread affinity it is
often good practice to state which the location threads should be pinned to.

We can also place threads by `socket` and `thread` rather than `core` as above
for `OMP_PLACES`. We can specify binding to off or on by the following
```bash
export OMP_PROC_BIND=false
export OMP_PROC_BIND=true
```
respectively. Rather than closely packed we can spread them out with
`OMP_PROC_BIND=spread` or allocate them to the master thread with
`OMP_PROC_BIND=master`. There are multiple options, but the main aim here is
fix affinity, we will touch on thread placement in subsequent sections.

### MPI

We can often control MPI rank pinning through the `mpirun` command. There can
be slight variations in MPI libraries, so it always worth checking
documentation, but taking OpenMPI as an example we can bind to cores, sockets,
NUMA domains, etc. using 
```bash
mpirun -n 16 --bind-to <foo>
```
where `<foo>` can take: `slot`, `hwthread`, `core`, `l1cache`, `l2cache`,
`l3cache`, `socket`, `numa`, `board`, `cpu-list`, and `none`. This defaults to
`core` which for applications will be suitable, but against varying these
bindings can prove useful for tuning the runtime of certain applications.
Alternatively, there are also `--bind-to-core` and `--bind-to-socket` flags.

### LIKWID

The [LIKWID tool suite](https://github.com/RRZE-HPC/likwid) also gives us an
interface to select cores to pin too:
```bash
likwid-pin -c 0-3 ./code
```
For an MPI or hybrid parallel application we can also use
```bash
likwid-mpirun -np 4 ./code
```
and as with `likwid-pin` we can be specific in the physical cores we wish to
pin our ranks and threads to. Once more, we simply signpost LIKWID here as a
tool that is incredibly useful in performance-oriented software development.

## 8. Placement

For parallel applications we often can have choices about where threads, ranks,
etc. are placed. For example, where do we assign ranks for a GPU-aware MPI
application. Convention dictates one rank per GPU, but what about if we have an
OpenMP+MPI application. Do we place a rank per NUMA domain? Or socket? Or node?
There is no obvious answer to these questions, but benchmarking can hold the
key. We can design our experiments to look into different methods of placing
our processors.

One example is that for some compute-bound codes, close processor placement can
be beneficial. Yet, for a code that is memory-bound it can be useful to place
cores across different NUMA domains so they can exploit greater memory
bandwidth across different memory regions.

### OpenMP

We saw how with the `OMP_PLACES` and `OMP_PROC_BIND` flags how we can specify
the locations and affinity of threads on hardware. We can be even more exact
with thread placement by specifying the physical core IDs
```bash
OMP_PLACES="{0,1,2,3},{4,5,6,7},{8,9,10,11},..."
```
We can also verify the thread affinity and placement with
```bash
export OMP_DISPLAY_AFFINITY=TRUE
```
which prints the pinning at runtime.

### MPI

We can be very specific to list the processor IDs using
```bash
mpirun --cpu-list "0,1,2,4"
```
which can also be fed as an argument to the `--bind-to` flag. Similarly, we
might want to allocate ranks in a round robin fashion e.g., by socket so that
the cores can be spread out across the available sockets. To do this we use
```bash
mpirun --map-by <foo>
```
where `<foo>` can take many values: `slot`, `hwthread`, `core`, `L1cache`,
`L2cache`, `L3cache`, `socket`, `numa`, `board`, `node`, `sequential`,
`distance`, and `ppr`. Many of these naming conventions are intuitive, however,
care needs to be taken....

### LIKWID

We have already seen with `likwid-pin` and `likwid-mpirun` that we have a high
degree of control with the thread and rank placement, and so this can be a
quicker way to test and configure different pinning and placement schemes.

LIKWID allows for specifying cores by node, socket, NUMA domain, etc.

## 9. Scaling

A common aspect of benchmarking is scaling, i.e., exploring how runtime and
other metrics vary with core count. We briefly look over the two predominant
forms of scaling: strong and weak.

### Strong scaling

Put simply, strong scaling is increasing core count for fixed problem size. In
an ideal case, doubling the core count should half the runtime. In reality this
is never true for many reasons, not least because applications tend to have a
serial portion which will retain fixed for increasing core counters. 

A simple way of producing a strong scaling analysis for an MPI application is
```bash
for i in {1..128}
do
  /usr/bin/time mpirun -n $i ./code
done
```
By default this will print timing data to standard output, so we can pipe this
data simply into a `*.csv` file and generate strong scaling plots. 

### Weak scaling

In short, weak scaling is increasing core count with increasing problem size,
so the work per core stays (in theory) approximately constant.

We can automate this as for strong scaling by iteratively allocating more and
more cores, however, we need to equally scale up the problem size. This could
be something like the following
```bash
for i in {1 2 4 8}
do
  /usr/bin/time mpirun -n $i ./code --input file_$i.dat
done
```
we where are doubling the core count each at iteration, and are supplying an
input file which doubles the problem size.

There is a difficult with weak scaling and that is how does the problem scale?
If the problem scales linearly then doubling a scaling parameter, e.g., the
number of grid points for the problem is simple. However, many problems may
scale logarithmically and so greater care has to be taken.

## 10. Metrics

Above we have seen several variables we can explore from affinity to placement
to scaling. In all of this, our observable is total runtim which can then use
to look at speeds up in scaling analyses. However, there are other metrics we
can use. For example, we might want to explore domain specific metrics.
It can be really useful in defining a metric that is specific to an algorithm
or code, e.g., for lattice-based methods, something like the 'number of lattice
site updates' can be really useful for code specific performance metrics.
Alternatively, we can repeat above methods but gather metrics from hardware
counters using `likwid-perfctr`, then pairing with scaling analyses we can see
how metrics such as memory bandwidth or NUMA behaviour scales.

For more information, please see the [`likwid-perfctr` documentation on the
LIKWID Wiki](https://github.com/RRZE-HPC/likwid/wiki/likwid-perfctr) but here
we will just higlight some key features to get started with.

To see which **performance groups** are available on the system of interest, we run
```bash
likwid-perfctr -a
```
we can then select a performance group of interest. **Please note**:
performance groups are not universal. Different systems - i.e., vendors and
chip generations - allow for different performance groups, so always check
which are available on a system. Once we select a performance group we can use
`likwid-perfctr` command, along with our pinning and placement notation. For
the `MEM` performance group, which looks at traffic from main memory, we would
use the following
```bash
likwid-perfctr -C 0-7 -g MEM ./code
```
which runs across the first 8 cores on our node. This will print out raw
hardware counter data, but useful for the average user are the summarised
metrics which we can use to study our code's performance.

These metrics are captured globally across the whole application. If we want to
target specific code blocks - e.g., if we have used a profiler and found a
particular hotspot that we want to analyse - then we can use LIKWID's marker
API to collect metrics on the specific code blocks.

Finally, as we used `likwid-pin` to coordinate our affinity and placement, and
then `likwid-perfctr` to extend this functionality to gather hardware
performance counters, we can add the gathering of hardware performance counter
data to `likwid-mpirun` for MPI and hybrid parallel jobs. We can do this by
adding `-g <PERFORMANCE_GROUP>` to our `likwid-mpirun` call.

In summary, hardware performance counters can extend some of the benchmarking
we have seen earlier to help us add more data to our benchmarking beyond total
runtimes and speed-ups. However, this analysis can become quite detailed and so
we do not recommend skipping right to this step. Instead, it is best to
step-by-step work through earlier sections in documentation, experimentation
with placement, affinity and scaling. We can then turn to hardware performance
counters for more detailed analysis.

# Supporting materials

We list below further materials to help in your future benchmarking!

## SHAREing

This blog has given just an introduction to some benchmarking concepts and as
part of SHAREing we are building a performance assessment of which benchmarking
forms the basis. To get started in following SHAREing's performance
methodology, we have GitHub hosted
[templates](https://github.com/SHAREing-DRI/assessment-template) for our
[pre-assessment](https://github.com/SHAREing-DRI/assessment-template/blob/main/pre-assessment-report.md)
and [high-level
assessment](https://github.com/SHAREing-DRI/assessment-template/blob/main/high-level-report.md)
which covers much of the topics covered here. More detail can be found in the
[SHAREing performance assessment
guidebook](/assets/pdfs/perf_analysis_workbook_brief.pdf).

## Reproducible and automated benchmarking

Likewise, for automating benchmarking consider looking into
[Reframe](https://reframe-hpc.readthedocs.io/en/stable/) or
[JUBE](https://apps.fz-juelich.de/jsc/jube/docu/index.html). This can help
automate benchmarking workflows to aggregate together statistics. A paper by
the ExCALIBUR project on automated and reproducible benchmarking practices can
be found [here](https://doi.org/10.1145/3624062.3624133). If benchmarking is to
become a feature of your research outputs, then there is a useful paper on
benchmarking best practice particularly in reporting results linked
[here](https://doi.org/10.1145/2807591.2807644).

## HPC Wiki

Finally, a useful resource for many concepts in HPC is the [HPC
Wiki](https://hpc-wiki.info/hpc/HPC_Wiki) which presents useful overviews of
concepts and workflows in both benchmarking and scaling analysis, linked
[here](https://hpc-wiki.info/hpc/Benchmarking).

---
