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
- deny_all: allow nothing, which allows no access to anything at all
- public_networks: the same as our current public networks ASG - that is, open access to the public internet
- services_network: allows access to our services network (RDS, Elasticsearch, Redis)

The global default ASG would be deny_all. OrgManagers and SpaceManagers can request that we bind the
public_networks and/or services_network ASGs to their spaces via support ticket. Users needing fine-grained
control would create a dedicated space to host a proxy (e.g. squidproxy) in. That space would have
the public_networks ASG bound. They'd then run their apps in their normal spaces with only the deny_all 
ASG bound, and allow access to the proxy app from their access-limited app via network policies.

We should provide a reference implementation so users can see how this all goes together.

In new orgs, we'll create 6 spaces by default (names TBD):
- dev-open-egress
- dev-closed-egress
- staging-open-egress
- staging-closed-egress
- production-open-egress
- production-closed-egress

### Transition plan

Currently, our users expect all apps to have all access all the time. Because of this, the migration should look like:

1. Announce as loudly as possible
2. Create a new public_network ASG
3. Create deny_all and services_network ASGs
4. Individually bind the new public_networks and services_network ASGs to every currently-existing space
5. Set deny_all ASG as platform default

## Miscellany

- This plan should not be blocked by lack of a reference implementation since the option
  to bind the public_networks ASG allows users to get to the same state as we're in now,
  and we could potentially borrow a reference implementation from one of our users (with
  their permission, of course)
- Sandboxes should have access to the public_networks ASG for staging by default. We should
  determine whether or not they should have access to it at runtime.
- Users could (should?) use credentialed proxies, with unique creds per application.
  This would allow users to disable outbound traffic on a suspected-compromised app
- After we have ASGs and reference implementations in place, we could conceivably
  make a broker that creates/manages proxies for users
- This solution probably only solves access to HTTP(S)
