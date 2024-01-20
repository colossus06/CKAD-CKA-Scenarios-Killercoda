# Storage Class

Create a PersistentVolumeClaim named "data-pvc" that requests a minimum of 2Gi of storage and uses the "standard" StorageClass. Mount the persistent volume to a container at "/data" in a Pod named "data-pod" using the PVC.
Values:
PersistentVolumeClaim name: data-pvc
Requested storage: 2Gi
StorageClass: standard
Mount path: /data
Pod name: data-pod
