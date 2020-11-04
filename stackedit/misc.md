# Connecting to Stuff

## AWS Authentication
https://wiki.audaxhealth.com/x/b5cgBQ

### Okta
```sh
rally-okta -P  # Configure SSO password for OKTA auth
rally-okta -B. # Bootstrap OKTA configuration
```

### AWS Profiles
```sh
rally-okta -w  # Write AWS Credentials for all profiles
rally-okta -s # View session expiration
```

## SCAB
https://github.com/AudaxHealthInc/ops-access-tools/blob/master/README-connect-to-scab.md
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTE4OTE3MTMxLC01NjI2NTE2OTZdfQ==
-->