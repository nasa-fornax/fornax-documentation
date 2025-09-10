(compute-environments)=
# Compute Environments

The Fornax Science Console offers compute environments which you can select by choosing a container image when starting your server. All the images uses an x86_64 Ubuntu linux system.
Each compute environment comes pre-installed with JupyterLab extensions as well as one or more Python software environments (or simply, "environments").
You can customize your experience by installing additional extensions and software.

## Working with Python Environments

`python3` is the default python {term}`environment <environment>`.
It has general astronomy and plotting software.

Each of the Fornax demo notebooks has its own environment with a name of the form `py-{notebook-name}` (e.g. `py-light_curve_collector` and `py-multiband_photometry`).
Each environment has the packages required to run the notebook pre-installed (see {ref}`view-preinstalled-software`).
When opening the notebook, the corresponding {term}`kernel <kernel>` should automatically start.
You can also select it from the drop down kernel menu at the top-right of an open notebook.

To activate a specific pip-based environment (see {ref}`environment-types` for details) from the {term}`terminal <terminal>`, run: `source $ENV_DIR/{environment-name}/bin/activate`.
For example, to activate the `py-light_curve_classifier` environment, run:

```sh
source $ENV_DIR/py-light_curve_classifier/bin/activate
```

and the following to deactivate it:

```sh
deactivate
```
(environment-types)=
### Environment Types

There are two types of python environments, **pip**-based and **conda**-based.

**pip**-based:
The **pip**-based environments use [uv](https://docs.astral.sh/uv/) to manage the packages.
These environments contain `pip`-installable packages and are used in most cases.
The default environments are installed under `$ENV_DIR`.
They are activated as indicated above with `source $ENV_DIR/{env-name}/bin/activate`.

**conda**-based:
These use [micromamba](https://mamba.readthedocs.io/en/latest/user_guide/micromamba.html) to manage the packages (similar to conda/mamba):
The `conda`-based environments are used when packages that are not `pip`-installable.
Examples of this include `heasoft` and `ciao` in the high-energy container image.
These are activated with `micromamba activate {env-name}` and deactivated with `micromamba deactivate`.
These are also installed under `$ENV_DIR`

### Pre-installed Environments

The following environments are pre-installed:

-   `python3`: This is the default Python environment.
    It has general astronomy and plotting software.
-   `py-{notebook-name}`: Each of the Fornax demo notebooks has its own environment with a name of the form `py-{notebook-name}` (e.g. `py-light_curve_collector` and `py-multiband_photometry`).
    Each environment has the packages required to run the notebook pre-installed.
    When opening the notebook, the corresponding {term}`kernel <kernel>` should automatically start.
    You can also select it from the drop down kernel menu at the top-right of an open notebook.

See {ref}`view-preinstalled-software` to learn about specific libraries each environment contains.

### Select an Environment

**Notebook:** To activate a specific environment from a {term}`notebook <Jupyter Notebook>`, click on the name of the notebook's current environment at the top right and then select your desired environment from the kernel drop down menu.

**Terminal:** To activate a specific environment from the {term}`terminal <terminal>`, run: `source $ENV_DIR/{environment-name}/bin/activate`.
For example, to activate the `py-light_curve_classifier` environment, run:

```sh
source $ENV_DIR/py-light_curve_classifier/bin/activate
```

and the following to deactivate it:

```sh
deactivate
```

### Install Additional Software

To install additional software, you can either update an existing environment or create a new one.

#### Update an Existing Environment

To add packages to a currently installed environment, you install them with `pip` (or the faster `uv pip`) after activating the relevant environment.

-   Inside a {term}`notebook <Jupyter Notebook>` running the relevant environment, run `!uv pip install ...`, passing the extra packaged needed.
-   In the {term}`terminal <terminal>`, after activating the environment run: `uv pip install ...`.

**Note** that packages installed this way are added in the `$ENV_DIR` folder, and therefore are not saved for the next session.
To ensure the packages are available in the next session, you can install them in your home directory by adding `--user` to the pip command.

Note also, that if the container image is updated, packages installed with the `--user` option may not be compatible with the new image and package conflicts may arise.
The solution is this case is to create your own environments that are independent of the container image (next bullet).

#### Create a New Environment

To create a new environment that persists between sessions, create a folder in your home directory where user environments will be installed.
Say `mkdir ~/user-envs`.
Then inside that folder run the following to create an environment:

```sh
cd ~/user-envs
uv venv myenv --python=3.11
source myenv/bin/activate
# add numpy for example
uv pip install "numpy<2"
```

This will create a new environment with python version 3.11, activate it, and then install a "numpy<2".

In order to use this new environment in a {term}`notebook <Jupyter Notebook>`, you'll need to install `ipykernel` inside the environment and then register it with jupyterlab.

```sh
uv pip install ipykernel
python -m ipykernel install --name myenv --user
```

The {term}`kernel <Kernel>` should show up in the JupyterLab main launcher page and in the kernel selection dropdown menu inside a running notebook.

The same can be done for conda enviornments. A conda environment can be created by:

```sh
micromamba create -p ~/user-envs/my-conda-env python=3.12 pandas
micromamba activate -p ~/user-envs/my-conda-env
```

Similarly, to use this environment in a {term}`notebook <Jupyter Notebook>`, you'll need to install `ipykernel` and register it with jupyterlab like for pip-installed environments.

**Note**: It is recommended that you remove user environments that are no longer needed, as they may deplete your home storage.

## JupyterLab Extensions

Pre-installed extensions are described on the {ref}`jupyterlab` page.

### Install a New Extension

Instructions on how to find and install extensions can be found at [JupyterLab: Extensions](https://jupyterlab.readthedocs.io/en/stable/user/extensions.html).
Extensions may include a front-end component, a server-side component, or both.
You can install front-end extensions after JupyterLab starts, and they can show up if you refresh the page, as long they are installed in the environment running JupyterLab (`/opt/jupyter/`).
Extensions that include a server-side component cannot be installed by individual users because they must be installed before JupyterLab starts.
In that case, please open a helpdesk request on the {ref}`intro-forum`.

## Compilers and General Software
As part of the system optimization and to allow for users to manage their own software,
the list of packages installed in the system (using ubuntu `apt`) is kept to a minimum.
Many of the useful packages (vim, htop, git, awscli, etc) are installed from `conda-forge`
into the `base` conda environment under `$ENV_DIR/base`. You can add packages to this envionment
by doing:
```sh
micromamba install package_name
```
including compilers. For example, you can do:
```sh
micromamba install c-compiler cxx-compiler fortran-compiler
```
to install C, C++ and Fortran compilers. For non-python tools (e.g. `htop`, `vim` etc),
they can be run directly from the terminal without a need for activatign the base
environment, as they are included in the `PATH` by default.
