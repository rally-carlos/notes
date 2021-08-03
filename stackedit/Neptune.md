
## Postman

### Docs

- https://wiki.audaxhealth.com/display/ENG/Neptune+API+Access+Postman
- https://github.com/AudaxHealthInc/neptune-infra#postman-collections
- [openapi_to_postman.py](https://github.com/AudaxHealthInc/neptune-infra/blob/master/scripts/openapi_to_postman.py#L1-L17)

### Steps

```sh
brew install postman
git clone --depth 1 --single-branch git@github.com:AudaxHealthInc/neptune-infra.git
PIPENV_VENV_IN_PROJECT=true pipenv install
pipenv shell
npm install -g openapi-to-postmanv2
AWS_PROFILE=rally-dev AWS_DEFAULT_REGION=us-east-1 python3 scripts/openapi_to_postman.py --session-auth
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMTU4MzIxMTgsLTI1MjMyOTMwMSwyMT
IwMzA0MzcwXX0=
-->