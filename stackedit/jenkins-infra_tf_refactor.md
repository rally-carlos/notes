
```bash
terraform plan -lock=false -no-color | tee tfplan.output.txt

terraform state pull | tee terraform.tfstate

for ITEM in $(grep -E '^ *- ' tfplan.output.txt | grep -v destroy | sed -e 's/^ *- //'); do \
  terraform state mv -lock=false -state=terraform.tfstate ${ITEM} module.cje.${ITEM} ; \
done

# !!!
# CHANGE TF S3 BACKEND KEY TO `terraform.tfstate`
# This will make it easy to swing back to previous state if nessacary.
# I assume the S3 bucket is versioned, but still.
# !!!

terraform init
terraform push -lock=false
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzU1ODg2NjAwLDczNTYyMjIzNCwtMTAxNT
I5Mzg0NiwtMTk4NzIzNDE3M119
-->