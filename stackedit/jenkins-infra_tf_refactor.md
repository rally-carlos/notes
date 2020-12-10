
```bash
terraform plan -lock=false -no-color | tee tfplan.output.txt

terraform state pull | tee terraform.tfstate

for ITEM in $(grep -E '^ *- ' tfplan.output.txt | grep -v destroy | sed -e 's/^ *- //'); do \
  terraform state mv -lock=false -state=terraform.tfstate ${ITEM} module.cje.${ITEM} ; \
done
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzM1NjIyMjM0LC0xMDE1MjkzODQ2LC0xOT
g3MjM0MTczXX0=
-->