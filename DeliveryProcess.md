
# Delivery process

The cloud.gov team applies a subset of [the Scaled Agile Framework](http://www.scaledagileframework.com/) (SAFe) to guide its program structure, as described in [Essential SAFe](http://www.scaledagileframework.com/guidance-essential-safe/). We set goals and prioritize work in three month periods called "program increments," or PIs, and practice a number of SAFe rituals around this quarterly cadence.

To manage our day-to-day work, we practice Scrumban, which means we practice [Kanban](http://blog.crisp.se/2009/06/26/henrikkniberg/1246053060000) around cardwall-style boards that track work from left-to-right as it is identified, prioritized, explored, delivered, and demonstrated. We augment Kanban with a subset of Scrum activities: 

- a rapid (15-minute vidconf) or asynchronous (in Slack) daily standup per squad to communicate about the status of work on the board
- bi-weekly sprint demos for stakeholders and colleagues of each squad's recent work
- bi-weekly retrospectives for each squad
- occasional higher-level planning and grooming sessions
 
## Squads
We've structured our team into 5 squads, each centered around a different [theme](https://github.com/18F/cg-product#sub-teamsthemes-of-work), and generally working on features under that theme:

- Atlas/AgentQ:
  - Adam Kendall, Chris Nelson, Josh Carp, Roger Ruiz, Lenny Bogdonoff (Bret Mogilefsky, PM)
  - Comm channels: #cloud-gov-atlas and #cloud-gov-agent-q
  - Skills involved:
    - Atlas: SRE skills like Terraform, BOSH, etc.
    - AgentQ: Clojure, Ruby, Golang, Python, Bash; Linux, Infrastructure, Networking, Automation; Monitoring
   - [Board view](https://favro.com/organization/1e11108a2da81e3bd7153a7a/68a186775e1a0ee297ee81ed)

- HighBar:
  - Britta Gustafson (Bret Mogilefsky, PM)
  - Comm channel: #cloud-gov-highbar, and group messages
  - Skills involved: UI design, account management, comms and content
  - [Board view](https://favro.com/organization/1e11108a2da81e3bd7153a7a/d9f8e73b7402f22b1ff55cf9)

- Navigator:
  - Marco Segreto (engineering lead), Aaron Borden
  - Comm channel: #cloud-gov-navigator, #cloud-gov-nav-news and group messages
  - Skills involved: UX research, UI design, front-end dev
  - [Board view](https://favro.com/organization/1e11108a2da81e3bd7153a7a/c7aa5db5d32d16974700b110)

- Migration:
  - James Scott, Fureigh (Andrew Suprenant, PM)
  - Comm channel: #cloud-gov-migration and group messages
  - Skills involved: Python, Ruby, Go, Networking, account management, comms
  - [Board view](https://favro.com/organization/1e11108a2da81e3bd7153a7a/e166f9041ce97085a6cdd859) (private due to details about customers)

- SkyPorter:
  - James Hupp (content strategist)
  - Comm channel: #cloud-gov-skyporter and group messages
  - Skills involved: user research, service design, content strategy including drafting and information architecture design
  - [Board view](https://favro.com/organization/1e11108a2da81e3bd7153a7a/3096442fc5df09a723661c78)

## Business Unit
Cloud.gov's business unit (BU) focuses on business strategy and development as well ensuring customer support gets handled. Currently, the BU consists of Shashank Khandelwal (Acting Director) and Britta Gustafson (Acting Deputy Director). Their comms channel is #cloud-gov-business.

## Kanban process

Kanban basically says cards go through a set of states, but it doesn't say much about what the cards represent or how the states are defined. Here's what they mean to us.

### Cards

Cards on our boards capture either a Feature or Story. Each type represents work to be done at a particular level of detail.

- **Features** are user-notable, program-sequenced, roadmap-worthy changes in product capabilities tracked against cadence-driven periodic milestones... big stuff that's worth planning and announcing on a regular basis. Features are fairly general, encompassing a set of stories which break down the actual changes in product behavior that we're after to get the intended benefits of the feature. Generally we do coarse analysis and UX exploration work at the Feature level.
- **Stories** represent tactical increments of individually-valuable work deliverable by a squad within a single iteration... often an isolated change in functionality aimed at achieving a goal for a particular kind of stakeholder, whether customer, user, or operator/admin. We try to set the scope of stories such that we anticipate they will take no more than three days of concentrated work to complete.

### Column sequence
Features are generally tracked by their status and against the quarterly cadence on [the Program collection](https://favro.com/organization/1e11108a2da81e3bd7153a7a/0b64f44bc57f65052fad8244). Stories are tracked on the collections of the squad that is most responsible for them.

**Features** progress through these columns in the Feature Kanban on the [the Program collection](https://favro.com/organization/1e11108a2da81e3bd7153a7a/0b64f44bc57f65052fad8244):

- Funnel (to note that we have heard about the need but otherwise not advanced it)
- Analysis (where we explore our options for overall UX and implementation, and set objective metrics and outcomes)
- Backlog (when the feature is basically well-understood at a high level and awaits squad-level attention)
- Implementing (while implementation is in progress)
- Verifying (while they are being evaluated as delivering their intended benefit, open to customer feedback)
- Done (when they are confirmed as meeting their target, and no longer a focus)

Features are also tracked against the Program Increment (PI) where we suspect they'll be delivered based on our best understanding of our current priorities and progress.

**Stories** progress through these columns (although there is some variation from squad to squad):

- Triage (where reported issues, and newly-identified stories appear)
- Backlog (when they are sequenced alongside other stories prioritized for attention)
- Icebox (where they go when they are not planned to get attention any time soon)

*Note that Triage, Backlog, and Icebox lists are at the left in Favro. This is because those lists tend to get loooooong. By separating them from the board, it remains easy to scroll around when you have multiple boards in your collection.* 
- Grooming (when they're being refined for implementation)
- Ready (when they're in a shovel-worthy state, just waiting for team capacity to do the work)
- In Progress (when someone is actively working on the issue)
- Awaiting Acceptance (when work is considered complete and awaiting review/merging/feedback)
- Done (when work warrants demonstration to stakeholders and is awaiting the next sprint review)
- Done, but archived (when work has been demoed, released, announced, and is no longer worth looking at)

### WIP Limits

If you see a number after a column name, that's a work-in-progress (WIP) limit. That means we expect to see no more than that number of cards in the column at a time. If you want to move a card right into a column that's already at its WIP limit, first figure out how to help move one of the existing cards out to the right! If the next column is also at its WIP limit, that's your cue to keep working your way over to the right, asking "how can I help?" when you encounter something being worked on for which there's space to move.

In general we use WIP limits to gate how much time and effort we put into grooming stories when we haven't got capacity to do them yet, and to gate how many things we're trying to do at once so that we focus on finishing existing work before starting new work. We don't want individuals to be responsible for more than one or two cards in progress at a time, and we like people to collaborate and pair up to get work done, so our WIP limit for cards actually getting development attention is set intentionally low to encourage this!

## Definition of "Done"

An agile "Definition of Done" (DoD) captures the team's agreed-upon standards for how we get work done at a consistent level of quality. Having a DoD ensures that non-functional requirements (NFRs) don't have to be re-litigated for every piece of work taken on, cards can be focused on just the relevant details, and new team members aren't surprised by assumed expectations of their colleagues.

At our [sprint reviews](https://docs.google.com/presentation/d/192PxdXMrCS__QcG6-px5x7n4Mp860ZSb_gqCDlrQwiE/edit), we demo work that has reached the "Done" column and is of interest to our users, teammates, or other people apart from the squad that built it. (As an example of finished work that may not be necessary to demo, fixing internal tech debt may not be of interest outside the squad that fixed it.)

### Column exit criteria
For cloud.gov, our DoD is broken up into a set of statements that should be true for each card before it moves to the next column on the board. 

Before advancing a card from one column to the next on the board, it should meet the "exit criteria" for the current column, which are listed below.  The exit criteria for a column varies a bit when the column is used for both Features and Stories.

#### Triage

- Relevant points from any discussion in the comments is captured in the initial post.
- Decision is made to move to the Backlog or Icebox columns, or close.

#### Backlog

##### Features

- Describe what we're after, what benefits it's expected to deliver, and any relevant design/research artifacts. That's it! Any more detail than that should appear in stories.

##### Stories

- Indicate the intended benefit and who it's for in one of these forms:
 - Story: We prefer the ["In order"](http://blog.crisp.se/2014/09/25/david-evans/as-a-i-want-so-that-considered-harmful) form (rather than the common "As a/I want/so that" form).
 - Hypothesis: What's the lean hypothesis being tested, and how it will be validated?

#### Grooming

- Has testable/demoable Acceptance Criteria that we expect to be able to check off to help us understand when the work is done. (Try wording them as [Gherkin](https://en.wikipedia.org/wiki/Behavior-driven_development#Behavioural_specifications), and use [GFM checklists](https://github.com/blog/1375-task-lists-in-gfm-issues-pulls-comments) for them).
- Discussed by the team and implementation sketched (use more checklists here).
- The scope of the work is easily doable in a few days (otherwise, split it!).
- Any authentication/authorization and data persistence points are discussed and requirements are addressed via Acceptance Criteria (e.g., "Authenticate using [login.cloud.gov]" or "Any ephemeral data resulting from usage is backed up/recoverable").
- There's a communication plan for any user-visible changes which require their attention/action.

Required for compliance: 
<!-- Security impact analysis is due to CM-3 part b, CM-4 -->
<!-- New software integration check is due to CM-7 (5) part a -->
<!-- Noah said we need to check with him before integrating new services -->

- The team has analyzed and documented any potential security impact of the changes proposed by the story.
- If the story includes integrating new software (such as a new open source component) into the core platform, the cloud.gov System Owner has approved the plan.
- If the story includes integrating a new external service (a service outside the cloud.gov FedRAMP authorization boundary) or changing an external service configuration/usage in a way that may have a security/compliance impact, the cloud.gov Authorizing Official has approved the plan.

#### Ready

- No info or assistance is needed from outside the team to start work and likely finish it.
- There's capacity available to work on the story (e.g., this column is a buffer of shovel-ready work).

#### In Progress

- Acceptance criteria are demonstrably met.
- Relevant tasks complete, irrelevant checklists removed or captured on a new story.
- Follows documented coding conventions.
- Pair-programmed or peer-reviewed (e.g., use pull-requests).
- Test coverage exists and overall coverage hasn't been reduced.
- User-facing and internal operation docs have been updated.
- Demoable to other people in their own time (e.g., staging environment, published branch).
- Any deployment is repeatable (e.g., at least documented to increase [bus factor](https://en.wikipedia.org/wiki/Bus_factor) beyond one) and if possible automated via CI/CD.
 - If the deployment is difficult to automate, then a story for making it automated is created at the top of `Triage`.
- Deployment happens in the AWS GovCloud deployment (not just AWS East/West).
- All UAA accounts are provisioned using the Cloud Foundry secrets or the cloud.gov [service account](https://cloud.gov/docs/services/cloud-gov-service-account/) or [identity provider](https://cloud.gov/docs/services/cloud-gov-identity-provider/) services.

Required for compliance:

- The deployment must follow our [Configuration Management plan](https://docs.cloud.gov/ops/configuration-management/).  If not possible, [a new issue is filed in cg-site](https://github.com/18F/cg-site/issues) to update the plan.  
- If the deployment includes 18F-developed code, ensure the repository is configured to run [Code Climate static analysis on each PR](https://docs.codeclimate.com/docs/github#pull-requests).
  - Code Climate scan results are reviewed, and any false positives are flagged / scanning rules are updated to exclude irrelevant files (vendored code, tests, etc).
- [Proposed] Appropriate alerting for new stuff is set up and reporting to Riemann.

#### Awaiting Acceptance

- A team-local proxy for the people the story affects reviews and approves the work as meeting acceptance criteria.
- If the work is suitable to demo at our biweekly sprint review, add a description of it to the [sprint review slide deck](https://docs.google.com/presentation/d/192PxdXMrCS__QcG6-px5x7n4Mp860ZSb_gqCDlrQwiE/edit), ideally including a link to the live work or a screenshot (especially for visual work).
- If the work as completed is obviously unscalable and will cause problems if we try, then a story for making it scalable is created at the top of `Triage`.

Required for compliance:

- The work completed adheres to all our policies (for [18F](https://github.com/18F/compliance-docs) and [cloud.gov](https://github.com/18f/cg-compliance)).
- If the work changes an aspect of our system or operating environment that is (or would ideally be) documented in our System Security Plan (SSP), [a new issue is filed in cg-compliance](https://github.com/18F/cg-compliance/issues) to note the change.

#### Done

- The work is user-visible and announceable at any time.

