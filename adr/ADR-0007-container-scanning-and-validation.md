# Container Scanning & Validation

## What we need

We need to scan containers we use so we can track issues with security, compliance, and best practices.

### Goals:

These are the important goals to keep in mind while selecting an implementation path:
- minimize developer friction when adding or updating containers
- prevent major CVEs from entering our network
- provide visibility into less severe issues, so we can iterate on them
- provide a stable, compliant solution

### Scope

We need to ensure we're scanning containers used in-boundary. Currently, this means:

- concourse resources

## Options

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
