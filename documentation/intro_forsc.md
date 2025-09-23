(intro-forsc)=
# Fornax Science Console Capabilities

The Fornax Science Console is a NASA-funded web-based application that provides access to a limited amount of cloud computing via {term}`JupyterLab`, which offers access to {term}`Jupyter Notebook`s, {term}`Jupyter Console`, and the {term}`terminal`.
Users must register to login to the system, but usage is free.
Once logged in, users will have access to data sets curated by repositories around the world, and can upload moderate amounts of private data.
To get started quickly, users can choose from a variety of example notebooks as well as pre-installed software environments.
These can be modified to suit user needs.

The Fornax Science Console supports many astronomical use cases, but users will find it especially beneficial for analyses:

-   on large cloud-hosted data sets that would be cumbersome to download;
-   that require complicated software pre-installed on the platform; or
-   that are parallelizable and require a large number of {term}`CPU`s.

(intro-best-practices)=
## Fornax Resources and Best Practices

Cloud compute is billed to NASA on an hourly basis—even when resources are idle.
Likewise, storage is charged based on the amount allocated, not the amount actively used.
To ensure efficient allocation of these limited resources across the community, users are encouraged to use the least amount of compute and storage necessary to accomplish their tasks.

### Computing Resources

The Fornax Science Console offers four choices for compute capacity:

-   **Small** (8 GB {term}`RAM`, 2 {term}`CPU`s): Ideal for exploratory or prototype work.
    With no usage time constraints, this is the best place to start developing.
-   **Medium** (16 GB {term}`RAM`, 4 {term}`CPU`s): This is a good server size to test workflows.
-   **Large** (64 GB {term}`RAM`, 16 {term}`CPU`s): Suited for tested and parallelized workflows.
    Users may access the large compute environment for several hundred hours per year while staying within cloud cost guidelines.
-   **XLarge** (512 GB {term}`RAM`, 128 {term}`CPU`s): Reserved for the most demanding, highly parallel jobs.
    Available by approval only and intended for limited, efficient use of roughly 100 hours in a given year.

See {ref}`server-and-env-options` for more information.

### Storage Resources

The Fornax Science Console currently offers 3 types of storage:

-   **Persistent home directory:** Each user has a 20 GB private home directory on the file system for storing important files that need to be saved long term. Users can request a size increase incremently up to 100 GB by opening a Support topic in [Fornax Community forum](https://discourse.fornax.sciencecloud.nasa.gov/).
-   **Shared and temporary storage** While a detailed sharing solution is being implemented (planned for early 2026), sharing is currently available via the `~/shared-storage` folder (also accessed from `/shared-storage`). This is a shared efs drive that is writable by all users. To use, create a folder with your name that stores your files. This folder can be used for both sharing and also for short term (~weeks) storage of large files that you want to persist between sessions, but do not fit in the home directory. Note, however, that the content of this folder is visible and writable by all users.
-   **Long term s3 storage:** For long term storage (more than a few weeks), users have access to private AWS S3 storage under `~/s3-storage`. Although access is generally available using the AWS tools ([Command line interface](https://docs.aws.amazon.com/cli/latest/reference/s3/) or [`boto3`](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html) in python), it is conveniently mounted as a file system under `~/s3-storage`, but it does not always behave like a file system. It is especially not efficient for repeated access of many small files, so it is recommended for files that are not accessed often. Use it, for example, to store spectra or images that have been generated in a pipeline and you want them for reproducibility. Tar the files into a single file and store them in the `~/s3-storage` folder.

The Fornax team is actively working on a solution for both short term and sharing storage. The second option above is only temporary while the solution is being implemented. 

You are also welcome to "bring your own storage".
This may be anything that you can access using an API, such as an Amazon S3 or Google Cloud Storage bucket, Google Drive, Box, etc.

(view-preinstalled-software)=
## View Pre-installed Software

There are two ways to view the pre-installed environments and software that come with each container:

-   **Inside the Console**:
    The list of environment files (`*.yml` for conda and `requirements-*.txt` for pip) of all the installed environments can be found in the folder `$LOCK_DIR`.
    Each environment in the container has a corresponding file there.
    For instance:
    -   *requirements-python3.txt*: is the pip requirement file for the `python3` environment.
    -   *base-lock.yml*: is the conda environment file for the base conda environment.
    -   *heasoft-lock.yml*: is the conda environment file for the heasoft conda environment.
      etc.
-   **Outside the Console**: The same environment files are also available for every release of the container images on github.
    They are grouped by image name and available in the [container images release page](https://github.com/nasa-fornax/fornax-images/releases).
