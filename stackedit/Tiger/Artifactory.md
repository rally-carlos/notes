# Artifactory

## Access
```bash
AWS_PROFILE='rally-prod' aws eks update-kubeconfig --name eks-artifactory-prod-1 --role-arn arn:aws:iam::738699725475:role/k8s-ops-access --region=us-east-1
kubectl config rename-context arn:aws:eks:us-east-1:738699725475:cluster/eks-artifactory-prod-1 artifactory-prod
```

## k9s
```
k9s --context artifactory-prod --namespace artifactory-ha
```

## Datadog

- [Synthetics](https://app.datadoghq.com/synthetics/details/i5c-44j-qnn)
- [Artifactory-HA Deployment dashboard](https://app.datadoghq.com/dashboard/nrc-brf-43w)

## Misc

* [Delete artifact](https://wiki.audaxhealth.com/x/ppLOAg)
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjA1MjU5MzQ5LDc4OTUzOTYzNCwtMTk5OT
Q1NTM0MiwxNjczOTQyODI5LDI4NzA3NDg0NSwtNjEzMzE3MzQw
LDE2NjQwMjczNDNdfQ==
-->