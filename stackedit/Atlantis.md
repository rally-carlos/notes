# Production
* AWS Account: `rally-prod`
* Region: `us-east-1`
* EKS Cluster: `eks-ops-prod-1`
&nbsp;
* Tenant: `ops-prod-1`
* Web UI: https://atlantis.werally.com/

```
AWS_PROFILE=rally-prod AWS_DEFAULT_REGION=us-east-1 aws eks update-kubeconfig --name eks-ops-prod-1
ATLANTIS_POD=$(kubectl get pods --namespace=ops | grep -F atlantis | cut -d' ' -f1)
kubectl logs --namespace ops --follow ${ATLANTIS_POD}
kubectl exec --stdin --tty --namespace ops ${ATLANTIS_POD} -- bash
```

# Kyle's POC
* AWS Account: `rally-ops`
* IP: `54.242.6453`
* Web UI: http://54.242.64.53:4141/

```
Host atlantis-kyle
	HostName 54.242.64.53
	User ec2-user
	IdentityFile /Users/carlos.meza/.ssh/dev_nodes_ed25519
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MDQ5MzAwOTMsLTIwOTgxMDY1MTUsMT
c5NzI0MjIzNSw0MTYyNDE2MjFdfQ==
-->