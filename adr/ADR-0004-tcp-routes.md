# TCP Routing

## Why

Users have requested this for various reasons, but the most common is that they
want to offer PIV/CAC authentication without relying on external services. PIV 
authentication requires TLS termination by the PIV application, so terminating
HTTPS at the router does not work for this use case.

## Challenges

### Incompatibility with mTLS

Currently, we have mTLS configured between the gorouters and diego cells. Cloud
Foundry doesn't differentiate TCP routes from HTTPS routes in that configuration,
so having mTLS and TCP routes are mutually exclusive. We can work around this by 
having an isolation segment dedicated to tcp routes and a dedicated set of gorouters
as well.

### Scarce Shared Resource

Because TCP routes don't consider names in their routing decision, the number of
available routes is much smaller, and much more difficult to increase. We can combat
this primarily with quotas and pricing. By charging appropriately for TCP routes, we
recover the cost of scaling and disincentivise misuse.

## The Plan

### Architecture

We'll add
- one AWS NLB 
- three gorouters
- five diego cells 

The new diego cells will be in a new isolation segment, and the new gorouters will 
be dedicated to that segment, with the AWS NLB in front of them.

### Usage

Isolation segments are _allowed/disallowed_ at an organization level and _assigned_ 
on a space level, so an organization can have many isolation segments mapped to it, 
but a space is mapped to exactly one isolation segment.

By default, nobody should have access to this isolation segment. When customers are
onboarded to the isolation segment, they should be strongly cautioned about the lack
of TLS enforcement and potential compliance implications. They should create one or
more spaces on the tcp isolation segment. We should advise that only applications
requiring direct TCP access be run in the space, and that applications within those 
spaces should have TLS termination. 

### Pricing

We should have a setup fee to recover our time spent configuring access, and a
recurring monthly fee to recover our maintenance, monitoring, and infrastructure/AWS
costs. This fee should include a (to be determined) number of routes (each route 
corresponds to one port). Additional routes should be available for an additional
monthly cost, but without an additional setup fee.


## Other Considerations

### Open questions

- how many routes come in a pack? Three should allow for dev, stage, and production, 
  assuming apps that require only one route each
- what is an appropriate cost? Consider:
  - the time we spend implementing this (setup fee)
  - the time and cost of SCR/3PAO assessment (setup fee)
  - the increased maintenance of a more complex system (maintenance fee)
  - the infrastructure costs (maintenance fee)
- can/should we run any enforcement of TCP routes only in the new isolation segment?
- can/should we run any checks for TLS on TCP routes?

### Scaling

Adding isolation segments complicates our scaling considerations. This highlights
that we should have a better story around scaling up _and down_ as conditions change.
This shouldn't be a blocker for implementation, but we should be mindful of this and 
address it soon. Autoscaling would be nice, but we should start with setting some 
service level objectives and correlating them to components.