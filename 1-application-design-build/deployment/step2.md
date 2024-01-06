Open the manifest file running

`vim frontend.yaml`

Add the following lines under containerPort:

```sh
env:
- name: VERSION
  value: '1.3.0'
```




