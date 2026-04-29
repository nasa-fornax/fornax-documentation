----
short_title: Tutorial Notebooks
----

(fornax-tutorials)=
# Fornax Python Tutorial Notebooks

The Fornax Initiative has established a [github repository of Python Tutorial Notebooks](https://github.com/nasa-fornax/fornax-demo-notebooks) that demonstrate how to access and analyze NASA Astrophysics datasets.
The notebooks in this repository are tested frequently and automatically to guarantee that they successfully run using the software environments provided within the Fornax Science Console.

Once tested, these notebooks are rendered into HTML for easy reading: [Fornax Tutorial Notebooks](https://nasa-fornax.github.io/fornax-demo-notebooks/).
They can be downloaded in `.md` (Markdown) format and run in any JupyterLab environment with the same user experience as traditional `.ipynb` notebooks.
See {ref}`working-with-markdown`.

(notebooks-in-fornax)=
## Notebooks in the Console

When you log in to the console, the tutorial notebooks are available in your home directory at `~/fornax-notebooks`.
The packages required to run the notebooks are already installed.

The notebooks directory is read-only, and its content is reset with every session.
If you want to make modifications to the notebooks, make your own copy or clone and modify it.
For example, to copy the Light Curve Collector notebook (along with the directories it depends on) to your home directory, do:

```sh
notebook_dir=~/fornax-notebooks/fornax-demo-notebooks/light_curves
# Use --no-preserve=mode so the notebook will be editable.
cp --no-preserve=mode $notebook_dir/light_curve_collector.md ~/.
# Also copy the directories it depends on.
cp -r --no-preserve=mode $notebook_dir/code_src $notebook_dir/output ~/.
```

Or, to clone the entire fornax-demo-notebooks repo:

```sh
git clone https://github.com/nasa-fornax/fornax-demo-notebooks.git
```

## Other NASA Astrophysics Notebooks

The [Fornax Tutorial Notebooks](https://nasa-fornax.github.io/fornax-demo-notebooks/) showcase science that can be carried out by combining data across the NASA Astrophysics Archives, and have been tested using the software environments offered in the Fornax Science Console.
Each of the NASA Astrophysics Archives also offer notebook tutorials more focused on single-archive use cases:

[MAST Science Tutorials](https://github.com/spacetelescope/tike_content/blob/main/markdown/science-examples.md)

[HEASARC SciServer Cookbooks](https://github.com/HEASARC/sciserver_cookbooks/blob/main/README.md)

[IRSA Python Tutorial Notebooks](https://caltech-ipac.github.io/irsa-tutorials/)
