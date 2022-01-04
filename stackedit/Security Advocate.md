# Vault Tool

## connect
```sh
AWS_PROFILE='' rally-okta -w
for RENV in defaultaccess-rally-dev scab-rally-prod; do connect-to-scab -D -e ${RENV}; done
```

### new

```
connect-to-scab -e defaultaccess-rally-dev -t stoic-hoover -s 3130
connect-to-scab -e defaultaccess-rally-dev -t prickly-flower -s 3132 -D
connect-to-scab -e scab-rally-prod -D
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMTY4MTIwMSwtMTEyNjYxNTkyNiw4Nj
c5MzczNTBdfQ==
-->