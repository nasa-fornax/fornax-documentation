(quick-start)=
# Quick Start Guide

The Fornax Science Console is a robust tool for scientific research.
This quick-start guide introduces the basic steps to begin using it effectively.

## 1. Get an Account

To create a Fornax Science Console and Community Forum account, go to https://signup.fornax.sciencecloud.nasa.gov and follow the instructions that ask you for some information as follows:

-   A valid email address and mobile phone number that will be used for verification only.
    Note that if you use an email address that is not from a whitelisted domain (currently nasa.gov), there will be a delay while a human verifies that you are not likely to be a malicious user.
-   We also ask for your institute affiliation and career level for demographics.
-   Most importantly, we ask for a brief description of the science analysis you would like to use Fornax for.
    Again, this is merely for verification that the proposed usage of Fornax is appropriate.

Once your account is created, you will receive an email with further instructions on how to log in and find information and help, etc.

## 2. Log In

Once you receive your credentials, log into the Fornax Science Console at:
🔗 [https://science-console.fornax.sciencecloud.nasa.gov/](https://science-console.fornax.sciencecloud.nasa.gov/)

## 3. Select JupyterHub

After logging in, you will see a Resource Dashboard.
You can learn more about it in the {ref}`forsc-dashboard` section.
For now, go to the left-hand menu and choose JupyterHub under Compute.

## 4. Select a Server Type and Environment

You’ll be prompted to select the following:

-   **Server Type**: Size of the compute instance.
    Please choose **Small** until you have carefully read the {ref}`intro-best-practices` section.
-   **Environment**: Container image providing your base environment.
    The **Default Astrophysics** environment is recommended for most use cases.
    {ref}`base-environment` describes the options in more detail.

## 5. Launch JupyterLab

Click **Start** to launch the base environment.
It is normal for JupyterLab to take a couple of minutes to start.
At this point, the server you have chosen will begin accruing cost, even though you have not started any computations.
Since you have chosen the **Small** server, this cost will be low.

## 6. Open a New Notebook

In JupyterLab, you will see a main menu at the top, your persistent home directory on the left, and a work area on the right.
The Launcher tab is open in the work area by default.
You can click the **+** to the right of the tab name just under the main menu to open a new Launcher tab at any time.

-   In the Launcher tab, select **python3** under the **Notebook** section.
    A new notebook tab will open in the work area.
-   When you are ready to save your work to your Fornax home directory, click on the **Save** icon in the notebook tab.
-   To download your notebook to your local machine, click on your notebook in your home directory on the left side of the screen.
    Then go to the main menu and select **File** → **Download**.

## 7. Shut Down Your Server

Since running sessions continuously use the allocated credit, it is strongly recommended that you should terminate your session when you are done using it for awhile.
Be sure to save your work to your persistent home directory before doing this.
Anything not saved will be lost, including both files and software customizations.
See {ref}`install-additional-software` for information about how to install software that persists between sessions.

The session can be stopped by clicking **Stop My Server** from the JupyterHub control panel page, which is accessed from from:

- **Fornax** → **Shutdown Server**, or
- **File** → **Hub Control Panel**, both in the top menu.

Note that clicking **Logout** from the File menu (or in the upper right corner of the JupyterHub control page) does not stop the session or shut down the server.
It only logs you out of JupyterHub but leaves the Fornax session running (and the $$ accruing).

```{warning}
JupyterLab sessions that appear to be inactive or reach the time limit will be automatically shut down.
See {ref}`jupyterlab-session-information` for details, including the Keep-Alive option.
```
