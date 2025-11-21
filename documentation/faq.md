# Frequently Asked Questions (FAQ)

## If my internet connection goes away or is intermittent - what happens to the running notebook?

If you have a running job and your internet is disrupted, the job should continue to run as long as the session does not expire (See {ref}`jupyterlab-session-information`).
You can connect to a running session using the same browser or different browser.
You can even connect to the same session from different machines.

## How will my analysis be affected by CPU and memory limitations?

If your workload exceeds your server size, your server may be allowed to use additional resources temporarily.
This can be convenient but should not be relied on.
In particular, be aware that your job may be killed automatically and without warning if its {term}`RAM` needs exceed the allotted memory.
This behavior is not specific to Fornax or AWS but users may encounter it more often on the science console due to the flexible machine sizing options.
(Your laptop needs to have the max amount of {term}`memory <RAM>` that you will ever use while working on it.
On the science console, you can choose a different server size every time you start it up – this is much more efficient, but also requires you to be more aware of how much {term}`CPU` and {term}`RAM` your tasks need.)

## Why was my session stopped?

The Fornax Science Console is currently intended for interactive use and will cull sessions which appear to be inactive.
The team is working on tools to enable users to submit jobs to run asynchronously.
For efficient resource usage, idle interactive sessions will be culled automatically.
If you want to keep your session running for longer, you can use the Keep-alive feature in the Fornax menu.
See the {ref}`jupyterlab-session-information` section for details.

how long is the period of inactivity that gets culled?
It is set to 15 minutes, but it can take a few minutes longer for culling service to be triggered.

## I am getting an error when cloning a github repo with git@github.com

Cloning a repo of the form `git@github.com/...` uses SSH connection, which is disabled on the Fornax system.
You can still clone repos using HTTPS. See {ref}`using-git` for more details.
