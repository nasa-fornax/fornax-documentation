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

(intro-best-practices)=
## Compute and Storage

Fornax offers cloud-based computing with multiple server and data storage options, and an allotment of credits to spend as they wish.

Credits
:   NASA provides each user with an allotment of credits to spend however they like on compute, storage, and {term}`egress`.
    There is no monetary cost to users.
    The credit allotments renew annually.
    Users can also request more credits before the renewal date by contacting the [](#helpdesk).

Compute Power
:   Multiple server sizes are available, offering different amounts of CPU and RAM.
    These range from a fraction of a typical laptop up to an order of magnitude or more above a typical laptop.
    Users can choose a different server size each time they start one up.
    See [](#server-and-env-options) for details about server sizes and guidelines for use.

Storage Solutions
:   Both traditional filesystem and cloud-based storage (AWS S3) options are available for users to store data.
    There is no strict upper limit on the volume of data users can keep.
    (In practice, this is restricted by how users choose to spend their credits.)
    See [](#data-storage) for details about the types of storage available and guidelines for use.

### How far will my credits take me?

While Fornax is not a super-computing center, substantial results can be achieved when using resources wisely.
To help users get a sense of how much they can do with their credit allotments and the server and storage options available to them, [User Resource Allotments and Costs](change-controlled-documents/user-resource-allotments-and-costs) details the number of credits charged for each activity and outlines typical usage scenarios.

As is typical with cloud computing, the unit charges are small but accrue constantly while a resource is in use, and the charges stop as soon as resource usage stops.

Compute Charges
:   A Fornax user's credits are charged for the entire time they have a server running, irrespective of whether notebooks or code are being executed.
    Compute charges stop as soon as the server is stopped.
    Charges accrue at an hourly rate that depends on the chosen server size.
    Larger servers have a higher rate, but can also complete large workloads much faster than smaller servers when the code is parallelized and makes full and efficient use of the larger CPU and RAM.

Storage Charges
:   Charges begin accruing for a given chunk of data when it is saved to the filesystem or bucket, and stop when it is deleted.
    Storage is charged by the hour at a rate that depends on the volume of data stored and the chosen storage solution.
    Filesystem storage has a higher rate than S3 but performs better for frequently accessed data.

### Community Sustainability

A key difference from typical cloud computing is that Fornax users spend free credits, courtesy of NASA.
To help ensure that NASA can continue to provide these services to the community for a long time to come, we ask users to remain aware of their activity and data storage on Fornax and to spend their free credits wisely.

## Software

Fornax has a wide variety of [pre-installed software](#preinstalled-software), including:

-   Common Python libraries, such as NumPy, SciPy, Scikit-Learn, Matplotlib, Bokeh, Seaborn, Pandas, and Dask.
-   Python libraries used in astronomy, such as Astropy, Astroquery, LSDB, and Firefly client.
-   Non-Python libraries commonly used in astronomy, such as The Tractor, HEASoft, Chandra CIAO, Fermitools, and XMM-Newton SAS.
-   AWS tools, such as the Command Line Interface and S3Fs.

Users can also install other Python and non-Python software of their choosing.
