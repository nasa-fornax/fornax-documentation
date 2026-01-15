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

The XLarge server type provides a large amount of memory and CPU, and should be used wisely to avoid wasting resources.
We require users to submit a request to the [Helpdesk](#intro-forum) before using the XLarge server.
In your request, please include:

- Estimated total runtime.
- Brief description of your scientific use case.
- Brief description of your code development and readiness for scaling up.
    - For example: "I have parallelized my code and tested it on the Medium server type, and I believe it will make efficient use of the XLarge server."

Once approved, you may use the XLarge server within the parameters of your request.
You do not need additional approval to stop and restart your server as long as you remain within the original estimated runtime.

If you require additional time beyond your estimate, please notify us by posting a brief justification to your Helpdesk request.
If your analysis exceeds the estimated runtime, we may reach out to discuss potential termination.
