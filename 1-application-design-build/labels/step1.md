- Run the following command to create a pod named "app" with the specified labels:

`kubectl run app --image=nginx --labels=env=test,tier=app,team=dev --restart=Never`

- Run the following command to list pods that have the label tier=backend:

`kubectl get po -l tier=backend --show-labels`





