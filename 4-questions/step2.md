# Create a cronjob

Namespaces and folders aren't created, you need to create them when necessary.


Create a manifest file for a CronJob named `ping` on `ckad/temp/cj.yaml` in the `blog` namespace.


It should run only to one successful completion. 
It should ping a [website](devtechops.dev) every minute with a busybox container and should complete within 13 seconds.
Validate the successful ping.








