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

 - monitoring
 - alerting

# Risks

 - Accessing secrets from Vault

# Limitations

 - One runner / instance type per Github App. [https://github.com/philips-labs/terraform-aws-github-runner/issues/73](https://github.com/philips-labs/terraform-aws-github-runner/issues/73)**
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUxNDYyOTk5OCwzMjg1MjcyNzksMjEyND
U3MTgwNiwxMTE3MDgzMTIsMjE0NzE4NDQxMSwxNDk0MjY3NTYx
LC0xMTEyODY2OTQxLC0xNDQyNzc3Njk5LC0xNTI1NzIzMDExXX
0=
-->