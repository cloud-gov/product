# Container Scanning & Validation

## What we need

We need to scan containers we use so we can track issues with security, compliance, and best practices.

This scanning must comply with the [FedRAMP Vulnerability Scanning Requirements for Containers](https://www.fedramp.gov/assets/resources/documents/Vulnerability_Scanning_Requirements_for_Containers.pdf).

### Goals

These are the important goals to keep in mind while selecting an implementation path:
- minimize developer friction when adding or updating containers
- prevent major CVEs from entering our network
- provide visibility into less severe issues, so we can iterate on them
- provide a stable, compliant solution

### Scope

We need to ensure we're scanning containers used in-boundary. Currently, this means:

- concourse resources


## Selected option and rationale

We are opting to go with [SaaS registry with explicit push](#container-registry-saas-wexplicit-push). Primary rationale:
- [Scan and list](#scan-and-list) is too brittle for day-to-day usage, plus does not solve the problem well enough for non-concourse usage
- [cloud.gov registry with passthrough](#container-registry-run-our-own--passthrough) probably does not meet FedRAMP requirements, which
  seem to state that we must scan an image before usage in production
- [cloud.gov registry with explicit push](#container-registry-run-our-own--explicit-push) requires too much operational overhead for the 
   time being.
- [SaaS registry with explicit push](#container-registry-saas-wexplicit-push) seems to meet all our requirements for a relatively low
   level of effort

### Rough sketch and next steps

(this sketch drafted following our discussion and decision)

We are planning to go forward using ECR as our container registry. We hope to leverage the built-in scanning tools as our scanning 
solution. We'll start by building a proof-of-concept for a push->scan->promote pipeline using ECR. Pending results there, we'll work
with our compliance team to make sure it's production-ready and approved for use, then start adding images used by Concourse to the 
pipeline, and switch Concourse to use ECR as its registry.

### Requirements

These statements are pulled directly from the [FedRAMP Vulnerability Scanning Requirements for Containers](https://www.fedramp.gov/assets/resources/documents/Vulnerability_Scanning_Requirements_for_Containers.pdf).  We need to make sure they are accounted for and implemented as a part of our solution.

#### Hardened Images

_Final configurations must be validated by a 3PAO to ensure they meet FedRAMP requirements for the baseline controls CM-6, SC-2, SC-3, SC-4, SC-6, SC-28, and SC-39._

We will need to iron out the details of this piece as whatever images we put into ECR will have to be hardened by us beforehand.  We already perform [hardening with our stemcells Ubuntu images](https://github.com/cloud-gov/cg-harden-boshrelease), so this will likely serve as our baseline for hardening future images.

#### Build, Test, and Orchestration Pipeline

_These automated tools must be validated by a 3PAO to meet FedRAMP requirements for the baseline controls CA-2, CM-2, CM-3, SC-28, SI-3, and SI-7._

The pipeline we build will require an SCR and validation by a 3PAO.  ECR will provide the registry and scanning pieces, Concourse will provide the deployment piece, but we will need to figure out the image hardening piece a stated above.

#### Vulnerability Scanning for Container Images

_Prior to deploying a container to a production environment, all components in the image must be scanned according to the [FedRAMP Vulnerability Scanning Requirements](https://www.fedramp.gov/assets/resources/documents/CSP_Vulnerability_Scanning_Requirements.pdf) document. When possible, the container orchestration process should incorporate scanning as one of the steps in the deployment pipeline. The 30-day scanning window begins as soon as the container is deployed to the production registry. Only containers from images that have been scanned within a 30-day vulnerability scanning window can be actively deployed on the production environment._

ECR can provide this for us with its [Image Scanning](https://docs.aws.amazon.com/AmazonECR/latest/userguide/image-scanning.html) functionality.  In addtion to scanning the image upon pushing it into the registry, it also supports continuous scanning with alerts should any OS or programming language vulnerabilities be found during a scan (alerts are sent via EventBridge).

#### Security Sensors

_If utilized, security sensors should be deployed everywhere containers execute to include within registries, as general-purpose sensors, and within CI/CD pipelines. If this approach is taken, the sampling guidance found in the [Guide for Determining Eligibility and Requirements for the Use of Sampling for Vulnerability Scans](https://www.fedramp.gov/assets/resources/documents/CSP_Vulnerability_Scan_Requirements_Using_Sampling.pdf) document may be applicable._

Security sensors are not required but are recommended according to the FedRAMP guidance.  We will have to research this separately and create a separate ADR for our approach to a security sensor solution.

#### Registry Monitoring

_The container registry must be monitored per unique image to ensure that containers corresponding to an image that has not been scanned within the 30-day vulnerability scanning window are not actively deployed on production._

From the [ECR Monitoring documentation](https://docs.aws.amazon.com/AmazonECR/latest/userguide/monitoring.html):

>ECR provides metrics based on your API usage for authorization, image push, and image pull actions.

Being able to monitor both push and pull actions for images will help us keep track of image usage.  Furthermore, the [enchanced scanning](https://docs.aws.amazon.com/AmazonECR/latest/userguide/image-scanning-enhanced.html) feature has extra support with the continuous scanning option that accounts for the following:

> When continuous scanning is enabled for a repository, if an image hasn't been updated in the past 30 days based on the image push timestamp, then continuous scanning is suspended for that image. Images with suspended scanning will show a scan status of SCAN_ELIGIBILITY_EXPIRED.

If we include checks in our image pulls to verify the scan status and make sure it's not `SCAN_ELIGIBILITY_EXPIRED`, we should be able to account for this requirement.

#### Asset Management and Inventory Reporting for Deployed Containers

_A unique asset identifier must be assigned to every class of image which corresponds to one or more production-deployed containers. These image-based asset identifiers must be documented in the [FedRAMP Integrated Inventory Workbook Template](https://www.fedramp.gov/assets/resources/templates/SSP-A13-FedRAMP-Integrated-Inventory-Workbook-Template.xlsx). Instances of production-deployed containers must be tracked internally by the CSP via an automated mechanism, which must be validated by a 3PAO to meet the baseline control CM-8. Every production-deployed container must correspond to the image from which the deployed container originated, in order to identify the total number of relevant vulnerabilities on production associated with that container._

We can accomplish this using tagging within ECR and assign each image a unique hash as an ID.  ECR also provides an option to [make tags immutable](https://docs.aws.amazon.com/AmazonECR/latest/userguide/image-tag-mutability.html), so they cannot be changed or overwritten once used.

Concourse provides ways for us to identify which image it pulled when it is deploying a container, which covers the tracking requirement.  We may need to build or configure a bit of extra reporting to be able to see this information at a glance instead of going into Concourse directly and manually looking at pipeline build history.


## Proposed Options

- [Scan and list](#scan-and-list)
- [SaaS registry with explicit push](#container-registry-saas-wexplicit-push)
- [cloud.gov registry with explicit push](#container-registry-run-our-own--explicit-push)
- [cloud.gov registry with passthrough](#container-registry-run-our-own--passthrough)

## Scan and list

In this option, we scan docker containers, then pull from Docker Hub by image hash.

We'd add one or more concourse pipelines that 
- pull images
- scan them using our to-be-identified image scanner
- if the image passes as usable, adds the image hash to a trusted list in a global store
- if the image has any findings, puts reports/summaries of those findings somewhere to be consumed by the team

Concourse pipelines that use images would need to reference images by _hash_ rather than _tag_

_Adding a new image looks like_

- add the image to the checker pipeline
- consume the SHAs from the checker 

_Updating an image version looks like_

- get a SHA from the image checker

_Revoking a scary version looks like_

- change SHAs wherever they're consumed

### Open questions

#### image tag parametrization
Can concourse use a variable from credhub as the image tag?

This is pretty key to how workable this solution is. If this works, this solution is _fairly_ low-lift.
If this doesn't work, this solution becomes very high-friction, especially if/when we have to revoke 
an image version.


### Pros

- low setup cost
- low operational cost
- no SCR needed?

### Cons
- if tag parametrization doesn't work, this is a pretty high-friction solution
- doesn't work well for non-concourse usage (which is currently low/zero, but could be an issue in the future)

## Container registry: SaaS w/explicit push

Here we use something like AWS Elastic Container Registry (ECR) as a container store. We configure
concourse (and other container-using-services) to use this registry instead of using docker hub.

We then scan images from other sources (e.g. Docker Hub) and upload them to the registry if they
pass our gates.


_Adding a new image looks like_

- Add image to scan-and-push pipeline

_Updating an image version looks like_

- handled by scan-and-push pipeline

_Revoking a scary version looks like_

- delete image from repository

### Pros

- low lift on concourse and other container runtimes (just tell them to pull from the registry)
- also lets us host images without any Docker Hub usage
- using a registry for all container pulls means we don't have to worry about forgetting to scan images
- low/no maintenance for registry

### Cons
- probably needs an SCR
- requires work up front to add a new image
- (depending on SaaS) might require acq for SaaS


## Container registry: run our own + explicit push

This is the same as above, but we run our own registry (e.g. Sonatype Nexus, Artifactory, docker registry)

Here we stand up a repository manager with BOSH and use that as our container store. We configure
concourse (and other container-using-services) to use this registry instead of using docker hub.

We then scan images from other sources (e.g. Docker Hub) and upload them to the registry if they
pass our gates.


_Adding a new image looks like_

- Add image to scan-and-push pipeline

_Updating an image version looks like_

- handled by scan-and-push pipeline

_Revoking a scary version looks like_

- delete image from repository

### Pros

- low lift on concourse and other container runtimes (just tell them to pull from the registry)
- also lets us host images without any Docker Hub usage
- using a registry for all container pulls means we don't have to worry about forgetting to scan images
- potentially useful for other resource types (npm, pypi, maven, etc, repos)
- high auditability for image usage

### Cons
- probably needs an SCR
- requires work up front to add a new image
- high maintenance for registry
- (depending on registry) might require acq for registry licence


## Container registry: run our own + passthrough

This is the same as above, but we allow pass-through on the registry

Here we stand up a repository manager with BOSH and use that as our container store. We configure
concourse (and other container-using-services) to use this registry instead of using docker hub.

We configure the repository manager to pull images on-demand, and add some process to scan images
post hoc.


_Adding a new image looks like_

- just start using it

_Updating an image version looks like_

- just keep using it

_Revoking a scary version looks like_

one of:
- add an explicit deny in the repository manager (not always supported)
- push or alias a new/safe image that shadows the bad one
- configure clients manually to skip the bad one 

### Pros

- low lift on concourse and other container runtimes (just tell them to pull from the registry)
- also lets us host images without any Docker Hub usage
- using a registry for all container pulls means we don't have to worry about forgetting to scan images
- potentially useful for other resource types (npm, pypi, maven, etc, repos)
- high auditability for image usage

### Cons
- probably needs an SCR
- high maintenance for registry
- potential for very insecure container to be used before being scanned
- (depending on registry) might require acq for registry licence
