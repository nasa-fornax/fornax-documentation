---
short_title: Markdown Notebooks
---

(working-with-markdown)=
# Working with Notebooks in Markdown Format

A {term}`Jupyter Notebook` is a feature-rich application supporting data exploration and code development.
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
