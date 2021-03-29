# Business Problem

 - The current Jenkins platform
	 - a lot of maintaince and engineer engagment time
	 - produces serveral support requests per day (including #jenkins-smes, SO, Jira tickets)
	 - difficult to scale because platform is non-homogenous as every team is allowed to modify their controller
	 - security conideration since each team can configure their controller without best practices
	 - incured monitary cost from CloudBees licening and support
 - The current CI is very customized making it non-intuative, especially to new engineers

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

## Development / Product Engineers

 - Immediate team onboarding (with a single, homogenous platform)

## Ops Engineers
 - Faster onboarding and
 - Less support
 

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

# Hypotheses

- Reduce team provisioning time to 0
- Reduce team specific support questions to 0

# What’s the most important thing we need to learn first?

 - Will this be adopted?
 - Features required / prioritize.
 - Rally's best practices and usage patterns

# Roadmap

## Phase 1 - Minimal Usable Product (a.k.a. MVP)

 - Execute in AWS `rally-dev` account
 - Access artificats in Artifactory
 - Validation
	 - Successfully run basic linting
		 - Terraform 
		 - Python

## Phase 2 - Earlier Adopters: Operations

 - CI Platform team - FluxCD
 - Publicize / demo to operations teams
 - Start developing usage/best-practices (recommended happy path) guides

## Phase 3 - Build Service

 - TBD (HelloPlay?)

## Phase 4 - Productionalizing

 - monitoring
 - alerting

# Risks

 - Accessing secrets from Vault
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2OTkxNjc5ODksMTExNzA4MzEyLDIxND
cxODQ0MTEsMTQ5NDI2NzU2MSwtMTExMjg2Njk0MSwtMTQ0Mjc3
NzY5OSwtMTUyNTcyMzAxMV19
-->