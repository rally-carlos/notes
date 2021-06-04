
```bash
terraform plan -lock=false -no-color | tee tfplan.output.txt

# comment out backend
tf-shim init -lock=false -force-copy
# OR 
# terraform state pull | tee terraform.tfstate

for ITEM in $(grep -E '^ *- ' tfplan.output.txt | grep -v destroy | sed -e 's/^ *- //'); do \
  terraform state mv -lock=false -state=terraform.tfstate ${ITEM} module.cje.${ITEM} ; \
done

# uncomment out backend
# CHANGE TF S3 BACKEND KEY TO `terraform.tfstate`
# This will make it easy to swing back to a previous state if necessary.
tf-shim init -lock=false -force-copy
```

Dont forget to cleanup S3 bucket
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNTg4MTk4NzddfQ==
-->