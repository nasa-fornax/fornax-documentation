(compute-environments)=
# Compute Environments

The Fornax Science Console offers {ref}`Base Environments <base-environment>` which you can select by choosing a container image when starting your server.
Each base environment comes pre-installed with one or more specific software environments (or simply, "environments").
You can customize your environment by installing additional software and extensions.

## Environment Selection

`python3` is the default python environment.
It has general astronomy and plotting software.

Each of the Fornax demo notebooks has its own environment with a name of the form `py-{notebook-name}` (e.g. `py-light_curve_collector` and `py-multiband_photometry`).
Each environment has the packages required to run the notebook pre-installed.
When opening the notebook, the corresponding {term}`kernel` should automatically start.
You can also select it from the drop down {term}`kernel` menu at the top-right of an open notebook.

To activate a specific environment from the {term}`terminal <terminal>`, run: `source $ENV_DIR/{environment-name}/bin/activate`.

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
    -   Inside a {term}`notebook <Jupyter Notebook>` running the relevant environment, run `!uv pip install ...`, passing the extra packaged needed.
    -   In the {term}`terminal <terminal>`, after activating the environment run: `uv pip install ...`.

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

    In order to use this new environment in a {term}`notebook <Jupyter Notebook>`, you'll need to install `ipykernel` inside the environment and then register it.

    ```sh
    uv pip install ipykernel
    python -m ipykernel install --name myenv --user
    ```

    The {term}`kernel <Kernel>` should show up in the JupyterLab main launcher page and in the kernel selection dropdown menu inside a running notebook.

    **Note**: It is recommended that you remove user environments that are no longer needed, as they may deplete your home storage.

## Installing Extensions on the Fornax Science Console

There are two types Jupyerlab extensions.
Front-end (menus etc), and server extensions.
Most extensions include both components.
Instructions on how to find and install extensions can be found at [JupyterLab: Extensions](https://jupyterlab.readthedocs.io/en/stable/user/extensions.html).
The front-end extension can be installed after JupyterLab starts, and can show up if you refresh the page, as long they are installed in the environment running JupyterLab (/opt/jupyter/).
Note: Extensions that include a server-side component cannot be installed by individual users because they must be installed before JupyterLab starts.
In that case, please open a request in the [Fornax Community Forum](https://discourse.fornax.sciencecloud.nasa.gov/) "Support" category.
