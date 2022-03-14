# Joining the cloud.gov team

cloud.gov helps government teams attack core impediments to smooth, iterative deployment of government services, including compliance, security, and scalability. The cloud.gov team develops, operates, and supports cloud.gov so that we can offer it to agencies as a service they can use on their own.

## Instructions

When someone new joins the cloud.gov team:

1. The System Owner (Director or Deputy Director) creates a new issue in the [cg-product Github repo](https://github.com/cloud-gov/product/issues) called "Authorize Onboarding for [NewPerson]".  This constitutes 'formal approval' by leadership.
  - The System Owner must do this step. An assignee can add the checklist afterward if the System Owner hasn't already.
  - Use of an issue that only the System Owner is authorized to create before onboarding can proceed helps us satisfy the AC-2 control.
2. The cloud.gov Director or Deputy Director adds the new team member to the `cloud-gov` team in GitHub.
3. The System Owner or an assignee creates a new issue in the [cg-product Github repo](https://github.com/cloud-gov/product/issues) called `System Owner Authorization for Onboarding a New Team Member`
4. The System Owner or the person who bravely volunteered to be the new person's Onboarding Buddy can then proceed to create the onboarding checklist issue for the new person
5. Put the onboarding checklist issue into the _Doing_ column in our [project board](https://github.com/orgs/cloud-gov/projects/2).

## Onboarding

Review the [Getting started at TTS guide](https://handbook.tts.gsa.gov/getting-started/) first. (Contractors, we're presuming you have an equivalent process you've gone through for onboarding with your employer.)

Everyone joining the cloud.gov team will get assigned a team onboarding buddy. This person should be working on similar things to what you will be working on, so that they can answer questions in your domain.

You and your team onboarding buddy must follow the instructions in your onboarding issue that will guide you through tasks that will get you up to speed and contributing in no time. You (and your buddy) must track your progress by checking the boxes as you complete tasks.

Our onboarding checklists help us fulfill important security and compliance requirements, so each new team member needs to have their own checklist in our issue-tracker to document their progress. This is true even if you're rejoining the cloud.gov team after being in it previously.

## Tools and project artifacts

Whenever possible, we err on the side of putting data where the public can see it. Some data might be kept in Google Drive for convenience of presentation, commenting, etc. but we consider public GitHub repositories the intended destination whenever possible.

Several tools are used for project management, but the main one you will probably be using is GitHub to submit and merge pull requests and GitHub Project boards for tracking in-flight work.

## Security/compliance context

As a service offered to other federal agencies, cloud.gov must hold itself to a rigorous security standard in both our technical work and our team operations. We follow a formal set of security requirements as part of our FedRAMP P-ATO process. ([FedRAMP](https://www.fedramp.gov/) is a GSA-run program that assesses cloud services for government use, and we participate in this program.)

* When you log into our cloud.gov CLI or dashboard for cloud.gov work, such as to work on a component that sits on cloud.gov as an application (for example the dashboard or the website), and GSA SecureAuth prompts you for multi-factor authentication (MFA), pick an MFA option that isn't email — use the phone/text/app MFA option. This helps us comply with our FedRAMP requirements.

## Things we maintain

- cloud.gov as a platform
  - our Cloud Foundry instance
  - [The Dashboard](https://dashboard.fr.cloud.gov)
  - [The cloud.gov homepage and docs](https://cloud.gov/)
- All [cloud.gov repositories](https://cloud.gov/docs/ops/repos/)
  - Repositories in the [cloud-gov Github organization](https://github.com/cloud-gov).
- a [Google Drive folder](https://drive.google.com/a/gsa.gov/folderview?id=0Bx6EvBXVDWwheUtVckVnOE1pRzA&usp=sharing) full of artifacts related to design, user research, etc (also expected to move to GitHub in time)
- [The cloud.gov support Google Group](https://groups.google.com/a/gsa.gov/forum/?hl=en#!forum/cloud-gov-support), where we currently wrangle inquiries from various agencies, and some support.

We liberally make upstream pull requests for stuff we use. We try to transfer broadly-useful Cloud Foundry-related projects to [the Cloud Foundry community GitHub organization](https://github.com/cloudfoundry-community/). 

## Important terminology and context

- Amazon Web Services (AWS) – the infrastructure (IaaS) provider we use.
- Authority to Operate (ATO) - approval from an agency's Authorizing Official to run a digital service under FISMA.
- Azure – Microsoft's IaaS. They are regular contributors to various cloud.gov components.
- Azure App Service - Microsoft's PaaS offering, built on top of their IaaS.
- BOSH (rhymes with "squash") – the configuration/server management tool we use to run Cloud Foundry. Basically, it's what keeps the platform running.
- BOSH Lite – [https://github.com/cloudfoundry/bosh-lite](https://github.com/cloudfoundry/bosh-lite)
- cloud.gov ("cloud dot gov").
- CFT – Cloud Formation Templates.
- CenturyLink – a company that contributes heavily to Cloud Foundry, and runs their own Cloud Foundry-based PaaS, [AppFog](https://www.ctl.io/appfog/).
- [Cloud Foundry](https://www.cloudfoundry.org/)(CF) - the open-source platform-as-a-service software that cloud.gov is built on. Also sometimes used informally to refer to the Cloud Foundry Foundation, the non-profit formed to shepherd the community surrounding Cloud Foundry. (It's sometimes important to distinguish; as the government, we are clear to talk about the tech we're using but avoid the appearance of endorsement of particular organizations or people.)
- [Concourse](https://concourse-ci.org) - the continuous integration tool built by Pivotal we use to deploy Cloud Foundry, among other things.
- ConMon - [Continuous monitoring](https://cloud.gov/docs/ops/continuous-monitoring/).
- The Dashboard – the web app we offer to allow users to manage their applications and accounts. It lives at [dashboard.fr.cloud.gov](https://dashboard.fr.cloud.gov/), and the code is in the [cg-dashboard](https://github.com/cloud-gov/cg-dashboard) repository.
- [Elastic Load Balancing](https://aws.amazon.com/elasticloadbalancing/) (ELB) – the proxy we use in front of Cloud Foundry.
- [FedRAMP](https://www.fedramp.gov/) - a program whereby which Cloud Service Providers (CSPs) are rigorously examined for compliance with FISMA before being identified as generally fit for use by all government agencies.
- [FISMA](https://en.wikipedia.org/wiki/Federal_Information_Security_Management_Act_of_2002) - The federal law that governs digital service delivery in the federal government.
- [FISMA-Ready](https://github.com/fisma-ready) - A repository of hardened configurations for common open source infrastucture, suitable for incorporation into a digital service.
- IaaS – infrastructure as a service. We use Amazon Web Services (AWS) GovCloud (the region Amazon runs explicitly for the federal government).
- IBM Bluemix – IBM's hosted version of Cloud Foundry.
- InfoSec – information security.
- PaaS – platform as a service. We use Cloud Foundry to run the cloud.gov PaaS.
- [Pivotal](https://pivotal.io/) – the company that originally started Cloud Foundry.
- UAA - UAA is the User Authentication and Authorization hub for Cloud Foundry. It can delegate identity management via common standards such as LDAP/Active Directory, SAML, OAuth/OpenID Connect, and so forth. UAA is deployed as part of cloud.gov. 

Also see [the Cloud Foundry glossary](http://docs.cloudfoundry.org/concepts/glossary.html) for  terms that are specific to the technology powering our platform.

# Joining the Federalist team

Federalist is a platform to build, launch, and manage static web sites for government agencies. The team develops, operates, and supports the platform so that we can offer it to agencies as a service.

## Onboarding

Review the [Getting started at TTS guide](https://handbook.tts.gsa.gov/getting-started/) first. (Contractors, we're presuming you have an equivalent process you've gone through for onboarding with your employer.)

Everyone joining the team will get assigned a team onboarding buddy. This person should be working on similar things to what you will be working on, so that they can answer questions in your domain.

You and your team onboarding buddy must follow the instructions in your onboarding issue that will guide you through tasks that will get you up to speed and contributing in no time. You (and your buddy) must track your progress by checking the boxes as you complete tasks.

Our Onboarding Checklist helps us fulfill important security and compliance requirements, so each new team member needs to have their own checklist in our issue-tracker to document their progress. This is true even if you're rejoining the team after being in it previously.
