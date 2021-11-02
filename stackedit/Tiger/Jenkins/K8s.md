## Create configs
```bash
aws --profile rally-dev --region us-east-1 eks update-kubeconfig --role-arn arn:aws:iam::144137586169:role/k8s-ops-access --name eks-staging-cje-k8s --alias cje-staging

aws --profile rally-dev --region us-east-1 eks update-kubeconfig --role-arn arn:aws:iam::144137586169:role/k8s-ops-access --name eks-cje-k8s --alias cje-live

for E in slive; do
  role-arn arn:aws:iam::144137586169:role/k8s-ops-access --name "eks-${E//live}cje-k8s" --alias "cje-${E}"
  ${E//live}
  kubectl config set-context "cje-${E}" --namespace cje
done
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzAxNDM2ODk2LDQ3MTc1MzE5OF19
-->