(server-and-env-options)=
# Server and Environment Options

Once you have logged in to the Fornax Science Console and clicked "JupyterHub" to start a server (see {ref}`quick-start`), you will be asked to specify a **Server Type** and a base **Environment**, as shown in the screenshot below.

```{figure} ../_static/forsc_jupyterlab_servers.png
:alt: JupyterLab server options menu as deployed in the Fornax Science Console

JupyterLab Server options on the Fornax Science Console.
```

## Server Type

The Fornax Science Console offers four server types: **Small**, **Medium**, **Large**, and **XLarge**.
Basic specifications for each are described in the {ref}`intro-best-practices` section.

Compute resources on Fornax are cloud-based and funded by NASA.
While the platform is designed for high performance, these resources are limited.
Being mindful of usage helps ensure that the platform remains sustainable and accessible to the broader astrophysics community.
Please follow these guidelines:

**Start small:** Begin by testing your workflow on the smallest server that meets your needs.
Limit initial runs in scope (e.g., fewer sources, shorter iterations, smaller datasets).
Scale up to a larger server or full analysis only after verifying that your code runs successfully at a smaller scale.

**Shut down when done**:
Having an active compute instance—even if you're not currently running code—still consumes resources and counts against your allocation.
Simply closing your browser window does not stop the server.
To properly shut it down, go to File → Hub Control Panel and click “Stop My Server.”

**Approval required for XLarge instance:**
To use the XLarge compute instance, please open a request by starting a new topic in the Fornax Community Forum [Support/Compute](https://discourse.fornax.sciencecloud.nasa.gov/c/support/compute) category with a brief description of your scientific use case and an estimated total runtime.
You do not need approval for stopping and restarting your instance as long as you remain within the original estimated runtime.
However, if you require additional time beyond your estimate, please notify us by posting a brief justification to your topic.
If your analysis exceeds the estimated runtime, we may reach out to discuss potential termination.

(base-environment)=
## Base Environment

The Fornax Science Console offers a number of software {term}`environments <environment>` to choose from.
They are currently grouped into two base environments.
You can select a base environment by choosing one of the following container images from the "Environment" dropdown in the screenshot above:

(base-environment-default)=
### **Default Astrophysics**
- The base Fornax container will be sufficient for many use cases, and provides a pre-installed set of commonly used astronomy tools. This includes the Python environments (managed with _uv_; see {ref}`compute-environments`) required to run the demonstration notebooks.

- This image is referred to as **Default Astrophysics** - *please note that there is currently also a `Dev Astrophysics' environment option, and we do not recommend its use unless suggested by the support team.*

When a default astrophysics Fornax instance has been launched, the existing software environments can be activated by following the instructions provided in - {ref}`compute-environments-select-python`.

(base-environment-hea)=
### **High-Energy Astrophysics**
- The second base environment contains pre-installed versions of software required for the analysis of high-energy (X-ray, Gamma-ray, etc.) observations.

- This image is referred to as **High-Energy Astrophysics** - *please note that there is currently also a `Dev High-Energy Astrophysics' environment option, and we do not recommend its use unless suggested by the support team.*

- Fornax-hea currently includes HEASoft, CIAO, and FermiPy environments; XMM-SAS support is under active development, and plans also exist to include an eROSITA-eSASS install.

Once launched, access to Fornax-hea software environments is provided through _micromamba_ (essentially a light-weight replacement for _conda_) environments - you can list available environments with:

```bash 
micromamba env list
```

Once you know the name of an environment you want to activate (e.g., *ciao*), you can activate it with:

```bash 
micromamba activate ciao
``` 
Though many pieces of high-energy astrophysics software are not installable through conda/micromamba, the micromamba environments are set up such that, once activated, the software will be activated and usable through the command-line-interface. 

Jupyter Notebooks launched with a high-energy micromamba environment kernel will also initialize the software, allowing (for instance) HEASoft tools to be called in Jupyter cells by prepending '!' to the command. 

---
 
See {ref}`compute-environments` for more information about the specific software environments that are pre-installed in each container image and how to customize your environment after your server starts up.
