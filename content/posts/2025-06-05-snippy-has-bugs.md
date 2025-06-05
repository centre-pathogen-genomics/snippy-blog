+++
title = 'Ew! Snippy-NG has Bugs!'
date = 2025-06-04T11:19:48+10:00
draft = false
tags = ["github", "bugs", "issues"]
+++

Snippy's farther ([tseemann](https://github.com/tseemann)) is a notorious GitHub bug hunter. He has over [1.8K closed](https://github.com/search?q=author%3Atseemann+is%3Aissue+state%3Aclosed&type=issues) and about [500 open](https://github.com/search?q=author%3Atseemann+is%3Aissue+state%3Aopen&type=issues) issues on GitHub. In the spirit of Torsten's contributions to the open source community, we are making it easy for anyone to report bugs in Snippy-NG.

## Reporting Bugs

In the latest version of Snippy-NG ([v1.0.0](https://github.com/centre-pathogen-genomics/snippy-ng/releases)), we have added a new flag `snippy-ng --bug` that allows users to report bugs directly from the command line. This command will open a new issue on the Snippy-NG GitHub repository with a bug report template and some pre-filled labels.

## Automatic Bug Catching

In addition to the `--bug` flag, we have also added a new feature that automatically catches runtime bugs in Snippy-NG. If there is an unhandled exception in Snippy-NG, it will automatically generate a bug report with prefilled information like the version of snippy and users operating system. Users can click a link to open the bug report in their browser, where they can add more details and submit it.

```
Oh no! You broke Snippy-NG... Congrats! Please use the following URL to report this bug:

https://github.com/centre-pathogen-genomics/snippy-ng/issues/new?template=bug_report.md&labels=cli,bug&type=bug&title=Your+bug+title+here

Above is a pre-filled bug report template. Please copy/paste it into the GitHub issue form.
```

## Bonus

We also added new formatting for the logs that makes it easier to read and understand which stages are running.
```
-------------------------------------------------------------------
                         Running Snippy-NG                         
-------------------------------------------------------------------
[17:30:29 - INFO] Version: 1.0.0
[17:30:29 - INFO] Stages:
[17:30:29 - INFO]   1. PrepareReference
[17:30:29 - INFO]   2. PreAlignedReads
[17:30:29 - INFO]   3. FreebayesCaller
---------------------- CHECKING DEPENDENCIES ----------------------
[17:30:29 - INFO] Checking dependencies for PrepareReference...
[17:30:29 - INFO] Found biopython v1.85
[17:30:29 - INFO] Checking dependencies for PreAlignedReads...
[17:30:29 - INFO] Found samtools v1.20
[17:30:29 - INFO] Found samclip v0.4.0
[17:30:29 - INFO] Checking dependencies for FreebayesCaller...
[17:30:29 - INFO] Found freebayes v1.3.9
[17:30:29 - INFO] Found vt v0.5772
[17:30:29 - INFO] Found bcftools v1.21
[17:30:29 - INFO] Dependencies look good!
-------------------------------------------------------------------
[17:30:29 - INFO] Setting working directory to 'out'
------------------------ PrepareReference -------------------------
[17:30:29 - INFO] cpus=1 ram=8 outdir=PosixPath('out') tmpdir=Po...
```