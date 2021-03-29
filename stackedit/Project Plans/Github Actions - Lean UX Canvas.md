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
 - Increase inovation from CI platform team (reduce mainace and support)
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

# Minimal Usable Product (a.k.a. MVP)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM5NDg2ODQ5LDExMTcwODMxMiwyMTQ3MT
g0NDExLDE0OTQyNjc1NjEsLTExMTI4NjY5NDEsLTE0NDI3Nzc2
OTksLTE1MjU3MjMwMTFdfQ==
-->