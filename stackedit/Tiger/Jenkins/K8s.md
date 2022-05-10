## Create configs

```bash
# Authenticate
rally-okta -w -e rally-dev
aws --profile=rally-dev  --region=us-east-1 eks update-kubeconfig --role-arn arn:aws:iam::144137586169:role/k8s-ops-access --name eks-staging-cje-k8s

# Set user friendly context name
kubectl config rename-context arn:aws:eks:us-east-1:144137586169:cluster/eks-staging-cje-k8s cje-stage

# Profit w/ k9s
k9s --context cje-stage --namespace cje
```


```bash
for E in live staging; do
  aws --profile rally-dev --region us-east-1 eks update-kubeconfig --role-arn arn:aws:iam::144137586169:role/k8s-ops-access --name "eks-${E#live}$([ "${E}" != 'live' ] && printf -- '-')cje-k8s" --alias "cje-${E}"
kubectl config set-context "cje-${E}" --namespace cje  
done
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3OTUwMDcwNCwtNjM2NTA1ODIxLDEzNz
c2OTI2NjYsLTE4Nzg5MjUxMzcsMTQ5NjM1MjMzMCw0NzE3NTMx
OThdfQ==
-->