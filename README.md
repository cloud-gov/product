# cloud.gov Product Management
Program-level artifacts, workflow and status for delivery of products within the cloud.gov umbrella

## What is cloud.gov?

cloud.gov is a set of tools designed and supported by US government workers, for US government work. cloud.gov's mission is to reduce the barriers to rapid, incremental, compliant, secure, and scalable delivery of government services for all government agencies by leveraging best-of-breed modern practices in an opinionated way.

## Sub-teams/themes of work

Delivery of cloud.gov is a large endeavor, and there can be a lot of cross-talk due to the range of activity happening at any given time. As we grow we're finding the grain along which to split our work into smaller themes to keep meetings, boards, repositories, Slack channels, etc. efficient and relevant.

When we're well-staffed, we break into sub-teams around the different themes, but when we're short-staffed, we consolidate the team into one and prioritize across all of the themes.

Here are the themes of work we've identified so far and the products for which they're responsible.

- [Platform](https://cm-jira.usa.gov/secure/RapidBoard.jspa?rapidView=1926&projectKey=CG&view=detail) (#cg-platform)
  - The Platform theme aims to keep a solid, dependable, tested, and proven platform up and running strong for everyone in government to use. This includes a lot of automation; infrastructure-as-code is the key theme.
  - "cloud.gov" refers to the [cloud.gov](https://cloud.gov) Platform-as-a-Service (PaaS), which is cloud.gov's first product. The PaaS provides a comfortable abstraction which handles cloud-based operations and greatly reduces the complications of infrastructure management for delivery teams. Our PaaS builds on the widely-used and open source [Cloud Foundry](https://www.cloudfoundry.org/), deployed with practices geared toward meeting [strict government compliance requirements](https://en.wikipedia.org/wiki/Federal_Information_Security_Management_Act_of_2002).
  - This theme includes activity related to the FedRAMP authorization of cloud.gov. Compliance auditing and pen-testing activities are coordinated here, as well as necessary remediation that results.
- [Customer](https://cm-jira.usa.gov/secure/RapidBoard.jspa?rapidView=1929) (#cg-customer)
  - The Customer theme aims to make infrastructure and deployment self-service and easy to use, and ensure people can find answers when they need them.
  - Customer theme encompasses all the user- and tenant-facing features of cloud.gov. That includes UX for web UI, billing workflow, as well as overall design, branding, IA, and integration in our customer-facing presence.
  - Customer focuses on designing the customer experience of cloud.gov from a prospective customer's inquiry about the product through a new customer's onboarding and early use. This includes ongoing user research to understand customer needs and to improve customer interactions, content strategy (including content development and information architecture for our website) to educate customers about our offerings, and other work related to evangelism and training.

In addition to squads, we have a business unit (BU), which, in addition to guiding cloud.gov's business-related decisions, acts as the "front-office" for our customers and stakeholders. The BU consists of cloud.gov's Director and Deputy Director and represents the product in direct communication with customers as they progress from the what-is-this-thing to the productively-using-the-platform-on-their-own stage.

We keep separate backlogs, kanban boards, etc. reflecting each of these themes of work. The [`cg PaaS Program` kanban board](https://cm-jira.usa.gov/secure/RapidBoard.jspa?rapidView=1918) consolidates the activity of all of these sub-themes into a single program-level view against higher-level objectives.

Other notable Slack channels for 18F folk

- #cg-support
  - This is where we direct and handle support from 18F-internal sources
- #cg-business
  - People concerned with tracking outside use of cloud.gov work here.
- #devops-public
  - This is where we invite the public to discuss DevOps topics with us, which sometimes includes PaaS in general or cloud.gov specifically, Docker, etc. Folks external to 18F get access via https://chat.18f.gov.

## Non-team-specific work

- Services (#cg-services)
  - The Services theme aims to instantly outfit teams with the key services and capabilities they need to achieve their mission. This includes managed services, route services, and other configurable enhancements that teams can take advantage of to build their apps.
- Compliance (#cg-compliance)
  - The Compliance theme works on tools and processes that help our team and other teams confidently and routinely exceed high government standard for compliance, security, and accessibility. 
  
## Roadmap and ChangeLog

We publish [roadmap and recent-change information for the overall cloud.gov effort](https://cm-jira.usa.gov/secure/PortfolioProgramView.jspa?id=3) tagged by primary theme. Features are listed in planning increments (PIs) of around three months. Note this information is live, and the priority of anything beyond the next three months is subject to change at any time!

## Following our work in progress

We have a top-level [Jira](https://cm-jira.usa.gov/projects/CG/summary) project collecting our various kanban boards.

## Joining and leaving our team

New contributors should check out our [Onboarding guide and checklist](https://github.com/18F/cg-product/blob/master/Onboarding.md) to get productive quickly. The team follows an [Offboarding checklist](https://github.com/18F/cg-product/blob/master/OffboardingChecklist.md) to clean up access when people leave.

## Delivery Process

We document [the processes that govern the delivery of our work](https://github.com/18F/cg-product/blob/master/DeliveryProcess.md), which is shared (and potentially embellished) with themes in other repositories. Our process is revised periodically when we reflect on common patterns observed across retrospectives.

## Wiki

We maintain a [wiki](https://github.com/18F/cg-product/wiki) with information including product background, key research findings, and design principles.
