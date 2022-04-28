# Story lifecycle

**Compliance Note**: This document partially fulfills [SA-11](https://nvd.nist.gov/800-53/Rev4/control/SA-11). All updates should ensure we maintain security assessments throughout the story and feature lifecycle, and otherwise comply with our our System Security Plan.

## Stories

Stories and issues are created to capture work that might need be done by the team. Our goal is to create multiple smaller stories that can be worked on incrementally rather than one large story that takes significant time to complete.

Refined stories that are on the board in the Backlog represent work we agree needs to be done in the near term (eg one quarter). 

**Story Definition**: Story-level work is captured on "cards" that move across a kanban board with multiple columns reflecting our delivery process. Refined stories that we accept onto the board in the Backlog should:

* Include a clear "definition of done" or "acceptance criteria" (AC) so the team understands when work is complete
  * ACs should be clearly demoable/verifiable whenever possible. 
  * We default to specifying ACs using [BDD](https://en.wikipedia.org/wiki/Behavior-driven_development#Behavioral_specifications) to make it easier to demonstrate the outcome of the work.
* Include a reviewed "Security Considerations" section. Especially ensure any authentication/authorization and data persistence points are discussed and requirements are addressed via Acceptance Criteria (e.g., "Authenticate using [login.fr.cloud.gov]" or "Any ephemeral data resulting from usage is backed up/recoverable").
* Be reasonably small. 
  * If we agree a story is likely to take more than two weeks of concentrated effort to complete, we [split the story into smaller, individually-valuable stories](https://www.humanizingwork.com/the-humanizing-work-guide-to-splitting-user-stories/) and prioritize them independently.

Required for compliance:

* If necessary, the story includes a security testing plan. For example, the ACs include automated tests and alerts for unexpected behavior.
<!-- @mogul says: It's not clear to me why all this feature-level language is in the StoryLifecycle document; we already have it in the FeatureLifecycle document! -->
* If a story is a _feature_ added to the cloud.gov system, then it requires a _*security impact analysis*_ as we ensure every feature undergoes compliance oversight:
  * We've reviewed the feature for impact according to our [significant change rubric](https://cloud.gov/docs/ops/continuous-monitoring/#appendix-significant-change-rubric).
  * We summarize the feature for the JAB Technical Reviewers in (or in a doc linked from) the [agenda for the next bi-weekly JAB Technical Reviewers meeting](https://docs.google.com/document/d/1jGddQkjkQ6e9B0UTq9hfQqHe0btAbTeBGL_DxkozAcg/edit#).
    * We've received a determination from the JAB Technical Reviewers as to whether they agree a Significant Change Request (SCR) is warranted. If the determination is "yes", the card is tagged with `SCR:Yes`. Otherwise the card is tagged with `SCR:No`.
    * If the card is tagged `SCR:Yes`:
    * The feature should include an AC covering delivery of a [Significant Change Request](https://docs.google.com/a/gsa.gov/document/d/16GaDO1xnHrqEEetbonNpo4P10LlGoDHR-jedqBo1yB8/edit?usp=drive_web) in [Google Drive](https://drive.google.com/drive/folders/0B1cewEqKcWCbU1lSUXhEVUNZWUU).
    * The SCR is submitted to the JAB Technical Reviewers (with 3PAO testing results if necessary).
    * The JAB Technical Reviewers have approved the SCR.

Compliance control notes:

* Security impact analysis is due to CM-3 part b, CM-4
* New software integration check is due to CM-7 (5) part a
* Security test planning is due to SA-11 part a

## Board columns

We place cards on the kanban board in columns to help track and communicate the state of the work as it flows through our process.

The work can be moved from column A to column B when:
*  the story meets _both_ column A's "exit conditions" _and_ column B's "entrance conditions"
*  column B is not "at capacity" - the team does not "push the rope" out of A, but rather "pulls the rope" into B.

The columns explicitly specified include:

### Backlog

* Groomed and sequenced stories/issues.
  * **Entrance condition**: During a weekly planning meeting, stories driving the greatest progress on our program priorities, immovable deadlines, and urgent chores are brought onto the board and sequenced into the backlog. The backlog should not have more work in it that we think is reasonable for the coming quarter.
  * **Exit condition**: Knowledgeable people in the team have sketched out a suitable approach to delivering the work, eg a checklist of things to do.

### Doing

* Stories/issues that are in progress/actively being worked on. (Note we explicitly limit the number of cards that can be in the Doing state to encourage the team to pair up and transfer skills and knowledge.)
  * **Entrance condition**: No one else needs help, and a team member has the capacity and context needed to begin work on a story/issue near the top of the backlog.
  * **Exit conditions**: 
    * The Acceptance Criteria can be confirmed 
      * Ideally attach screenshots/GIFs/slides to the issue for review by others (either asynchronously or in a meeting)
    * Required for compliance:
      * The development and deployment of the work must follow our [Configuration Management plan](https://cloud.gov/docs/ops/configuration-management/).  If not possible, contact the Program Management team to modify the story or discuss how to update the Configuration Management plan.  
      * If the deployment includes a new cloud.gov-owned code repository, the repository is configured to run [Code Climate static analysis on each PR](https://docs.codeclimate.com/docs/github#pull-requests).
        * Code Climate scan results are reviewed, and any false positives are flagged / scanning rules are updated to exclude irrelevant files (vendored code, tests, etc).
      * The work completed adheres to all of [cloud.gov's policies and procedures](https://github.com/cloud-gov/compliance-docs).
      * If the work changes an aspect of our system or operating environment that is (or should be) documented in our System Security Plan (SSP), [note necessary changes in our pending SSP change document](https://docs.google.com/a/gsa.gov/document/d/1CWi8efCQKi6TS5oxm76YpSvx3pyQMiW-F0i7lIsdBXk/edit?usp=drive_web) to note the change.

### Ongoing

* Stories/issues that are percolating along and getting attention, but are not blocked or blocking other tracked work. Often these issues are just tracking assignment of chores.
  * **Entrance conditions**: The team agrees that the issue needs ongoing visibilty, but is not constantly taking up unplanned team capacity 
  * **Exit conditions**: Stories/issues are moved to the Closed column once they are complete, or the Blocked column if work cannot proceed
* Sample work we expect to find in Ongoing:
  * A team member is going through the onboarding process
  * Someone is assigned to the recurrent maintenance rotation
  * Someone is supporting a customer-initiated migration or cutover event

### Blocked

* Work that is blocked by internal or external dependencies.
* **Entrance conditions**: The team is being prevented from completing the work. Entering cards are edited to include a "snooze-until" date to ensure they're reviewed after an appropriate interval.
* **Exit conditions**: All blockers have been resolved. Cards will usually move _backwards_ from Blocked into either the Doing column (if there is capacity) or the top of the Backlog (if there is not).

### Closed

**Entrance conditions**: The work is complete (satisfies the acceptance criteria) OR stories/issues are no longer relevant or a priority.

## Document information

Last review/update: April 2022

Additional related compliance controls: CM-4, CM-9, CM-11, SC-18
