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
- `internal_only`: allow nothing, which allows no access to anything outside the platform
- `public_networks`: the same as our current public networks ASG - that is, open access to the public internet
- `services_network`: allows access to our services network (RDS, Elasticsearch, Redis)

The global default ASG would be `internal_only`. OrgManagers and SpaceManagers can request that we bind the
`public_networks` and/or `services_network` ASGs to their spaces via support ticket. Users needing fine-grained
control would create a dedicated space to host a proxy (e.g. squidproxy) in. That space would have
the `public_networks` ASG bound. They'd then run their apps in their normal spaces with only the `internal_only`
ASG bound, and allow access to the proxy app from their access-limited app via network policies.

We should provide a reference implementation so users can see how this all goes together.

In new orgs, we'll create 6 spaces by default (names TBD):
- `dev-open-egress`
- `dev-closed-egress`
- `staging-open-egress`
- `staging-closed-egress`
- `production-open-egress`
- `production-closed-egress`

The `*-closed-egress` spaces would have the platform default `internal_only` and `services_network`
ASGs bound to them, and users (SpaceManagers and OrgManagers) could have the `services_network` removed via
support request.
The `*-open-egress` would have `internal_only`, `services_network`, and `public_networks` ASGs bound.

### Transition plan

Currently, our users expect all apps to have all access all the time. Because of this, the migration should look like:

1. Announce as loudly as possible
2. Create a new `public_networks` ASG
3. Create `internal_only` and `services_network` ASGs
4. Individually bind the new `public_networks` and `services_network` ASGs to every currently-existing space
5. Set `internal_only` ASG as platform default

### Acceptance tests

To improve our confidence through the transition and ongoing deployments, a test suite to verify space egress rules will be added to the cloudfoundry deployment. The initial test suite will deploy a CF app per unique space with endpoints to test egress access to `public_networks` and `services_network`.

__Testing Matrix__

The following matrix will test three different endpoints across three different spaces. The following test spaces will be assigned theses application security groups: __`no-egress`__(`internal_only`), __`closed-egress`__(`internal_only` + `services_network`), and __`open-egress`__(`internal_only` + `services_network` + `public_networks`). The root endpoint `/` tests the app's beign accessible via URL, the `/service-network` endpoint tests querying an internal cloud.gov service, and the `/public-network` endpoint tests querying an external API outside of cloud.gov.


The following table is the expected HTTP status codes for each endpoint based on the corresponding test space.

| |`no-egress`|`closed-egress`|`open-egress`|
|-|-----------|---------------|-------------|
|`/`|`200`|`200`|`200`|
|`/service-network`|`500`|`200`|`200`|
|`/public-network`|`500`|`500`|`200`|

These tests will run in each cloud.gov environment and should be passing before the deployment can be promoted to the next environment.

## Miscellany

- This plan should not be blocked by lack of a reference implementation since the option
  to bind the `public_networks` ASG allows users to get to the same state as we're in now,
  and we could potentially borrow a reference implementation from one of our users (with
  their permission, of course)
- Sandboxes should have access to the `public_networks` ASG for staging by default. We should
  determine whether or not they should have access to it at runtime.
- Users could (should?) use credentialed proxies, with unique creds per application.
  This would allow users to disable outbound traffic on a suspected-compromised app
- After we have ASGs and reference implementations in place, we could conceivably
  make a broker that creates/manages proxies for users
- This solution probably only solves access to HTTP(S)
