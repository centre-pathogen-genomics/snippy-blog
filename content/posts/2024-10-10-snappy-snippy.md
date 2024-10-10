+++
title = 'Snippy must be Snappy'
date = 2024-10-10T11:19:48+10:00
draft = false
tags = ["python", "design", "performance", "hyperfine", "CI"]
+++

In the last post we detailed the decision to use Python as the primary programming language for the new version of Snippy. I can hear millions of crustaceans crying out at this decision, so in this post we will explore the performance implications of this decision and the steps we are taking to ensure that Snippy remains a snappy tool for microbial genomics research.

First up Snippy is glue. It joins together a number of existing bioinformatics tools to perform its analysis. These tools are written in a variety of languages. For example:

| Tool      | Language | Description                                      |
|-----------|----------|--------------------------------------------------|
| freebayes | C++      | Bayesian haplotype-based polymorphism discovery  |
| bcftools  | C        | Tools for manipulating VCF and BCF files         |
| samtools  | C        | Utilities for manipulating alignments in SAM/BAM |
| bwa       | C        | Burrows-Wheeler Aligner for sequence alignment   |
| minimap2  | C        | Long-read mapping tool                           |
| snpEff    | Java     | Variant annotation and effect prediction tool    |

The performance of Snippy is therefore dependent on the performance of these tools (Python/Perl does very little of the actual analysis). With that said we still want to ensure that Snippy itself i.e. the CLI experience is as fast as possible.

> Did you know? The name Snippy is a combination of SNP (pronounced "snip"), snappy (meaning "quick") and Skippy the Bush Kangaroo (to represent its Australian origin)

# Continuous Benchmarking

The slowest Snippy CLI command runs in <img src="https://byob.yarr.is/centre-pathogen-genomics/snippy-ng/benchmark" style="display:inline;"/>.

We use benchmarking to ensure the snippy CLI is snappy. [`hyperfine`](https://github.com/sharkdp/hyperfine) is a command-line benchmarking tool written in rust (you're welcome) that can be used to measure the execution time of a command. It is designed to be easy to use and provides a number of features that make it a good choice for benchmarking software tools.

Humans perceive events as instantaneous if they occur under 100 milliseconds. Anything less than 200 milliseconds is surely snappy so we will use this as our benchmark. We've created a [Github Action](https://github.com/centre-pathogen-genomics/snippy-ng/actions/workflows/benchmark.yaml) (inspired by the hatch package manager) that will run `hyperfine` on the Snippy CLI and fail if it takes longer than 200 milliseconds to execute. This will ensure that we are always aware of the performance of the Snippy CLI and can take action if it becomes too slow. 
