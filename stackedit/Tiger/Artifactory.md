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

## Misc

* [Delete artifact](https://wiki.audaxhealth.com/x/ppLOAg)
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTg2MzIxNjIyLDcyNzIyNDUyMCw2MDUyNT
kzNDksNzg5NTM5NjM0LC0xOTk5NDU1MzQyLDE2NzM5NDI4Mjks
Mjg3MDc0ODQ1LC02MTMzMTczNDAsMTY2NDAyNzM0M119
-->