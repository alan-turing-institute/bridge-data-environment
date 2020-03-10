# JupyterHub Computational Environment

A repo to manage to user environment deployed to JupyterHub https://github.com/alan-turing-institute/bridge-data-platform

The `.binder` folder contains [configuration files](https://repo2docker.readthedocs.io/en/latest/config_files.html) for installing programming languages and packages into the computing environment of a JupyterHub.
The environment will be built by [repo2docker](https://repo2docker.readthedocs.io/) and pushed to a Docker Hub repository where it can be pulled by the JupyterHub and served to the users.

## Python Environment

### `runtime.txt`

Define the required version of Python to use in the `runtime.txt` file as follows.

```bash
python-3.7  # This will install Python 3.7
```

### `requirements.txt`

Add any desired Python packages to the `requirements.txt` file as a list.
