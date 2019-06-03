# Summary: [short, single-line summary of the feature, eg "Brokered SQS service"]

## What we're after
[Brief high-level characterization of the capability expected, eg "Tenants can easily provision SQS capability for their hosted apps"]

## Hypothesized benefits/why:
[ bullet(s) indicating the expected impact(s) from doing the work ]
- Enables easier migration of queue-dependent apps to cloud.gov
- Reduce burden on bespoke provisioning of AWS resources outside cloud.gov for those already using SQS

---
 
### Further context for those unfamiliar with what we're doing

[cloud.gov](https://cloud.gov) is a deployment and hosting platform for government digital services. [add any background context necessary to understand what this feature is about or why it's needed; in this case, maybe talk about what OSBAPI/a broker is.]

[list what you would expect to the feature to include in more detail. talk about any critical workflows. For example "cloud.gov should allow users to request and view the options available for an SQS service, create an SQS service instance for their Cloud Foundry space, and associate/disassociate the SQS service instance with one or more apps. When the Cloud Foundry service instance is deleted, the SQS service that was instantiated upon service creation and any credentials issued for bind operations should be deleted as well.""]

### Notes for implementers

- [Pointers to relevant languages, components, frameworks, prior art/examples, user research, mockups, etc.]
- [a technical sketch if we're confident of how to approach implementation]
- [Example: "We need to create a new broker. Get familiar with [the docs](https://docs.cloudfoundry.org/services/overview.html). [Broker API](https://github.com/pivotal-cf/brokerapi) is a good starting point. Implementation can be done with any AWS account; no access to existing cloud.gov infrastructure should be needed to develop or demo it. The behavior can be demonstrated via exercise of the broker’s REST APIs.]

#### Non-functional requirements that are to be assumed
The implementer is responsible for the following stages of the [cloud.gov Story Lifecycle](https://github.com/18F/cg-product/blob/master/StoryLifecycle.md)
  - Grooming / Ready
      - Work with a member of the cloud.gov team to create a backlog and discuss implementation details
  - In Progress
  - Awaiting Acceptance
      - Work with a member of the cloud.gov team to accept the delivered work.

#### How to deliver
- Submit a series of pull-requests in these repositories
  - https://github.com/18f/[reponame(s)]

---

## User stories and acceptance criteria

Here's a draft backlog of user stories describing changes/behaviors we think are needed to deliver this capability. It's always based on our best understanding of what's needed when we last discussed this feature. That means it's not set in stone, and it can and should be updated amd expanded whenever better understanding of the work involved is available! We use this as both a running catalog of work yet-to-do, as well as a guide to demonstrating and evaluating the submitted work. 

[Gherkin](https://en.wikipedia.org/wiki/Cucumber_(software)#Gherkin_language) is a domain language for capturing [behavioral specifications](https://en.wikipedia.org/wiki/Behavior-driven_development#Behavioral_specifications) as scenarios. For clarity, the stories and acceptance criteria are specified here using Gherkin. (Actual BDD step implementations that validate the behavior and increase test coverage would be great! However, it's not necessary to include BDD test automation for the work to be accepted.)

### User stories

[a sample proto-backlog for the example feature follows]

**Background:**

- Given Broker is a running, properly-configured instance of the SQS broker
- And Broker is configured to offer an SQS plan
- And Client is an authenticated client with access to the broker's OSBAPI port

**Scenario:** Clients can view the available SQS options via OSBAPI

- Given there is one service plan for the SQS service
- When Client requests the Broker’s catalog
- Then the response should be in [JSON] format
- And the response should include the SQS service
- And the response should include the name of the SQS service plan
- And the response should include a description of the service plan
- And the response should include the pricing associated with the SQS service plan

**Scenario:** Clients can provision a new SQS service instance for use with their apps

- Given there is one SQS plan
- When Client requests a new service instance of a valid plan
- Then an SQS queue is created and assigned an instance ID
- And the response should be a valid OSBAPI provision response
- And the response should include details about the instance that was created

**Scenario:** An app gets valid credentials when bound to the SQS service instance

- Given there is an SQS service instance
- When an app id is bound to the instance
- Then new IAM user credentials are returned for that app
- And that IAM user has access to the queue associated with the instance

**Scenario:** An app id’s credentials are invalidated when unbound to the SQS service instance

- Given there is an SQS service instance
- And an app id that is bound to the instance
- When the app id is unbound from the instance
- Then the app id’s IAM user credentials no longer have access to the queue associated with the instance

**Scenario:** Removing service instance results in deletion of associated SQS queue and IAMs

- Given there is an SQS service instance
- And there is an app id bound to the service instance
- When the service instance is removed
- Then the associated SQS queue is deleted
- And any IAM credentials issued for that queue are revoked

