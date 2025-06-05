# Compute Environments

The Fornax Science Console offers a few Software environments, the most relevant of which are:

- **Default Astrophysics** (recommended for most use cases)
- **High-Energy Astrophysics**


To view the software pre-installed in each environment:

1. Open a terminal in the Fornax Science Console JupyterLab.
2. Activate the environment you want to inspect using:
   ```conda activate <environment-name>```
3. Run the following command to list all installed packages:
    ```conda list```


For more details, see the official [conda list documentation](https://docs.conda.io/projects/conda/en/latest/commands/list.html).

## Installing additional software on the Fornax Science Console

There are two basic ways to install software that you would like to use in the Fornax Science Console, if the offereed environments do not meet your needs.

### Create your own Conda Environment

Creating your own Conda environment gives you full control to install custom packages, libraries, and tools—and your environment will be saved across sessions, even if you log out or restart your server.

How to get started:

1. Login to the Fornax Science Console, start JupyterHub, and open a terminal from the JupyterLab Launcher.

2. Create a new Conda environment:

```conda create --name myenv python=3.10```

3. Activate it:

```conda activate myenv```

4. Install any additional packages you need:

```conda install numpy matplotlib astropy```

For more detailed help, check out the Conda documentation:

- [Getting Started with Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html)  
- [Managing Environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)

### Install packages using `pip` within a notebook

You can install Python packages directly from a notebook using `pip`. These installations will persist across kernel restarts within the same session, so you won’t need to reinstall them every time you rerun your code.

However, they do not persist if you stop and restart your server (e.g., by logging out or shutting down your workspace)—unless you install the package using the `--user` flag. This tells `pip` to install the package into your home directory, making it available across sessions.

Example:

```!pip install --user package-name```

To check the version and metadata for a specific installed package, use the following terminal command:

```pip show package-name```

