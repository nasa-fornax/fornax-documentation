(server-and-env-options)=
# Server Options

The Fornax Science Console offers four server types: **Small**, **Medium**, **Large**, and **XLarge**.
They differ in the amount of {term}`CPU` and {term}`RAM` they provide.
Their basic specifications and intended use are described below.

## Server Types

Small (8 GB RAM, 2 CPU)
:   Ideal for exploratory or prototype work.
    This is the best place to start developing.

Medium (16 GB RAM, 4 CPU)
:   This is a good server size to test workflows.

Large (64 GB RAM, 16 CPU)
:   Suited for tested and parallelized workflows.

XLarge (512 GB RAM, 128 CPU)
:   Reserved for the most demanding, highly parallel jobs.
    Available by approval only and intended for limited, efficient use.

## Starting a Server

You can choose a different server size each time you start one up.
When you [start a server session](#start-server-session), you will see a **Server Options** page similar to the screenshot below where you can choose a **Server Type**.

```{figure} ../_static/forsc_jupyterlab_servers.png
:alt: JupyterLab server options menu as deployed in the Fornax Science Console

Server Options page on the Fornax Science Console.
```

## Guidelines for Use

Compute resources on Fornax are cloud-based and funded by NASA.
While the platform is designed for high performance, please use the resources wisely to help ensure that NASA can continue to provide these free services to the broader astrophysics community.

### Start small

Begin by testing your workflow on the smallest server that meets your needs.
Limit initial runs in scope (e.g., fewer sources, shorter iterations, smaller datasets).
Scale up to a larger server or full analysis only after verifying that your code runs successfully at smaller scale.

### Shut down when done

You are continuously charged credits for a running server regardless of whether you're actively using it.
So it's important to [stop your server](#stop-server-session) when you're done using it for a period of time (for example, overnight).

```{warning}
Simply closing your browser window or logging out of your Fornax account does not stop your server.
```

To properly stop your server, go to `File → Hub Control Panel` and then click **Stop My Server**.

### Get approval to use the XLarge server

We require users to get approval before using the XLarge server to help ensure that the significant compute resources are not wasted.
To request approval, please contact the [](#helpdesk).
