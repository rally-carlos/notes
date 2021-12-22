


Integration [Platform] (Tiger)
- Bump Jenkins worker capsity to 20 to prevent large build queues
- Cleanup artifacts in Artifactory to improve speed

Deployment (BigCat)
- Announcing neptunectl
- Preping to move API to prod

Metrics (Gizmo)
- Updated dashboards

Performance (Golden Gate)
- N/A

Lean Coffee

- Should there be Deployment Automation mini-brownbags
	- yes! - Carlos and Poorva
- Is there availble documentation for onboarding to GitHub Actions
  - TL;DR: no
  - WIP w/ Force team to onboard -Pavan
  - Maybe worth docing Linting , Unit Test -Carlos
- Performance test and firedrills
	- manifests not being maintained
	- Ben H. will be rattling cages of those responsible to update their manifest
- How do better deal w/ log4j of the future
	- Centralized build image -Glenn
	- Limit the number of base images, base, jvm version, node versions. - Exceptions requires Sec. -Carlos
	- Pavan investigating base container
	- Have Ariemites query for transitive deps -Glenn
-
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MTc1MDQyMTgsLTEwODMzNjE0MDgsLT
QyMjIxODA3OSw4NDk4MzU2LC0xNDYwMDc2NjAsLTE0OTU3NTM5
NjcsLTU3MTkyNjk4NSw2ODI3NzY2MzVdfQ==
-->