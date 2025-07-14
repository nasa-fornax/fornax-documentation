# Troubleshooting

## If my internet connection goes away or is intermittent - what happens to the running notebook?

If you have a running job and your internet is disrupted, the job should continue to run as long as the session does not expire (See [#jupyterlab-session-information](session information) section). You can connect to a running session using the same browser or different browser. You can even connect to the same session from different machines.


## How will my analysis be affected by memory limitations?
If your workload exceeds your server size, your server may be allowed to use additional resources temporarily. This can be convenient but should not be relied on. In particular, be aware that your job may be killed automatically and without warning if its RAM needs exceed the allotted memory. This behavior is not specific to Fornax or AWS, but users may encounter it more often on the science console due to the flexible machine sizing options. (Your laptop needs to have the max amount of memory that you will ever use while working on it. On the science console, you can choose a different server size every time you start it up – this is much more efficient, but also requires you to be more aware of how much CPU and RAM your tasks need.)

## Save your work!
The Science Console is currently intended for interactive use and will cull sessions which appear to be inactive. The team is working on tools to enable users to submit jobs to run asynchronously. For efficient resource usage, idle interactive sessions will be culled automatically. If you want to keep your session running for longer, you can use the Keep-alive feature in the Fornax menu.

how long is the period of inactivity that gets culled? 15 minutes.
