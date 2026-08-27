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

<!-- 
 HOW TO WRITE BLOG POST CONTENT

- Write your post in Markdown or simple HTML for consistent formatting.
- **Headings**: Use <h2> for main sections.
  Example: 
    <h2>Revisiting our foundations</h2>
    
- **Paragraphs**: Wrap normal text in <p> tags.
  Example:
    <p>This is a normal paragraph describing your content.</p>
    
- **Quotes / Highlights**: Use the blog-quote class for important statements or decisions.
  Example:
    <div class="blog-quote">This is an important quote or highlight.</div>
    
- **Images**: Include images using <img> tags or Markdown, with descriptive alt text.
  Example:
    <img src="/assets/eventphotos/image-name.jpeg" alt="Description of image">
    
-->

Benchmarking can sound simple: run a code, measure how long it takes. However,
this approach hides a lot of nuance. It can be very easy to report benchmarking
results which are unreliable or sell a narrative. We want our benchmarking to
run like clean, reproducible experiments wherever possible.

In this blog we run
through some basic steps to get started with benchmarking, and signpost
some resources to consider in future benchmarking.

# Getting started

The aim of getting started with benchmarking is essentially choosing the
software to benchmark with the hardware to benchmark on, and then document in
detail the steps needed to get the benchmark built and running. This is
particularly important as there are many variables in these steps which can
impact performance. We must remember: **documentation is key!**

## 1. The code

To get started, we need a benchmark. If you are working on a code that does not
currently ship with any benchmarks, SHAREing has written up some basic
guidelines on how to write a representative benchmark which we link
[here](/assets/pdfs/shareing-benchmark-guide.pdf).

It can be really useful in defining a metric that is specific to an algorithm
or code, e.g., for lattice-based methods, something like the 'number of lattice
site updates' can be really useful for code specific performance metrics.

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
`likwid-topology` and MAQAO, or files such as `/proc/cpuinfo` on Linux systems.
However, these outputs are typically very detailed and go far beyond the data
often used in simple hardware comparisons for benchmarking. Some example
values, given by `likwid-topology` are core counts, cache sizes and NUMA
domains.

## 3. Software dependencies

As with hardware a code's software dependencies can impact performance, and so
what we recommend with all of this is document. We want our benchmarking to be
as reproducible as possible, so we document on a specific system any specific
software. For example, note down compilers, libraries and version numbers.

On a cluster we can just note down the dependencies using the 
```bash
module list
```
command.

## 4. Build

We just simply follow and document the build steps. This may include typical
compiler flags used in the production code. Build steps are a classic example
of a step where the configuration can change code performance, so we just
simply note down what we begin with. Then, once we have begun to collate
results, we can see about whether there are different compilation options we
can use, and then compare software performance.

## 5. Run

For a first run, we recommend just running naively. We can play around with
parallel resources, etc. in the future, but to begin with we just pick a
certain setup and run. This is verify that the code runs, but we can also use
this as an opportunity check some basic resource usage such as total runtime
and memory footprint.

On a SLURM based system we can use 
```bash
sacct -j <job-number> --format=elapsed,maxRSS
```
to give the total runtime (`elapsed`) and the memory footprint (`maxRSS`). 

Alternatively, we can time an application using `/usr/bin/time` which is a
standardised tool (so recommend avoid just using `time`), and then reading off
the `real` time from this output. Then for total memory usage, on most Linux
systems we have access to the `valgrind` tool which is used in detecting memory
leaks, etc.
```bash
valgrind --tool=massif ./code
```

# Further things to consider

Now that we have documented our hardware, software and basic workflows for
building and running the benchmark, we can then consider what other controls we
have at our disposal.

## 6. Affinity

We like to fix threads to physical cores as much as possible. We can do this with

* OpenMP - environment variables
* MPI - through the `mpirun` command
* `likwid-pin`

## 7. Compiler optimisations

As mentioned above, build steps are an aspect of benchmarking that can have
significant effects on performance. Some hardware may have advanced
instructions that can be exploited via compiler flags. 

There is vast documentation online for compilers and their flags, often with
pages dedicated to optimisation flags. Similarly, tools like MAQAO can suggest
compiler flags that can exploit hardware features. As with all aspects of
benchmarking, comparison is key. Saving our total runtime and any other metrics.

## 8. Scaling

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

## 9. Placement

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

## 10. Metrics

We like to also gather hardware counters from these using `likwid-perfctr`,
then pairing with scaling analyses we can see how metrics such as memory
bandwidth or NUMA behaviour scales.

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
