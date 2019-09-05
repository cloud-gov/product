# Summary: Example of running custom brokers for AWS/Azure/GCP

## What we're after
What we're after: Tenants have a runbook / well-paved path for brokering services not directly supported by cloud.gov

## Hypothesized benefits/why:
- Enable migration of apps with unsupported dependencies to cloud.gov
- Enable tenants to integrate cloud.gov with their pre-existing investments in other cloud resources

---
 
### Further context for those unfamiliar with what we're doing

Cloud.gov is a deployment and hosting platform for government digital services. Cloud.gov is based on Cloud Foundry which uses brokers to manage the lifecycle of services for its users. Cloud.gov tenants can run their own brokers for services not supported / brokered by cloud.gov. This issue seeks to document how customers can do this is a straight-forward, secure, and easy to replicate way.

### Notes for implementers
- Implementation can be done with any Cloud Foundry instance; no access to existing cloud.gov infrastructure is needed to develop or demo it.
  - For example, this work can be implemented locally using [cf dev](https://github.com/cloudfoundry-incubator/cfdev)

- Installing the broker on a existing Cloud Foundry instance should be easy to reproduce, making use of existing tooling where appropriate.
  - [deploy-to-cf](https://github.com/jmcarp/deploy-to-cf)
  - [Terraform Provider for Cloud Foundry](https://github.com/mevansam/terraform-provider-cfy)
  - [Managing Service Brokers](https://docs.cloudfoundry.org/services/managing-service-brokers.html)
  - [Register your own service broker with any Cloud Foundry](https://www.starkandwayne.com/blog/register-your-own-service-broker-with-any-cloud-foundry/)

- Services from multiple external cloud providers should be included in the demo.
  - [Google Cloud Platform Service Broker](https://cloud.google.com/kubernetes-engine/docs/concepts/google-cloud-platform-service-broker)
  - [Open Service Broker for Azure](https://osba.sh/)

- The demo should include showing how to acesss the brokered services through the Stratos UI.
  - [Stratos: Web-based Console UI for Cloud Foundry](https://github.com/cloudfoundry-incubator/stratos)

#### Non-functional requirements that are to be assumed
- The implementer is responsible for the following stages of the [cloud.gov Story Lifecycle](https://github.com/18F/cg-product/blob/master/StoryLifecycle.md)
  - Grooming / Ready
      - Work with a member of the cloud.gov team to create a backlog and discuss implementation details
  - In Progress
  - Awaiting Acceptance
      - Work with a member of the cloud.gov team to accept the delivered work.
- The solution should include an automated test suite that completes the major portions of the tutorial as if a user was doing it from the CLI. That is, the tutorial will guide the user through a series of steps to register a broker and make it available as a service. The `cf` or other CLI commands enumerated in the tutorial to accomplish this will be executed within an automated test suite, mimicking the steps a user takes while working through the tutorial. This verifies the steps in the tutorial are correct. An automated test suite allows the cloud.gov team to ensure the solution works on the platform. The automated test suite could also be used as a guide for the IaC a user would create in their environment.

#### How to deliver
- Submit a series of pull-requests to cloud.gov github repositories. The appropriate repositories will be determined during the Grooming / Ready phase.
- Implementation can be done with any Cloud Foundry instance; no access to existing cloud.gov infrastructure is needed to develop or demo it. The video demonstrating usage need not use cloud.gov-specific URLs.

---

## User stories and acceptance criteria

Here's a draft backlog of user stories describing behaviors we think are needed to deliver this capability. It's always based on our best understanding of what's needed when we last discussed this feature. That means it's not set in stone, and it can and should be updated amd expanded whenever better understanding of the work involved is available! We use this as both a running catalog of work yet-to-do, as well as a guide to demonstrating and evaluating the submitted work. 

[Gherkin](https://en.wikipedia.org/wiki/Cucumber_(software)#Gherkin_language) is a domain language for capturing [behavioral specifications](https://en.wikipedia.org/wiki/Behavior-driven_development#Behavioral_specifications) as scenarios. For clarity, the stories and acceptance criteria are specified here using Gherkin. (Actual BDD step implementations that validate the behavior and increase test coverage would be great! However, it's not necessary to include BDD test automation for the work to be accepted.)

### User stories
**Background:**

- Given a public repository exists containing code and documentation
- And a suitable Cloud Foundry instance
- And the Cloud Foundry instance is running an instance of Stratos

**Scenario:** Clients can view a video covering the entire process

- Given the the Client is using a supported browser
- When the Client views the README for the repository
- Then there is a Video embedded in the README
- When the Client clicks play
- Then the Video should play

**Scenario:** Clients can replicate the video demo

- Given the repository is cloned locally
- And the Client has all requirements installed
- And the Client provides a correct configuration file
- When the Client runs the code in the repository
- Then the Broker can be accessed via it's URL
- And the Broker offers the configured plans
- And the Client can see the broker's plans in Stratos
- And the Client can provision a service instance via Stratos