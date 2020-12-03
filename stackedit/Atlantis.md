# Production
* AWS Account: `rally-prod`
* Region: `us-east-1`
* EKS Cluster: `eks-ops-prod-1`
&nbsp;
* Tenant: `ops-prod-1`
* Web UI: https://atlantis.werally.com/
&nbsp;
* [Deployment Build](https://ci.rally-dev.com/teams-cure/blue/organizations/cure/rally-docker-ops-atlantis/)
* [Deployment Build](https://ci.rally-dev.com/teams-cure/job/cure/job/rally-docker-ops-atlantis/)

```
AWS_PROFILE=rally-prod AWS_DEFAULT_REGION=us-east-1 aws eks update-kubeconfig --name eks-ops-prod-1
ATLANTIS_POD=$(kubectl get pods --namespace=ops | grep -F atlantis | cut -d' ' -f1)
kubectl logs --namespace ops --follow ${ATLANTIS_POD}
kubectl exec --stdin --tty --namespace ops ${ATLANTIS_POD} -- su - atlantis -s /bin/bash
```

## Run Terraform in container
To deal w/ secrets in Vault refer to `docker_entrypoint.sh` to see what other vars are required.
```
kubectl exec --stdin --tty --namespace ops ${ATLANTIS_POD} -- bash
gosu atlantis bash -c "\
  VAULT_TOKEN=$(cat $ILLUMINATI_VAULT_K8S_TOKEN_PATH) \
  VAULT_URL=$ILLUMINATI_VAULT_URL \
  AWS_ACCESS_KEY_ID=$(curl -s --header "X-Vault-Token: $(cat $ILLUMINATI_VAULT_K8S_TOKEN_PATH)" $ILLUMINATI_VAULT_URL/v1/secret/data/ops/atlantis/aws_access_key_id | jq '.data.data[]' | tr -d '"') \
  AWS_SECRET_ACCESS_KEY=$(curl -s --header "X-Vault-Token: $(cat $ILLUMINATI_VAULT_K8S_TOKEN_PATH)" $ILLUMINATI_VAULT_URL/v1/secret/data/ops/atlantis/aws_secret_access_key | jq '.data.data[]' | tr -d '"') \
  bash"
cd ~/.atlantis/repos/AudaxHealthInc/<repo>/<pull-request>/<workspace>
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
eyJoaXN0b3J5IjpbLTEyNDU3MjM0NzEsLTIxMDI5NzY3OTcsLT
k0NTUyODYyNSwtMTYwNDkzMDA5MywtMjA5ODEwNjUxNSwxNzk3
MjQyMjM1LDQxNjI0MTYyMV19
-->