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

export AWS_PROFILE="rally-dev"
export AWS_DEFAULT_REGION="us-east-1"
export ROLE_SESSION_NAME="defaultaccess-rally-dev"
export AWS_DEFAULT_OUTPUT="text"

## K8s


## SCAB
https://github.com/AudaxHealthInc/ops-access-tools/blob/master/README-connect-to-scab.md
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNTc5MjQ0NTEsNTE4OTE3MTMxLC01Nj
I2NTE2OTZdfQ==
-->