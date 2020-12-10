
```bash
terraform plan -lock=false -no-color | tee tfplan.output.txt

terraform state pull | tee terraform.tfstate

for ITEM in $(grep -E '^ *- aws' tfplan.output.txt | sed -e 's/^ *- //'); do \
  printf "${ITEM}\n" ;\
  terraform state mv -lock=false -state=terraform.tfstate ${ITEM} module.cje.${ITEM} ;\
done
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMTA0ODEyNSwtMTk4NzIzNDE3M119
-->