
# Multi-container pod design

You are going to create a multi-container Pod named `logger` from `multi.yaml` file for real-time logging purposes. Create the manifest file, name the main application container `main`, and use image `nginx`. 

Name the second container `helper` using another `nginx` image. Specify the commands 'less +F /var/log/nginx/access'.

Create an `emptydir` volume named and mount it to `/var/log/nginx` for main and helper containers and name this shared volume `shared-vol`.

<details>
<summary>Solution</summary>

## Create manifest imperatively

```sh
k run logger --image=nginx --dry-run=client -oyaml --restart=Never -- /bin/sh -c "less +F /var/log/nginx/access" > logger.yaml
```

Add the emptydir volume `shared-vol` and mount on the pods

```sh
apiVersion: v1
kind: Pod
metadata:
  name: multi
  namespace: log
spec:
  containers:
  - image: nginx
    name: main
    volumeMounts:
    - name: shared-vol
      mountPath: /var/log/nginx
  - args:
    - /bin/sh
    - -c
    - less +F /var/log/nginx/access
    name: helper
    image: nginx
    volumeMounts:
    - name: shared-vol
      mountPath: /var/log/nginx
  volumes:
  - name: shared-vol
    emptyDir: {}
```

```sh
k apply -f logger.yaml
```


<details>