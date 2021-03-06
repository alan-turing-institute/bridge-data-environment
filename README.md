# JupyterHub Computational Environment

[![repo2docker build](https://github.com/alan-turing-institute/bridge-data-environment/workflows/repo2docker%20build/badge.svg)](https://github.com/alan-turing-institute/bridge-data-environment/actions?query=workflow%3A%22repo2docker+build%22+branch%3Amaster)

A repo to manage the user environment deployed to JupyterHub :point_right: <https://github.com/alan-turing-institute/bridge-data-platform>

The `.binder` folder contains [configuration files](https://repo2docker.readthedocs.io/en/latest/config_files.html) for installing programming languages and packages into the computing environment of a JupyterHub.
The environment will be built by [repo2docker](https://repo2docker.readthedocs.io/) and pushed to the [Turing's Docker Hub repository](https://hub.docker.com/repository/docker/turinginst/bridge-data-env) where it can be pulled by the JupyterHub and served to the users.

- [Contributing](#contributing)
- [Python Environments](#python-environments)
- [R Environments](#r-environments)
- [`postBuild`](#postbuild)

---

## Contributing

Before starting, please read our [Code of Conduct](.community/CODE_OF_CONDUCT.md) :purple_heart: and [Contributing Guidelines](.community/CONTRIBUTING.md) :space_invader:

Anyone can make a [Pull Request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests) to this repository to install a new language or package into the image.

You can find ideas on how to configure different languages here :point_right: <https://github.com/binder-examples>

:rotating_light: **Please be aware that this is a publicly shared image, so whoever chooses to pull this image will be able to access the packages that you've installed.** :rotating_light:

You can find guides on which configuration files are compatible with each other (for example, `environment.yml` overrrides `requirements.txt`) here :point_right: <https://repo2docker.readthedocs.io/en/latest/config_files.html>

## Python Environments

Python environments are configured using the `environment.yml` file.

The runtime version of Python to be installed is defined in this file under the `dependencies` block.
For example:

```yaml
dependencies:
  - python=3.7
```

Any desired pip-installable Python packages are installed under the `pip` block of the file.
For example:

```yaml
dependencies:
  - pip:
    - my-python-package
```

## R environments

R environments are also configured using the `environment.yml` file.

R code is installed through the [`conda-forge`](https://conda-forge.org/) channel which we defined under the `channels` block.
For example:

```yaml
channels:
  - conda-forge
```

The runtime version of R to be installed is defined in the `dependencies` block.
For example:

```yaml
dependencies:
  - r-base=3.6
```

Any R packages are also specified under the `dependencies` block :warning: **provided they are available on `conda-forge`** :warning:
For example:

```yaml
dependencies:
  - r-tidyverse
```

If your desired R packages are not available on `conda-forge`, please look into using a [`runtime.txt` file](https://repo2docker.readthedocs.io/en/latest/config_files.html#runtime-txt-specifying-runtimes) with either an [`install.R`](https://repo2docker.readthedocs.io/en/latest/config_files.html#install-r-install-an-r-rstudio-environment) file or [`DESCRIPTION`](https://repo2docker.readthedocs.io/en/latest/config_files.html#description-install-an-r-package) file.

## `postBuild`

This file is a `bash` script that is executed during the `docker build` phase but after the environment has been installed.
[`postBuild`](https://mybinder.readthedocs.io/en/latest/config_files.html#postbuild-run-code-after-installing-the-environment) can be used for a number of functions, including:

- pulling data,
- enabling widgets,
- exporting installed packages to your `$PATH`.
