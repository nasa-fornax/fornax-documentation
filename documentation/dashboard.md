(forsc-dashboard)=
# Dashboard

The purpose of the Fornax Science Console Dashboard is to provide users the status of their compute and storage resource consumption.
The image below shows a screenshot of the Dashboard.

```{figure} ../_static/forsc_dashboard.png
:alt: The Fornax Science Platform Dashboard listing spending categorized by resource.

The Fornax Science Console Dashboard
```

-   **Total Spend** tracks the total number of dollars spent on {term}`egress <egress>`, storage, and compute so far this calendar year.
-   **Credits Remaining** tracks the total number of dollars left to be spent on any combination of egress, storage, and compute for the rest of this calendar year.
-   **Egress Spend** tracks total number of dollars spent on egress so far this calendar year.
    Egress refers to data that is transferred out of a cloud provider's system to somewhere else, like your local computer or another cloud.
-   **Total Egress** tracks the volume of data in GB egressed so far this calendar year.
-   **Storage Spend** tracks the total number of dollars spent on storage so far this calendar year.
-   **Storage Allocated** tracks the volume of storage reserved for your use in GiB so far this calendar year.
    If you have already used some of this storage, this will be different than the amount of *available* storage.
-   **Compute Spend** tracks the total number of dollars spent on compute so far this calendar year.
-   **Running Jupyter Servers** this is 0 if you are not running a compute environment, or 1 if you are.
    Note there is a delay in this value of about 1-2 minutes, so if you shut down your server, you will have to wait a bit before this number shows the update.

To see changes, you can reload the Dashboard at any time without affecting a {term}`server <server>` you may have running, but note that there may be a delay of up to a few minutes before recent usage is reflected.
