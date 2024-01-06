
- Run the following command to generate a YAML manifest for the pod:

`kubectl run label --image=alpine --labels=env=test,tier=backend --restart=Never --dry-run=client -o yaml > label.yaml
`


- Run the following command to apply the generated YAML manifest and create the pod:

`kubectl apply -f label.yaml`


- Run the following command to get information about the created pod, including its assigned labels:

`kubectl get po --show-labels`

- Change the pod's label env=test to env=QA imperatively.

Override and list the labels:

```sh
k label po label env=QA --overwrite
k get po --show-labels
```

