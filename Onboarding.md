# Joining the cloud.gov team

cloud.gov helps government teams attack core impediments to smooth, iterative deployment of government services, including compliance, security, and scalability. The cloud.gov team develops, operates, and supports cloud.gov so that we can offer it to agencies as a service they can use on their own.

## Onboarding

Get through [the 18F onboarding guide for your discipline](https://handbook.18f.gov/#teams) first. (Contractors, we're presuming you have an equivalent process you've gone through for onboarding with your employer.)

Everyone joining the cloud.gov team will get assigned a team onboarding buddy. This person should be working on similar things to what you will be working on, so that they can answer questions in your domain.

You and your team onboarding buddy must follow the instructions in [the Onboarding Checklist](https://github.com/18F/cg-product/blob/master/OnboardingChecklist.md) to create an issue that will guide you through tasks that will get you up to speed and contributing in no time. You (and your buddy) must track your progress by checking the boxes as you complete tasks.

Our Onboarding Checklist helps us fulfill important security and compliance requirements, so each new team member needs to have their own checklist GitHub issue and track their progress. This is true even if you're rejoining the cloud.gov team after being in it previously.

## How to Tock your time

We use four lines in Tock to track our hours worked:

* cloud.gov - operations and services (Atlas & Agent Q)
* cloud.gov - UI/UX (Navigator)
* cloud.gov - business / comms (Skyporter)
* cloud.gov - compliance (Highbar)

Our guideline: if the work you’re doing was driven by a story with a label, Tock to the line corresponding to that label.

Program-level work, such as program-level stand-up and sprint review meetings, should be tocked to Skyporter.

## Tools and project artifacts

Whenever possible, we err on the side of putting data where the public can see it. Some data might be kept in Google Drive for convenience of presentation, commenting, etc. but we consider public GitHub repositories the intended destination whenever possible.

Several tools are used for project management, but the main one you will probably be using is GitHub, with the addition of the [ZenHub](https://zenhub.io) browser extension to add inline kanban boards, hierarchical issues, and burndown charts. 

We also use [Aha!](https://18f.aha.io) for macro-level cadence and roadmapping. In many cases, Aha! artifacts are linked to GitHub issues. Stories and features are tracked one per issue. Feature issues act as parents for others, tracking the macro-status of a related body of work. Please try to parent new/split tactical issues created in GitHub onto Feature issues whenever appropriate so that the relationship is clear, and the remaining work involved in higher-level milestones can be recognized properly upstream.

We also have some boards still in [Trello](https://trello.com/), although many of these are migrating to GitHub/ZenHub. In general, the structure of Trello boards and ZenHub boards is very similar.

## Security/compliance context

As a service offered to other federal agencies, cloud.gov must hold itself to a rigorous security standard in both our technical work and our team operations. We follow a formal set of security requirements as part of our FedRAMP P-ATO process. (FedRAMP is a GSA-run program that assesses cloud services for government use, and we participate in this program.)

This means we have additional team rules on top of your standard 18F team rules. Your onboarding checklist will introduce you to them! Also here are bits of additional compliance guidance:

* When you log into our cloud.gov CLI or dashboard for cloud.gov work, such as to work on a component that sits on cloud.gov as an application (for example the dashboard or the website), and GSA SecureAuth prompts you for multi-factor authentication (MFA), pick an MFA option that isn't email — use the phone/text/app MFA option. This helps us comply with our FedRAMP requirements.

## Things we maintain

- cloud.gov as a platform
  - our Cloud Foundry instance
  - [The Dashboard](https://dashboard.cloud.gov)
  - [The cloud.gov homepage](https://cloud.gov/)
  - [docs.cloud.gov](https://docs.cloud.gov)
- All [cloud.gov repositories](https://docs.cloud.gov/ops/repos/)
  - Any repositories under [github.com/18F](https://github.com/18F/) with the prefix [`cg-*`](https://github.com/18f?utf8=%E2%9C%93&query=cg-) ("cloud.gov") or [`cf-*`](https://github.com/18f?utf8=%E2%9C%93&query=cf-) ("Cloud Foundry")
  - [Compliance Toolkit](https://github.com/18F/compliance-toolkit/)
  - [Compliance Masonry](https://github.com/opencontrol/compliance-masonry)
- a [Google Drive folder](https://drive.google.com/a/gsa.gov/folderview?id=0Bx6EvBXVDWwheUtVckVnOE1pRzA&usp=sharing) full of artifacts related to design, user research, etc (also expected to move to GitHub in time)
- our [soon-to-be-legacy Trello board](https://trello.com/b/ChGzyepo/gov-dev)
- A high-level overview of how we (ideally) do horizon planning in [Murally](http://mur.al/bklqnALZ)
- A very broad story map capturing how we conceptualize the user experience on [Stories on Board](https://18f.storiesonboard.com/m/gov-dev)
- [The cloud.gov support Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov-support), where we currently wrangle inquiries from various agencies, and some support.

We liberally make upstream pull requests for stuff we use. We try to transfer broadly-useful Cloud Foundry-related projects to [the Cloud Foundry community GitHub organization](https://github.com/cloudfoundry-community/). We also try to move others to the [opencontrol](https://github.com/opencontrol) or [fisma-ready](https://github.com/fisma-ready) GitHub organizations whenever appropriate. 

To release: `ci.cloud.gov -> deploy-cf project`

## Important terminology and context

- Amazon Web Services (AWS) – the infrastructure (IaaS) provider we use.
- Authority to Operate (ATO) - approval from an agency's Authorizing Official to run a digital service under FISMA.
- Azure – Microsoft's PaaS. They are regular contributors to various cloud.gov components.
- BOSH (rhymes with "squash") – the configuration/server management tool we use to run Cloud Foundry. Basically, it's what keeps the platform running.
- BOSH Lite – [https://github.com/cloudfoundry/bosh-lite](https://github.com/cloudfoundry/bosh-lite)
- cloud.gov ("cloud dot gov").
- CF – Cloud Foundry.
- CFT – Cloud Formation Templates.
- CenturyLink – a company that contributes heavily to Cloud Foundry, and runs their own Cloud Foundry-based PaaS, [AppFog](https://www.ctl.io/appfog/).
- Cloud Foundry – [Cloud Foundry](https://www.cloudfoundry.org/) is the open-source the platform-as-a-service that cloud.gov is built on.
- Concourse – [Concourse](https://concourse.ci) is the continuous integration tool built by Pivotal we use to deploy Cloud Foundry, among other things.
- The Dashboard – the web app we offer to allow users to manage their applications and accounts. It lives at [dashboard.cloud.gov](https://dashboard.cloud.gov/), and the code is in the [cg-dashboard](https://github.com/18F/cg-dashboard) repository.
- Elastic Load Balancing (ELB) – the proxy we use in front of Cloud Foundry. [More info](https://aws.amazon.com/elasticloadbalancing/)
- [FedRAMP](https://www.fedramp.gov/) - a program whereby which Cloud Service Providers (CSPs) are rigorously examined for compliance with FISMA before being identified as generally fit for use by all government agencies.
- [FISMA](https://en.wikipedia.org/wiki/Federal_Information_Security_Management_Act_of_2002) - The federal law that governs digital service delivery in the federal government.
- [FISMA-Ready](https://github.com/fisma-ready) - A repository of hardened configurations for common open source infrastucture, suitable for incorporation into a digital service.
- IaaS – infrastructure as a service. We use Amazon Web Services.
- IBM Bluemix – IBM's hosted version of Cloud Foundry.
- InfoSec – information security.
- PaaS – platform as a service. We use Cloud Foundry to make cloud.gov's PaaS.
- Pivotal – the company that originally started Cloud Foundry.
- Pivotal Web Services – Pivotal's hosted commercial version of Cloud Foundry.
- UAA - UAA is the authentication and authorization hub for Cloud Foundry. It can  delegate identity management via LDAP/AD, SAML, OAuth/OpenID Connect and so forth. UAA is deployed as part of cloud.gov. We use the out of the box install, with some stuff specific to [our own release](https://github.com/18F/cg-cf-release/tree/master/src).

Also see [the Cloud Foundry glossary](http://docs.cloudfoundry.org/concepts/glossary.html) for  terms that are specific to the technology powering our platform. 
