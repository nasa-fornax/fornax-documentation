# Troubleshooting

## If my internet connection goes away or is intermittent - what happens to the running notebook?
Restart kernel will solve some problems, especially if the cells were run 
out of order

Under the kernel menu: restart kernel...

Restart Fornax - will solve version issues if packages with different 
versions were loaded since these won’t persist across Fornax restarts

## How will my analysis be affected by memory limitations?
If your workload exceeds your server size, your server may be allowed to use 
additional resources temporarily. This can be convenient but should not be 
relied on. In particular, be aware that your job may be killed automatically 
and without warning if its RAM needs exceed the allotted memory. This behavior 
is not specific to Fornax or AWS, but users may encounter it more often on the 
science console due to the flexible machine sizing options. (Your laptop needs 
to have the max amount of memory that you will ever use while working on it. 
On the science console, you can choose a different server size every time you 
start it up – this is much more efficient, but also requires you to be more 
aware of how much CPU and RAM your tasks need.)

## Save your work!
The Science Console is primarily intended for interactive use and will cull 
sessions which appear to be inactive. Your session will not be culled if there 
is CPU activity. Keeping your computer from sleeping will also keep your 
session active; regardless of any interactivity. If you want a notebook or 
script to run longer than about 15 minutes and there is no processing in your 
notebook or you will not be interacting with the Console, running top during 
that time can help keep the session active.

## How long is the period of inactivity that gets culled? 
15 minutes.
