
## Postman

### Docs

- https://wiki.audaxhealth.com/display/ENG/Neptune+API+Access+Postman
- https://github.com/AudaxHealthInc/neptune-infra#postman-collections

### Steps

```sh
brew install postman
git clone --depth 1 --single-branch git@github.com:AudaxHealthInc/neptune-infra.git
PIPENV_VENV_IN_PROJECT=true pipenv install
pipenv shell
npm install openapi-to-postmanv2
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAyNDkxNzcyMF19
-->