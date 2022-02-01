# Static IP for user apps

## Why

Users have asked for static IP addressing for some time. In most cases, we're able to provide sufficient
workarounds for them, but there are some cases where a user can't work around this need. The main use 
case is a user who wants to support their users browsing to their apex domain. This is currently impossible
for most users because AWS Application Load Balancers have dynamic IP addresses, so they can't create A or 
AAAA records pointing to them, and they can't create CNAME records because the CNAME specification does not
support apex records.

## Background

Our current custom domain support without CDNs is through the external-domain and custom-domains brokers 
which share a set of AWS Application Load Balancers. Users then create CNAME records pointing to the ALBs


## Proposal

We should support static IP addressing for custom domains on ALBs. We'll do this by:
- adding one NLB each in front of our existing ALBs
- updating the external domain broker to not reselect ALBs when it rotates certificates
- updating the external domain broker to not reselect ALBs when it makes other updates
- updating the external domain broker to emit the static IPs of the NLBs when provisioning is complete

The user process for using this looks like:
1. Decide on a hostname (in our example, myapp.agency.gov)
1. Create the cf domain 
   `cf create-private-domain myapp.agency.gov`
1. Push an app with that domain as a route
1. Create the domain service instance
   `cf create-service external-domain domain my-domain -p '{"domains": ["myapp.agency.gov"]}'`
1. Wait for domain to finish provisioning
1. (exact process to be determined) interact with CF to get the associated static IPs
1. using the agency's DNS provider, create A and AAAA records for myapp.agency.gov pointing to the ip addresses from 6

## Open Questions

- How do we get the static IP to users? I _think_ CAPI's implementation of the OSBAPI only allows passing 
  information back to the user via `LastOperation` or service keys, but we should test if there are other
  ways (e.g. [service instance metadata](https://github.com/openservicebrokerapi/servicebroker/blob/v2.16/spec.md?plain=1#L1018))
- This means we're no longer assuming we can rely on the intermediate *.external-domains-production.cloud.gov
  addresses - where do we rely on that assumption currently, other than rebalancing ALBs?

## Miscellany

- We should *not* support this on the normal apps ALB (e.g. app.cloud.gov), since that's really intended for 
  the kinds of prototyping that shouldn't need static IPs
- one of the main groups requesting this is Federalist users. For them (and others looking for static IPs
  and cloudfront) we should be suggesting they run a redirect app at the static IP/apex and run their CDN
  on a non-apex domain using ALIAS or CNAME records
