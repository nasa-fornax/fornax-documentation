(server-and-env-options)=
# Server Options

When you [start a server session](#start-server-session), you will see a **Server Options** page similar to the screenshot below where you can choose a **Server Type**.

```{figure} ../_static/forsc_jupyterlab_servers.png
:alt: JupyterLab server options menu as deployed in the Fornax Science Console

Server Options page on the Fornax Science Console.
```

## Server Types

The Fornax Science Console offers four server types: **Small**, **Medium**, **Large**, and **XLarge**.
They differ in the amount of {term}`CPU` and {term}`RAM` they provide.
Basic specifications for each are described in the {ref}`intro-best-practices` section.

## Guidelines

Compute resources on Fornax are cloud-based and funded by NASA.
While the platform is designed for high performance, resources should be used wisely to avoid wasting them.
Being mindful of usage helps ensure that the platform remains sustainable and accessible to the broader astrophysics community.

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
