# Artifactory

## Access
```bash
aws --profile rally-prod --region us-east-1 eks update-kubeconfig --name eks-artifactory-prod-1 --role-arn arn:aws:iam::738699725475:role/k8s-ops-access
kubectl config rename-context arn:aws:eks:us-east-1:738699725475:cluster/eks-artifactory-prod-1 artifactory-prod
```

## k9s
```
k9s --context artifactory-prod --namespace artifactory-ha
```

## Datadog

- [Synthetics](https://app.datadoghq.com/synthetics/details/i5c-44j-qnn)
- [Artifactory-HA Deployment dashboard](https://app.datadoghq.com/dashboard/nrc-brf-43w)
- [Artifactory](https://app.datadoghq.com/dashboard/gju-pue-mxj) (RDS)

## Infrastructure As Code

- https://github.com/AudaxHealthInc/helm-artifactory-ha
- https://github.com/AudaxHealthInc/artifactory-ha-infra

## Misc

* [Delete artifact](https://wiki.audaxhealth.com/x/ppLOAg)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjQwNzI0ODAwLDU4NjMyMTYyMiw3MjcyMj
Q1MjAsNjA1MjU5MzQ5LDc4OTUzOTYzNCwtMTk5OTQ1NTM0Miwx
NjczOTQyODI5LDI4NzA3NDg0NSwtNjEzMzE3MzQwLDE2NjQwMj
czNDNdfQ==
-->