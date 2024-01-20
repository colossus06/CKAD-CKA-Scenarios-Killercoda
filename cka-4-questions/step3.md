# Persistent volume

Create a deployment named "webapp" with two replicas, using the image "nginx:latest". Configure the deployment to use a PersistentVolumeClaim named "webapp-pvc" as the persistent storage for the containers. The PVC should request a minimum of 1Gi of storage and use the "standard" StorageClass. Mount the persistent volume to the container at "/usr/share/nginx/html".
Values:
Deployment name: webapp
Image: nginx:latest
Replicas: 2
PersistentVolumeClaim name: webapp-pvc
Requested storage: 1Gi
StorageClass: standard
Mount path: /usr/share/nginx/html
