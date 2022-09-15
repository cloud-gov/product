# Egress Control for tenants

## Why

Multiple users (most/all TTS users) have compliance findings for lacking egress control.
Effective egress control is important for users to prevent command-and-control, data
exfiltration, and supply-chain attacks.

## Background

Cloud Foundry provides firewall-like control via application security groups (ASGs). They
are allow-list only, and additive only (e.g. if you have an ASG allowing access to 8.8.8.8,
you cannot undo that allow with a further list). ASGs are bound either platform-wide or per-space
in two separate contexts: runtime and staging. Cloud Foundry allows only admins to create,
modify, and bind ASGs. We've currently applied a default ASG which
allows access to the services network (for RDS, etc) and all of the public internet.

## Proposal

### End-state

We should have 3 generally-available ASGs:
- `closed-gress`: allow nothing, which allows no access to anything outside the platform
- `public-egress`: the same as our current public networks ASG - that is, open access to the public internet
- `restricted-egress`: allows access to our services network (RDS, Elasticsearch, Redis, S3)

The global default ASG would be `closed-egress`. OrgManagers and SpaceManagers can request that we bind the
`public-egress` and/or `restricted-egress` ASGs to their spaces via support ticket. Users needing fine-grained
control would create a dedicated space to host a proxy (e.g. squidproxy) in. That space would have
the `public-egress` ASG bound. They'd then run their apps in their normal spaces with only the `closed-egress`
ASG bound, and allow access to the proxy app from their access-limited app via network policies.

We should provide a reference implementation so users can see how this all goes together.

In new orgs, we'll create 6 spaces by default (names TBD):
- `dev-open-egress`
- `dev-closed-egress`
- `staging-open-egress`
- `staging-closed-egress`
- `production-open-egress`
- `production-closed-egress`

The `*-closed-egress` spaces would have the platform default `closed-egress` and `restricted-egress`
ASGs bound to them, and users (SpaceManagers and OrgManagers) could have the `restricted-egress` removed via
support request.
The `*-open-egress` would have `closed-egress`, `restricted-egress`, and `public-egress` ASGs bound.

### Transition plan

Currently, our users expect all apps to have all access all the time. Because of this, the migration should look like:

1. Announce as loudly as possible
2. Create a new `public-egress` ASG
3. Create `closed-egress` and `restricted-egress` ASGs
4. Individually bind the new `public-egress` and `restricted-egress` ASGs to every currently-existing space
5. Set `closed-egress` ASG as platform default

### Acceptance tests

To improve our confidence through the transition and ongoing deployments, a test suite to verify space egress rules will be added to the cloudfoundry deployment. The initial test suite will deploy a CF app per unique space with endpoints to test egress access to `public-egress` and `restricted-egress`.

__Testing Matrix__

The following matrix will test three different endpoints across three different spaces. The following test spaces will be assigned theses application security groups: __`no-egress`__(`closed-egress`), __`closed-egress`__(`closed-egress` + `restricted-egress`), and __`open-egress`__(`closed-egress` + `restricted-egress` + `public-egress`). The root endpoint `/` tests the app's beign accessible via URL, the `/service-network` endpoint tests querying an internal cloud.gov service, and the `/public-network` endpoint tests querying an external API outside of cloud.gov.


The following table is the expected HTTP status codes for each endpoint based on the corresponding test space.

| |`no-egress`|`closed-egress`|`open-egress`|
|-|-----------|---------------|-------------|
|`/`|`200`|`200`|`200`|
|`/service-network`|`500`|`200`|`200`|
|`/public-network`|`500`|`500`|`200`|

These tests will run in each cloud.gov environment and should be passing before the deployment can be promoted to the next environment.

## Miscellany

- This plan should not be blocked by lack of a reference implementation since the option
  to bind the `public-egress` ASG allows users to get to the same state as we're in now,
  and we could potentially borrow a reference implementation from one of our users (with
  their permission, of course)
- Sandboxes should have access to the `public-egress` ASG for staging by default. We should
  determine whether or not they should have access to it at runtime.
- Users could (should?) use credentialed proxies, with unique creds per application.
  This would allow users to disable outbound traffic on a suspected-compromised app
- After we have ASGs and reference implementations in place, we could conceivably
  make a broker that creates/manages proxies for users
- This solution probably only solves access to HTTP(S)

## Addenda

### s3 egress in restricted ASG

To simplify client accessibility for S3 we have added s3 access in the restricted ASG.
- We accomplished this by leveraging a private endpoint for s3 in each VPC and setting a policy that allows access to buckets by users belonging to a list of accounts (ie the AWS accounts owned by cloud.gov)
  - `cg-provision` contains the policy creation and outputs the IP ranges and VPC dns names
  - [cg-deploy-cf](https://github.com/cloud-gov/cg-deploy-cf) contains changes to the ASGs to include the IP ranges and DNS names output by cg-provision
  - the VPCs in AWS each contain a pair of S3 private endpoints ( gateway and singular) for access to S3 over the AWS internal network. 
- Clients wanting to access their own buckets not provisioned by service broker, must still use public ASG or a proxy to a public ASG. 
  - buckets that exist in other regions from the cloud.gov current production region ( `us-gov-west-1` ) can be accessed transparently with standard API endpoints
  - buckets that exist in the same region as cloud.gov production will need to use an alternate endpoint that is created by our Terraform: `*.vpce-01beaa66570dfb2b9-1hlav4x8.s3.us-gov-west-1.vpce.amazonaws.com`. This is due to the fact that private endpoints are regional in AWS and hence by default all traffic to S3 buckets in `us-gov-west-1` will have the implemented policy applied. 
  
