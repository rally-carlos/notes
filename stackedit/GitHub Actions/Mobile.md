
# 2021-07-29 Mobile Meeting Notes

**Primary Objective**: Migrate off of CircleCI

## Plan

Mobile teams will run point on the actual migration of builds.
Tiger is available to share knowledge/experience with GitHub Actions.

Tiger provided an initial potential workflow, from their understanding of Android/Gradle builds: https://github.com/AudaxHealthInc/megazord-android/pull/4042

### Phase 1: Leverage GitHub Actions hosted runners

Attempt to builds in hosted runners. Use Mac runners for Android builds if necessary. (This validates the possibility or make visible any potential issues.)

### Phase 2: Optimize CI

If hosted runners are too expensive, there is now a stronger business case to prioritize resources to providing GitHub Actions self-hosted runners.

## Contacts

 - iOS: Chase, https://github.com/AudaxHealthInc/lib-mobile-ditto/tree/main/.github/workflows
 - Android: Scott
 - Tiger: Carlos
<!--stackedit_data:
eyJoaXN0b3J5IjpbODk4Nzg1NzFdfQ==
-->