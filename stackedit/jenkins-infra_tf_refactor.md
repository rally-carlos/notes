
```bash
terraform plan -lock=false -no-color | tee tfplan.output.txt

terraform state pull | tee terraform.state

for ITEM in $(grep -E '^ *- aws' tfplan.output.txt | sed -e 's/^ *- //'); do \
  printf "${ITEM}\n" ;\
  terraform state mv -lock=false -state=terraform.state ${ITEM} module.cje.${ITEM} ;\
done
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5ODcyMzQxNzNdfQ==
-->