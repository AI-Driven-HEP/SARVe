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

