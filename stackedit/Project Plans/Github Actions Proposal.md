
# Overview

A CI platform should also be scalable and a consistent experience with best-practices across an organization. The infrastructure should be an implementation detail that users are unconcerned about (outside infrastructure-specific builds, i.e., Docker).

Currently, supporting a team's build needs require tightly coupled customizations to the build server (i.e., Jenkins plugins), which results in each team free to customize their build server. Snowflake build servers makes support difficult and introduces security concerns. Excessive time is spent troubleshooting and maintaining build servers rather than troubleshooting the builds themselves or innovating and maturing the CI platform. More recently, teams are beginning to adopt alternative CI platforms on their own, signifying a demand for a new solution.

Github Action provides a homogenous CI platform loosely coupled from build-level modification (actions vs. plugins). One-to-one feature parity with the current CI platform is not the intention of Github Actions. Github Actions’ initial adoption plan includes smaller scoped tests, such as lint and unit tests, and CI workflows designed with Github Actions in mind, i.e. FluxCD.

# Vision

 - Reduce cycletime (by focusing more on troubleshooting builds over build server)
	Amount TBD
 - Enable CI platform maturity and invocation by reducing maintenance and support (free up CI platform to build a better "Space Elevator" [ref](https://docs.google.com/presentation/d/17XkhdQtP1ThbOH_C8JYm0Zygsv0bhpPWIjnQX8BMeM4/edit#slide=id.gaad5158c7d_3_244)).
   - Decrease support time from 8h/week to 4/week (initially, this may be higher)
   - Decrease maintenance from 6h/month to 2h/month
   - Reduce team provisioning time to 0
   - Reduce team-specific support questions to 0 (more focus on platform level inquiries)
 - Decrease in costs with ephemeral infrastructure and no additional vendor licensing.
    The exact current costs are unknown. GH Action runner infrastructure is more efficient and not persistent (besides AMIs, Lambdas, etc.).

# Users and Customers

 - CI Platform Engineers
 - Operation Engineers
 - Development Engineers

## User Benefits

### All / General

 - Increase crowdsourced support (due to a homogenous platform)
 - Reduce CI/build part of cycletime (remove current queue and agent issues)
 - Immediate team onboarding (with a single, homogenous platform)

### CI / Jenkins Platform Engineers

 - Reduce team onboarding overhead
 - Less support request (with more decoupled homogenous platform)
 - Reduce platform maintenance (as the environment is ephemeral)
 - Increase in CI platform team reputation

# Design Notes

## On-Prem vs. SasS

On-prem runners places the CI execution inside Rally VPCs where Ops can control network access and ACL/IAMs roles. Furthermore, concerns about moving data outside of Rally are mitigated.

## K8s vs. EC2
[enter link description here](s)
EC2 over K8s can "stay quite close to the current GitHub approach" ([philips-labs/terraform-aws-github-runner/README.md#motivation](https://github.com/philips-labs/terraform-aws-github-runner/blob/develop/README.md#motivation)). Also, EC2 will more easily support more use cases, such as Docker and avoid DinD.

# Risks

 - Accessing secrets from Vault does not have a clear path/solution.

# Limitations

 - One runner / instance type per Github App. [philips-labs/terraform-aws-github-runner#73](https://github.com/philips-labs/terraform-aws-github-runner/issues/73)
 - General [usage limits](https://docs.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners#usage-limits).

# Lessons to Learn

These lessons will guide adjustments to the roadmap:

 - How will users leverage this?
   - Features required / prioritize.
   - Rally's best practices and usage patterns

# Roadmap

## Milestone 1 - Minimal Usable Product (a.k.a. MVP)

 - Execute in AWS `rally-dev` account
 - Access artifacts from Artifactory
 - Validate usability via linting jobs
   - Terraform
   - Python

## Milestone 2 - Earlier Adopters: Operations

 - CI Platform team - FluxCD
 - PubliPublicize/democize / demo to operations teams
 - Start developing usage/best-practices (recommended happy path) guides

## Milestone 3 - Build A Service

 - TBD (HelloPlay?)
  
## Milestone 4 - Productionalizing

 - Monitoring
 - Alerting
 - Automate reprovisioning of "dummy" runner.
   Note: A “dummy” self-hosted runner will need to be periodically recreated. It is a requirement to trigger events, even though it is not actually used. “A self-hosted runner is automatically removed from GitHub if it has not connected to GitHub Actions for more than 30 days.” -- [https://docs.github.com/en/free-pro-team@latest/actions/hosting-your-own-runners/about-self-hosted-runners#about-self-hosted-runners](https://docs.github.com/en/free-pro-team@latest/actions/hosting-your-own-runners/about-self-hosted-runners#about-self-hosted-runners)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMyOTQwMjg5LC05NDAxNjMwMzAsLTIwOD
Q1Mjc2OTIsMTYyNzQzMzMxLDkzMDI5ODQyOSw0MjU4NTA0MjYs
MTU3NjQxOTAwNiwtMTc4MDI0NDE2MiwtMTU2NzM0NjAyLDMzMT
U3Mjk1MiwxNDE3MzE5ODY4LC00NDcyMDk4MjksMTk1NDA3NzAx
OCwxMjc2ODE0MDM0LC0xMzQ5NDIwOTE4XX0=
-->