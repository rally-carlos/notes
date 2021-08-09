# Vault Tool

## connect
```sh
AWS_PROFILE='' rally-okta -w
for RENV in defaultaccess-rally-dev scab-rally-prod; do connect-to-scab -D -e ${RENV}; done
```

### new

```
AWS_PROFILE='' rally-okta -w
connect-to-scab -e defaultaccess-rally-dev -t stoic-hoover -s 3130
connect-to-scab -e scab-rally-prod -D
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMjY2MTU5MjYsODY3OTM3MzUwXX0=
-->