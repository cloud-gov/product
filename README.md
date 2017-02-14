<a href="https://zenhub.io"><img src="https://raw.githubusercontent.com/ZenHubIO/support/master/zenhub-badge.png"></a>
# Cloud.gov Product Management
Program-level artifacts, workflow and status for delivery of products within the cloud.gov umbrella

## What is cloud.gov?

cloud.gov is a set of tools designed and supported by US government workers, for US government work. cloud.gov's mission is to reduce the barriers to rapid, incremental, compliant, secure, and scalable delivery of government services for all government agencies by leveraging best-of-breed modern practices in an opinionated way.

## Sub-teams/themes of work

Delivery of cloud.gov is a large endeavor, and there can be a lot of cross-talk due to the range of activity happening at any given time. As we grow we're finding the grain along which to split our work into smaller themes to keep meetings, boards, repositories, Slack channels, etc. efficient and relevant. 

When we're well-staffed, we break into sub-teams around the different themes, but when we're short-staffed, we consolidate the team into one and prioritize across all of the themes. 

Here are the themes of work we've identified so far and the products for which they're responsible.

- [Atlas](https://github.com/18F/cg-product#boards?labels=Atlas&showPRs=false) (#cloud-gov-atlas)
  - The Atlas theme aims to keep a solid, dependable, tested, and proven platform up and running strong for everyone in government to use. This includes a lot of automation; infrastructure-as-code is the key theme.
  - "cloud.gov" commonly refers to the [cloud.gov](https://cloud.gov) Platform-as-a-Service (PaaS), which was cloud.gov's first product. The PaaS provides a comfortable abstraction which handles cloud-based operations and greatly reduces the complications of infrastructure management for delivery teams. Our PaaS builds on the widely-used and open source [Cloud Foundry](https://www.cloudfoundry.org/), deployed with practices geared toward meeting [strict government compliance requirements](https://en.wikipedia.org/wiki/Federal_Information_Security_Management_Act_of_2002).
  - This theme includes activity to establish FEDRAMP recognition of cloud.gov, and publishes [machine-friendly descriptions of cloud.gov security controls](https://github.com/18F/cg-compliance). Compliance auditing and pen-testing activities are coordinated here, as well as necessary remediation that results.
- [Agent Q](https://github.com/18F/cg-product#boards?labels=AgentQ&showPRs=false) (#cloud-gov-agent-q)
  - The Agent Q theme aims to instantly outfit teams with the key services and capabilities they need to achieve their mission. This includes managed services, route services, and other configurable enhancements that teams can take advantage of to build their apps.
- [HighBar](https://github.com/18F/cg-product#boards?labels=HighBar&showPRs=false) (#cloud-gov-highbar)
  - The HighBar theme works on tools and processes that help teams confidently and routinely exceed high government standard for compliance, security, and accessibility. HighBar is packaging those tools and processes into a product usable for people both inside and outside of 18F to reduce their effort to gain ATO.
  - HighBar focuses a great deal on the [Compliance Toolkit](https://github.com/18F/compliance-toolkit) continuous assurance service. Compliance Toolkit provides a heads-up view of code compliance, security, and quality suitable for integration into a delivery team's CI/CD process. Compliance Toolkit helps teams develop to a high standard, enter the compliance process with confidence, and demonstrate continued high quality/compliance long after they have [Authority to Operate](https://www.fedramp.gov/resources/faqs/what-is-an-authority-to-operate-ato/), as new requirements and vulnerabilities emerge. Compliance Toolkit includes [Compliance Masonry](https://github.com/opencontrol/compliance-masonry), which publishes static compliance documentation generated from composable, testable code. Compliance Toolkit can be used with or without the cloud.gov PaaS, but will be easier to take advantage of for apps being deployed there.
- [Navigator](https://github.com/18F/cg-product#boards?labels=Navigator&showPRs=false) (#cloud-gov-navigator)
  - The Navigator theme aims to make infrastructure and deployment self-service and easy to use, and ensure people can find answers when they need them.
  - Navigator encompasses all the user- and tenant-facing features of cloud.gov. That includes UX for web UI, billing workflow, as well as overall design, branding, IA, and integration in our customer-facing presence.
- [SkyPorter](https://github.com/18F/cg-product#boards?labels=SkyPorter&showPRs=false) (#cloud-gov-skyporter)
  - SkyPorter focuses on designing the customer experience of cloud.gov from a prospective customer's inquiry about the product through a new customer's onboarding and early use. This includes ongoing user research to understand customer needs and to improve customer interactions, content strategy (including content development and information architecture for our website) to educate customers about our offerings, and other work related to evangelism and training. 
  
In addition to squads, we have a business unit (BU), which, in addition to guiding cloud.gov's business-related decisions, acts as the "front-office" for our customers and stakeholders. The BU consists of cloud.gov's Director and Deputy Director and represents the product in direct communication with customers as they progress from the what-is-this-thing to the productively-using-the-platform-on-their-own stage.

We keep separate backlogs, kanban boards, etc. reflecting each of these themes of work. The [`cg-product` kanban board](https://github.com/18F/cg-product#boards) consolidates the activity of all of these sub-themes into a single view as they fan out into assorted GitHub repositories. To get a view reflecting only one of the themes, use the label filter above the board.

Other notable Slack channels for 18F folk

- #cloud-gov-support
  - This is where we direct and handle support from 18F-internal sources
- #cloud-gov-business
  - People concerned with tracking outside use of cloud.gov work here.
- #devops-public
  - This is where we invite the public to discuss DevOps topics with us, which sometimes includes PaaS in general or cloud.gov specifically, Docker, etc. Folks external to 18F get access via https://chat.18f.gov.

## Roadmap and ChangeLog

We publish [roadmap and recent-change information for the overall cloud.gov effort](https://18f.aha.io/published/068c364a0302b89521045f9fbd258374), exposed for public consumption and tagged by primary theme. Features are listed in planning increments (PIs) of around three months. Note this information is live, and the priority of anything beyond the next three months is subject to change at any time!

## Following our work in progress

We are using [ZenHub](https://www.zenhub.io) to provide a top-level kanban board and burndown charts showing the status of related work happening across many repositories in GitHub. Install it, then click "Boards" above to see it.

## Joining and leaving our team

New contributors should check out our [Onboarding guide and checklist](https://github.com/18F/cg-product/blob/master/Onboarding.md) to get productive quickly. The team follows an [Offboarding checklist](https://github.com/18F/cg-product/blob/master/OffboardingChecklist.md) to clean up access when people leave.

## Delivery Process

We document [the processes that govern the delivery of our work](https://github.com/18F/cg-product/blob/master/DeliveryProcess.md), which is shared (and potentially embellished) with themes in other repositories. Our process is revised periodically when we reflect on common patterns observed across retrospectives.

## Wiki

We maintain a [wiki](https://github.com/18F/cg-product/wiki) with information including product background, key research findings, and design principles. 

## Including new repositories in this program

To include artifacts from another repository in our program-level view, use ZenHub to set up a board that resembles [the program board](https://github.com/18F/cg-product#boards). Then merge that board into the program board, mapping similar columns appropriately.

