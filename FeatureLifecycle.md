# Feature Lifecycle

**Features** are user-notable, program-sequenced, roadmap-worthy changes in product capabilities tracked against cadence-driven periodic milestones... big stuff that's worth planning and announcing on a regular basis. Features are typically not achievable completely within a single sprint, but are achievable within a single quarter.

Features are fairly general, with detail delegated to a set of stories which break down the actual changes in product behavior that we're after to get the intended benefits of the feature. Generally we do coarse analysis and UX exploration work at the Feature level before breaking them down into stories "just in time" for us to deliver the features in a given quarter.

## Funnel
To note that we have heard about the need but otherwise not advanced it.
## Scoring
Where we discuss and score the feature to aid sequencing of further analysis.
- The card includes a rough (implementation-agnostic) description of what we're after and what benefits we hypothesize it will deliver.
- The card includes any existing or potential metrics we could track to demonstrate we're delivering that benefit.
- The card has WSJF scores for `User/Business Value`, `Time Sensitivity`, and `Risk-reduction/Opportunity-enablement`.
## Sketching
Where we explore our options for overall UX and implementation, and set objective metrics and outcomes.
- The approach for UX and architecture is sufficient for PI planning purposes (for example, elaborated via research or spike stories, proto-backlog available).
- The card points to any relevant design/research artifacts. Any more detail than that should appear in stories that get parented onto the feature.
- The card has a WSJF score for `Effort`, and the card is tagged with `WSJF:<value>`.
## Security Impact Analysis
Where we ensure every feature undergoes compliance oversight.
- We've summarized the feature for the JAB Technical Reviewers in (or in a doc linked from) the [agenda for the next bi-weekly JAB Technical Reviewers  meeting](https://docs.google.com/document/d/1jGddQkjkQ6e9B0UTq9hfQqHe0btAbTeBGL_DxkozAcg/edit#).
- We've received a determination from the JAB Technical Reviewers as to whether they require a Significant Change Request (SCR) be filed. If the determination is "yes", the card is tagged with `SCR:Yes`. Otherwise the card is tagged with `SCR:No`.
- If the card is tagged `SCR:Yes`:
  - The card includes a link to a [Significant Change Request](https://docs.google.com/a/gsa.gov/document/d/16GaDO1xnHrqEEetbonNpo4P10LlGoDHR-jedqBo1yB8/edit?usp=drive_web) format [in Google Drive](https://drive.google.com/drive/folders/0B1cewEqKcWCbU1lSUXhEVUNZWUU).
  - The SCR has been submitted to the JAB Technical Reviewers.
  - The JAB Technical Reviewers have approved the SCR.
## Backlog
When the feature is basically well-understood at a high level and awaits squad-level attention.
- The program commits to taking on the Feature during a PI Planning meeting.
## Implementing
While implementation is in progress.
- It should be possible to find the set of stories related to the feature.
- The feature is tracked against the Program Increment (PI) where we suspect it'll be delivered.
## Validating
While they are being evaluated as delivering their intended benefit, open to customer feedback.
- We are confident that we are delivering the intended benefit and that we are seeing any key metrics change.
## Done
When they are confirmed as meeting their target, and no longer a focus.
- The feature is recorded as having been completed during a particular planning increment.
