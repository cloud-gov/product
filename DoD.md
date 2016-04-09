
# Our process and the Definition of Done
Here we document our process for advancing work across the kanban board, and the non-functional requirements (NFRs) for our delivery, aka the agile "Definition of Done" (DoD).

## Card types

There are cards on our board for each issue representing a Feature or Story. The sequence of columns varies depending on the card type.

### Features

Features are user-notable, program-sequenced, roadmap-worthy changes in product capabilities tracked against cadence-driven periodic milestones. Feature issues refer to specific stories in other issues.

The column-sequence for features is:

- Features (while implementation is in progress)
- Awaiting Acceptance (when they are ready for widespread demonstration/release)
- Closed (when they are released and announced)

### Stories

Stories represent tactical increments of individually-valuable work deliverable by a team within a single iteration. 

The column-sequence for stories is:

- New (where ungroomed issues, PRs, and stories appear)
 - Icebox (when under consideration but not immediately scheduled)
- Backlog (when are sequenced against features in progress)
- Grooming (when they're being prepared for team attention)
- Ready (when they're in a shovel-worthy state, just waiting for team capacity to do the work)
- In Progress (when someone is actively working on the issue)
- Awaiting Acceptance (when work is considered complete and awaiting review)
- Closed (when work is released)

## Column exit criteria

Before advancing a card from one column to the next on the board, it should meet the "exit criteria" for the current column, which are listed below.  The exit criteria for a column varies between Features and Stories.

### New

- Relevant points from any discussion in the comments is captured in the initial post
- Decision is made to move to the Backlog or Icebox columns, or close

### Backlog

#### Features

- Describe what we're after, and what benefits it's expected to deliver

#### Stories

- Indicate the intended benefit and who it's for in one of these forms:
 - # Story: We prefer the ["In order"](http://blog.crisp.se/2014/09/25/david-evans/as-a-i-want-so-that-considered-harmful) form (rather than the common "As a/I want/so that" form).
 - # Hypothesis: What's the lean hypothesis being tested, and how it will be validated?

### Grooming

- Has testable/demoable Acceptance Criteria (try wording them as [Gherkin](https://en.wikipedia.org/wiki/Behavior-driven_development#Behavioural_specifications), and use [GFM checklists](https://github.com/blog/1375-task-lists-in-gfm-issues-pulls-comments) for them)
- Discussed by the team and implementation sketched (use more checklists here)
- The scope is easily doable in a few days (else split it!)
- Any authn/authz and data persistence points are discussed and requirements are addressed via Acceptance Criteria (eg "Authenticate using [18F GitHub org|login.cloud.gov]" or "Any ephemeral data resulting from usage is backed up/recoverable")
- There's a communication plan for any user-visible changes which require their attention/action

### Ready

- No info or assistance is needed from outside the team to start work and likely finish it
- There's capacity available to work on the story (eg this column is a buffer of shovel-ready work)

### In Progress

- Acceptance criteria are demonstrably met
- Relevant tasks complete, irrelevant checklists removed or captured on a new story
- Follows documented coding conventions
- Pair-programmed or peer-reviewed (eg use pull-requests!)
- Test coverage exists and overall coverage hasn't been reduced
- User-facing and internal operation docs have been updated
- Demoable to other people in their own time (eg staging environment, published branch)
- Any deployment is repeatable (eg at least documented to increase bus-factor beyond one) and if possible automated via CI/CD.
 - If the deployment is difficult to automate, then a story for making it automated is created at the top of `New Issues`.

### Awaiting Acceptance

- Stakeholders (or a team-local proxy) see and approve the work as meeting acceptance criteria
- If the work has a visual aspect, post a screenshot attached for later documentation/announcement/demo purposes
- If the work as completed is obviously unscalable and will cause problems if we try, then a story for making it scalable is created at the top of `New Issues`.

### Closed

- The work is user-visible and announceable.

## Parking Lot (potential future additions)

- Minimizing user disruption
 - How do we ensure system stability for relying teams? 
 - How do we avoid overhead in retraining users due to incremental release? 
 - What conditions might trigger bunching stories for simultaneous release, and how would our criteria capture that status?
