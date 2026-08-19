# Jupyter

**Jupyter** is the main system used in SARVe. JupyterHub is used to spawn user servers. By default it spawns an instance of JupyterLab in your server.

## JupyterHub Options


## Storage

For each server, there are three types of storage available:
| Storage Type      | Path            | Description                                                                                            | Available across sessions | Available across computers | Hardware |
| ----------------- | --------------  | ------------------------------------------------------------------------------------------------------ | ------------------------- | -------------------------- | -------- |
| Local storage     | ~/localstorage  | :fontawesome-solid-sd-card: Use this for data that need fast access. (e.g. conda environments)         | :material-check:          | :material-close:           | NVMe SSD |
| Shared storage    | ~               | :fontawesome-solid-floppy-disk: Use this for mission critical data. It is slower but lives in a trusted RAID array for maximum safety.  | :material-check:          | :material-check:           | RAID Array |
| Ephemeral storage | Everywhere else | :simple-linux: This is the storage assigned to your server for system functions, this gets erased on server shutdown. | :material-close:          | :material-close:           | NVMe SSD |


## Step 1 — Navigate to Your Storage Directory

After logging into SARVe, open a terminal and move to your storage directory:



This location will be used to store your custom Conda environments and project files.

---

## Step 2 — Create a New Conda Environment

Create a new Conda environment using a local installation path.

Example:

```bash

```

### Explanation

* `conda create` → Creates a new Conda environment.
* `--prefix ./test_env` → Installs the environment inside the current directory (`localstorage/test_env`).
* `python=3.13` → Specifies the Python version.

You may replace:

* `test_env` with your preferred environment name.
* `3.13` with another supported Python version if needed.

---

## Step 3 — Initialize Conda

If Conda has not been initialized previously, run:

```bash
conda init
```

This configures your shell to recognize Conda commands.

After running this command for the first time, restart your terminal or reload your shell configuration.

---

## Step 4 — Activate the Environment

Activate your newly created environment:

```bash
conda activate ~/localstorage/test_env
```

### Explanation

Since the environment was created using `--prefix`, activation requires the **full path** to the environment directory.

Replace:

```text
test_env
```

with the name of your environment if you used a different one.

---


### Why is this necessary?

`ipykernel` allows your Conda environment to appear as a selectable Python kernel inside Jupyter notebooks.

---

## Step 6 — Register the Environment as a Jupyter Kernel

Register the environment so it becomes available in SARVe Jupyter notebooks:

```bash
python -m ipykernel install --user --name test_env --display-name "Python (test_env)"
```

### Explanation

* `--user` → Installs the kernel for your user account.
* `--name test_env` → Internal kernel identifier.
* `--display-name "Python (test_env)"` → Name displayed in Jupyter.

You can customize the display name if desired.

---

## Step 7 — Use Your Environment in Jupyter

After completing the installation:

1. Open the SARVe Jupyter interface.
2. Create a new notebook or open an existing one.
3. Navigate to:

```text
Kernel → Change Kernel
```

4. Select:

```text
Python (test_env)
```

Your notebook will now use the newly created environment.

---
