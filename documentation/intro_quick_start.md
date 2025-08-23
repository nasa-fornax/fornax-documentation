# Quick Start Guide

The Fornax Science Console is a robust tool for scientific research.
This quick-start guide introduces the basic steps to begin using it effectively.

## 1. Get an Account
The Fornax Science Console is currently available by invitation only.
To get started, request access through your point of contact.

## 2. Log In
Once you receive your credentials, log into the Fornax Science Console at:
🔗 [https://science-console.fornax.sciencecloud.nasa.gov/](https://science-console.fornax.sciencecloud.nasa.gov/)

## 3. Select JupyterHub

After logging in, you will see a Resource Dashboard.
You can learn more about it in the {ref}`forsc_dashboard` section.
For now, go to the left-hand menu and choose JupyterHub under Compute.

## 4. Select a Server Type
You’ll be prompted to select the size of the compute instance.
Please choose **Small** until you have carefully read the {ref}`intro-best-practices` section.

## 5. Select a Software Environment

Choose the **Astrophysics Default Image**.

## 6. Launch JupyterLab

Click **Start** to launch the environment.
It is normal for Jupyterlab to take a couple of minutes to start.
At this point, the server you have chosen will begin accruing cost, even though you have not started any computations.
Since you have chosen the **Small** server, this cost will be low.

## 7. Open a New Notebook
In JupyterLab, you will see a main menu at the top, your persistent home directory on the left, and a work area on the right.

- Click the **blue +** just under the main menu.
This will open a new Launcher tab in the work area.

- In the Launcher tab, select **notebook** under the **Notebook** section.
A new notebook tab will open in the work area.

- When you are ready to save your work to your Fornax home directory, click on the **Save** icon in the notebook tab.

- To download your notebook to your local machine, click on your notebook in your home directory on the left side of the screen.
Then go to the main menu and select **File-->Download**.

## 8. Shut Down Your Server

When you are done with your work session, you must shut down the Standard server you launched.

In the main menu, choose **File**-->**Hub Control Panel**.

In the new JupyterHub browser tab that opens, click on the red button labeled **Stop My Server**.


## 9. Logout

Click **Logout** in the upper right corner of the new browser JupyterHub tab.
