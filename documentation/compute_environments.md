(compute-environments)=
# Software Environments

The Fornax Science Console comes with a variety of pre-installed software environments for astronomy, and you can install additional software or create your own environments.
This page explains what's available and how to customize it.

(preinstalled-envs)=
## Pre-installed Environments

A wide variety of software is pre-installed, organized into several {term}`environments <environment>`.
Each environment has a corresponding {term}`kernel <kernel>` with the same name.
These environments are installed in the `$ENV_DIR` directory.
They are described below, grouped by use case.
To learn whether a specific software package is installed, see [](#preinstalled-software).

General astronomy and plotting
:   The `python3` environment ({term}`pip`-based) includes general astronomy and plotting software.
    It is the default environment and is usually a good choice for Python work that doesn't involve high-energy data or Fornax tutorial notebooks.

High-energy astrophysics
:   There are several environments ({term}`conda`-based) containing high-energy software:
    `heasoft` ([HEASoft](https://heasarc.gsfc.nasa.gov/docs/software/lheasoft/)),
    `ciao` ([Chandra CIAO](https://cxc.cfa.harvard.edu/ciao/)),
    `fermi` ([Fermi analysis software](https://fermi.gsfc.nasa.gov/ssc/data/analysis/software/)),
    and `sas` ([XMM-Newton SAS](https://www.cosmos.esa.int/web/xmm-newton/sas)).

    :::{tip} Calibration data
    Some high-energy tools require access to calibration or support data.
    The data are available in the directory `/shared-storage/support-data`.
    Associated environment variables are automatically defined when an environment is activated.
    For example, activating the `heasoft` environment automatically defines the variable `$CALDB`, which points to calibration data on AWS S3 buckets for efficient access.
    :::

Fornax tutorial notebooks
:   The [](#fornax-tutorials) have their own environments ({term}`pip`-based).
    They are named using the syntax `py-{notebook-name}`, for example, `py-light_curve_collector` and `py-multiband_photometry` ([find environment names](#env-dirs)).
    All software needed to run the notebook is pre-installed.
    The correct kernel should start automatically when you open a notebook.
    You can also select it from the kernel drop-down menu at the top right of an open notebook.

Julia and R
:   There are two environments ({term}`conda`-based) for work in languages other than Python.
    The [Julia](https://julialang.org/) environment is named using the syntax `julia-{version-number}` ([find environment names](#env-dirs)).
    It also includes basic astronomy packages.
    The [R](https://www.r-project.org/) environment is named `Renv`.
    Current support for these environments is minimal, but you can [](#install-additional-software).

(select-environment)=
## Activate/Deactivate an Environment

To activate an environment from within a {term}`Jupyter Notebook` or {term}`Console <Jupyter Console>`, activate the corresponding kernel by clicking on the current kernel name at the top right and selecting the desired kernel name from the drop-down menu.
To deactivate the environment, either activate a different kernel or shut down the kernel from the menu `Kernel → Shut Down Kernel`.

To activate or deactivate an environment from the {term}`terminal`, choose from the following instructions depending on whether the [environment is pip- or conda-based](#is-env-pip-conda):

::::{tab-set}
:sync-group: env-type
:::{tab-item} pip-based
:sync: pip
First, you need to [know the environment's name and where it's stored](#env-dirs).
Then, use the syntax `source {env-dir}/{env-name}/bin/activate` to activate (where `{env-dir}` is either `$ENV_DIR` or `$USER_ENV_DIR`, and `{env-name}` is the environment name).
To deactivate, use `deactivate`.

```bash
# Example: Activate the pre-installed `python3` environment.
source $ENV_DIR/python3/bin/activate

# Deactivate the environment.
deactivate
```
:::

:::{tab-item} conda-based
:sync: conda
First, you need to [know the environment's name](#env-dirs).
Then, use the syntax `micromamba activate {env-name}` to activate (where `{env-name}` is the environment name).
To deactivate, use `micromamba deactivate`.

```bash
# Example: Activate the pre-installed `heasoft` environment.
micromamba activate heasoft

# Deactivate the environment.
micromamba deactivate
```
:::
::::

(install-additional-software)=
## Install Additional Software

:::{tip}
Any software from [Python Package Index (PyPI)](https://pypi.org/) or [Anaconda](https://anaconda.org/) can be installed.

See also: [](#install-compilers)
:::

:::{warning}
The `$ENV_DIR` directory is reset when your server restarts.
This means that software added to a pre-installed environment or a temporary, user-created environment will only be available during your current session.
To install software that persists across restarts, [](#create-new-env) with the `--user` option and install your software inside it.
(A workaround for PyPI software is given in the 'pip-based' tab below.)
:::

First, [activate](#select-environment) your desired environment.
Then choose from the following instructions depending on whether the [environment is pip- or conda-based](#is-env-pip-conda):

:::::{tab-set}
:sync-group: env-type
::::{tab-item} pip-based
:sync: pip
Any software available on [PyPI](https://pypi.org/) can be installed in pip-based environments.
The command syntax is `uv pip install {package-name}`.

```bash
# Terminal example: Install the PyYAML package.
uv pip install PyYAML
```

```python
# Notebook example: Prepend `!` so it will execute as a shell command.
!uv pip install PyYAML
```

:::{dropdown} Install persistent software without creating your own environment first
If you want to add PyPI packages that persist across restarts but you don't want to create a full new environment, use the following workaround.

1.  Install to `$USER_ENV_DIR/{my-dir}`, where `{my-dir}` is a directory name of your choosing.
    This only needs to be done once.

    ```bash
    # Terminal example: Install PyYAML in `$USER_ENV_DIR/my-software`.
    uv pip install --target $USER_ENV_DIR/my-software PyYAML
    ```

2.  Add `$USER_ENV_DIR/{my-dir}` to your `$PYTHONPATH`.
    **This needs to be done every time you activate an environment.**

    ```bash
    # Terminal example: Add the directory from step 1 to `PYTHONPATH`.
    export PYTHONPATH=$USER_ENV_DIR/my-software:$PYTHONPATH
    ```

    ```python
    # Notebook example.
    import os
    import sys
    sys.path.insert(0, f"{os.environ['USER_ENV_DIR']}/my-software")
    ```
:::
::::

::::{tab-item} conda-based
:sync: conda
Any software available on [Anaconda](https://anaconda.org/) can be installed in conda-based environments.
We recommend choosing from the [conda-forge channel](https://anaconda.org/channels/conda-forge) whenever possible to reduce dependency conflicts.
The command syntax is `micromamba install {channel-name}::{package-name}`.
To install from the default channel (`conda-forge`), only the package name is needed.

```bash
# Terminal example: Install PyYAML from the default channel.
micromamba install pyyaml
```

:::{tip}
It's possible to install software from [PyPI](https://pypi.org/) in conda-based environments, but this should only be done if the desired software isn't available from Anaconda.
To do this, follow the pip-based instructions in the other tab.
Beware that the conda and pip package managers don't talk to each other, so using both increases the chance of dependency conflicts.
You can reduce the risk by installing software from PyPI only *after* you've installed all software from Anaconda.
:::
::::
:::::

(create-new-env)=
## Create a New Environment and Kernel

You should create a new environment if either of the following is true:

-   You want to install software that persists across server restarts.
-   You want to install software that is isolated from the other software that's installed on the Science Console, perhaps to avoid dependency conflicts.

:::{tip} Persistent vs temporary environments
To create a **persistent** environment, use the `--user` option with the convenience script described below.
A persistent environment and any software you install inside it will be available until you [delete the environment](#delete-env).

To create a **temporary** environment, omit the `--user` option.
A temporary environment and its software will be automatically deleted when you shut down your server.

See also: [](#env-dirs)
:::

First, choose whether you want a {term}`pip`- or {term}`conda`-based environment.
[](#install-additional-software) has more information about what can be installed in each type.
Pip-based environments tend to be faster to create and much smaller in size.

Then, follow these pip or conda instructions:

:::::{tab-set}
:sync-group: env-type
::::{tab-item} pip-based
:sync: pip
Complete the two steps below to create a pip-based environment and a corresponding kernel using the provided convenience script, `setup-pip-env`.
For additional help with the script, run `setup-pip-env -h` in a terminal.
If you'd prefer not to use the script, skip to the 'manual' drop-down at the end of this section.

1.  Create a text file and name it using the syntax `requirements-{env-name}.txt`, where `{env-name}` is an environment name of your choosing.
    In the file, list the packages you want to install.

    ```text
    # Example pip requirements file.
    # Installs NumPy v2.2.0 and the most recent compatible version of Astropy.
    numpy == 2.2.0
    astropy
    ```

    :::{tip}
    To create a copy of an existing environment, create a requirements file that lists its packages.
    First, [find the existing environment's name and path](#env-dirs), then create the file using a command with the syntax `{path-to-existing-env}/bin/pip freeze > requirements-{new-env-name}.txt`.

    ```bash
    # Example: Create a requirements file for a new environment named `my-pip-env`
    # containing packages from the pre-installed `python3` environment.
    $ENV_DIR/python3/bin/pip freeze > requirements-my-pip-env.txt
    ```
    :::

2.  Run the script in a terminal in the same folder as your requirements file.

    ```bash
    # Option 1:
    # Create a persistent environment from the requirements file in this directory.
    setup-pip-env --user

    # Option 2:
    # Create a temporary environment from the requirements file in this directory.
    setup-pip-env
    ```

    The script will find your file and ask you to press the 'Y' key to continue or 'N' to exit.
    If you press 'Y', it will create your environment and a corresponding kernel.

:::{dropdown} Manual method
If you want more control than the convenience script offers, here are the basic instructions to manually create a pip-based environment and kernel.

1.  Choose whether you want a persistent or temporary environment and `cd` into the directory.

    ```bash
    # Option 1: Persistent environment
    cd $USER_ENV_DIR

    # Option 2: Temporary environment
    cd $ENV_DIR
    ```

2.  Create a virtual environment using [uv](https://docs.astral.sh/uv/), activate it, and install software.

    ```bash
    # Example: Create an environment called `my-pip-env` with
    # Python v3.13, activate it, and install NumPy v2.
    uv venv my-pip-env --python=3.13
    source my-pip-env/bin/activate
    uv pip install "numpy>=2"
    ```

3.  Install [ipykernel](https://pypi.org/project/ipykernel/) and create a kernel for your environment.

    ```bash
    # Install ipykernel in your environment.
    uv pip install ipykernel

    # Example: Create a kernel for the `my-pip-env` environment.
    # `--user` is required. Unlike above, it does not determine persistency.
    # Run `python -m ipykernel install --help` to learn more.
    python -m ipykernel install --name my-pip-env --user
    ```

    Your kernel will show up in the kernel selection drop-down menu inside a running notebook (top right).
    Kernels for persistent environments will also appear on the JupyterLab Launcher page.
:::
::::

::::{tab-item} conda-based
:sync: conda
Complete the two steps below to create a conda-based environment and a corresponding kernel using the provided convenience script, `setup-conda-env`.
For additional help with the script, run `setup-conda-env -h` in a terminal.
The tutorial [Setting Up a Conda Environment on Fornax](https://github.com/nasa-fornax/fornax-howtos/blob/main/tutorials/environment_setup/environment_setup.md) walks through an example in more detail.
If you'd prefer not to use the script, skip to the 'manual' drop-down at the end of this section.

1.  Create a yaml file and name it using the syntax `conda-{env-name}.yml`, where `{env-name}` is an environment name of your choosing.
    In the file, list the packages you want to install.

    ```yaml
    # Example conda requirements file for an environment called `my-conda-env`.
    # Installs Python v3.13 and NumPy v2.2.0.
    name: my-conda-env
    channels:
    - conda-forge
    dependencies:
    - python=3.13
    - numpy=2.2.0
    ```

    :::{tip}
    To create a copy of an existing environment, create a requirements file that lists its packages.
    First, [find the existing environment's name](#env-dirs), then create the file using a command with the syntax `micromamba env export -n {existing-env-name} > conda-{new-env-name}.yml`.
    Be sure to edit the file and add your new environment's name at the top and remove the `prefix` line at the bottom.

    ```bash
    # Example: Create a requirements file for a new environment named `my-conda-env`
    # containing packages from the pre-installed `heasoft` environment.
    micromamba env export -n heasoft > conda-my-conda-env.yml

    # Remember to edit the file and add your new environment's
    # name at the top and remove the `prefix` line at the bottom.
    ```
    :::

2.  Run the script in a terminal in the same folder as your yaml file.

    ```bash
    # Option 1:
    # Create a persistent environment from the yaml file in this directory.
    setup-conda-env --user

    # Option 2:
    # Create a temporary environment from the yaml file in this directory.
    setup-conda-env
    ```

    The script will find your file and ask you to press the 'Y' key to continue or 'N' to exit.
    If you press 'Y', it will create your environment and a corresponding kernel.
    Running the setup may take many minutes and the resulting environment may be GB in size.

:::{dropdown} Manual method
If you want more control than the convenience script offers, here are the basic instructions to manually create a conda-based environment and kernel.

1.  Choose whether you want a persistent or temporary environment and `cd` into the directory.

    ```bash
    # Option 1: Persistent environment
    cd $USER_ENV_DIR

    # Option 2: Temporary environment
    cd $ENV_DIR
    ```

2.  Create an environment using [micromamba](https://docs.astral.sh/uv/), activate it, and install software.

    ```bash
    # Example: Create an environment called `my-conda-env` with
    # Python v3.13, activate it, and install NumPy v2.
    micromamba create -p ./my-conda-env python=3.13
    micromamba activate my-conda-env
    micromamba install "numpy>=2"
    ```

3.  Install [ipykernel](https://pypi.org/project/ipykernel/) and create a kernel for your environment.

    ```bash
    # Install ipykernel in your environment.
    micromamba install ipykernel

    # Example: Create a kernel for the `my-conda-env` environment.
    # `--user` is required. Unlike above, it does not determine persistency.
    # Run `python -m ipykernel install --help` to learn more.
    python -m ipykernel install --name my-conda-env --user
    ```

    Your kernel will show up in the kernel selection drop-down menu inside a running notebook (top right).
    Kernels for persistent environments will also appear on the JupyterLab Launcher page.
:::
::::

(delete-env)=
## Delete an Environment and Kernel

First, be sure to [deactivate the environment and kernel](#select-environment).

To delete an environment, [find the environment](#env-dirs) and then delete its directory.

```bash
# Example: Delete a persistent user-created environment called `my-conda-env`.
rm -r $USER_ENV_DIR/my-pip-env
```

To delete a kernel, [find the kernel](#env-dirs) and then delete its directory.

```bash
# Example: Delete a user-created kernel called `myenv`.
rm -r ~/.local/share/jupyter/kernels/myenv
```

(other-languages)=
## Julia and Other Languages

Although our focus is on Python, you can work in other languages.
Basic [environments for Julia and R are pre-installed](#preinstalled-envs).
You can also [create your own environment](#create-new-env) (choose conda) and/or [install any software](#install-additional-software) you want.
Many languages offer installation packages via conda, for example:

-   [rust](https://anaconda.org/channels/conda-forge/packages/rust/overview)
-   [gfortran](https://anaconda.org/channels/conda-forge/packages/gfortran/overview)
-   [julia](https://anaconda.org/channels/conda-forge/packages/julia/overview)
-   [r](https://anaconda.org/channels/conda-forge/packages/r/overview)

See also: [](#install-compilers)

## System Tools

As part of system optimization and to allow users to manage their own software, the list of packages installed via Ubuntu `apt` is kept to a minimum.
Many useful packages (`vim`, `htop`, `git`, `awscli`, etc.) are installed from `conda-forge` into the `base` conda environment under `$ENV_DIR/base`.
You can add packages to this environment by running:

```bash
micromamba install package_name
```

For non-Python tools (e.g. `htop`, `vim`), they can be run directly from the terminal without activating the base environment, as they are included in the `PATH` by default.

(shell-config)=
## Shell Configuration

The system uses bash as the default shell.
The JupyterLab terminal uses a non-login shell, which means `~/.bashrc` is not called by default when a new terminal session starts.
`~/.profile` on the other hand is called.
You can therefore use it for any bash initialization code.
A new `~/.profile` is created at login time if it does not exist, and it also calls `~/.bashrc`, so you can add your customization (e.g. update `PATH`, set up Rust or Julia, etc.) to either one.
