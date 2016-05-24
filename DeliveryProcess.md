
# Delivery process

The cloud.gov team practices Scrumban, which means we practice [Kanban](http://blog.crisp.se/2009/06/26/henrikkniberg/1246053060000) around cardwall-style boards that track work from left-to-right as it is identified, prioritized, explored, delivered, and demonstrated. We augment Kanban with a subset of Scrum activities: 

- a rapid (15 minutes vidconf) or asynchronous (in Slack) daily standup per stream to communicate about the status of work on the board
- bi-weekly sprint demos for stakeholders and colleagues of each stream's recent work
- bi-weekly retrospectives for each stream
- occasional higher-level planning and grooming sessions
 
## Kanban process

Kanban basically says cards go through a set of states, but it doesn't say much about what the cards represent or how the states are defined. Here's what they mean to us.

### Cards

Cards on our boards capture either a Feature or Story. Each type represents work to be done at a particular level of detail.

- **Features** are user-notable, program-sequenced, roadmap-worthy changes in product capabilities tracked against cadence-driven periodic milestones... big stuff that's worth planning and announcing on a regular basis. Features are fairly general, referring to stories which break down the actual changes in product behavior that we're after to get the intended benefits of the feature. Generally we do coarse analysis and UX work at the Feature level.
- **Stories** represent tactical increments of individually-valuable work deliverable by a team within a single iteration... often a single change in functionality aimed at achieving a goal for a particular kind of stakeholder, whether customer, user, or operator/admin.

We track both higher-level features and their constituent stories on the same boards. 

### Column sequence
The sequence of columns goes left-to-right, but a different subset is used depending on the card type.

**Features** progress through these columns:

- Features (while implementation is in progress)
- Awaiting Acceptance (when they are ready for widespread demonstration/release)
- Closed (when they are released and announced)

**Stories** progress through these columns:

- New (where reported issues, PRs, and newly-identified stories appear)
 - Icebox (when under consideration but not immediately scheduled)
- Backlog (when they are sequenced against stories prioritized for attention)
- Grooming (when they're being refined for implementation)
- Ready (when they're in a shovel-worthy state, just waiting for team capacity to do the work)
- In Progress (when someone is actively working on the issue)
- Awaiting Acceptance (when work is considered complete and awaiting review)
- Closed (when work is released)

### WIP Limits

If you see a number in brackets after a column name, that's a work-in-progress (WIP) limit. That means we expect to see no more than that number of cards in the column at a time. If you want to move a card right into a column that's already at its WIP limit, first figure out how to help move one of the existing cards out to the right! If the next column is also at its WIP limit, that's your cue to keep working your way over to the right, asking "how can I help?" when you encounter something being worked on for which there's space to move.

In general we use WIP limits to gate how much time and effort we put into grooming stories when we haven't got capacity to do them yet, and to gate how many things we're trying to do at once so that we focus on finishing existing work rather than starting new work. We don't want individuals to be responsible for more than one or two cards in progress at a time, and we like people to collaborate and pair up to get work done, so our WIP limit for cards actually getting development attention is set intentionally low to encourage this!

## Definition of "Done"

An agile "Definition of Done" (DoD) captures the team's agreed-upon standards for how we get work done at a consistent level of quality. Having a DoD ensures that non-functional requirements (NFRs) don't have to be re-litigated for every piece of work taken on, cards can be focused on just the relevant details, and new team members aren't surprised by assumed expectations of their colleagues.

### Column exit criteria
For cloud.gov, our DoD is broken up into [a set of statements that should be true for each card](https://github.com/18F/cg-product/blob/master/DeliveryProcess.md) before it moves to the next column on the board. 

Before advancing a card from one column to the next on the board, it should meet the "exit criteria" for the current column, which are listed below.  The exit criteria for a column varies a bit when the column is used for both Features and Stories.

#### New

- Relevant points from any discussion in the comments is captured in the initial post
- Decision is made to move to the Backlog or Icebox columns, or close

#### Backlog

##### Features

- Describe what we're after, what benefits it's expected to deliver, and any relevant design/research artifacts. That's it! Any more detail than that should appear in stories.

##### Stories

- Indicate the intended benefit and who it's for in one of these forms:
 - # Story: We prefer the ["In order"](http://blog.crisp.se/2014/09/25/david-evans/as-a-i-want-so-that-considered-harmful) form (rather than the common "As a/I want/so that" form).
 - # Hypothesis: What's the lean hypothesis being tested, and how it will be validated?

#### Grooming

- Has testable/demoable Acceptance Criteria that we expect to be able to check off to help us understand when the work is done. (Try wording them as [Gherkin](https://en.wikipedia.org/wiki/Behavior-driven_development#Behavioural_specifications), and use [GFM checklists](https://github.com/blog/1375-task-lists-in-gfm-issues-pulls-comments) for them)
- Discussed by the team and implementation sketched (use more checklists here)
- The scope of the work is easily doable in a few days (else split it!)
- Any authn/authz and data persistence points are discussed and requirements are addressed via Acceptance Criteria (eg "Authenticate using [18F GitHub org|login.cloud.gov]" or "Any ephemeral data resulting from usage is backed up/recoverable")
- There's a communication plan for any user-visible changes which require their attention/action

#### Ready

- No info or assistance is needed from outside the team to start work and likely finish it
- There's capacity available to work on the story (eg this column is a buffer of shovel-ready work)

#### In Progress

- Acceptance criteria are demonstrably met
- Relevant tasks complete, irrelevant checklists removed or captured on a new story
- Follows documented coding conventions
- Pair-programmed or peer-reviewed (eg use pull-requests!)
- Test coverage exists and overall coverage hasn't been reduced
- User-facing and internal operation docs have been updated
- Demoable to other people in their own time (eg staging environment, published branch)
- Any deployment is repeatable (eg at least documented to increase bus-factor beyond one) and if possible automated via CI/CD.
 - If the deployment is difficult to automate, then a story for making it automated is created at the top of `New Issues`.

#### Awaiting Acceptance

- Stakeholders (or a team-local proxy) see and approve the work as meeting acceptance criteria
- If the work has a visual aspect, post a screenshot attached for later documentation/announcement/demo purposes
- If the work as completed is obviously unscalable and will cause problems if we try, then a story for making it scalable is created at the top of `New Issues`.

#### Closed

- The work is user-visible and announceable.

## Parking Lot (potential future additions)

- Minimizing user disruption
 - How do we ensure system stability for relying teams? 
 - How do we avoid overhead in retraining users due to incremental release? 
 - What conditions might trigger bunching stories for simultaneous release, and how would our criteria capture that status?
