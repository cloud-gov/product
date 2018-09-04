# Summary: Example of running custom brokers for AWS/Azure/GCP

## What we're after
What we're after: Tenants have a runbook / well-paved path for brokering services not directly supported by cloud.gov

## Hypothesized benefits/why:
- Enable migration of apps with unsupported dependencies to cloud.gov
- Enable tenants to integrate cloud.gov with their pre-existing investments in other cloud resources

---
 
### Further context for those unfamiliar with what we're doing

Cloud.gov is a deployment and hosting platform for government digital services. Cloud.gov is based on Cloud Foundry which uses brokers to manage the lifecycle of services for its users. Cloud.gov tenants can run their own brokers for services not supported / brokered by cloud.gov. This issue seeks to document how customers can do this is a straight-forward, secure, and easy to replicate way.

Implementation can be done with any Cloud Foundry instance; no access to existing cloud.gov infrastructure is needed to develop or demo it.

### Notes for implementers
- Installing the broker on a Cloud Foundry instance should be automated using a tool such as Terraform.
- [Google Cloud Platform Service Broker](https://cloud.google.com/kubernetes-engine/docs/concepts/google-cloud-platform-service-broker)
- [Open Service Broker for Azure](https://osba.sh/)
- [Managing Service Brokers](https://docs.cloudfoundry.org/services/managing-service-brokers.html)
- [Stratos: Web-based Console UI for Cloud Foundry](https://github.com/cloudfoundry-incubator/stratos)
- [cf dev](https://github.com/cloudfoundry-incubator/cfdev)
- [Terraform Provider for Cloud Foundry](https://github.com/orange-cloudfoundry/terraform-provider-cloudfoundry)


#### Non-functional requirements that are to be assumed
- ***[TBD: What stage is the implementer responsible for vs cloud.gov team accepting the work](https://github.com/18F/cg-product/blob/master/StoryLifecycle.md)***

#### How to deliver
- Submit a series of pull-requests in these repositories
  - ***TBD: https://github.com/18f/???***
- Implementation can be done with any Cloud Foundry instance; no access to existing cloud.gov infrastructure is needed to develop or demo it. The behavior can be demonstrated via exercise of the broker’s REST APIs.

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

- Given there is a Video embedded in the README
- And the Client is viewing it in a supported browser
- And the Client clicks play
- Then the Video should play


**Scenario:** Clients can replicate the video demo

- Given the repository is cloned locally
- And the Client has all requirements installed
- And the Client provides a correct configuration file
- And the Client runs executes the code in the repository
- Then the Broker can be accessed via it's URL
- And the Broker offers the configured plans
- And the Client can see the broker's plans in Stratos
- And the Client can provision a service instance via Stratos
