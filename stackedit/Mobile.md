
# 2021-07-29 Mobile Meeting Notes

**Primary Objective**: Migrate off of CircleCI

## Plan

Mobile teams teams will run point on actually migration of builds.
Tiger is available to share knowledge/experience with GitHub Actions. Tiger provided an initial potential workflow, from their understanding of Android/Gradle builds: https://github.com/AudaxHealthInc/megazord-android/pull/4042

### Phase 1: Leverage GitHub Actions hosted runners

Attempt to builds in hosted runners. Use Mac runners for Android builds if necessary. (This validate the posiblitity or make visable any potential issues.)

### Phase 2: Optimize CI

If hosted runners are too expenisive, there is now a stronger buinesses case to prioritize resources to providing GitHub Actions self-hosted runners.

## Contacts

 - iOS: Chase
 - Android: Scott
 - Tiger: Carlos

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY5NTQ0NDMyOF19
-->