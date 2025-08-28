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

-   **Small** (4 GB {term}`RAM`, 2 {term}`CPU`s): Ideal for exploratory or prototype work.
    With no usage time constraints, this is the best place to start developing.
-   **Medium** (16GB {term}`RAM`, 4 {term}`CPU`s): This is a good server size to test workflows.
-   **Large** (64 GB {term}`RAM`, 16 {term}`CPU`s): Suited for tested and parallelized workflows.
    Users may access the large compute environment for several hundred hours per year while staying within cloud cost guidelines.
-   **XLarge** (512 GB {term}`RAM`, 128 {term}`CPU`s): Reserved for the most demanding, highly parallel jobs.
    Available by approval only and intended for limited, efficient use of roughly 100 hours in a given year.

See {ref}`server-and-env-options` for more information.

### Storage Resources

The Fornax Science Console offers two types of storage:

-   **Persistent home directory:** Each user has a 10 GB home directory on the file system for storing important files that need to be saved long term.
-   **Extended temporary storage:** For project work lasting several months, users can request up to 5 TB of object storage on {term}`S3`, intended for data that doesn’t require fast file system access and won’t be stored permanently.

You are also welcome to "bring your own storage".
This may be anything that you can access using an API, such as an Amazon S3 or Google Cloud Storage bucket, Google Drive, Box, etc.
