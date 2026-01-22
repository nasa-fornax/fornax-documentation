---
short_title: Forum and Helpdesk
---

(intro-forum)=
# Fornax Community Forum and Helpdesk

{button}`Fornax Community Forum<https://discourse.fornax.sciencecloud.nasa.gov>`

The Fornax Community Forum fosters collaboration and knowledge-sharing among Fornax users.
Members can get help, engage in discussions, ask questions, share ideas, and collaborate on topics such as data integration, cloud computing tools, astrophysics analysis, and more.

The forum has three categories that serve different purposes:

-   **Announcements**: Learn about new features, changes, and other important information.
-   **Helpdesk**: Ask questions, report issues, request features, and get help from the Fornax team and the wider community.
    See [](#helpdesk).
-   **User Discussion**: Share insights and engage in collaborative discussions about using NASA Astrophysics mission data and Fornax resources for scientific research.

To post on the forum, you will need a [Fornax account](#get-an-account).
The forum can be read without an account.

(helpdesk)=
## Helpdesk

To get support from Fornax staff, request a new feature, or report a bug, please open a topic in the Helpdesk category of the Community Forum:

{button}`Fornax Helpdesk<https://discourse.fornax.sciencecloud.nasa.gov/c/helpdesk>`

You will need a [Fornax account](#get-an-account) to post on the Helpdesk.
If you are having trouble logging in to your account, you don't have an account, or you need to contact us privately, please email us at [fornax-helpdesk@lists.nasa.gov](mailto:fornax-helpdesk@lists.nasa.gov).

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

```{dropdown} Submit an effective bug report for Fornax
To help us quickly diagnose and resolve any issues you're experiencing, please provide as much of the following information as possible when submitting a bug report.

-   **Location within Fornax** where the issue occurred.
    For example, "the JupyterLab Dask extension".
-   **Actions you were performing and any relevant context**.
    For example, "running a notebook in the `python3` kernel on a Medium server type".
    If the issue involves a notebook or code, include a link to the exact version you were using, if possible.
-   **Expected behavior**. What you anticipated would happen.
-   **Observed behavior**. What actually happened.
    Screenshots are helpful.
    If error messages, logs, or tracebacks were generated, include them in full.
-   **Steps-by-step instructions to reproduce the problem**.
-   **Date and time (with timezone)** when the issue occurred.
-   **Web browser (name and version)** you were using.
    For example, "Chrome 125.0.64422.142".
-   **Any additional information** that might help.
    For example, if you successfully completed the same task on a previous occasion, including the date and time.

Providing detailed information will help us resolve your issue more efficiently.
Thank you!
```
