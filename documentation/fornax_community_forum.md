---
short_title: Community Forum and Helpdesk
---

(intro-forum)=
# Fornax Community Forum and Helpdesk

{button}`discourse.fornax.sciencecloud.nasa.gov<https://discourse.fornax.sciencecloud.nasa.gov>`

The [Fornax Community Forum](https://discourse.fornax.sciencecloud.nasa.gov) fosters collaboration and knowledge-sharing among Fornax users.
Members can get help, engage in discussions, ask questions, share ideas, and collaborate on topics such as data integration, cloud computing tools, astrophysics analysis, and more.

```{figure} ../_static/community_forum.png
:alt: The Fornax Community Forum, with topics listed in the main area and categories including "Announcements", "Support", and "User Discussion" on the left.

Fornax Community Forum
```

There are three categories that serve different purposes:

-   **Announcements**: New features, changes, and other important information.
-   **Support**: The [](#helpdesk).
-   **User Discussion**: Hub for users to share insights and engage in collaborative discussions about using NASA Astrophysics mission data and Fornax resources for scientific research.

To post on the forum, you will need a [Fornax account](#get-an-account).
The forum can be read without an account.

(helpdesk)=
## Helpdesk

The Support category on the Fornax Community Forum serves as our Helpdesk:

{button}`discourse.fornax.sciencecloud.nasa.gov/c/support<https://discourse.fornax.sciencecloud.nasa.gov/c/support>`

Please start a new topic there to get support from Fornax staff, request a new feature, get approval to use the XLarge server, or report a bug.

```{tip}
You will need a [Fornax account](#get-an-account) to post on the forum.
If you are having trouble logging in to your account, you don't have an account, or you need to contact us privately, please email us at [fornax-helpdesk@lists.nasa.gov](mailto:fornax-helpdesk@lists.nasa.gov).
```

```{dropdown} Request the XLarge server
We require users to get approval before using the XLarge server to help ensure that the significant compute resources are not wasted.
To request approval, please open a Helpdesk topic and include the following information:

-   Estimated total runtime.
-   Brief description of your scientific use case.
-   Brief description of your code development and readiness for scaling up.
    -   For example: "I have parallelized my code and tested it on the Medium server type, and I believe it will make efficient use of the XLarge server."

Once approved, you may use the XLarge server within the parameters of your request.
You do not need additional approval to stop and restart your server as long as you remain within the original estimated runtime.

If you require additional time beyond your estimate, please notify us by posting a brief justification to your Helpdesk request.
If your analysis exceeds the estimated runtime, we may reach out to discuss potential termination.
```

```{dropdown} Submit an effective bug report
To help us quickly diagnose and resolve any issues you're experiencing, please provide as much of the following information as possible when submitting a bug report.

-   **Location within Fornax** where the issue occurred (for example, while running a notebook in JupyterLab and using the Dask extension)
-   **Actions you were performing** when the issue occurred
-   **Expected behavior** (what you anticipated would happen)
-   **Observed behavior** (what actually happened)
-   **Error messages, logs, tracebacks, or other relevant output** that were generated
-   **Date and time (with timezone)** when the issue occurred
-   **Web browser (name and version)** you are using to access the Fornax Science Console (e.g., Chrome 125.0.64422.142)
-   **Additional context** that might help (e.g., if you successfully completed the same task on a previous occasion, including the date and time)

Providing detailed information will help us resolve your issue more efficiently.
Thank you!
```
