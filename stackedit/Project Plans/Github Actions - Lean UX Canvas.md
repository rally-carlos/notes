# Business Problem

 - The current Jenkins platform
	 - high platform maintaince cost (time)
	 - high support costs; produces serveral support requests per day (including #jenkins-smes, SO, Jira tickets)
	 - difficult to scale because platform is non-homogenous as every team is allowed to modify their controller
	 - security concerns, each team can configure their controller without best practices (managing Jenkins is not their primary focus)
	 - incured monitary cost from CloudBees licening and support
	 - non-intuative to work with CI

 - Teams are quick to blame build server over investigating the build itself.
 
# Business Outcome

 - Reduce cycletime (with more focus on troubleshooting builds over build server)
 - Increase inovation from CI platform team (reduce maintance and support; free to build a better "Space Elevator" [ref](https://docs.google.com/presentation/d/17XkhdQtP1ThbOH_C8JYm0Zygsv0bhpPWIjnQX8BMeM4/edit#slide=id.gaad5158c7d_3_244))
 - Decrease in costs  (with enphemeral infrastracture and no vendor licensing)

# Users and Customers

 - CI / Jenkins Platform Engineers
 - Operation Engineers
 - Development Engineers

# User Benifets

## All / General

 - Increase crowd sourced support (with a homogenous platform)
 - Reduce CI/build part of cycletime (remove current queue and agent issues)
 - Immediate team onboarding (with a single, homogenous platform)

## CI / Jenkins Platform Engineers

 - Reduce team on-boarding overhead
 - Less support request (with more decoupled homogenous platform)
 - Reduce platform maintance (as enviroment is enphemeral)
 - Increase in CI platform team reputation

# Proposed Solution

## On-prem Github Action runners

Create:
 - a more lossely coupled CI platform to process.
 - homogenous platform

### K8s vs EC2
EC2 over K8s is able to "stay quite close to the current GitHub approach". Also, EC2 will more easiliy support more use cases,  such as Docker and avoid DinD.

# Hypotheses

- Reduce team provisioning time to 0
- Reduce team specific support questions to 0

“We believe that [business outcome] will be achieved if [user] attains [benefit] with [feature].”

We believe that reduced cost will be achieved if
We believe that decreased cycle time will be achieved if
We believe that improved CI platform maturity and inovation i

# Leasons to Learn

This will guide adjustments to the roadmap:

 - How will users actually leverage this?
	 - Features required / prioritize.
	 - Rally's best practices and usage patterns

# Roadmap

## Phase 1 - Minimal Usable Product (a.k.a. MVP)

 - Execute in AWS `rally-dev` account
 - Access artificats in Artifactory
 - Validation: successfully lint
	 - Terraform 
	 - Python

## Phase 2 - Earlier Adopters: Operations

 - CI Platform team - FluxCD
 - Publicize / demo to operations teams
 - Start developing usage/best-practices (recommended happy path) guides

## Phase 3 - Build A Service

 - TBD (HelloPlay?)

## Phase 4 - Productionalizing

 - Monitoring
 - Alerting
 - Automate reprovisioning of "dummy" runner.
   Note: A “dummy” self-hosted runner will need to be maintained. It is required to trigger events, but will not actually be used.”  “A self-hosted runner is automatically removed from GitHub if it has not connected to GitHub Actions for more than 30 days.” -- [https://docs.github.com/en/free-pro-team@latest/actions/hosting-your-own-runners/about-self-hosted-runners#about-self-hosted-runners](https://docs.github.com/en/free-pro-team@latest/actions/hosting-your-own-runners/about-self-hosted-runners#about-self-hosted-runners)

# Risks

 - Accessing secrets from Vault

# Limitations

 - One runner / instance type per Github App. [philips-labs/terraform-aws-github-runner#73](https://github.com/philips-labs/terraform-aws-github-runner/issues/73)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5ODI1NDcwODEsLTExMTMwODk3MjQsMz
I4NTI3Mjc5LDIxMjQ1NzE4MDYsMTExNzA4MzEyLDIxNDcxODQ0
MTEsMTQ5NDI2NzU2MSwtMTExMjg2Njk0MSwtMTQ0Mjc3NzY5OS
wtMTUyNTcyMzAxMV19
-->