# Create a persistent volume

Create a hostPath PersistentVolume named `sg-pv`, allocate `1Gi`, with access mode `ReadWriteOnce`. Volume should be in the `/mnt/shared` directory. Specify a storage class name `sg-rocking`.

Check the pv status, and verify that it is available.

Create a pv claim named `i-need` that requests at least 256Mi` and specifies an access mode of ReadWriteOnce. Check the pvc status, it should be bound.


Create a pod named `user` with the image nginx, label it app=frontend. This pod should use the pvc `i-need` as a volume. Mount the volume to `/usr/share/nginx/html` inside the pod. Create a `test.txt` file in this directory.


Recreate the pod and verify that you can see the `test.txt` file.




<details>
<summary>Solution </summary>

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


</details>