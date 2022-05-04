# Opensearch For Logging

## Why

The existing Logsearch package is difficult to maintain securely, and lacks support. 

## Background

Right now we're the owners of the filtering authentication plugin used on logsearch-for-cloudfoundry. It works via query injection, but that's a coarse way to do this. We have had incidents in the past and FedRAMP has asked that we resolve this. We are also up against Elastic's licensing restrictions for newer versions of ES.

By switching to Opensearch we can remove our bespoke filter and use the supported filtering in the upstream auth plugin, which is better tested and used by a large community. We can also stay open source and avoid procurement/budget hassles.

Opensearch includes several other plugins which add nice features which we may want to explicitly turn on or off, but the purpose of this work is just to resolve the tension around the difficulty of maintenance and obstacles to smooth, routine upgrades.


## Proposal

We want to replace the existing community-supported logsearch-boshrelease and logsearch-for-cloudfoundry-boshrelease with 
a new bosh release based on Opensearch leveraging Opensearch's document-level security along with an authentication proxy to provide more robust tenant isolation.

Intended notable changes from existing release:
- leverage Opensearch document-level security
- move from index-per-day to index-per-org-per-day for tenant logs
- mTLS by default (for zero-trust)
- use openJDK for anything java (so we can patch faster)

Features we need to make sure we maintain:
- user-created dashboards (ideally with better tenant isolation)
- export to CSV

We do _not_ want to provide a direct migration path between these. We intend to migrate by importing logs from S3 into a new
cluster, maintaining both during a user transition period, then sunsetting the original.

We intend to offer some of the other features of ODfE in the future, such as alerting and anomaly detection, but these are not
part of the initial launch. 

## Open Questions

- given that we build our bosh releases all funny, how do we make this community-friendly within our approved processes?
- will this _just work_ with the prometheus bosh release, or will we need to make changes there too?
- does the rest of the community care about platform logs, tenant logs, or both?
- can we limit complexity of JSON log input


## Future improvements we'd like to see

- internal alerting around log parse failures for when CF provides new log formats
- alerting plugin for platform/internal use
- alerting plugin for tenant use

