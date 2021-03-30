# Overview

A CI platform infrastructure should be an implentation detail that users are unconcerned about. It should also be a scalable consistant experiance with best-practices across an organization. Currently, excessive time is spent troubleshooting and maintaining build servers rather than troubleshooting the builds themseles or inovating and maturing the CI platform. A team's build needs require unique customization that are tightly couple to the build server (i.e. Jenkins pluggins). This need results in each team being free to customize their build server. This make support more difficult and introduce security concerns. More recently, teams are beinging to adopt alternative CI platforms on their own signifing, a demand for a new solution.

Github Action provide a homogenous CI platform that is loosly coupled from build infrastructure modification.

# Vission
 - Reduce cycletime (by focusing more on troubleshooting builds over build server)
   Amount TBD
 - Enable CI platform maturity and invoation by reducing maintance and support (free up CI platform to build a better "Space Elevator" [ref](https://docs.google.com/presentation/d/17XkhdQtP1ThbOH_C8JYm0Zygsv0bhpPWIjnQX8BMeM4/edit#slide=id.gaad5158c7d_3_244)).
	- Decrease support time from 8h/week to 4/week (though initially this may be higher)
	- Decrease maintance from 6h/month to 2h/month
	- Reduce team provisioning time to 0
	- Reduce team specific support questions to 0 (does not elimate platform level inqueries)inquiries
 - Decrease in costs with enphemeral infrastracture and no additional vendor licensing.
    Exact current costs are unknown. GH Action runner infrastructure is more efficent and not persistant (besides such things as AMIs and Lambdas).

# Users and Customers

 - CI Platform Engineers
 - Operation Engineers
 - Development Engineers

## User Benifets

### All / General

 - Increase crowd sourced support (with a homogenous platform)
 - Reduce CI/build part of cycletime (remove current queue and agent issues)
 - Immediate team onboarding (with a single, homogenous platform)

### CI / Jenkins Platform Engineers

 - Reduce team on-boarding overhead
 - Less support request (with more decoupled homogenous platform)
 - Reduce platform maintance (as enviroment is enphemeral)
 - Increase in CI platform team reputation

# Proposed Solution

### K8s vs EC2
EC2 over K8s is able to "stay quite close to the current GitHub approach". Also, EC2 will more easiliy support more use cases,  such as Docker and avoid DinD.

# Hypotheses



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

 - Accessing secrets from Vault does not have a clear path/solution.

# Limitations

 - One runner / instance type per Github App. [philips-labs/terraform-aws-github-runner#73](https://github.com/philips-labs/terraform-aws-github-runner/issues/73)
 - General [usage limits](https://docs.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners#usage-limits).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwOTExNzg3MjMsLTQ0NzIwOTgyOSwxOT
U0MDc3MDE4LDEyNzY4MTQwMzQsLTEzNDk0MjA5MThdfQ==
-->