+++
title = 'A Modular Architecture'
date = 2026-02-12T11:19:48+10:00
draft = false
tags = ["architecture", "modularity", "design"]
+++

A major goal of Snippy-NG is to be modular and extensible. We want to make it easy to add new features and functionality to Snippy-NG without having to modify the core logic. To achieve this, we have settled on a modular architectural design for Snippy-NG that allows us to easily add new stages, pipelines and subcommands.

# Stages

At the core of Snippy-NG is the concept of a "stage". A stage is a self-contained unit of work that performs a specific task. For example, the `PrepareReference` stage is responsible for preparing the reference genome for analysis, while the `SeqkitCleanLongReads` stage is responsible for cleaning long reads using the Seqkit tool. Each stage has its own dependencies and can be run independently of other stages.

# Pipelines

A pipeline is a linear collection of stages that are run in a specific order to perform a complete analysis. For example, the `AsmPipelineBuilder` class builds a pipeline for assembly-based variant calling, while the `TreePipelineBuilder` class builds a pipeline for phylogenetic tree construction. Pipelines are built at runtime based on the user's input and can be easily validated. This allows us to easily add new pipelines for different types of analyses buy simply linking together existing stages in a new way.

Snippy-NG pipelines are linear and contain not branching. All branching logic is contained within stages or applied as the pipeline is being built (e.g. conditions on which stages to include).

# Subcommands

A subcommand is a top-level command that can be run from the command line. For example, the `snippy-ng asm` subcommand runs the assembly-based variant calling pipeline, while the `snippy-ng tree` subcommand runs the phylogenetic tree construction pipeline. Subcommands are built on top of pipelines and provide a user-friendly interface for running complex analyses. A subcommand can be a mixture of existing pipelines and new stages, allowing us to easily add new functionality to Snippy-NG without having to modify the core logic.

# Conclusion and Future Directions

The modular architecture of Snippy-NG allows us to easily add new features and functionality. One potential future direction is to add support for bubbling stages up to the subcommand level, allowing users to run individual stages from the command line. This would results in a `snippy-ng run PrepareReference` command that runs the `PrepareReference` stage independently of any pipeline.