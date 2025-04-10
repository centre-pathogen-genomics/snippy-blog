+++
title = 'For the People'
date = 2025-04-09T11:19:48+10:00
draft = false
tags = ["CI", "CD", "github", "install"]
+++

We have seen that Snippy-NG will be [`by the people`](/posts/the-py-in-snippy/) i.e. it written in the lingua franca of the programming world, Python. In this post we will explore how Snippy-NG will be `for the people` i.e. easy to install.

## Installing Snippy

The original Snippy is a Perl script that required a number of dependencies to be installed on the system. While Conda offers some help, installation problems are one of the most common problems issues on Github. This has resulted in Snippy being called out for its [degraded installation experience](https://www.bacpop.org/guides/building_trees_with_ska).

We plan to solve the installation issues with Snippy-NG by using a number of modern software development practices. Most notability, we will provide a pre-built environment that will install Snippy-NG and all dependencies with a single command. This environment contains pinned versions of all dependencies to ensure that Snippy-NG will work the same on any system. In addition we use continuous integration and Github best practices to ensure that the environment is always up to date and that Snippy-NG is always working.

You can install `snippy-ng` via the install script with the follow command:

```bash
curl -sSL https://github.com/centre-pathogen-genomics/snippy-ng/releases/latest/download/install.sh | bash
```

This version of snippy-ng has all the of the dependencies pinned via the [pixi.lock](https://github.com/centre-pathogen-genomics/snippy-ng/blob/main/pixi.lock) file. Users installing snippy-ng via the install script will have the same versions of all dependencies.

## Pre-built Environment

We are using [Pixi](https://pixi.sh/latest/) and [pixi-pack](https://github.com/Quantco/pixi-pack) to create cross-platform self-extracting binaries of the full snippy environment. We have developed Github actions that will automatically [pack Pixi environments](https://github.com/Wytamma/pixi-pack-action) and [create a install script](https://github.com/Wytamma/pixi-pack-install-script). This will not only solve the installation issues but improve reproducibility.

## Github Best Practices

By adopting automated [semantic-releases](https://github.com/semantic-release/semantic-release) we ensure that Snippy-NG is always up to date and that any issues are quickly resolved. We are also using Github Actions to run [tests and benchmarks](https://github.com/centre-pathogen-genomics/snippy-ng/actions/workflows/PR.yaml) on every pull request and release to ensure that the code is always fast and working. We are committed to reaching [100% code coverage](https://app.codecov.io/github/centre-pathogen-genomics/snippy-ng) and have put checks in place to prevent drops in test code coverage. To release a new version of Snippy-NG code coverage must not go down. Additionally, blocked commits directly to the main branch to ensure that all changes are made through pull requests. This way all changes will be reviewed and tested before they are merged into the main branch.

![image](https://github.com/user-attachments/assets/4113d202-25db-41a3-ac64-bf6ae6d39f2e)

## Conclusion

In conclusion, Snippy-NG will be `for the people` by providing a modern installation experience and using best practices for software development. We are excited to see how this will improve the user experience and make Snippy-NG a more reliable tool for microbial genomics research. We are also looking forward to seeing how the community will contribute to the project and help us make Snippy-NG even better.
