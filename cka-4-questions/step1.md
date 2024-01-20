## StorageClass

Create a StorageClass named "fast-storage" with the provisioner set to "k8s.io/aws-ebs" and a throughput of 100 MB/s. Create a PersistentVolumeClaim (PVC) named "app-data-claim" that uses this StorageClass. Ensure the PVC requests 10Gi of storage. Provide the YAML manifest for both the StorageClass and the PVC.