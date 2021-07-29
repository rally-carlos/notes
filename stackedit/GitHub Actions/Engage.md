# 2021-07-29 Meeting Notes w/ Chris V

Chris like GitHub Actions because no additional code had to be written because of off the shelf Actions. Also, Chris expects better consistency from GitHub Actions over the Jenkins infra.

Chris is was blocked on pushing to Artifactory.
Tiger shared the test repo and action-artifact-access.

versioning:

 - libs need semantic versioning
 - services need continous versioning

Chris is currently using release/versioned branches to support multiple versions.

Chris is a maintainer for OpenZipkin. How releases are happening there, https://github.com/openzipkin/zipkin-finagle/blob/master/.github/workflows/create_release.yml

Chris will try to leverage GitHub Actions for libs, i.e. https://github.com/AudaxHealthInc/lib-kush.

We all agree continous deployment is where we want to be.

Per Chris, teams may not be ready for continous deployment because of testing.

Carlos suggested conventional commits to easy automating steps for continous deployment, i.e. versioning.

Tiger welcomes Chris as an early adopter for alpha/beta testing and feedback.

<!--stackedit_data:
eyJoaXN0b3J5IjpbOTY3ODk0ODU5LDEyNTY4MzU5NTAsLTQ2ND
UxMzQ0M119
-->