# Reference Manual

# Jupyter

**Jupyter** is the main system used in SARVe. JupyterHub is used to spawn user servers. By default it spawns an instance of JupyterLab in your server.

## JupyterHub Options


# Storage

For each server, there are three types of storage available:

| Storage Type      | Path            | Description                                                                                                                             | Available across sessions | Available across computers | Hardware   |
| ----------------- | --------------  | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- | -------------------------- | ---------- |
| Local storage     | ~/localstorage  | :fontawesome-regular-hard-drive: Use this for data that need fast access. (e.g. conda environments)                                          | :material-check:          | :material-close:           | NVMe SSD   |
| Shared storage    | ~               | :material-harddisk: Use this for mission critical data. It is slower but lives in a trusted RAID array for maximum safety.  | :material-check:          | :material-check:           | RAID Array |
| Ephemeral storage | Everywhere else | :simple-linux: This is the storage assigned to your server for system functions, this gets erased on server shutdown.                   | :material-close:          | :material-close:           | NVMe SSD   |


# FAQ

## Q: Conda activate throws an error and this is the first time using it.
A: This probably means that conda is not properly initialized. Use `conda init` to configures your shell to recognize conda commands.
After running this command, restart your terminal or reload your shell configuration.

## Q: Custom Python environments are not detected in JupyterLab
A: JupyterLab uses IPython and IPython uses kernels to run the Python interpreter.
To use a specific Python environment, you have to use that specific installation of Python interpreter.
To tell IPython to use another installation of Python interpreter first install `ipykernel` package in it's environment
and then use this command to register it as a IPython kernel:

```bash
python -m ipykernel install --user --name test_env --display-name "Python (test_env)"
```
??? info

    - `--user` → Installs the kernel for your user account.
    - `--name test_env` → Internal kernel identifier.
    - `--display-name "Python (test_env)"` → Name displayed in Jupyter.

    You can customize the display name if desired.

Then choose the created kernel in JupyterLab by navigating to:
```text
Kernel → Change Kernel
```
and selecting the newly created kernel.
