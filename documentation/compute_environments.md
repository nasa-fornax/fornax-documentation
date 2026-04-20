(compute-environments)=
# Compute Environments

The Fornax Science Console is a lightly customized {term}`JupyterLab` environment running on AWS cloud servers (x86_64 Ubuntu Linux).
Several {term}`software environments <environment>` and JupyterLab extensions are pre-installed.
Users can also customize their experience by installing additional software and/or JupyterLab extensions.
This page describes the pre-installed tools and customization instructions.

## Python Environments

(environment-types)=
### Environment Types

There are two types of Python environments, **pip**-based and **conda**-based.

**pip**-based
:   The **pip**-based environments use [uv](https://docs.astral.sh/uv/) to manage the packages.
    These environments contain `pip`-installable packages and are used in most cases.
    The default environments are installed under `$ENV_DIR`.

**conda**-based
:   These use [micromamba](https://mamba.readthedocs.io/en/latest/user_guide/micromamba.html) to manage the packages (similar to conda/mamba):
    The `conda`-based environments are used with packages that are not `pip`-installable.
    These are also installed under `$ENV_DIR`. You can also use `micromamba env list` to list the conda based environments.

    Currently-installed conda-based environments include: `heasoft`, `ciao`, `sas` and `fermi` for high energy astrophysics software.

(preinstalled-software)=
### Pre-installed Environments

A wide variety of software is pre-installed.
A detailed accounting can be found in the environment lock files in the `$LOCK_DIR` directory or on the [latest image release](https://github.com/nasa-fornax/fornax-images/releases/latest) page.
The software is organized into several environments.
Each environment has a corresponding {term}`kernel <kernel>` with the same name.

`python3`
:   This is the default Python environment and is **pip**-based.
    It has general astronomy and plotting software.
    This is usually a good choice for any work that doesn't involve high-energy data or a Fornax demo notebook.

`py-{notebook-name}`
:   These environments are **pip**-based.
    Each of the Fornax demo notebooks has its own environment with a name of the form `py-{notebook-name}` (e.g. `py-light_curve_collector` and `py-multiband_photometry`) and the packages required to run the notebook pre-installed.
    When opening a notebook, the corresponding kernel should automatically start.
    You can also select it from the drop down kernel menu at the top-right of an open notebook.

`heasoft`, `ciao`, `fermi`, `sas`
:   Environments for high energy software are **conda**-based and include:
    [heasoft](https://heasarc.gsfc.nasa.gov/docs/software/lheasoft/),
    [Chandra ciao](https://cxc.cfa.harvard.edu/ciao/),
    [Fermi analysis software](https://fermi.gsfc.nasa.gov/ssc/data/analysis/software/),
    and [XMM-Newton SAS](https://www.cosmos.esa.int/web/xmm-newton/sas).


(select-environment)=
### Activate an Environment

**Notebook:** To activate a specific environment from a {term}`notebook <Jupyter Notebook>`, click on the name of the notebook's current environment at the top right and then select your desired environment from the kernel drop down menu.
Notebooks can use either a **pip**-based or **conda**-based environment.
If you open a Fornax demo notebook and get a popup window asking you to select a kernel, choose the kernel from the drop down menu with the same name as the notebook you are opening.
If you open any other notebook and get a popup window asking you to select a kernel, `python3` is usually the best choice, unless you already know which environment you need.

**Terminal:** To activate a specific **pip**-based environment (see {ref}`environment-types` for details) from the {term}`terminal <terminal>`, run: `source $ENV_DIR/{environment-name}/bin/activate`.
For example, to activate the `py-light_curve_classifier` environment, run:

```bash
source $ENV_DIR/py-light_curve_classifier/bin/activate
```

and the following to deactivate it:

```bash
deactivate
```

To activate a specific **conda**-based environment (see {ref}`environment-types` for details) from the {term}`terminal <terminal>`, run: `micromamba activate {env-name}`.
For example, to activate the `heasoft` environment, run:

```bash
micromamba activate heasoft
```

and the following to deactivate it:

```bash
micromamba deactivate
```

(install-additional-software)=
### Install Additional Software - Update an Existing Environment

:::{note}
Note that packages installed this way are added in the global `$ENV_DIR` folder, which is reset when you start a new session.
It is highly recommended that you [create a new environment](#create-new-env) if you want to install new packages.
In this case, the environment is added to $USER_ENV_DIR
:::

To add packages to a currently installed environment, you install them with `pip` (or the faster `uv pip`) after activating the relevant environment.

-   Inside a {term}`notebook <Jupyter Notebook>` running the relevant environment, run `!uv pip install ...`, passing the extra package needed.
-   In the {term}`terminal <terminal>`, after activating the environment run: `uv pip install ...`.

This should work for both pip and conda-based environments.

If you want to add a small number of packages to a built-in environment, however, you can follow these steps:

- From the terminal, [activate the desired environment](#select-environment).
- Add the packages with: `uv pip install --target $USER_ENV_DIR/{env_name} package-1 package-2`, where `{env_name}` is the folder name of choice.
- Tell the environment about the new location:
    - In a terminal: `export PYTHONPATH=$USER_ENV_DIR/{env_name}:$PYTHONPATH`.
    - In a notebook, add the following at the top:
        ```python
        import os
        import sys
        sys.path.insert(0, f"{os.environ['USER_ENV_DIR']}/{env_name}")
        ```

(create-new-env)=
### Install Additional Software - Create a New Environment

Create a new environment when you want your installed packages to be persistent, isolated, and reproducible across sessions, rather than temporarily added to a shared environment that is reset when your session ends.
To create a new environment, we recommend using one of the provided scripts: `setup-pip-env` or `setup-conda-env`.

Run `setup-pip-env -h` or `setup-conda-env -h` from the {term}`terminal <terminal>` for detailed help.
These scripts take either a requirements file (former) or a conda yaml file (latter), and create the environment, including the setup of the kernel so you can use the environment in a notebook.

- For pip-based environments (recommended):
    - Create a requirement file named: `requirements-{env-name}.txt` (e.g. `requirements-myenv.txt` bellow).
    - Call `setup-pip-env` from the same folder.
      By default, the environment is created in a global location (`$ENV_DIR`), that is reset at the start of every session.
      Use this for environments that are needed for a single session.
      If you want the environment to persist between sessions, use `setup-pip-env --user`.
      This will install the new environment under `$USER_ENV_DIR` (defaults to `~/user-envs`).

    :::{dropdown} `Example requirements-myenv.txt`

    ```
    numpy == 2.2.0
    astropy
    ```
    :::

- For conda-based environments (if your packages are not pip-installable):
    - Create an environment file: `conda-{env-name}.yml` (e.g. `conda-myenv.yml` below).
    - From the terminal, call `setup-conda-env` --user.
      Similar to the pip-case, the environment is created in a global default location (`$ENV_DIR`), that is reset at the start of every session.
      If you do not want the environment to persist between sessions, use `setup-conda-env` (without the `--user`).
    - When you run `setup-conda-env` it will automatically find all the .yml files in your directory and ask which one to use.
    - Running the setup may take many minutes and be GB in size.
    - To use this environment, in the terminal you need to activate with:
        - `micromamba activate $USER_ENV_DIR/{env_name}`
        - or `micromamba activate $ENV_DIR/{env_name}` if you didn't pass --user
    - If you are working in a notebook, you can now choose that environment name as your kernel either by using the dropdown in the upper right or selecting the kernel menu -> change kernel

    :::{dropdown} `Example conda-myenv.yml`

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

:::{note} Details on manually installing new environments
:class: dropdown

You can also do all the setup by hand if you want more control.
Persistent environment should be installed under `$USER_ENV_DIR`:

```bash
cd $USER_ENV_DIR
uv venv myenv --python=3.11
source myenv/bin/activate
# add numpy for example
uv pip install "numpy<2"
```

This will create a new environment with Python version 3.11, activate it, and then install a "numpy<2".

In order to use this new environment in a {term}`notebook <Jupyter Notebook>`, you'll need to install `ipykernel` inside the environment and then register it with JupyterLab.

```bash
uv pip install ipykernel
python -m ipykernel install --name myenv --user
```

The {term}`kernel <Kernel>` should show up in the JupyterLab main launcher page and in the kernel selection dropdown menu inside a running notebook.

The same can be done for conda environments.
A conda environment can be created by:

```bash
micromamba create -p ~/user-envs/my-conda-env python=3.12 pandas
micromamba activate -p ~/user-envs/my-conda-env
```

Similarly, to use this environment in a {term}`notebook <Jupyter Notebook>`, you'll need to install `ipykernel` and register it with JupyterLab like the pip environments.
:::

(delete-user-env)=
### Deleting a User Environment

Deleting a user envivronment that was created either manually or with the scripts provided can be done with these two steps:

- Delete the environment folder under `~/user-envs/` (or wherever else it is was installed).
- Remove the kernel for that environment by deleting the the folder with the environment name from `~/.local/share/jupyter/kernels/`.

As a tip, running the following in the terminal, will list all the installed kernels. It can be used to find the location of installed kernels:
```bash
$JUPYTER_DIR/bin/jupyter kernelspec list
```

:::{attention}
It is recommended that you remove user environments in your home directory that are no longer needed, as they may deplete your home storage and consume your allocated credit.
:::

(calibration-data)=
### Calibration Data
Some software tools require access to calibration or support data. These are currently provided via:

- `/shared-storage/support-data`: This is a shared storage that contains the support data for some of the high energy software such as HEASoft, CIAO, XMM SAS etc.

- Environment variables associated with specific environments. For example, activating `heasoft` (see {ref}`select-environment`) defines the relevant environment variables for CALDB, which point to the calibration data on AWS S3 buckets for efficient access.

## Other Environments

Although the focus is on Python environments, additional environments are also available.
There are pre-installed [R](https://www.r-project.org/) and [Julia](https://julialang.org/) environments.
The current support for these environments is minimal, with no tutorial notebooks.
The `Julia` environment has basic astronomy packages installed, and the environment files are available under `$LOCK_DIR/julia`.
You can also [create your own Julia environment](https://pkgdocs.julialang.org/v1/environments/).

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
Many of the useful packages (vim, htop, git, awscli, etc) are installed from `conda-forge` into the `base` conda environment under `$ENV_DIR/base`.
You can add packages to this environment by doing:

```bash
micromamba install package_name
```

You can also include compilers.
For example, to install C, C++ and Fortran compilers, you can do:

```bash
micromamba install c-compiler cxx-compiler fortran-compiler
```

For non-Python tools (e.g. `htop`, `vim` etc), they can be run directly from the terminal without a need for activating the base environment as they are included in the `PATH` by default.

## Terminal Initialization scripts

The system uses bash as a default shell.
The Jupyterlab terminal uses a non-login shell, which means `~/.bashrc` is not called by default when a new terminal session starts.
`~/.profile` on the other hand is called.
You can therefore use it for any bash initialization code.
A new `~/.profile` is created at login time if it does not exist, and it also calls `~/.bashrc`, so you can add you customization (e.g. update `PATH`, setup rust or julia, etc) to either one.


# Using Fornax Software Environments Outside Fornax Console
The Fornax software environments are available as docker container images in the github container registry.
To use them outside the Fornax console (e.g. on your local machine),
you will need to install [docker](https://docs.docker.com/engine/install/).

## Setup
Start in a empty working direcotry that will be used for sharing data between the container and your system.

The Fornax images are available from the github registry: `ghcr.io/nasa-fornax/fornax-images`.

Two images are provided. `fornax-main` and `fornax-hea`:

- `fornax-main`: Contains general astronomy software, the Fornax tutorial notebooks and their pre-installed environments, Julia and R kernels.
- `fornax-hea`: Contains environments for analyzing high energy astrophysics data, including `heasoft`, `ciao` (for Chandra), `fermi`, `sas` (for XMM-Newton).


For each image, there are tags that keep track of the image versions:

- `stable`: the latest stable version
- `develop`: the latest develop version
- Named versions (e.g. `26.0202`). Previous stable versions. See the [image release page](https://github.com/nasa-fornax/fornax-images/releases) for details.

If you are familiar with docker, you can pull the image using the following example and start using it.

```sh
docker pull ghcr.io/nasa-fornax/fornax-images/fornax-main:stable
```

The following examples show how you can use the images in different contexts. We will define some variables to be used in subsequent steps. You can change these based on what image and tag you are using:

```sh
image="fornax-main"
tag="stable"

declare -a docker_options=()
docker_options+=(
    --user root -e NB_UID=$(id -u) -e NB_GID=$(id -g)
    -e CHOWN_HOME=yes -e CHOWN_HOME_OPTS='-R' -e NOTEBOOK_ARGS='--NotebookApp.token=""'
    -v $(pwd):/opt/workspace:rw
    -w /opt/workspace
    ghcr.io/nasa-fornax/fornax-images/${image}:${tag}
)
```


## Running JupyterLab
The most basic use of the images is run JupyterLab inside them and replicate what you get in the Fornax Console.

Running the following will create a container and starts jupyterlab inside it.
You can then access it by pointing your browser to: `http://localhost:8888`

```sh
docker run --rm -p 8888:8888 ${docker_options[@]}
```

With this setup, the notebooks are available in `~/fornax-notebooks`, and the `/opt/workspace/` folder is writable to the user.
Any files under `/opt/worksapce` are available outside the container in the folder in which the container started.
You can for example copy the notebooks to that folder and run them.


## Running the Container in Intractive Mode
In interactive mode, you start an interactive shell inside the container and proceed to running command line tools.

```sh
docker run --rm -it ${docker_options[@]} bash
```

## Running the Container in Batch Mode
In bath mode, you can pass the command you want to run directly to `docker run`.
It is recommended to call commands inside bash so the environment variables are setup correctly.

```sh
docker run --rm ${docker_options[@]} bash -c "ls /opt/envs/lock"
```
This will first print some initialization messages and then calls the passed commands and exits.


As a more useful example, we will run one of the demo notebooks available in the image.
We use the `jupytext --execute` (see {ref}`working-with-markdown` for details).
In this case the python kernel is already defined in the file's meta section.
The kernel can also be specified by using the `-k kernel-name` option for `jupytext`

```sh
# first, we check the content
nb_dir=/home/jovyan/fornax-notebooks/fornax-demo-notebooks
docker run --rm ${docker_options[@]} bash -c "ls $nb_dir"

# then run the notebooks
docker run --rm ${docker_options[@]} bash -c "jupytext --execute $nb_dir/light_curves/light_curve_classifier.md"
```

## Running the Container in Detached Mode
In detached mode, the container is started and commands are sent to it separately.

```sh
# start the container called `fornax`
docker run -d --rm --name fornax ${docker_options[@]}

# send commands to the running container
docker exec fornax pwd
# gives: /opt/worksapce

# run the notebook similar to the above
docker exec fornax bash -c "jupytext --execute $nb_dir/light_curves/light_curve_classifier.md"

# stop the container
docker stop fornax
```
