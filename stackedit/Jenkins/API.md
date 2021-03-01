# References
- https://ci-staging.werally.in/cjoc/cli/
- https://www.jenkins.io/doc/book/using/remote-access-api/
- https://support.cloudbees.com/hc/en-us/articles/218889337-How-to-build-a-job-using-the-REST-API-and-cURL-
&nbsp;
- https://support.cloudbees.com/hc/en-us/articles/360030526992-How-to-manage-Credentials-via-the-REST-API
- https://support.cloudbees.com/hc/en-us/articles/360035634631-How-to-create-a-Kubernetes-Team-Master-programmatically#createremotelyusingconfigfiles (scroll down)
- https://support.cloudbees.com/hc/en-us/articles/360035632851-How-to-create-a-Kubernetes-Managed-Master-programmatically (non-blueocean version, looks like a PITA)
)

## CLI
* [CLI over SSH](https://www.jenkins.io/doc/book/managing/cli/)
* [Go implementation](https://github.com/jenkins-zh/jenkins-cli)

## Useful Endpoints
 - list-masters
   https://ci-staging.werally.in/cjoc/view/Masters/api/json?depth=1&tree=jobs[name,displayName,fullName,description,online,approved,url,endpoint]&pretty=true
 - teams
   https://ci-staging.werally.in/cjoc/job/Teams/api/json?depth=1&tree=jobs[name,displayName,fullName,description,online,approved,url,endpoint]&pretty=true

### CasC Bundles
 - https://docs.cloudbees.com/docs/cloudbees-ci/latest/cloud-admin-guide/ci-casc-modern
 - https://docs.cloudbees.com/docs/cloudbees-ci-api/latest/bundle-management-api
<br/>
 - https://ci-staging.werally.in/cjoc/casc-bundle/list/


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4MjM2MzgwMzQsLTE5MDM3NzQ1NTgsLT
QzMDQ3NjcwNCwtMjA4NjM5MTYyOCwtMjA0NTUwMzM2OSwtMTMy
OTQ2MDk2OCw5NjEwMjY5NTcsMzA0MzkwMDUsNjM3NDk2ODc1LD
czMDk5ODExNl19
-->