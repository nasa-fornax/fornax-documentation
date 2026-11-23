(forsc-dashboard)=
# Dashboard

The Fornax Science Console Dashboard is the page you see when you [log in](#forsc-login).
From here you can start a server, manage your storage space and collaboration groups, get help, and track usage of the free credits that NASA provides.

```{figure} ../_static/forsc_dashboard.png
:alt: The Fornax Science Console Dashboard, with a left menu of links and central tiles showing credits spent and remaining, categorized by resource.

The Fornax Science Console Dashboard
```

## Left Menu

Compute
:   Start a [server](#start-server-session).

Storage
:   Manage your [temporary scratch space](#temporary-storage).

Collaboration
:   Create and manage [collaboration groups](#collaboration-storage) and their shared storage.

Documentation, Helpdesk, and Community
:   Open the documentation, contact the [](#helpdesk), or visit the [Forum](#intro-forum) and the [`nasa-fornax` GitHub organization](https://github.com/nasa-fornax).

## Credits and Usage

NASA gives each user a yearly allotment of credits to spend on compute, storage, and egress.
The Dashboard tiles track how many credits you've spent on each resource and how many remain.

Total Spend
:   Total Spend tracks the total number of credits spent on {term}`egress <egress>`, storage, and compute so far this year.

Credits Remaining
:   Credits Remaining tracks the total number of credits left to be spent on any combination of egress, storage, and compute for the rest of this year.

Egress Spend
:   Egress Spend tracks total number of credits spent on egress so far this year.
    Egress refers to data that is transferred out of a cloud provider's system to somewhere else, like your local computer or another cloud.

Total Egress
:   Total Egress tracks the total volume of data (in GB) that has been transferred out of the platform so far this year.

Storage Spend
:   Storage Spend tracks the total number of credits spent on storage so far this year.
    This includes all private [storage](#data-storage) areas, such as the home directory and S3 (based on amount used), and temporary storage (based on amount allocated).

Storage in Use
:   Storage in Use tracks the volume of storage in GB that you are currently using, including your home directory, S3, and temporary storage spaces.

Compute Spend
:   Compute Spend tracks the total number of credits spent on {term}`server sessions<Server Session>` so far this year.

Running Jupyter Servers
:   Running Jupyter Servers shows 0 if you don't have a server running, or 1 if you do.
    Note there is a delay in this value of about 1-2 minutes, so if you shut down your server, you will have to wait a bit before this number shows the update.

To see changes, you can reload the Dashboard at any time without affecting a {term}`server <server>` you may have running, but note that there may be a delay of up to a few minutes before recent usage is reflected.
