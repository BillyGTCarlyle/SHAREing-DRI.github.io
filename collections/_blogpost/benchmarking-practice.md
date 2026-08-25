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
other metrics vary with core count.

### Strong scaling

Increasing core count for fixed problem size.

### Weak scaling

Increasing core count with increasing problem size, so the work per core stays
(in theory) approximately constant.

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

Drop links here

---
