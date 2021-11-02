## Create configs
```bash
for E in live staging; do
  aws --profile rally-dev --region us-east-1 eks update-kubeconfig --role-arn arn:aws:iam::144137586169:role/k8s-ops-access --name "eks-${E#live}$([ "${E}" != 'live' ] && printf -- '-')cje-k8s" --alias "cje-${E}"
kubectl config set-context "cje-${E}" --namespace cje  
done
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYzNjUwNTgyMSwxMzc3NjkyNjY2LC0xOD
c4OTI1MTM3LDE0OTYzNTIzMzAsNDcxNzUzMTk4XX0=
-->