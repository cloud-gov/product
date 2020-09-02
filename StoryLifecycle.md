# Story lifecycle

**Compliance Note**: This document partially fulfills [SA-11](https://nvd.nist.gov/800-53/Rev4/control/SA-11). All updates should ensure we maintain security assessments throughout the story and feature lifecycle, and other comply with our our System Security Plan.

## Stories

Stories and issues are created to capture work that needs to be done by the team. Our goal is to create multiple smaller stories that can be worked on incrementally rather than one large story that takes significant time to complete.
Our team utilizes four swim lanes of "groomed" stories to manage our work.

**Story Definition**: Groomed stories that accepted for the backlog should include:

* A clear "definition of done" or "acceptance criteria" (AC) so the team understands when work is complete
* A reviewed "Security Considerations" section. Especially ensure any authentication/authorization and data persistence points are discussed and requirements are addressed via Acceptance Criteria (e.g., "Authenticate using [login.fr.cloud.gov]" or "Any ephemeral data resulting from usage is backed up/recoverable").

Required for compliance:

* If necessary, the story includes a security testing plan. For example, the ACs include automated tests and alerts for unexpected behavior.
* If a story is a _feature_ added to the cloud.gov system, then it requires a _*security impact analysis*_ as we ensure every feature undergoes compliance oversight:

  * We've reviewed the feature for impact according to our [significant change rubric](https://cloud.gov/docs/ops/continuous-monitoring/#appendix-significant-change-rubric).
  * We summarize the feature for the JAB Technical Reviewers in (or in a doc linked from) the [agenda for the next bi-weekly JAB Technical Reviewers meeting](https://docs.google.com/document/d/1jGddQkjkQ6e9B0UTq9hfQqHe0btAbTeBGL_DxkozAcg/edit#).
  
    * We've received a determination from the JAB Technical Reviewers as to whether they agree a Significant Change Request (SCR) is warranted. If the determination is "yes", the card is tagged with `SCR:Yes`. Otherwise the card is tagged with `SCR:No`.
    * If the card is tagged `SCR:Yes`:
    * The feature should include a story covering delivery of a [Significant Change Request](https://docs.google.com/a/gsa.gov/document/d/16GaDO1xnHrqEEetbonNpo4P10LlGoDHR-jedqBo1yB8/edit?usp=drive_web) in [Google Drive](https://drive.google.com/drive/folders/0B1cewEqKcWCbU1lSUXhEVUNZWUU).
    * The SCR is submitted to the JAB Technical Reviewers (with 3PAO testing results if necessary).
    * The JAB Technical Reviewers have approved the SCR.

Compliance control notes:

* Security impact analysis is due to CM-3 part b, CM-4
* New software integration check is due to CM-7 (5) part a
* Security test planning is due to SA-11 part a

## Swim Lanes

### Backlog

* Prioritized and groomed stories/issues. 
* **Entrance**: Weekly prioritization meeting reviews and prioritizes stories to develop a list in rank order of the 10 highest priorities stories/issues.
* **Exit**: The team pulls the next thing to work on from the top of the backlog and into the doing swimlane.

### Doing

* Stories/issues that are in progress/actively being worked on.
* **Entrance**: Team members pull a story into the doing column from the backlog when they begin work on a given story/issue.
* **Exit**: Stories/issues are moved to the closed swimlane once they are complete.

Required for compliance:

* The deployment must follow our [Configuration Management plan](https://docs.cloud.gov/ops/configuration-management/).  If not possible, contact the Program Management team to modify the story or discuss how to update the Configuration Management plan.  
* If the deployment includes 18F-developed code, ensure the repository is configured to run [Code Climate static analysis on each PR](https://docs.codeclimate.com/docs/github#pull-requests).

  * Code Climate scan results are reviewed, and any false positives are flagged / scanning rules are updated to exclude irrelevant files (vendored code, tests, etc).
* The work completed adheres to all of [cloud.gov's policies and procedures](https://github.com/18F/compliance-docs).
* If the work changes an aspect of our system or operating environment that is (or should be) documented in our System Security Plan (SSP), [note necessary changes in our pending SSP change document](https://docs.google.com/a/gsa.gov/document/d/1CWi8efCQKi6TS5oxm76YpSvx3pyQMiW-F0i7lIsdBXk/edit?usp=drive_web) to note the change.



### Blocked

* Work that is blocked by internal or external entities.
* **Entrance**: Stories or issues are moved to blocked if the team is being prevented from completing the work.
* **Exit**: Stories or issues are moved out of blocked once the blocker has been resolved.

### Closed

**Entrance**: Team members move stories/issues to the close swimlane once the work is complete (satisfy the acceptance criteria) OR stories/issues are no longer relevant or a priority.
