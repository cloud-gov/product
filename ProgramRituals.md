
# Program Rituals and Practices

Managing a small team for a short project can be challenging and require practices, discipline, and experience to run effectively.

When the team size and project duration expand, new sets of practices are required to both coordinate the efforts of a larger team (often broken down into smaller squads) and regularly set, evaluate, and reset objectives over a period of time to ensure cross-team collaboration and that the team regularly prioritizes the highest-value work while adapting to change, including shifts in business context, personnel churn, and other factors that may influence capacity and priorities.

On cloud.gov, which has now run for several years with a team size varying from nine to twenty-five members, we use a subset of [Scaled Agile Framework (SAFe)](http://www.scaledagileframework.com/guidance-essential-safe/) practices with other agile techniques to help meet these needs:


## Planning Increment (PI)

On cloud.gov, a planning increment (also known elsewhere as a [program increment](http://www.scaledagileframework.com/program-increment/)) is a macro cadence for building and validating system components. The PI is composed of approximately five to six sprints where the program team selects a maximum of ten high-level features on which to work. The PI basically matches a quarterly calendar so is both useful for higher-level roadmapping and also giving the team enough (but not too much) time to make progress against these features before reevaluating and beginning a new increment.


### Planning Increment (PI) planning

Each PI begins with a PI planning session, which is typically conducted over the course of two days with sessions for both the entire team and also squad breakouts. During these, the squads discuss the prioritized features for a given PI, including interdependencies and some implementation details along with risks and a plan for mitigating these. By the end of PI planning, the team should have at least a rough roadmap for each squad for each sprint within the PI and, ideally, enough groundwork completed to promptly start the first sprint. 

Of course, these plans may change over the course of the PI as business context shifts and the team learns more about their work, but the team should leave PI planning having had a chance to raise any ideas, questions, or concerns, and have clear next steps.

#### Planning artifacts

Key recordable outcomes of PI planning should include:
 - PI objectives and risks for each squad
 - PI objectives and risks for the whole program (ideally these get plopped into the "Inspect" presentation template as a first draft for that meeting immediately after PI planning ends) 

These often take the form of:
 - Prioritized high-level features (Favro)
 - Backlog of epics and related stories (Favro)
 - Planning Mural (Mural.ly)


### Program-level standup

In order to share progress, highlight dependencies, and resolve obstacles, we conduct a fifteen-minute program-level standup including all team members four days per week (with the fifth day up to squads/Business Unit to decide if/how they want to meet and share). The goal is to provide visibility into progress and impediments. The meeting is timeboxed to fifteen minutes, though followups may often be scheduled immediately afterwards to address problems that may have been identified. 


### Sprint review / System demo

The sprint review (or [System Demo](http://www.scaledagileframework.com/system-demo/) in SAFe terms) is a bi-weekly, once-per-sprint opportunity to catch up on what was accomplished across all product themes in the cycle that was just concluded. The intended audience are key stakeholders, as well as anyone who may be curious about new activity that may be unable or not interested in following day-to-day work.

During the meeting, squads walk through a presentation deck that list significant features shipped during the sprint, including visible demonstration of what was accomplished (e.g. artifacts written, features running in production or staging, or tested comps for upcoming designs). The team members responsible for the work being demonstrated generally present it. 

Additionally, team members also briefly highlight any significant work-in-progress that is likely to be completed in the next sprint and unlikely to be abandoned, with an indicator of how stakeholders can get involved. As these materials are presented, stakeholders are encouraged to give feedback.

### Mid-PI check-ins (50%, 75%)

Twice per PI (once halfway through and another at the three-quarter mark), the product team conducts a check-in meeting to review progress and begin to discuss features might make sense for the subsequent PI. These meetings are open to the entire team but require the participation of product and business leads.

If the PI is going slowly, features may be de-scoped or reprioritized in anticipation of the next PI planning meeting. If the PI is proceeding well, the team may pull in additional high-level features to the current increment. 

Looking ahead at the following PI, the team reviews the product backlog, which includes preliminary backlogs for the next couple increments as well as additional items contained in squad-specific backlogs. As the team sets priorities and gains clarity on the direction for the following PI, they may front-load several time-boxed research stories or technical spikes in the last couple sprints of the current PI so more information, such as analysis, design comps, or proofs-of-concept, are available during the next PI planning meeting so squads can make more informed decisions as they plan their work.


### Innovation and Planning (IP) Sprint

Once per program increment, we conduct the Innovation and Planning sprint. This sprint starts with seven days of decompression time for the team, and ends with a day for holding a stakeholder review (the "Inspect" session) and a program-wide retrospective to discuss what changes the team wants to make (the "Adapt" session). Finally, the IP sprint includes the two days needed for planning for the following PI (see "PI Planning" above). 

#### Innovation time

The first seven days are intended for the team to take a break from working on features and decompress, have some fun, and possibly learn or experiment. The individual team members select what they want to work on, rather than the collective decision-making process led by the product manager during a typical working sprint. The only requirements are that:

 - The work is feasibly related to cloud.gov
 - Team members articulate, in advance, what they’re going to try to accomplish
 - Team members present what they learned (even if they failed) to the whole team at the end of the sprint

The benefits of this are threefold. First, the team is able to refresh, reset, and come to the next PI with renewed focus and perspective. Second, the team has an opportunity to do some work that will benefit the project but typically may be difficult to prioritize during a regular working sprint – taking training, developing new skills, paying down bothersome tech debt, or prototyping a feature they really care about. Third, the entire team is similarly disengaged from the backlog so it's easier to do this work without the constant pull of teammates who are focused on a shared sprint goal.

Team members can also keep advancing features, but the IP sprint leaves the decisions to team members, not product managers.  Team members can also collaborate with each other on IP sprint work, but it’s not at all required. 

The outcome of Innovation time is presented at the tail end of the Inspect session; see below.

#### Inspect session (usually 1-2 hours)

This is a all-program demo session where the team's output for the PI are presented in a summarized form for the broadest possible set of stakeholders (higher-ups and neighboring teams at 18F, but also representatives from key customers). The presentation should cover: New and changed features, progress on key metrics, user-experience changes, etc. The results are compared against the PI objectives set for the program during PI planning and together we make an assessment of whether the intended objective was met. At the end of this session, prototypes and learnings from the Innovation time are presented, lightning-talk style. (Depending on the content, some outcomes may be presented after external stakeholders leave.) Once all external stakeholders are dismissed, team members representing the 18F Products and Platforms Business Unit also give an update on business metrics for cloud.gov as a whole for the remaining internal stakeholders.

#### Adapt session (usually 1 hour)

This is the PI-cadence, all-program retrospective (as opposed to squad retrospectives, which occur once per sprint, typically immediately after Sprint Review). Here, the team reflects on the entire Planning Increment and identifies actions for improvements going forward. These program-level improvements are tracked for visibility and follow-through over the course of the next PI.

#### PI Planning

Fresh from the presentation and feedback of the Inspect and Adapt sessions, the last two days of the PI are spent running the PI planning session for the next PI (see "PI Planning" above).

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


