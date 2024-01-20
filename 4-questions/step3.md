# Create a cronjob

Create a hostPath PersistentVolume named sg-pv, allocate 1Gi, with access mode should be ReadWriteOnce. Volume should be on the `/mnt/shared` directory. Specify a storage class name `sg-rocking`. check the pv status, it should be available.

Create a pv claim named `i-need` that requests at least or `256Mi`  and specifies an access mode of ReadWriteOnce. Check the pvc status, it should be bound.

Create a pod named `user` with the image nginx, label it app=frontend. This pod should use the pvc `i-need` as a volume. Mount the volume to `/usr/share/nginx/html` inside the pod. Create a test.txt file on this directory. Recreate the pod and verify that you can see the test.txt file.