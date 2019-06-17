# Feature Lifecycle

**Features** are user-notable, program-sequenced, roadmap-worthy changes in product capabilities tracked against cadence-driven periodic milestones... big stuff that's worth planning and announcing on a regular basis. Features are typically not achievable completely within a single sprint, but are achievable within a single quarter.

Features are fairly general, with detail delegated to a set of stories which break down the actual changes in product behavior that we're after to get the intended benefits of the feature. Generally we do coarse analysis and UX exploration work at the Feature level before breaking them down into stories "just in time" for us to deliver the features in a given quarter.

Features progress through these stages:

- Funnel (where new ideas go)
- Scoring (where we try to put objective metrics on the value of delivering on an idea)
- Sketching (where we explore options, conduct user research, maybe do spikes, and make an educated guess on effort; this is where an idea really becomes more of a feature)
- Backlog (where scored and sketched features are sorted by value-for-effort, waiting for team capacity)
- Implementing (where features are actively implemented across one or more sprints)
- Security Impact Analysis (where features are validated for FISMA compliance by a FedRAMP 3PAO and approved by the FedRAMP JAB)
- Validating (where we monitor the metrics associated with a feature to see if it's having the intended effect)
- Done (where we expect no further activity to happen on that particular feature, rather than followup features)

## Column exit criteria
For cloud.gov, features go through stages on a kanban board representing the stages above. Before advancing a card from one column to the next on the board, it should meet the "exit criteria" for the current column, which are listed below.

### Funnel
To note that we have heard about the need but otherwise not advanced it.
### Scoring
Where we discuss and score the feature to aid sequencing of further analysis.
- The card includes a rough (implementation-agnostic) description of what we're after and what benefits we hypothesize it will deliver.
- The card includes any existing or potential metrics we could track to demonstrate we're delivering that benefit.
- The card has WSJF scores for `User/Business Value`, `Time Sensitivity`, and `Risk-reduction/Opportunity-enablement`.

Here's a card template:

> **Title:** [a short phrase distinguishing this card from other Features]
> 
> **What we're after:** [a description of a new capability or change in the product]
> 
> **Hypothesized benefit(s)/why:**
> * [benefit 1]
> * [benefit 2]
> * [other feature this would enable]
> 
> 
> **Potential metrics**
> * [metric 1]
> * [metric 2]
  
At the end of this stage a typical card will look something like this:

> **Title:** Help customers understand package and usage fees
> 
> **What we're after:** A prospective customer can easily figure out what it will cost to use cloud.gov for a year at their level of need/usage.
> 
> **Hypothesized benefit(s)/why:**
> * Reduce friction in customer acquisition conversations
> * Help customers self-differentiate between packages
> * Improved sales overall
> 
> **Potential metrics**
> * % leads that bounce from our pricing page vs interact with it/contact us
> * % leads that already understand what they want to buy when they contact us
> * % leads that already understand what they will spend

(Note that this card is intentionally somewhat ambiguous as to the implementation; a very clear static page (simple) might be just as effective as a live calculator/quote-generator (complex) in moving the metrics, and it's up to the team to suggest alternatives and figure it out.)

### Sketching
Where we explore our options for overall UX and implementation, and set objective metrics and outcomes.
- The approach for UX and architecture is sufficient for PI planning purposes (for example, elaborated via research or spike stories, proto-backlog available).
- The card points to any relevant design/research artifacts. Any more detail than that should appear in stories that get parented onto the feature.
- The card has a WSJF score for `Effort`, and the card is tagged with `WSJF:<value>`.
### Backlog
When the feature is basically well-understood at a high level and awaits squad-level attention.
- The program commits to taking on the Feature during a PI Planning meeting.
### Implementing
While implementation is in progress.
- It should be possible to find the set of stories related to the feature.
- The feature is tracked against the Program Increment (PI) where we suspect it'll be delivered.
### Security Impact Analysis
Where we ensure every feature undergoes compliance oversight.
- We've reviewed the feature for impact according to our [significant change rubric](https://cloud.gov/docs/ops/continuous-monitoring/#appendix-significant-change-rubric).
- We summarize the feature for the JAB Technical Reviewers in (or in a doc linked from) the [agenda for the next bi-weekly JAB Technical Reviewers meeting](https://docs.google.com/document/d/1jGddQkjkQ6e9B0UTq9hfQqHe0btAbTeBGL_DxkozAcg/edit#).
- We've received a determination from the JAB Technical Reviewers as to whether they agree a Significant Change Request (SCR) is warranted. If the determination is "yes", the card is tagged with `SCR:Yes`. Otherwise the card is tagged with `SCR:No`.
- If the card is tagged `SCR:Yes`:
  - The feature should include a story covering delivery of a [Significant Change Request](https://docs.google.com/a/gsa.gov/document/d/16GaDO1xnHrqEEetbonNpo4P10LlGoDHR-jedqBo1yB8/edit?usp=drive_web) in [Google Drive](https://drive.google.com/drive/folders/0B1cewEqKcWCbU1lSUXhEVUNZWUU).
  - The SCR is submitted to the JAB Technical Reviewers (with 3PAO testing results if necessary).
  - The JAB Technical Reviewers have approved the SCR.
### Validating
While they are being evaluated as delivering their intended benefit, open to customer feedback.
- We are confident that we are delivering the intended benefit and that we are seeing any key metrics change.
### Done
When they are confirmed as meeting their target, and no longer a focus.
- The feature is recorded as having been completed during a particular planning increment.
