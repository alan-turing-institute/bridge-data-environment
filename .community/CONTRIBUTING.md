# Contributing Guidelines

:space_invader: :tada: Thank you for taking the time to read our Contributing Guidelines! :tada: :space_invader:

The following is a set of guidelines for working in the _Bridge Data Environment_ repository on GitHub.
These are mostly guidelines, not rules.
Use your best judgement and feel free to propose changes to this document in a Pull Request.

**Table of Contents**

- [Code of Conduct](#code-of-conduct)
- [What should I know before I get started?](#what-should-i-know-before-i-get-started)
  - [Repository Overview](#repository-overview)
  - [`repo2docker`](#repo2docker)
- [How can I contribute?](#how-can-i-contribute)
  - [Bug Reports](#bug-reports)
  - [Feature Requests](#feature-requests)
  - [Pull Requests](#pull-requests)
- [Styleguides](#styleguides)
- [Additional Notes](#additional-notes)
  - [Issue and Pull Request Labels](#issue-and-pull-request-labels)

---

## Code of Conduct

Everyone participating in this project is expected to have read, abide by and uphold our [Code of Conduct](CODE_OF_CONDUCT.md).
Please report unacceptable behaviour to [sgibson@turing.ac.uk](mailto:sgibson@turing.ac.uk).

## What should I know before I get started?

This repository (<https://github.com/alan-turing-institute/bridge-data-environment>) is setup to automatically build a computational environment compatible with [JupyterHub](https://jupyter.org/hub) using [`repo2docker`](https://repo2docker.readthedocs.io).
Any languages or packages listed within this repository will be compiled into a [Docker image](https://searchitoperations.techtarget.com/definition/Docker-image) and made available on the [Turing's Docker Hub organisation](https://hub.docker.com/repository/docker/turinginst/bridge-data-env).
This can then be accessed by a JupyterHub such that, when a user requests a server running this image, they find all the packages they require to perform their data analysis task.

The repository is automated in such a way that adding a new package or dependency to this image is as simple as opening a [Pull Request](#pull-requests).
Using [GitHub Actions](https://help.github.com/en/actions) as continuous integration, the image is automatically built and pushed to Docker Hub with each merge to the master branch.

### Repository Overview

- The `.binder` folder contains all the files required to build the computational environment
- The `.community` folder contains our [Code of Conduct](CODE_OF_CONDUCT.md) and these Contributing Guidelines
- The `.github` folder contains Issue/Pull Request templates and our GitHub Actions files for our continuous integration pipeline
- The `.tests` folder contains example Jupyter Notebooks that tests each language and available package

### `repo2docker`



## How can I contribute?

### Bug Reports

### Feature Requests

### Pull Requests

A Pull Request is a means for [a team to collaboratively work on changes](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests) before introducing them into the base branch.

Please follow these steps to have your contribution reviewed by the team members.

1. [Clone this repository](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/cloning-a-repository)
2. [Create a new branch](https://help.github.com/en/desktop/contributing-to-projects/creating-a-branch-for-your-work)
   1. Where possible and appropriate, please use the following convention to name your branch: `<type>/<issue-number>/<short-description>`.
      For example, if you're fixing a typo that was raised in issue number #11, your branch would be named as such: `fix/11/typo`.
3. Edit files or create new ones!
4. [Open your Pull Request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request)
   1. This repository has a [Pull Request template](/.github/PULL_REQUEST_TEMPLATE.md) designed to help others understand what your Pull Request is changing and how they should review it.
      Please complete it where possible.

Congratulations! :tada:
Now the team can review your changes.
They may make some suggestions for clarity and once these have been addressed, your changes can be merged!

## Styleguides

Hopefully you won't need to write too much code or documentation when contributing to this repo.
Therefore, we only ask you try and follow two guidelines specifically:

1. **Don't remove a dependency without discussion first.**
   It may be that that dependency is causing a conflict for you but is critical to someone else's analysis.
   Let's have a conversation first to minimise disruption for everyone.
2. **Before committing a Jupyter Notebook to the repository, please clear all outputs first.**
   Notebooks like to create a lot of metadata in their JSON files and this is a sure-fire way to creating merge conflicts.
   Clearing your outputs before committing will keep maintainers of this repository, and [our CI](/.github/workflows/clean-notebook-metadata.yml), very happy!

## Additional Notes

### Issue and Pull Request Labels

Issues and Pull Requests can have labels assigned to them which indicate at a glance what aspects of the project they describe.
It is also possible to [sort issues by label](https://help.github.com/en/github/managing-your-work-on-github/filtering-issues-and-pull-requests-by-labels) making it easier to track down specific issues.
Below is a table with the currently used labels in the repo.

| Label | Description |
| :--- | :--- |
| `bug` | Something isn't working |
| `ci` | Relating to the Continuous Integration workflows |
| `enhancement` | Introducing a new feature, language or package |
| `julia` | Relating to the Julia environment |
| `python` | Relating to the Python environment |
| `r` | Relating to the R environment |
| `testing` | Relating to testing the environment |
