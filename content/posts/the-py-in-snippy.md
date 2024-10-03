+++
title = 'The `py` in Snippy Stands for Python'
date = 2024-10-02T11:19:48+10:00
draft = false
+++

There are are several high-level design decisions that must be made when developing a new software tool (or is this case the a major revision to a beloved project). One of the most contentious is the choice of programming language. This decision can have far-reaching implications for the project's success, longevity, and adoption. In the case of this new version of Snippy, the choice was made to use Python as the primary programming language. This article will explore the reasons behind this decision and the implications for the project.

## Why not Perl?

The original version of Snippy was written in Perl, a high-level, general-purpose programming language that is known for its text processing capabilities. Perl has several similarities to Python, they are both high-level glue languages that can be used to connect different software tools together. However, Perl can be difficult to read and maintain, and is now only used by bioinformaticians who memorised the syntax in the 1990s.

## Why not Rust?

Rust is a systems programming language that is known for its safety, speed, and concurrency. It is a modern language that is designed to be memory-safe and thread-safe. Rust is a good choice for systems programming and low-level programming tasks. However, Rust is not as widely used as Python and does not have as large of a community or ecosystem of third-party libraries. Rust is also a more complex language than Python and can be more difficult to learn and use. Rust is a good choice for performance-critical tasks, but Python is a better choice for general-purpose programming and rapid development.

## Why not a workflow language?

Workflow languages like Nextflow, Snakemake, and CWL are designed for defining and executing complex workflows that involve multiple software tools and data processing steps. While this sounds like a good fit for Snippy, we decided against using a workflow language for several reasons, the main being that we believe that the complexity of a workflow languages will take away from the simplicity of Snippy. We want Snippy to be easy to use and easy to understand, and we believe that using a workflow language would make it more difficult for users to get started with Snippy.

## Why Python?

Python is a high-level, general-purpose programming language that is widely used in scientific computing, data analysis, and web development. It is known for its simplicity, readability, and ease of use. Python has a large standard library and a vibrant community and ecosystem of third-party libraries. Python is also a popular language for teaching programming and is widely used in introductory courses. Most if not all bioinformatics courses now use Python as a primary language. Thus we expect to see a lot of new contributors to the project. Overall, we are confident that we can develop a high-quality, maintainable, and extensible version of Snippy in Python.