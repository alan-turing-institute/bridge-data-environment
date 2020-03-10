# JupyterHub Computational Environment

A repo to manage to user environment deployed to JupyterHub :point_right: <https://github.com/alan-turing-institute/bridge-data-platform>

The `.binder` folder contains [configuration files](https://repo2docker.readthedocs.io/en/latest/config_files.html) for installing programming languages and packages into the computing environment of a JupyterHub.
The environment will be built by [repo2docker](https://repo2docker.readthedocs.io/) and pushed to a Docker Hub repository where it can be pulled by the JupyterHub and served to the users.

- [Contributing](#contributing)
- [Python Environments](#python-environments)
- [R Environments](#r-environments)
- [`postBuild`](#postbuild)

---

## Contributing

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

The runtime version of R to be installed is defined in the `dependecies` block.
For example:

```yaml
dependencies:
  - r-base=3.6
```

Any R packages are also specified under the `dependencies` block **provided they are available on `conda-forge`**.
For example:

```yaml
dependencies:
  - r-tidyverse
```

## `postBuild`

This file is a `bash` script that is executed during the `docker build` phase but after the environment has been installed.
`postBuild` can be used for a number of functions, including:

- pulling data,
- enabling widgets,
- exporting installed packages to your `$PATH`.
