# Server and Environment Options

Once you have logged in to the Fornax Science Console, you will be asked to specify a **Server Type** and an **Environment**, as shown in the screenshot below.

```{figure} ../_static/fsc_jupyterlab_servers.png
:alt: JupyterLab server options menu as deployed in the Fornax Science Console

JupyterLab Server options on FSC.
```

### Server Type

The Fornax Science Console offers three server types: **Standard**, **Large**, and **XLarge**. Basic specifications for each are described in [Fornax Resources and Best Practices](https://hackmd.io/ejQ6DQWUTiuim5LZjXclSw#Fornax-Resources-and-Best-Practices).

Compute resources on Fornax are cloud-based and funded by NASA. While the platform is designed for high performance, these resources are limited. Being mindful of usage helps ensure that the platform remains sustainable and accessible to the broader astrophysics community. Please follow these guidelines:

**Start small:** Begin by testing your workflow on the smallest server that meets your needs. Limit initial runs in scope (e.g., fewer sources, shorter iterations, smaller datasets). Scale up to a larger server or full analysis only after verifying that your code runs successfully at smaller scale.

**Shut down when done**:
Having an active compute instance—even if you're not currently running code—still consumes resources and counts against your allocation. Simply closing your browser window does not stop the server. To properly shut it down, go to File → Hub Control Panel and click “Stop My Server.”

**Approval required for XLarge instance:**
To use the XLarge compute instance, please contact the Help Desk with a brief description of your scientific use case and an estimated total runtime. You do not need approval for stopping and restarting your instance as long as you remain within the original estimated runtime. However, if you require additional time beyond your estimate, please notify the Help Desk with a brief justification. If your analysis exceeds the estimated runtime, we may reach out to discuss potential termination.


### Environment

The Fornax Science Console offers a number of software environments to choose from. These include:


- **Astrophysics Default Image** *(recommended for most users)* This software environment 
- **High Energy Astrophysics Image**
