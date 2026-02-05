---
short_title: Data Access
---

# Data Access from within Fornax

The Fornax Science Console provides multiple data access pathways, including direct file uploads, direct cloud access, and support for IVOA-compliant application program interfaces (APIs).
Users can also leverage Python libraries such as Astroquery and PyVO to programmatically access major astrophysics archives, including the NASA Astrophysics Archives: HEASARC, IRSA, and MAST.

By combining these data access options with Fornax's integrated compute resources, users can streamline the process of retrieving, analyzing, and processing astrophysical data, making complex analyses more efficient and accessible.
To understand data storage options on the Fornax Science Console, see {ref}`intro-best-practices`.

## Direct File Uploads

The **JupyterLab File Browser** includes an **Upload File** option, allowing users to transfer data files from their local machine directly into your Fornax Science Console home directory.
Once uploaded, these files are available for immediate use in your analysis, whether in {term}`Jupyter Notebook`s or other tools.
You can organize and manage files through the File Browser interface, view directory structures, and access the uploaded datasets for use with Python libraries, APIs, or the compute resources provided by Fornax.
If you need the full path to a file or directory you have uploaded, find it using the File Browser interface, then right-click on it and select "Copy Path".

## Direct Cloud Access

You can access cloud-hosted data directly from your JupyterLab session without downloading it first, regardless of whether the data is hosted on AWS, Google Cloud, Azure, or any other cloud provider.
The NASA Astrophysics Mission Archives (HEASARC, IRSA, MAST) offer curated datasets through the [AWS Open Data program](https://registry.opendata.aws/) (ODR). The tutorials available on the platform gives examples of to access that data.

Accessing data that is stored in the same region as your compute (Fornax, in this case) will generally be more efficient, meaning lower latency.
The Fornax Science Console runs on AWS in the `us-east-1` region.
Most of NASA's ODR datasets are also in the `us-east-1` region (in {term}`Amazon S3<s3>` buckets).

You can use the Python tool [`s3fs`](https://s3fs.readthedocs.io/) to interact with S3 buckets as if they were part of your local filesystem—opening FITS files, CSVs, or other data products directly by specifying the {term}`S3` path.
For image data, `Astropy` can retrieve cutouts and handle astronomical images in memory, while `pyarrow` enables fast, efficient access to large catalog tables in Parquet format.
These tools allow seamless and scalable analysis of large datasets without manual downloads or local storage overhead.

Access to NASA's ODR datasets is completely free for users, regardless of your compute location or access method.
You are also welcome to access other datasets from the Fornax Science Console, but note that you will be responsible for any associated costs.
Those charges would come from the cloud provider of the given dataset, not from NASA or Fornax, and you would handle them directly with that cloud provider just as you would if you weren't using Fornax.
Typically, accessing data that is hosted in the same region as your compute is not subject to inter-region data transfer costs (also called "{term}`egress`"), but may be subject to other charges.
Please check with the relevant cloud provider.

## Mounted Data Buckets
Some archive-curated data buckets are mounted directly on the platform so they can be accessed like read-only files (can be used with system tools like `cp`, `ls` etc). 
These are available under `/archive-data/`. The currently mounted buckets includes:

- `nasa-heasarc`: High energy data holdings from the HEASARC.

## Application Program Interfaces

Application Programming Interfaces (APIs) are powerful tools that allow users to programmatically access and retrieve astronomical data from remote repositories or cloud-hosted archives.
In astrophysics, APIs are crucial for:

1.  **Efficient Data Search and Querying**
    With APIs, users can perform specific queries to retrieve data, such as images, catalogs, and spectra.
    By specifying parameters like wavelength, object type, or time range, users can quickly narrow down datasets from vast collections.
    This is especially helpful when working with large archives, as it minimizes the need for manual searches and enables automated retrieval of relevant data.
2.  **Integration with worldwide Astrophysics Archives**
    Many worldwide astrophysics archives use standardized IVOA-based APIs to provide access to astronomical data, allowing users to interact with multiple data repositories consistently, regardless of the underlying storage or architecture.
    For instance, you can query data from different NASA archives (such as HEASARC, IRSA, and MAST) through the same IVOA-compliant services.
    Explore astronomy data access services through the [NAVO Directory](https://vao.stsci.edu/directory/keywordsearch.aspx), which aggregates available IVOA services.
3.  **Broad API Support from General Repositories**
    In addition to specialized astronomical archives, more general data repositories such as **Box** and **Google Cloud Storage** also offer APIs for retrieving and managing data.
    These APIs provide flexibility for integrating astronomical datasets stored in these platforms with other data services or workflows.

## Python Libraries

You can use Python tools like [Astroquery](https://astroquery.readthedocs.io/en/latest/) and [PyVO](https://pyvo.readthedocs.io/en/latest/) to easily access a wide range of astrophysics datasets.
`Astroquery` provides a simple interface for retrieving data from major astronomical archives such as MAST, HEASARC, and IRSA, allowing you to query catalogs, images, and spectra programmatically.
Similarly, `PyVO` supports IVOA-compliant web services, enabling seamless access to data from various virtual observatories.
These libraries allow you to integrate data retrieval directly into your analysis scripts, making it easier to automate the process of working with large astronomical datasets without leaving your Python environment.
