
Inconsistencies

There is unexpected behavior on some artifacts when pulling from Rally's Artifactory's virtual repos. The expected behavior is to update the mirror/cache based on 
```
❯ docker pull docker.io/ubuntu
...
❯ docker pull docker.werally.in/ubuntu
...
❯ docker image ls | grep ubuntu
ubuntu                                           latest    7e0aa2d69a15   9 days ago     72.7MB
docker.werally.in/ubuntu                         latest    e17b56e5200a   5 years ago    188MB
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg1MDM5MzI4NV19
-->