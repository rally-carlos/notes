
Inconsistencies
# Artifactory ACL Issue

## Problem

There is unexpected behavior on some artifacts when pulling from Rally's Artifactory's virtual repos. The expected behavior is to update the mirror/cache based on what is available in the official public repo. What is actually occuring is that Rally's Artifactory is serving custom artifacts that are inject into these virutal repos.

Anyone engi injected into any repo   using a single set of credientials for all engineers and not having any segmentation between teams. This 

### Example - Docker

```
❯ docker pull docker.io/ubuntu
...
❯ docker pull docker.werally.in/ubuntu
...
❯ docker image ls | grep ubuntu
ubuntu                                           latest    7e0aa2d69a15   9 days ago     72.7MB
docker.werally.in/ubuntu                         latest    e17b56e5200a   5 years ago    188MB
```

## Potential Solutions

- Segmented repositories, e.g. based on teams, solutions, etc
- Gate artifacts between development and production repositories.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg2MTYwNjkwXX0=
-->