# Cronjob

Namespaces and folders aren't created, you need to create them when necessary.


Create a manifest file named `ckad/temp/cj.yaml` for a CronJob `ping` in the `blog` namespace and name the cronjob `ping`.


`ping` cj should run only to one successful completion. 
when the cj runs it should ping a [website](kuberada.devtechops.dev) every minute with a busybox:1.28 container that shoud only start only on failure and should complete within 13 seconds.
Validate the successful ping.


<details>
<summary>Solution</summary>

```sh
k create ns blog
k create cj ping --image=busybox -n blog --schedule="* * * * *" --dry-run=client -o yaml --restart=Never -- /bin/sh -c 'ping -c 1 devtechops.dev' > cj.yaml

mkdir -p ckad/temp;mv cj.yaml ckad/temp
cd ckad/temp
vim cj.yaml
```

Edit the yaml file to look like this:

```sh
apiVersion: batch/v1
kind: CronJob
metadata:
  creationTimestamp: null
  name: ping
spec:
  jobTemplate:
    metadata:
      creationTimestamp: null
      name: ping
    spec:
      completions: 1
      activeDeadlineSeconds: 13
      template:
        metadata:
          creationTimestamp: null
        spec:
          containers:
          - command:
            - /bin/sh
            - -c
            - ping -c 1 devtechops.dev
            image: busybox:1.28
            name: ping
            resources: {}
          restartPolicy: OnFailure
  schedule: '* * * * *'
status: {}
```
Verify the succesfull ping

```sh
k apply -f cj.yaml
k get cj -n blog -w
k get po -n blog
k logs ping-<poname> -n blog
```

</details>








