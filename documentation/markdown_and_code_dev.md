# Working with Markdown and Developing Code

{ref}`Fornax Science Console: JupyterLab <jupyterlab>` describes the interface and tools available to support users in exploring data and developing code.
These include {term}`Jupyter Notebook`s, Linux {term}`command-line <terminal>` and {term}`Jupyter Console` terminals, file storage, JupyterLab extensions, and Python environments pre-installed with common astronomy software.
{ref}`compute-environments` describes how to install additional extensions and software.

(working-with-markdown)=
## Working with Markdown Notebooks

A Jupyter Notebook is a feature-rich application supporting data exploration and code development.
The notebook documents may be in either `.ipynb` or `.md` (Markdown) format.
The Fornax Tutorial Notebooks are in `.md` format following the standard practice of the Scientific Python ecosystem.
While many astronomers are familiar with the `.ipynb` format, we chose Markdown for its superior readability, ease of version control through diffing, simpler testing workflows, and smooth rendering to HTML.
To read more about the differences between `.md` and `.ipynb`, see the [MyST Markdown documentation](https://mystmd.org/guide/md-vs-ipynb).

### JupyterLab Markdown Dependencies

On the Fornax Science Console, all required dependencies for using Markdown in JupyterLab are pre-installed.
To use Markdown notebooks in JupyterLab outside of the Fornax Science Console, ensure the following tools are installed:

-   [`jupytext`](https://github.com/mwouts/jupytext) Python library
-   [`jupyterlab-myst`](https://github.com/executablebooks/jupyterlab-myst) JupyterLab extension

### Opening `.md` Files in JupyterLab

1.  Navigate to the `.md` file in the JupyterLab file browser.
2.  Right-click the file, select **Open With**, and choose **Notebook** or **Jupytext Notebook**.
3.  The Markdown file will open in an interactive notebook interface with cells and execution capabilities—just like a traditional `.ipynb` notebook.

### Converting `.md` Markdown Notebooks to `.py` Scripts

It is easy to convert from `.md` Markdown to a `.py` script, if that fits better into your workflow:

1.  Open a terminal.
2.  Install **jupytext** if necessary (it is pre-installed in the Fornax Science Console):

    ```pip install jupytext```

3.  Navigate to the directory containing your `.md` notebook file.
4.  Run the following command to convert it to a Python script:

    ```jupytext --to script <your_notebook_file>.md```

## Moving Between Compute Platforms

If you prefer to develop your code outside the Fornax Science Console, you can push your changes to a publicly available repository (e.g., GitHub) and synchronize that to your home directory on the Fornax Science Console.

### Using Git

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
