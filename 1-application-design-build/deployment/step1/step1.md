
Create a Deployment spec yaml for frontend in ns ckad01258 with 2 replicas exposing containerPort 80.

`kubectl create deployment frontend --image=nginx --replicas=2 -n ckad01258 --port=80 --dry-run=client -oyaml > frontend.yaml`

Open the deployment manifest file running

`cat frontend.yaml`

Verify that the app matches in the following 2 places:

- spec.selector.matchLabels
- spec.template.metadata

