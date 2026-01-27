(quick-start)=
# Quick Start Guide

The Fornax Science Console is a robust tool for scientific research.
This quick-start guide introduces the basic steps to begin using it effectively.

(get-an-account)=
## 1. Get an Account

To create a free Fornax Science Console and Community Forum account, complete the form at:

{button}`Sign up for a Fornax account<https://signup.fornax.sciencecloud.nasa.gov>`

The form will ask for the following:

-   Name, email address, and phone number.
    We use these for verification purposes only.
    Your email address will be used for ongoing Multi-Factor Authentication (MFA), so please choose one that receives messages quickly and reliably.
-   Institute affiliation and career stage, for demographics.
-   A brief description of the science analysis you would like to use Fornax for.
    We use this to verify that the proposed usage of Fornax is appropriate.
-   Desired username and password.

Once you submit the form, a verification link will be sent to your email address.
Click the link to verify your email address and then follow the instructions to verify your phone number.

A human will then review your request.
If approved, your account will be created and you will receive an email with further instructions and information, including the [User Agreement](change-controlled-documents/user-agreement) and [User Resource Allotments and Costs](change-controlled-documents/user-resource-allotments-and-costs).

```{note}
Email addresses from safelisted domains (currently, nasa.gov) are automatically approved.
All other requests require human review, which may take up to 2 US business days.
```

If you have trouble getting an account, please contact the [Helpdesk](#helpdesk).

(forsc-login)=
## 2. Log In

Once your [account](#get-an-account) has been created, log in to the Fornax Science Console:

{button}`Fornax Science Console<https://science-console.fornax.sciencecloud.nasa.gov/>`

After submitting your username and password, you will be prompted for a Multi-Factor Authentication (MFA) code.
The code will be automatically emailed to the address you used when registering your account.

Once logged in, you will see the [](#forsc-dashboard) with navigation links on the left and your account's resource and credit usage in the main area, similar to this:

```{figure} ../_static/forsc_dashboard.png
:alt: The Fornax Science Console Dashboard showing credit usage categorized by resource type and a navigation menu with links to JupyterHub, documentation, and help.

Fornax Science Console Dashboard
```

You can log out at any time by clicking the **Logout** button at the top right.
You will be automatically logged out after 24 hours.

(start-server-session)=
## 3. Start a Server Session

To start a {term}`compute session<Server Session>`, go to the left-hand menu on the [](#forsc-dashboard) and choose `Compute → JupyterHub`.
A new window will open and you will be prompted to choose a **Server Type**.
Please choose **Small** until you have carefully read [](#server-and-env-options).

```{figure} ../_static/forsc_jupyterlab_servers.png
:alt: JupyterLab server options menu, as deployed in the Fornax Science Console.
```

Click **Start** to launch your server.
It is normal for it to take a couple of minutes.
Once your server has started, you will see a JupyterLab interface similar to this:

```{figure} ../_static/forsc_jupyterlab.png
:alt: JupyterLab opening page with some Fornax customizations, as deployed in the Fornax Science Console.
```

At this point, the selected server will begin charging against your credit allotment, even though no computations have started yet.
Since you have chosen the **Small** server, the associated credit usage will be low.

```{warning}
Server sessions that appear to be inactive or reach the maximum time limit will be automatically shut down.
See {ref}`jupyterlab-session-information` for details, including the Keep-Alive option.
```

## 4. Open a New Notebook

In [](#jupyterlab), you will see a main menu at the top, your persistent home directory on the left, and a work area on the right.
The Launcher tab is open in the work area by default.
You can click the **+** to the right of the tab name just under the main menu to open a new Launcher tab at any time.

To start a new {term}`Jupyter Notebook`:

-   In the Launcher tab, select **python3** under the **Notebook** section.
    A new notebook tab will open in the work area.
-   When you are ready to save your work to your Fornax home directory, click on the **Save** icon in the notebook tab.
-   To download your notebook to your local machine, click on your notebook in your home directory on the left side of the screen.
    Then go to the main menu and select `File → Download`.

(stop-server-session)=
## 5. Shut Down Your Server

Since a running {term}`session <Server Session>` continuously uses your allocated credits, it is strongly recommended to terminate your session when you are done using it for awhile.
Be sure to save your work to your persistent home directory before doing this.
Anything not saved will be lost, including both files and software customizations.
See {ref}`install-additional-software` for information about how to install software that persists between sessions.

To stop your session:

- Navigate to the JupyterHub control panel page by clicking `Fornax → Shutdown Server` in the top menu bar (equivalently, click `File → Hub Control Panel`).
- On the control panel page, click **Stop My Server**.

```{warning}
Clicking **Logout** (either `File → Logout` or the button in the top right corner of the control panel) does not stop the session or shut down the server.
It logs you out of your Fornax account but leaves your server session running (and will continue using your credits).
```
