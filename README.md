# SARVe (Scalable Analytics and Research Virtual Environment)

This guide explains how to set up your working environment on **SARVe**, create and manage Python environments, and configure Jupyter kernels for interactive development and analysis.

---

## Overview

**SARVe** provides computational resources and Jupyter-based interactive environments for scientific computing, data analysis, and research workflows.

For best performance and persistence, it is strongly recommended to work within your **`localstorage/`** directory. This storage location offers faster access and is intended for user environments, project files, and installed packages.

While you may use the default **base environment** provided by the server, creating your own dedicated environment is generally recommended for reproducibility, package management, and dependency isolation.

> **Important:**
> Changes made to the server's default/base environment are **not persistent**. After your server is stopped or restarted, the base environment may reset to its original state, causing installed packages and modifications to be lost.

Using a personal Conda environment stored in `localstorage/` ensures that your setup remains available across sessions.


---

## Step 1 — Navigate to Your Storage Directory

After logging into SARVe, open a terminal and move to your storage directory:

```bash
cd localstorage/
```

This location will be used to store your custom Conda environments and project files.

---

## Step 2 — Create a New Conda Environment

Create a new Conda environment using a local installation path.

Example:

```bash
conda create --prefix ./test_env python=3.13
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
conda activate /home/jovyan/localstorage/test_env
```

### Explanation

Since the environment was created using `--prefix`, activation requires the **full path** to the environment directory.

Replace:

```text
test_env
```

with the name of your environment if you used a different one.

---

## Step 5 — Install Jupyter Kernel Support

Install the `ipykernel` package inside the environment:

```bash
conda install conda-forge::ipykernel
```

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

## Example Workflow

```bash
cd localstorage/

conda create --prefix ./test_env python=3.13

conda init

conda activate /home/jovyan/localstorage/test_env

conda install conda-forge::ipykernel

python -m ipykernel install --user --name test_env --display-name "Python (test_env)"
```

---

## Notes

* Store environments inside `localstorage/` to preserve your work.
* Use descriptive environment names for different projects.
* Install project dependencies after activating the environment.

Example:

```bash
conda install numpy scipy matplotlib pandas
```

or

```bash
pip install package_name
```

---

## Acknowledgement

### How to cite the facility in your acknowledgements

Please include the following statement in the acknowledgements section of your presentation, poster, or publication:


The authors acknowledge the computational resources provided by the Scalable Analytics and Research Virtual Environment (SARVe) facility at the School of Theoretical Physics, IPM.
