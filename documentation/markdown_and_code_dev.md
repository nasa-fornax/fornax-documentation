# Working with Markdown and Developing Code

{ref}`Fornax Science Console: JupyterLab <jupyterlab>` describes the interface and tools available to support users in exploring data and developing code.
These include {term}`Jupyter Notebook`s, Linux {term}`command-line <terminal>` and {term}`Jupyter Console` terminals, file storage, JupyterLab extensions, and Python environments pre-installed with common astronomy software.
{ref}`compute-environments` describes how to install additional extensions and software.

(working-with-markdown)=
## Working with Markdown Notebooks

A Jupyter Notebook is a feature-rich application supporting data exploration and code development.
The notebook documents may be in either `.ipynb` or `.md` (Markdown) format.
The Fornax Tutorial Notebooks are in `.md` format (specifically in [MyST](https://mystmd.org/) Markdown flavor) following the standard practice of the Scientific Python ecosystem.
While many astronomers are familiar with the `.ipynb` format, we chose Markdown for its superior readability, ease of version control through diffing, simpler testing workflows, and smooth rendering to HTML.
To read more about the differences between `.md` and `.ipynb`, see the [MyST Markdown documentation](https://mystmd.org/guide/md-vs-ipynb).

### JupyterLab Markdown Dependencies

On the Fornax Science Console, all required dependencies for using Markdown in JupyterLab are pre-installed.

To use Markdown notebooks in JupyterLab outside of the Fornax Science Console, ensure the following tools are installed:

-   [`jupytext`](https://github.com/mwouts/jupytext) Python library
-   [`jupyterlab-myst`](https://github.com/executablebooks/jupyterlab-myst) JupyterLab extension

(open-md-in-jupyterlab)=
### Opening `.md` Files in JupyterLab

In the Fornax Science Console, you can simply double click on a `.md` file in the file browser.
It will open in an interactive notebook interface with cells and execution capabilities — just like a traditional `.ipynb` notebook.
If you need to save the notebook output, pair it with a `.ipynb` document before running it by selecting: `File → Jupytext → Pair Notebook with ipynb document`.

If you are not in the Fornax Science Console then the default viewer for `.md` files might be different.
In that case, right-click the file, select **Open With**, and choose **Notebook** or **Jupytext Notebook** to open it in the interactive notebook interface.

### Converting To and From `.md` Format

:::{tip}
It is not necessary to convert `.md` to `.ipynb` before using a notebook!
Notebooks in `.md` format can be used in JupyterLab just like a traditional notebook.
See {ref}`open-md-in-jupyterlab`.
:::

It is easy to convert notebooks between file formats like `.md`, `.ipynb`, and `.py` using [jupytext](https://jupytext.readthedocs.io/):

1.  Open a terminal.
2.  Install **jupytext** if necessary (it is pre-installed in the Fornax Science Console):

    ```pip install jupytext```

3.  Navigate to the directory containing your notebook file.
4.  Run a `jupytext` command to convert the format.
    Some examples are:
    -   Convert `.ipynb` to a MyST Markdown `.md` notebook:

        ```jupytext --to md:myst <your_notebook_file>.ipynb```

    -   Convert `.md` to a `.ipynb` notebook (*not necessary for use in JupyterLab*):

        ```jupytext --to ipynb <your_notebook_file>.md```

    -   Convert `.md` to a `.py` Python script:

        ```jupytext --to script <your_notebook_file>.md```

## Moving Between Compute Platforms

If you prefer to develop your code outside the Fornax Science Console, you can push your changes to a publicly available repository (e.g., GitHub) and synchronize that to your home directory on the Fornax Science Console.

### Using Git

You can use `git` from the command line or the UI provided by the {ref}`Git extension <git-extension>`.

To set up `git` for the first time, configure your name and email by opening a {term}`terminal <terminal>` and running the following commands:

```sh
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

You will need to use HTTPS to authenticate with `git` on the Fornax Science Console.
SSH is not supported.
This means you will need to enter your username and password (or token) when interacting with a remote.
To reduce the number of times you need to enter them, you can configure `git` to cache them:

```sh
# Tell git to cache your credentials for all repos.
# To do this for a single repo instead, cd into the repo directory and remove '--global' before running the command.
git config --global credential.helper cache
```

For more information about using `git`, see https://git-scm.com/docs/gittutorial.
