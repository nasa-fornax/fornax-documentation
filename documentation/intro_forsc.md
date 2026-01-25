(intro-forsc)=
# Fornax Science Console Capabilities

The Fornax Science Console is a NASA-funded web-based application that provides access to cloud computing via {term}`JupyterLab`, which offers access to {term}`Jupyter Notebook`s, {term}`Jupyter Console`, and the {term}`terminal`.
Users will have access to data sets curated by repositories around the world, and can upload moderate amounts of private data.
To get started quickly, users can choose from a variety of example notebooks as well as pre-installed software environments.
These can be modified to suit user needs.

The Fornax Science Console supports many astronomical use cases, but users will find it especially beneficial for analyses:

-   on large cloud-hosted data sets that would be cumbersome to download;
-   that require complicated software which is pre-installed on the platform; or
-   that are parallelizable and require a large number of {term}`CPU`s.

## Registration and Cost

NASA provides each user with an allotment of credits to spend on compute, storage, and/or egress.
There is no monetary cost to users.

To register, follow the instructions at [](#get-an-account).
After completing the process, you will receive the following documents:

-   [User Resource Allotments and Costs](change-controlled-documents/user-resource-allotments-and-costs)
-   [User Agreement](change-controlled-documents/user-agreement)

(intro-best-practices)=
## Fornax Resources and Best Practices

Cloud compute is billed to NASA and charged to the user's credits on an hourly basis for a running {term}`Server Session`—even when resources are idle.
Storage may be charged based on either the amount allotted or the amount used, depending on the type of storage.
To ensure efficient allocation of these limited resources across the community, users are encouraged to use the least amount of compute and storage necessary to accomplish their tasks.

### Computing Resources

The Fornax Science Console offers four server sizes with different compute capacities ({term}`RAM` and {term}`CPU`).
See {ref}`server-and-env-options` for additional usage guidance and [User Resource Allotments and Costs](change-controlled-documents/user-resource-allotments-and-costs) for costs.

### Storage Resources

The Fornax Science Console offers both private and shared storage options.
See [](#data-storage) for more information.

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
