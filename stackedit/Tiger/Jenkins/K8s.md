## Create configs
```bash
aws --profile rally-dev --region us-east-1 eks update-kubeconfig --role-arn arn:aws:iam::144137586169:role/k8s-ops-access --name eks-staging-cje-k8s --alias cje-staging

aws --profile rally-dev --region us-east-1 eks update-kubeconfig --role-arn arn:aws:iam::144137586169:role/k8s-ops-access --name eks-cje-k8s --alias cje-live

for E in live staging; do
  aws --profile rally-dev --region us-east-1 eks update-kubeconfig --role-arn arn:aws:iam::144137586169:role/k8s-ops-access --name "eks-${E#live}$([ \"${E}\" != 'live' ] && printf -- '-')cje-k8s" --alias "cje-${E}"
  
done
$([ ${E} != 'live' ] && printf -- '-')
kubectl config set-context "cje-${E}" --namespace cje
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM3NzY5MjY2NiwtMTg3ODkyNTEzNywxND
k2MzUyMzMwLDQ3MTc1MzE5OF19
-->