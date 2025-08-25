# Compute Environments

The Fornax Science Console offers several Software environments, they are currently grouped into two containers:

-   **Default Astrophysics** (recommended for most use cases) contains many common astronomy software, including those required to run the demo notebooks.
    This container image is referred to as **fornax-main**.
-   **High-Energy Astrophysics** contains high-energy software, which currently includes HEASoft.
    Plans exist to add CIAO, XMM-SAS and Fermitools.
    This container image is referred to as **fornax-hea**.

There are two ways to view the software pre-installed in the containers:

-   **Inside the Console**:
    The list of environment files (`*.yml` for conda and `requirements-*.txt` for uv) of all the installed environments can be found in the folder `$LOCK_DIR`.
    Each environment in the container has a corresponding file there.
    For instance:
    -   *requirements-python3.txt*: is the pip requirement file for the `python3` environment.
    -   *base-lock.yml*: is the conda environment file for the base conda environment.
    -   *heasoft-lock.yml*: is the conda environment file for the heasoft conda environment.
      etc.
-   **Outside the Console**: The same environment files are also available for every release of the container images on github.
    They are grouped by image name and available in the [container images release page](https://github.com/nasa-fornax/fornax-images/releases).

## Environment Selection

`python3` is the default python environment.
It has general astronomy and plotting software.

Each of the Fornax demo notebooks has its own environment with a name of the form `py-{notebook-name}` (e.g. `py-light_curve_collector` and `py-multiband_photometry`).
Each environment has the packages required to run the notebook  pre-installed.
When opening the notebook, the corresponding kernel should automatically start.
You can also select it from the drop down kernel menu at the top-right of an open notebook.

To activate a specific environment from the terminal, run: `source $ENV_DIR/{environment-name}/bin/activate`.

For example, to activate the `py-light_curve_classifier` environment, run:

```sh
source $ENV_DIR/py-light_curve_classifier/bin/activate
```

and the following to deactivate it.

```sh
deactivate
```

There are two types of environments, **uv**-based and **conda**-based:

-   **uv**-based:
    The **uv**-based environments use [uv](https://docs.astral.sh/uv/) to manage the packages.
    These environments contain `pip`-installable packages and are used in most cases.
    The default environment are installed under `$ENV_DIR`.
    The are activated as indicated above with `source $ENV_DIR/{env-name}/bin/activate`.
-   **conda**-based (using [micromamba](https://mamba.readthedocs.io/en/latest/user_guide/micromamba.html)):
    The `conda`-based environments are used when packages that are not `pip`-installable.
    Examples this include `heasoft` and `ciao` in the high-energy container image.
    These are activated with `micromamba activate {env-name}` and deactivated with `micrmamba deactivate`.
    These are installed under `$CONDA_DIR/envs`

## Installing Additional Software on the Fornax Science Console

To install additional software, there are two options:

1.  Add to a current environment:
    To add packages to a currently installed environment, you install them with `pip` (or the faster `uv pip`) after activating the relevant environment.
    -   Inside a notebook running the relevant environment, run `!uv pip install ...`, passing the extra packaged needed.
    -   In the terminal, after activating the environment run: `uv pip install ...`.

    **Note** that packages installed this way are added in the `$ENV_DIR` folder, and therefore are not saved for the next session.
    To ensure the packages are installed in you home directory, and therefore saved between session, add `--user` to the pip command.
    Note also, that if the container image is updated, packages installed with the `--user` option may not be compatible with the new image and package conflicts may arise.
    The solution is this case is to create your own environments that are independent of the container image (next bullet).

2.  Create a new environment:
    To create a new environment that persists between sessions, create a folder in you home directory where user environments will be installed.
    Say `mkdir ~/user-envs`.
    Then inside that folder run the following to create an environment:

    ```sh
    uv venv myenv --python=3.11
    source myenv/bin/activate
    # add numpy for example
    uv pip install "numpy<2"
    ```

    This will create a new environment with python version 3.11, activate it, and then install a "numpy<2".

    In order to use this new environment in a notebook, you'll need to install `ipykernel` inside the environment and then register it.

    ```sh
    uv pip install ipykernel
    python -m ipykernel install --name myenv --user
    ```

    The kernel should show up in the jupyterlab main launcher page and in the kernel selection dropdown menu inside a running notebook.

    **Note**: It is recommended that you remove user environments that are no longer needed, as they may deplete your home storage.

## Installing Extensions on the Fornax Science Console

There are two types Jupyerlab extensions.
Front-end (menus etc), and server extensions.
Most extensions include both components.
Instructions on how to find and install extensions can be found at [JupyterLab: Extensions](https://jupyterlab.readthedocs.io/en/stable/user/extensions.html).
The front-end extension can be installed after jupyterlab starts, and can show up if you refresh the page, as long they are installed in the environment running jupyterlab (/opt/jupyter/).
Note: Extensions that include a server-side component cannot be installed by individual users because they must be installed before JupyterLab starts.
In that case, please open a request in the [Fornax Community Forum](https://discourse.fornax.sciencecloud.nasa.gov/) "Support" category.

## Using Git

You must use HTTPS to authenticate with `git` on the Fornax Science Console.
SSH is not supported.
This means you will need to enter your username and password (or token) when interacting with a remote.
To reduce the number of times you need to enter them, you can configure `git` to cache them by opening a terminal and running the following command:

```sh
# Tell git to cache your credentials for all repos.
# To do this for a single repo instead, cd into the repo directory and remove '--global' before running the command.
git config --global credential.helper cache
```

For more information about using `git`, see https://git-scm.com/docs/gittutorial.
