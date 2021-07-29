# 2020-07-29
Chris likes GitHub Actions because no additional code had to be written because of the off-the-shelf Actions. Also, Chris expects better consistency from GitHub Actions over the Jenkins infra.  
  
Chris is was blocked on pushing to Artifactory.  
Tiger shared the test repo that mimicks Proton, https://github.com/AudaxHealthInc/tmpl-test/blob/main/.github/workflows/main.yaml.

Tiger shared action to authenticate to Artifactory: https://github.com/AudaxHealthInc/action-artifact-access.  
  
versioning:  
- libs need semantic versioning  
- services need continuous versioning  
  
Chris is currently using release/versioned branches to support multiple versions.  
  
Chris is a maintainer for OpenZipkin. An example of how releases are happening there https://github.com/openzipkin/zipkin-finagle/blob/master/.github/workflows/create_release.yml.  
  
Chris will try to leverage GitHub Actions for libs, i.e., https://github.com/AudaxHealthInc/lib-kush.  
  
We all agree continuous deployment is where we want to be.  
  
Per Chris, teams may not be ready for continuous deployment because of testing.  
  
Carlos suggested conventional commits to easy automating steps for continuous deployment, i.e., versioning. It was noted that such a change would require socialization. Eric pointed any change to make builds consistent requires socialization.  
  
Tiger welcomes Chris as an early adopter for alpha/beta testing and feedback.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4Nzg2NTA0NiwxMzcxNjQzMzI5XX0=
-->