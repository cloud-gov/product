# Passive DNS

## Background on DNS

DNS is one of the core building blocks of the Internet. The fundamental purpose of DNS is to translate domain names (e.g. `google.com`) to resources (e.g. IP addresses) so that traffic can be routed to the correct resources to handle the requests.

One of the useful features of DNS is de-coupling: a DNS record is just a pointer to another resource, meaning that resource can change **without having to change the DNS record name**. Thus, whoever manages the DNS records for `google.com` can transparently change it to point to a new IP and new backend infrastructure, but the end-user gets the same experience of accessing `google.com`.

DNS is **dynamic** by nature, meaning that the resource address for a DNS record is looked up when you request it, though there are several caching layers built-in to the process for performance benefits. The downside of the dynamic nature of DNS is the inability to track how the resolution of DNS records has changed over time, among other things.

## What is Passive DNS?

Generally, "Passive DNS" refers to keeping historical records of how DNS queries are answered and resolved. It originated with the concept of ["Passive DNS replication" was introduced by Florian Weimer](https://www.enyo.de/fw/software/dnslogger/first2005-paper.pdf).

The benefits of passive DNS include:

- keeping track of how DNS records have changed over time
- identifying when DNS records have been repointed to malicious resources
- identifying DNS traffic to malicious resources

## Why do we care?

Our initial investigation into passive DNS was as a requirement of [Executive Order M-21-31](https://www.whitehouse.gov/wp-content/uploads/2021/08/M-21-31-Improving-the-Federal-Governments-Investigative-and-Remediation-Capabilities-Related-to-Cybersecurity-Incidents.pdf), as seen in [the research spike ticket](https://github.com/cloud-gov/product/issues/2153).

Beyond meeting compliance requirements, we are mostly concerned with the security and threat intelligence benefits of passive DNS. In particular, being able to identify DNS queries to malicious resources will greatly enhance our threat detection and remediation capabilities.

## Implementation options

All of our DNS records are managed using the [AWS Route53 service](https://aws.amazon.com/route53/).

Route53 has two features that support passive DNS:

- [Public DNS query logging](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/query-logs.html)
  - Logs all public DNS queries to your zones
- [DNS resolver query logging](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-query-logs.html)
  - Logs all DNS queries emanating from within specified VPCs

Public DNS query logging:

- does not include information about the resolution for a DNS query
- does include information about the request origin **in some cases**

From a security perspective, public DNS query logging could be useful for identifying outsider threats.

DNS resolver query logging includes much more information, including:

- the origin of the request (e.g. VPC, instance ID of resource)
- DNS response data (e.g. IP address for domain)
- whether a DNS firewall rule was triggered

The main caveat here is that resolver query logging only operates on queries from within specified VPCs, so from a security perspective it is useful for identifying insider threats.

## Recommendation

We should enable DNS resolver query logging in all of our environments because:

- DNS resolver query logging includes much more information and can help us achieve partial compliance with M-21-31
- Identifying insider threats is very valuable from a security perspective since we can take action to decommission or to quarantine compromised infrastructure

We should not enable public DNS query logging because the logs are limited in scope and utility. In theory, we could use the logs to identify malicious actors and target them with firewall rules, but in practice this is difficult given the lack of guarantee about request source information in the logs.

## Technical implementation

We should send the [resolver query logs to S3](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver-query-logs-choosing-target-resource.html). In keeping with M-21-31 guidance, we should keep these logs for 30 months, but after 12 months we can send them to a lower-cost, infrequent access storage tier.

From S3 we should ingest these logs into our platform logs system, which is currently built on the ELK stack. We will probably have to write a custom Logstash ingestor to handle ingesting these logs. Once the logs are ingested into Elasticsearch, they will be easily searchable in Kibana.