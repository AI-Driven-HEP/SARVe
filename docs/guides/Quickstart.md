# Quickstart
This guide explains how to set up your working environment on SARVe, create and manage Python environments, and configure JupyterLab kernels for interactive development and analysis.

## Python environment
We recomment using conda and/or mamba to manage your Python environment.

While you may use the default conda **base environment** provided by the server, creating your own dedicated environment is generally recommended for reproducibility, package management, and dependency isolation.

???+ Warning

    Changes made to the server's default/base environment are **not persistent** as they are stored in server's ephemeral storage. After your server is stopped or restarted, the base environment **will** reset to its original state, causing installed packages and modifications to be lost.

Using a dedicated Python environment ensures that your setup remains available across sessions.

???+ Tip

    For best performance, it is recommended to work within **`~/localstorage`** directory. See Storage for more details on different storage types and how you could use them in your project.

### Custom Python environment creation using conda
To quickly create a custom Python environment with conda with name env and using Python 3.13 in `localstorage`, open a terminal and use: 

```bash
conda create --prefix ~/localstorage/env python=3.13
conda init
conda activate ~/localstorage/env
```

### Adding a conda environment to Jupyter
The newly created environment is usable in terminal, but not in JupyterLab. To register it in JupyterLab install the `ipykernel` package inside the environment and use it to register the environment in JupyterLab kernel list.

```bash
conda install conda-forge::ipykernel
python -m ipykernel install --user --name env --display-name "Python (env)"
```

### Using a custom Python environment in JupyterLab
After creating a Python environment, JupyterLab won't automatically switch to it. To change the environment used by JupyterLab, change it's kernel to the kernel registered for your custom environment. To change the kernel used by JupyterLab:

1. Open the SARVe JupyterLab interface.
2. Create a new notebook or open an existing one.
3. Navigate to:
```text
Kernel → Change Kernel
```

4. Select:

```text
Python (env)
```

Your notebook will now use the newly created environment.

## Installing a Python package
To install a Python package, use your favorite Python package manager. We recommend using conda or mamba.

???+ Example

    ```bash
    conda install numpy scipy matplotlib pandas
    ```

???+ Note

    Python packages are installed in your Python environment. Make sure to create a personal environment if you want installed packages to persist over sessions.

## Installing a system package
The default JupyterLab server runs on ubuntu. To install a system package use `apt`. 

???+ Example

    ```bash
    sudo apt install gcc
    ```

???+ Note

    System packages are installed in ephemeral storage which means they get reset after your server is stopped. To permanently install a system package you have to create a custom container image and include the package in it. See custom container image creation for details on how the default image is created and how you can add packages to it.


*[SARVe]: Scalable Analytics and Research Virtual Environment