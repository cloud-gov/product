---
title: Federal Zero Trust Strategy - Public Comment from cloud.gov
---

# Federal Zero Trust Strategy


Thank you for this opportunity to respond to OMB's [Zero Trust Strategy - DRAFT](https://zerotrust.cyber.gov/downloads/Office%20of%20Management%20and%20Budget%20-%20Federal%20Zero%20Trust%20Strategy%20-%20DRAFT%20For%20Public%20Comment%20-%202021-09-07.pdf).

We're writing to provide the insights that come from operating TTS/GSA's [cloud.gov](https://cloud.gov), a multi-agency, multi-tenant Platform-as-a-Service (PaaS). These comments do not reflect the position of the General Service Administration (GSA) or the Technology Transformation Sevices (TTS)


Our comments reference the page numbers of the PDF.


Page 3, "**Required Actions**"

* This strategy lists 19 actions, but has only listed 1 (phishing-resistant verifiers) as the top priority.  For the other 18, unless OMB wants none of them complete for another 3 years, OMB should designate priority tiers. The nation's cybersecurity needs will be best met if the highest value actions are completed sooner, and lower value actions later.  

  If OMB cannot prioritize on behalf of agencies, then OMB should direct agencies to adopt a prioritization process, e.g. CD3 ([Cost of Delay Divided by Duration](https://blackswanfarming.com/cost-of-delay-divided-by-duration/)), and direct them to complete first the actions that provide the highest value, in the least time, before moving on to other actions. OMB would need to provide a means for determining the "protection value" for each action to support such agency-specific prioritization.

Page 4: "Agencies should re-prioritize funding in FY22 to achieve priority goals, or seek funding from alternative sources"

* We laud the purpose and goals of this plan, but achieving this vision will necessarily require de-prioritizing other goals, including those goals laid out in other OMB mandates. Budgeting is one issue, but a key limiting factor is the availability of qualified practitioners. Filling security and operations roles or hiring qualified contractors is already a significant challenge.  We can't likely meet these goals, and better secure our assets, unless OMB specifically de-prioritizes other work.  We recommend that OMB scale back IPv6 adoption mandates and reduce the scope of DNSSEC adoption so our resources can be focussed on the high-value activities this strategy lays out.

Page 9: "CISA will identify or make available to agencies one or more services to privately compare user passwords against known-weak and known-breached data"

* To facilitate adoption, this CISA service should be made available to FedRAMP-authorized (or FedRAMP-in-process) CSPs. That would enable CSPs to provide these checks as an inherited control.  FedRAMP currently requires that JAB-Authorized CSPs only use other JAB-authorized external services. OMB should direct FedRAMP to allow CISA-provided external services within a CSP Authorization Boundary when it's in the national interest.

Page 9: "agencies should proactively reset passwords for privileged accounts to ensure that they have been checked."

* This wording is confusing. Perhaps:
  > agencies should reset passwords for sensitive accounts as soon as a service for checking new passwords against known passwords is available.

Page 12: "Agencies must resolve DNS queries using encrypted DNS wherever it is technically supported."

* For encrypted DNS, OMB should specifically authorize use of "commercial-quality encryption" pending broad availability of FIPS 140-validated cryptography in this space.

Page 12: "CISA’s Protective DNS offering will support encrypted DNS communication, and will scale to accommodate use from agency cloud infrastructure and mobile endpoints."

* CISA and FedRAMP should work to allow CSPs providing government-only services to provide Protective DNS as an inheritable control. Broadening use of Protective DNS to CSPs will speed adoption.  For workloads that are not on-premises or IaaS, Protective DNS can only practically be provided by the cloud-provider. This should be allowed and supported.

Page 12: Encrypting HTTP traffic

* Since DNSSEC, if adopted, will not be of value to the general public using HTTPS for accessing .gov sites, agencies should monitor certificate transparency (CT) logs for any misuse of their domain names by certificate authorities.
To support that, CISA should establish CT monitoring and alerting services for the .gov domain. This service should also be available to government CSPs, and be authorized for use by FedRAMP as an external service. 

Page 13: Agencies must enforce HTTPS for all production HTTP traffic

* For encrypted HTTPS, OMB should specifically authorize use of "commercial-quality encryption" pending broad availability of FIPS 140-validated cryptography for low-sensitivity or public data.


Page 14: an end state where every distinct application they run is in its own separate network environment

* The current wording would seem to imply that high-level PaaSes, like cloud.gov, would no longer be acceptable. This would be a net negative, as we should instead be encouraging use of platforms that provide a high-level of inheritance of security controls.  We suggest that this be amended to include: 
  > or, in multi-tenant environments, is operated with secure tenant isolation through features such as overlay networks and mutual authentication

Page 22: Agencies must reach the first incident logging maturity level (IL1) as described in Memorandum M-21-31

* There is no IL1 in M-21-31, but there is "EL1: Event Logging Tier 1"

* The full web application packet capture will likely be a significant burden to access and disentangle for agencies making use of multi-tenant SaaS and PaaS clouds.  OMB and CISA and FedRAMP should work with CSPs on capturing and managing such data to support the overall goals, and not leave it it each agency to re-implement multiple times, or be unable to comply.



Peter Burkholder, cloud.gov Compliance and Security Lead

Lindsay M Young, cloud.gov Director (Acting)

