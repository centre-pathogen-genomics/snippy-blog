+++
title = 'For the People'
date = 2025-04-09T11:19:48+10:00
draft = false
tags = ["CI", "CD", "github", "install"]
+++

We’ve seen that Snippy-NG will be [`by the people`](/posts/the-py-in-snippy/) i.e. it is written in the lingua franca of the programming world: Python. In this post, we’ll explore how Snippy-NG will be `for the people` i.e. easy to install.

## Installing Snippy

The original Snippy is a Perl script that required a number of system-level dependencies. While Conda helps to some extent, installation issues remain one of the most common problems reported on GitHub. This has led to Snippy being criticized for its [degraded installation experience](https://www.bacpop.org/guides/building_trees_with_ska).

We plan to address these issues in Snippy-NG by adopting modern software development practices. Most notably, we will provide a pre-built environment that installs Snippy-NG and all its dependencies with a single command. This environment uses pinned versions of all dependencies to ensure Snippy-NG behaves consistently across systems. In addition, we use continuous integration and GitHub best practices to keep the environment up to date and Snippy-NG always functional.

You can install `snippy-ng` via the install script using the following command:

```bash
curl -sSL https://github.com/centre-pathogen-genomics/snippy-ng/releases/latest/download/install.sh | bash
```

This version of Snippy-NG includes all dependencies pinned via the [pixi.lock](https://github.com/centre-pathogen-genomics/snippy-ng/blob/main/pixi.lock) file. Users installing Snippy-NG through this script will get the same versions of all dependencies, ensuring reproducibility.

## Pre-built Environment

We are using [Pixi](https://pixi.sh/latest/) and [pixi-pack](https://github.com/Quantco/pixi-pack) to create cross-platform, self-extracting binaries of the complete Snippy-NG environment. We’ve developed GitHub Actions that automatically [pack Pixi environments](https://github.com/Wytamma/pixi-pack-action) and [generate an install script](https://github.com/Wytamma/pixi-pack-install-script). This approach not only solves installation issues but also enhances reproducibility.

## GitHub Best Practices

By adopting automated [semantic releases](https://github.com/semantic-release/semantic-release), we ensure Snippy-NG is always up to date and that issues are resolved quickly. We also use GitHub Actions to run [tests and benchmarks](https://github.com/centre-pathogen-genomics/snippy-ng/actions/workflows/PR.yaml) on every pull request and release to guarantee performance and correctness. 

We're committed to achieving [100% code coverage](https://app.codecov.io/github/centre-pathogen-genomics/snippy-ng) and have checks in place to prevent any regression. To release a new version of Snippy-NG, code coverage must not decrease. Additionally, we have blocked direct commits to the `main` branch—ensuring that all changes go through pull requests, where they are reviewed and tested before being merged.

![image](https://github.com/user-attachments/assets/4113d202-25db-41a3-ac64-bf6ae6d39f2e)

## Conclusion

Snippy-NG will be `for the people` by offering a streamlined installation experience and following best practices in software development. We're excited to see how this will improve the user experience and make Snippy-NG a more reliable tool for microbial genomics research. We also look forward to community contributions that will help us make Snippy-NG even better.