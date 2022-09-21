# Passive DNS

## What is Passive DNS?

DNS is one of the core building blocks of the Internet. The fundamental purpose of DNS is to translate domain names (e.g. `google.com`) to resources (e.g. IP addresses) so that traffic can be routed to the correct resources to handle the requests.

One of the key benefits of DNS is de-coupling: a DNS record is just a pointer to another resource, meaning that resource can change **without having to change the DNS record name**. Thus, whoever manages the DNS records for `google.com` can transparently change it to point to a new IP and new backend infrastructure without any end-user impact.

DNS is **dynamic** by nature, meaning that the resource address for a DNS record is looked up when you request it, though there are several caching layers built-in to the process for performance benefits. The downside of the dynamic nature of DNS is the inability to track how the resolution of DNS records has changed over time, among other things.

In order to gain more insight into , ?

the concept of ["Passive DNS replication" was introduced by Florian Weimer](https://www.enyo.de/fw/software/dnslogger/first2005-paper.pdf).

Generally, Passive DNS refers to keeping historical records of how DNS queries are answered and resolved.

The benefits of passive DNS include:

- security
  - identifying DNS records have been repointed to malicious resources
  - identifying outgoing DNS traffic to malicious resources
- administrative
  - having clear records of how the use of DNS records has changed over time

## Why do we care?

## Implementation

### Options

### Recommendation