# Artifactory

## Access
```bash
AWS_PROFILE='rally-prod' aws eks update-kubeconfig --name eks-artifactory-prod-1 --role-arn arn:aws:iam::738699725475:role/k8s-ops-access --region=us-east-1
kubectl config rename-context arn:aws:eks:us-east-1:738699725475:cluster/eks-artifactory-prod-1 artifactory-prod
```

## k9s
```
k9s --context artifactory-prod --namespace artifactory-h
```


## Misc

* [Delete artifact](https://wiki.audaxhealth.com/x/ppLOAg)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY3Mzk0MjgyOSwyODcwNzQ4NDUsLTYxMz
MxNzM0MCwxNjY0MDI3MzQzXX0=
-->