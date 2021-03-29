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

&nbsp;
 - reduced costs when team run soley on Github Actions


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

 - Reduce on-boarding team time
 - Less support request (with more decoupled homogenous platform)
 - Reduce platform maintance (as enviroment is enphemeral)
 
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
eyJoaXN0b3J5IjpbLTE2MzUyOTQyNDgsMjE0NzE4NDQxMSwxND
k0MjY3NTYxLC0xMTEyODY2OTQxLC0xNDQyNzc3Njk5LC0xNTI1
NzIzMDExXX0=
-->