(intro-forsc)=
# Fornax Science Console Capabilities

The Fornax Science Console is a NASA-funded web-based application that provides access to a limited amount of cloud computing via {term}`JupyterLab`, which offers access to {term}`Jupyter Notebook`s, {term}`Jupyter Console`, and the {term}`terminal`.
Users will have access to data sets curated by repositories around the world, and can upload moderate amounts of private data.
To get started quickly, users can choose from a variety of example notebooks as well as pre-installed software environments.
These can be modified to suit user needs.

The Fornax Science Console supports many astronomical use cases, but users will find it especially beneficial for analyses:

-   on large cloud-hosted data sets that would be cumbersome to download;
-   that require complicated software pre-installed on the platform; or
-   that are parallelizable and require a large number of {term}`CPU`s.

## Registration and Cost

Users must register for an account to login to the system.
See [Quick Start: Get an Account](#get-an-account) for instructions.
New users will receive the following two documents, also viewable on this site for reference:

-   [User Resource Allotments and Costs](change-controlled-documents/user-resource-allotments-and-costs)
-   [User Agreement](change-controlled-documents/user-agreement)

There is no monetary cost to users.
NASA provides each user with an allotment of credits to spend on compute, storage, and/or egress.
See the new user documents above for details.

(intro-best-practices)=
## Fornax Resources and Best Practices

Cloud compute is billed to NASA and charged to the user's credits on an hourly basis for a running {term}`Server Session`—even when resources are idle.
Storage may be charged based on either the amount allotted or the amount used, depending on the type of storage.
To ensure efficient allocation of these limited resources across the community, users are encouraged to use the least amount of compute and storage necessary to accomplish their tasks.

### Computing Resources

The Fornax Science Console offers four server sizes with different compute capacities ({term}`RAM` and {term}`CPU`), listed below.
See {ref}`server-and-env-options` for additional usage guidance and [User Resource Allotments and Costs](change-controlled-documents/user-resource-allotments-and-costs) for costs.

Small (8 GB RAM, 2 CPU)
:   Ideal for exploratory or prototype work.
    This is the best place to start developing.

Medium (16 GB RAM, 4 CPU)
:   This is a good server size to test workflows.

Large (64 GB RAM, 16 CPU)
:   Suited for tested and parallelized workflows.

XLarge (512 GB RAM, 128 CPU)
:   Reserved for the most demanding, highly parallel jobs.
    Available by approval only and intended for limited, efficient use.

### Storage Resources

The Fornax Science Console offers the following storage options:

Private storage
:   Users have 2 types of private storage: Home Directory and AWS S3.
    Please see [User Resource Allotments and Costs](change-controlled-documents/user-resource-allotments-and-costs) for details.

    S3 usage guidance:
    S3 storage is accessible via standard AWS tools ([Command line interface](https://docs.aws.amazon.com/cli/latest/reference/s3/) or [`boto3`](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html) in Python) and is also mounted in the Console as a file system at `~/s3-storage` for convenience.
    However, S3 doesn't always behave like a traditional file system.
    In particular, it is inefficient for repeated access of many small files.
    It's best suited for infrequently accessed data, such as archival storage of pipeline outputs (catalogs, spectra, images, etc.) needed for reproducibility.
    When storing multiple files, consider using `tar` to collect them into a single file before saving to `~/s3-storage`.

Shared storage
:   Shared storage is currently available via the `~/shared-storage` folder (also accessed from `/shared-storage`).
    This is a shared efs drive that is writable by all users.
    To use, create a folder with your name that stores your files.
    This folder can be used for both sharing and also for short term (~weeks) storage of large files that you want to persist between sessions, but do not fit in the home directory.
    Note, however, that the content of this folder is visible and writable by all users.

    This shared storage is only temporary while a more permanent solution is being developed.

Bring your own storage
:   You are also welcome to "bring your own storage".
    This can be anything that you can access using an API.
    Examples include Google Drive, Box, AWS S3 and Google Cloud Storage buckets, etc.

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
    They are grouped by image name and available in the [container images release page](https://github.com/nasa-fornax/fornax-images/releases) (expand the "Assets" section).
