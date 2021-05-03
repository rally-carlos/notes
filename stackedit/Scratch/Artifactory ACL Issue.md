# Artifactory ACL Issue

## Problem

Rally's Artifactory's virtual repositories serve the incorrect artifacts. The expected behavior is to update the mirror/cache based on what is available in the official public repo. What is actually occurring is that Rally's Artifactory is serving custom artifacts that are injected into virtual repos.

Anyone engineer can inject artifacts and change tags in any repository, accidentally or maliciously. A consumer of a repository with an injected artifact will no longer be receiving the expected artifact. This is possible because Rally uses a single set of credentials for all engineers and not having any segmentation between teams.

In a repository that has had an artifact pushed to it that matches an upstream tag, Artifactory will no longer look at the public repo, as it assumes overriding the tag was intentional. This can be observed in pulling an Ubuntu Docker container image:

```
❯ docker pull docker.io/ubuntu
...
❯ docker pull docker.werally.in/ubuntu
...
❯ docker image ls | grep ubuntu
ubuntu latest 7e0aa2d69a15 9 days ago 72.7MB
docker.werally.in/ubuntu latest e17b56e5200a 5 years ago 188MB
```

### Impact

* **Production stability**
* The artifact can be unexpectedly changed. That would be difficult to discover and resolve during a TPS.
* **Security posture**
* Repositories would no longer properly update and miss patches.
* There is a large blast radius as a bad actor can update any artifact such as a "base" image.

## Potential Solutions

- Segmented repositories, e.g. based on teams, solutions, etc
- Gate artifacts between development and production repositories.
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTcxNjk3MjIxLDI3NzU2MjQ0NF19
-->