(compute-environments)=
# Compute Environments

The Fornax Science Console offers several pre-installed {term}`environments <environment>`.
The specific environments that are available depend on the {ref}`base-environment` (container image) you selected when starting your server.
All container images use an x86_64 Ubuntu Linux system.
Each comes pre-installed with JupyterLab extensions as well as one or more Python software environments.
You can customize your experience by installing additional Python software in the pre-installed environments as well as creating new environments, installing additional JupyterLab extensions, and installing non-Python software.
This page describes the details.

## Working with Python Environments

`python3` is the default Python {term}`environment <environment>`.
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

There are two types of Python environments, **pip**-based and **conda**-based.

**pip**-based
:   The **pip**-based environments use [uv](https://docs.astral.sh/uv/) to manage the packages.
    These environments contain `pip`-installable packages and are used in most cases.
    The default environments are installed under `$ENV_DIR`.
    They are activated as indicated above with `source $ENV_DIR/{env-name}/bin/activate`.

**conda**-based
:   These use [micromamba](https://mamba.readthedocs.io/en/latest/user_guide/micromamba.html) to manage the packages (similar to conda/mamba):
    The `conda`-based environments are used with packages that are not `pip`-installable.
    Examples of this include `heasoft` and `ciao` in the high-energy container image.
    These are activated with `micromamba activate {env-name}` and deactivated with `micromamba deactivate`.
    These are also installed under `$ENV_DIR`. You can use `micromamba env list` to list the environments.

### Pre-installed Environments

The following environments are pre-installed:

`python3`
:   This is the default Python environment.
    It has general astronomy and plotting software.

`py-{notebook-name}`
:   Each of the Fornax demo notebooks has its own environment with a name of the form `py-{notebook-name}` (e.g. `py-light_curve_collector` and `py-multiband_photometry`).
    Each environment has the packages required to run the notebook pre-installed.
    When opening the notebook, the corresponding {term}`kernel <kernel>` should automatically start.
    You can also select it from the drop down kernel menu at the top-right of an open notebook.

`heasoft`, `ciao`, `fermi`, `sas`
:   Environments for high energy software that includes:
    [heasoft](https://heasarc.gsfc.nasa.gov/docs/software/lheasoft/),
    Chandra [ciao](https://cxc.cfa.harvard.edu/ciao/),
    [Fermi analysis software](https://fermi.gsfc.nasa.gov/ssc/data/analysis/software/),
    and [XMM-Newton SAS](https://www.cosmos.esa.int/web/xmm-newton/sas).
    

See {ref}`view-preinstalled-software` to learn about specific libraries each environment contains.

(select-environment)=
### Select an Environment

**Notebook:** To activate a specific environment from a {term}`notebook <Jupyter Notebook>`, click on the name of the notebook's current environment at the top right and then select your desired environment from the kernel drop down menu.
If you open a Fornax demo notebook and get a popup window asking you to select a kernel, choose the kernel from the drop down menu with the same name as the notebook you are opening.
If you open any other notebook and get a popup window asking you to select a kernel, `python3` is usually the best choice.

**Terminal:** To activate a specific environment from the {term}`terminal <terminal>`, run: `source $ENV_DIR/{environment-name}/bin/activate`.
For example, to activate the `py-light_curve_classifier` environment, run:

```sh
source $ENV_DIR/py-light_curve_classifier/bin/activate
```

and the following to deactivate it:

```sh
deactivate
```

(install-additional-software)=
### Install Additional Software

To install additional Python software, you can either update an existing environment or create a new one.

#### Update an Existing Environment

To add packages to a currently installed environment, you install them with `pip` (or the faster `uv pip`) after activating the relevant environment.

-   Inside a {term}`notebook <Jupyter Notebook>` running the relevant environment, run `!uv pip install ...`, passing the extra packaged needed.
-   In the {term}`terminal <terminal>`, after activating the environment run: `uv pip install ...`.

This should work for both pip and conda-based environments.

**Note** that packages installed this way are added in the global `$ENV_DIR` folder, which is reset when you start a new session.
It is highly recommended that you create new environments if you want to install new packages (See {ref}`create-new-env`),
but if you want add a small number of packages to a built-in environment, you can follow these steps:

- From the {term}`terminal <terminal>`, activate the desired environment (see {ref}`view-preinstalled-software`).
- Add the packages with: `uv pip install --target $USER_ENV_DIR/{env_name} package-1 package-2`. Where `{env_name}` is the folder name of choice.
- Tell the environment about the new location:
    - In a {term}`terminal <terminal>`: `export PYTHONPATH=$USER_ENV_DIR/{env_name}`.
    - In a {term}`notebook <Jupyter Notebook>`, add the following at the top:
```python
import sys, os
sys.path.insert(0, f"{os.environ['USER_ENV_DIR']}/{env_name}")
```

The solution is this case is to create your own environments that are independent of the container image (next section).

(create-new-env)=
#### Create a New Environment

To create a new environment, we recommend using one of the provided scripts: `setup-pip-env` or `setup-conda-env`.

Run `setup-pip-env -h` or `setup-conda-env -h` from the {term}`terminal <terminal>` for detailed help.
These scripts take need either a requirements file (former) or a conda yaml file (latter), and create
the environment, including the setup of the kernel so you can user the environment in a notebook.

- For pip-based environments (recommended):
    - Create a requirement file named: `requirements-{env-name}.txt` (e.g. `requirements-myenv.txt` bellow).
    - Call `setup-pip-env`. By default, the environment is created in a global location (`$ENV_DIR`),
      that is reset at the start of every session. Use this for environment that are needed for a single
      session.
      If you want the environment to persist between sessions, use `setup-pip-env --user`. This will install
      the new environment under `$USER_ENV_DIR` (defaults to `~/user-envs`).

:::{dropdown} `requirements-myenv.txt`

```
numpy == 2.2.0
astropy
```
:::

- For conda-based environment (If your packages are not pip-installable):
    - Create an environment file: `conda-{env-name}.yml` (e.g. `conda-myenv.yml` below).
    - Call `setup-conda-env`. Similar to the pip-case, the environment is created in a global default location (`$ENV_DIR`),
      that is reset at the start of every session.
      If you want the environment to persist between sessions, use `setup-conda-env --user`.

:::{dropdown} `conda-myenv.yml`

```yaml
name: myenv
channels:
  - conda-forge
dependencies:
  - python=3.11
  - numpy=2.2.0
  - pip
  - pip:
    - matplotlib
```
:::

\

:::{note} Details on installing new enviornments by hand
:class: dropdown

You can also do all the setup by hand if you want more control.
Persistent environment should be installed under `$USER_ENV_DIR`:

```sh
cd $USER_ENV_DIR
uv venv myenv --python=3.11
source myenv/bin/activate
# add numpy for example
uv pip install "numpy<2"
```
This will create a new environment with Python version 3.11, activate it, and then install a "numpy<2".

In order to use this new environment in a {term}`notebook <Jupyter Notebook>`, you'll need to install `ipykernel` inside the environment and then register it with JupyterLab.

```sh
uv pip install ipykernel
python -m ipykernel install --name myenv --user
```

The {term}`kernel <Kernel>` should show up in the JupyterLab main launcher page and in the kernel selection dropdown menu inside a running notebook.

The same can be done for conda environments. A conda environment can be created by:

```sh
micromamba create -p ~/user-envs/my-conda-env python=3.12 pandas
micromamba activate -p ~/user-envs/my-conda-env
```

Similarly, to use this environment in a {term}`notebook <Jupyter Notebook>`, you'll need to install `ipykernel` and register it with JupyterLab like for pip-installed environments.
:::

:::{attention}
It is recommended that you remove user environments that are no longer needed, as they may deplete your home storage.
:::

## JupyterLab Extensions

Pre-installed extensions are described on the {ref}`jupyterlab` page.

### Install a New Extension

Instructions on how to find and install extensions can be found at [JupyterLab: Extensions](https://jupyterlab.readthedocs.io/en/stable/user/extensions.html).
Extensions may include a front-end component, a server-side component, or both.
You can install front-end extensions after JupyterLab starts, and they can show up if you refresh the page, as long they are installed in the environment running JupyterLab (`/opt/jupyter/`).
Extensions that include a server-side component cannot be installed by individual users because they must be installed before JupyterLab starts.
In that case, please open a helpdesk request on the {ref}`intro-forum`.

## Compilers and General Software

As part of the system optimization and to allow for users to manage their own software, the list of packages installed in the system (using ubuntu `apt`) is kept to a minimum.
Many of the useful packages (vim, htop, git, awscli, etc) are installed from `conda-forge` into the `base` conda environment under `$ENV_DIR/base`. You can add packages to this environment by doing:

```sh
micromamba install package_name
```

You can also include compilers.
For example, to install C, C++ and Fortran compilers, you can do:

```sh
micromamba install c-compiler cxx-compiler fortran-compiler
```

For non-Python tools (e.g. `htop`, `vim` etc), they can be run directly from the terminal without a need for activating the base environment as they are included in the `PATH` by default.
