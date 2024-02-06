# Persistenting Volumes

Create a hostPath PersistentVolume named `sg-pv`, allocate `1Gi`, with access mode `ReadWriteOnce`. Volume should be in the `/mnt/shared` directory. Specify a storage class name `sg-rocking`.

Check the pv status, and verify that it is available.

Create a pv claim named `i-need` that requests at least 256Mi` and specifies an access mode of ReadWriteOnce. Check the pvc status, it should be bound.


Create a pod named `user` with the image nginx, label it app=frontend. This pod should use the pvc `i-need` as a volume. Mount the volume to `/usr/share/nginx/html` inside the pod. Create a `test.txt` file in this directory.


Recreate the pod and verify that you can see the `test.txt` file.




<details>
<summary>Solution </summary>

## Create the PV

```sh
vim sg-pv.yaml
```

```sh
apiVersion: v1
kind: PersistentVolume
metadata:
 name: sg-pv
spec:
  capacity:
    storage: 1Gi
  accessModes:
  - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  storageClassName: sg-rocking
  hostPath:
    path: /mnt/shared
```


```sh
k apply -f sg-pv.yaml
```

## Create the PVC

```sh
vim i-need.yaml
```

```sh
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
 name: i-need
spec:
 accessModes:
 - ReadWriteOnce
 resources:
  requests:
  storage: 256Mi
 storageClassName: sg-rocking
```

```sh
kubectl apply -f i-need.yaml
```

## Create the pod

```sh
k run user --image=nginx -l=app=frontend --dry-run=client --restart=Never -oyaml > user.yaml
```

```sh
apiVersion: v1
kind: Pod
metadata:
 name: user
 labels:
 app: frontend
spec:
  containers:
  - name: nginx-container
    image: nginx
    volumeMounts:
    - name: user-volume
      mountPath: /usr/share/nginx/html
  volumes:
  - name: user-volume
    persistentVolumeClaim:
      claimName: i-need
```

```sh
k apply -f user-pod.yaml
```
## Get a shell into the container

```sh
k exec -it user -- touch /usr/share/nginx/html/test.txt
```

## Recreate the pod an display the file

```sh
k delete -f user.yaml
k apply -f user.yaml
k exec user -- sh -c "cd /usr/share/nginx/;ls -la"
```

</details>