# Python Notebook Tutorials

The Fornax Initiative has established a [github repository of Python Tutorial Notebooks](https://github.com/nasa-fornax/fornax-demo-notebooks/tree/main) that demonstrate how to access and analyze NASA Astrophysics datasets

The notebooks in this repository are tested frequently and automatically to guarantee that they successfully run using the software environments provided within the Fornax Science Console.

Once tested, these notebooks are [rendered into HTML](https://nasa-fornax.github.io/fornax-demo-notebooks/) for easy reading.

## Notebooks in the Console

When you login to the console, the notebooks available in `/opt/notebooks`, which is linked in the user's home directory as `~/fornax-notebook`.

As the notebooks are continuously developed, the clone in the console can lag behind.
To get the latest version of the notebooks, run the `update-notebooks.sh` script from the terminal.

Note that the notebooks directory is reset with every session.
if you want to make modifications to the notebooks, make you own copy or clone and modify it.

## Running Fornax Markdown Notebook Tutorials Outside the Fornax Science Console

Fornax Notebooks can be downloaded in `.md` (Markdown) format.
While many astronomers are familiar with the `.ipynb` format, Markdown was chosen for its superior readability, ease of version control through diffing, simpler testing workflows, and smooth rendering to HTML.
To read more about the differences between .md and .ipynb, we refer to the [MyST Markdown documentation](https://mystmd.org/guide/md-vs-ipynb).

### JupyterLab Markdown Dependencies

On the Fornax Science Console all required dependencies for using Makdown in JupyterLab are pre-installed.
To use Markdown notebooks in JupyterLab locally, ensure the following tools are installed:

- [`jupytext`](https://github.com/mwouts/jupytext) Python library
- [`jupyterlab-myst`](https://github.com/executablebooks/jupyterlab-myst) JupyterLab extension

### Opening `.md` Files in JupyterLab

1. Navigate to the `.md` file in the JupyterLab file browser.
2. Right-click the file, select **Open With**, and choose **Notebook** or **Jupytext Notebook**.
3. The Markdown file will open in an interactive notebook interface with cells and execution capabilities—just like a traditional `.ipynb` notebook.

## Converting `.md` Markdown Notebooks to `.py` Scripts

It is easy to convert from `.md` Markdown to a `.py` script, if that fits better into your workflow:

1. Open a terminal.
2. Install **jupytext** if necessary (it is pre-installed in the Fornax Science Console):

    ```pip install jupytext```

3. Navigate to the directory containing your `.md` notebook file.
4. Run the following command to convert it to a Python script:

   ```jupytext --to script <your_notebook_file>.md```

## Moving Between Compute Platforms

If you prefer to develop your code outside the Fornax Science Console, you can push your changes to a publicly available repository (e.g., GitHub) and synchronize that to your home directory on the Fornax Science Console.

## Other NASA Astrophysics Notebooks

The [Fornax Tutorial Notebooks](https://nasa-fornax.github.io/fornax-demo-notebooks/) showcase science that can be carried out by combining data across the NASA Astrophysics Archives, and have been tested using the software environments offered in the Fornax Science Console.
Each of the NASA Astrophysics Archives also offer notebook tutorials more focused on single-archive use cases:

[MAST Science Tutorials](https://github.com/spacetelescope/tike_content/blob/main/markdown/science-examples.md)

[HEASARC SciServer Cookbooks](https://github.com/HEASARC/sciserver_cookbooks/blob/main/README.md)

[IRSA Python Tutorial Notebooks](https://caltech-ipac.github.io/irsa-tutorials/)
