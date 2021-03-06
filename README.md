# ScalaQuest Final Reports

![CI](https://github.com/scalaquest/Reports/workflows/CI/badge.svg)
![Release](https://img.shields.io/github/v/release/scalaquest/Reports?label=Release)

This is the entry point for PPS and LSS reports. We decided to set them in a
separate repository, as the structure of them begun to rise in complexity.

The documentation is written in Markdown, available in the `src` directory. Anyway, more convenient consultation formats 
are provided: for
each release, PDF LaTeX and web version are generated automatically, using [Pandoc](https://pandoc.org/index.html).

## How to consult sources?

The repository uses [scalaquest/PandocBootstrap](https://github.com/scalaquest/PandocBootstrap) as a Git Submodule. As such, a plain clone does not initialize submodules. You have to clone the project this way:

```
git clone --recurse-submodules https://github.com/scalaquest/Reports.git
```

Besides performing the clone, also recursively initialize submodules. Also, the submodule have to be updated manually periodically, by using

```
git submodule update --remote --recursive
```

## How to consult the documentation?

You can examine the web version of reports and the appendix document from the
[PPS report website](https://scalaquest.github.io/Reports/pps-report/pps-report.html),
[LSS report website](https://scalaquest.github.io/Reports/lss-report/lss-report.html) and
[appendix website](https://scalaquest.github.io/Reports/appendix/appendix.html).

If you prefer a LaTeX PDF version, you can download the latest release 
[from here](https://github.com/scalaquest/Reports/releases/latest).
