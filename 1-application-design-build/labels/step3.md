- Run the following command to generate a YAML manifest for the pod and set annotations:

`kubectl run po annt --image=nginx --dry-run=client -o yaml > annt.yaml`

- Edit the generated annt.yaml file to include the annotations. Add the following lines under the metadata section:

```sh
metadata:
  annotations:
    author: "YourName"
    project: "Study Group"
```

- Run the following command to apply the edited YAML manifest and create the pod:

`kubectl apply -f annt.yaml`

- Describe the pod and display its current labels and annotations:

`kubectl describe pod annt`

- Remove the "project" annotation from the pod:

`kubectl annotate pod annt project-`

- Describe the pod and verify that the "project" annotation has been removed:

`kubectl describe pod annt`