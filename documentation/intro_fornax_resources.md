(intro-best-practices)=
# Fornax Resources and Best Practices

Cloud compute is billed to NASA on an hourly basis—even when resources are idle.
Likewise, storage is charged based on the amount allocated, not the amount actively used.
To ensure efficient allocation of these limited resources across the community, users are encouraged to use the least amount of compute and storage necessary to accomplish their tasks.

## Computing Resources

The Fornax Science Console offers four choices for compute capacity:

-   **Small** (4 GB RAM, 2 CPUs): Ideal for exploratory or prototype work.
    With no usage time constraints, this is the best place to start developing.
-   **Medium** (16GB RAM, 4CPUs): This is a good server size to test workflows.
-   **Large** (64 GB RAM, 16 CPUs): Suited for tested and parallelized workflows.
    Users may access the large compute environment for several hundred hours per year while staying within cloud cost guidelines.
-   **XLarge** (512 GB RAM, 128 CPUs): Reserved for the most demanding, highly parallel jobs.
    Available by approval only and intended for limited, efficient use of roughly 100 hours in a given year.

See {ref}`server-and-env-options` for more information.

## Storage Resources

Fornax also offers three types of storage:

-   **Persistent home directory:** Each user has a 10 GB home directory on the file system for storing important files that need to be saved long term.
-   **Short-term scratch space:** Users can request up to 5 TB of temporary space on the file system, available for up to two weeks, for files needed only during active work.
-   **Extended temporary storage:** For project work lasting several months, users can request up to 5 TB of object storage on S3, intended for data that doesn’t require fast file system access and won’t be stored permanently.

You are also welcome to "bring your own storage".
This may be anything that you can access using an API, such as an AWS S3 or Google Cloud Storage bucket, Google Drive, Box, etc.
