# Frequently Asked Questions (FAQ)

## Can I run high-performance computing (HPC) workflows?

Although the Fornax Science Console isn't a traditional HPC system, it provides many similar features and benefits.
By selecting a very large [server size](#server-and-env-options), users can run highly parallelized workflows on a single node and achieve performance that often eliminates the need for a multi-node HPC system.
In addition to the substantial compute power for data *processing*, the high network bandwidth enables massively parallel *access* to [cloud-hosted data](#cloud-hosted-data).
Fornax also provides built-in TB-scale temporary and long-term [storage options](#data-storage), giving users several choices for reading and writing large datasets.

Users have access to the {term}`command line <Terminal>` where they can [install software](#install-additional-software) and launch jobs from scripts.

Unlike typical HPC systems, Fornax does not have a job scheduler.
We do plan to add support for batch or asynchronous job submission in a future release.

Be aware that server sessions can be automatically terminated under certain circumstances.
See [](#jupyterlab-session-information) for details.

## What are the pre-installed directories and files used for?

You can store files and data in the directories `~/` (home directory), `~/s3-storage`, `~/shared-storage`, and `/scratch`.
See [](#data-storage) for details.

The directory `~/fornax-notebooks` contains demo and tutorial notebooks.
It is read-only.
See [](#notebooks-in-fornax) for details.

`$ENV_DIR` and `$USER_ENV_DIR` are aliases to directories where {term}`environments <Environment>` are stored.
`$LOCK_DIR` is an alias to a directory where you'll find lists of the software installed in the built-in environments.
See [](#compute-environments) for details.

The file `~/.profile` is an initialization script that runs when a {term}`terminal <Terminal>` session starts.
See [](#terminal-initialization) for details.

## What is the difference between saving and downloading a file?

"Saving" a file will place it in a location in your Fornax storage.
To save a file, click on your notebook in your directory on the left side of the screen.
Then go to the main menu and select `File → Save`.
There are a few save options.
Alternatively you can click the image of the disk under the tab on an open file.

"Downloading" a file will move a copy to your local machine.
To download a file, click on your notebook in your directory on the left side of the screen.
Then go to the main menu and select `File → Download`.
You can also right click on the file name and select `Download`.

## Can I use Fornax for exoplanet research?

Yes! Fornax is well-suited for many exoplanet workflows, especially computationally intensive tasks that parallelize well.
Atmospheric retrievals are a prime example: tools like petitRADTRANS (pRT) require running thousands of forward models to sample parameter space, which maps naturally onto Fornax's scalable cloud compute.
[Exoplanet Retrieval Quickstart](https://github.com/nasa-fornax/fornax-howtos/blob/main/tutorials/exoplanet_retrievals/quickstart.md) is a tutorial for setting up and running a pRT retrieval on Fornax.
Similarly, tasks like injection-recovery tests, transit timing analyses across large light curve sets, and population-level modeling all benefit from the ability to spin up many parallel workers.

Fornax is also co-located with NASA archive data on the cloud, making it easy to pull large datasets without the bottleneck of downloading to a local machine.
Cloud-hosted NASA mission data are readily accessible at high bandwidth directly from the Fornax Science Console.

## If my Internet connection goes away or is intermittent, what happens to the running notebook?

If you have a running job and your Internet is disrupted, the job should continue to run as long as the {term}`session<Server Session>` does not expire (See {ref}`jupyterlab-session-information`).
You can connect to a running session using the same browser or different browser.
You can even connect to the same session from different machines.

## I was logged out while having a running job. What happens to it?

Being logged-in and having a running job or server are independent.
An active {term}`Server Session` is running in the cloud regardless of whether you logged in or not (See {ref}`jupyterlab-session-information`).
To **access** that active {term}`Server Session` (to stop it or modify it),
you need to be {term}`logged in<Login Session>`.
So your running job will not be affected.

## Why is my server unavailable or unreachable?

If you see a pop-up dialog like the one below, it means that your {term}`server session <Server Session>` was automatically terminated.

```{figure} ../_static/forsc_server_unavailable.png
:alt: A pop-up dialog titled "Server unavailable or unreachable" with the message that the server is not running and buttons to Restart or Dismiss.

The "Server unavailable or unreachable" dialog appears when your session has been automatically terminated.
```

This can happen for two reasons: your server was either culled or it ran out of memory.
There's no way to determine which was the cause after the server shuts down, but you can make an educated guess based on what you had running.

Sessions may be culled if they appear inactive or reach the maximum time limit.
[](#jupyterlab-session-information) explains the details.
Sessions executing code might still appear inactive if, for example, they wait a long time to receive data.
The Keep-Alive feature can be used to prevent culling due to inactivity.
However, keep in mind that your credits are charged while your server is running, even if it is inactive.

A session will run out of memory if the code or task(s) being executed require more {term}`RAM` than the server has.
Starting a new session with a larger [server size](#server-and-env-options) will increase the available RAM.

## How long is the period of inactivity before a session gets culled?

It is set to 15 minutes, but it can take a few minutes longer for the culling service to be triggered.

## Why is my HTML page blank when opened inside JupyterLab with Safari?

This is a known issue in displaying HTML files inside JupyterLab in Safari.
The workaround is to right-click (double finger tap) on the HTML file and select 'Open in New Browser Tab'.
The file should open correctly in a new browser tab.

(using-git)=
## How do I use Git from Fornax?

If you want to clone notebooks or code from a Git repository (repo) into the Fornax Science Console, you can use either the `git` command-line tool from the {term}`terminal <terminal>` or the {ref}`Git extension <git-extension>` UI.

Basic instructions to get started using Git on Fornax are below, including details that are specific to Fornax.
For a detailed tutorial about how to use Git in any context, see https://git-scm.com/docs/gittutorial.

### One-time setup

To set up Git on Fornax for the first time, configure your username and email by opening a terminal and running the following commands:

```bash
# Use the username and email associated with your Git account (not your Fornax account).
git config --global user.name "username"
git config --global user.email "your.email@example.com"
```

To be able to *read* (or clone) a *private* repo, or to *write* to *any* repo, you will need to use credentials.
You can either use your username and password or an access token, both of which you would set up through your Git provider (for example, GitHub).

:::{hint} For GitHub access, we recommend using a personal access token.

To set up GitHub access, it is highly recommended that you create a personal access token.
For details, please follow the [GitHub documentation](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token).
Then, to clone a repo use the syntax `git clone https://{your-token}@github.com/{repo-owner}/{repo-name}`.
:::

You can reduce the number of times you need to enter your credentials by configuring `git` to cache them.
In a terminal on Fornax, execute the following command:

```bash
# Tell git to cache your credentials for all repos.
# To do this for a single repo instead, cd into the repo directory and remove '--global' before running the command.
git config --global credential.helper cache
```

### Clone a repository

After setting up your credentials (if necessary; see above), you can clone a repo using a command similar to one of the following.

**Option 1**: Clone without passing credentials.
(You will be asked to provide them later if/when doing something that requires them.)

```bash
git clone https://github.com/{repo-owner}/{repo-name}
```

**Option 2**: Pass your personal access token while cloning.

```bash
git clone https://{your-token}@github.com/{repo-owner}/{repo-name}
```

:::{warning} Warning: SSH is not supported
You will need to use HTTPS to authenticate with Git on the Fornax Science Console.
In practice, this means you must clone the repo using a URL that starts with `https://`.
Addresses that start with `git@` use an SSH connection, which will not work because SSH is disabled on the Fornax system.
:::
