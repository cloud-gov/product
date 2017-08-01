# Feature Lifecycle

**Features** are user-notable, program-sequenced, roadmap-worthy changes in product capabilities tracked against cadence-driven periodic milestones... big stuff that's worth planning and announcing on a regular basis. Features are typically not achievable completely within a single sprint, but are achievable within a single quarter.

Features are fairly general, with detail delegated to a set of stories which break down the actual changes in product behavior that we're after to get the intended benefits of the feature. Generally we do coarse analysis and UX exploration work at the Feature level before breaking them down into stories "just in time" for us to deliver the features in a given quarter.
 
Features are generally tracked by their status and against the quarterly cadence on [the Program collection](https://favro.com/organization/1e11108a2da81e3bd7153a7a/0b64f44bc57f65052fad8244).

Features progress through these columns in the Feature Kanban on the [the Program collection](https://favro.com/organization/1e11108a2da81e3bd7153a7a/0b64f44bc57f65052fad8244):

- Funnel (to note that we have heard about the need but otherwise not advanced it)
  - TODO
- Analyzing (where we explore our options for overall UX and implementation, and set objective metrics and outcomes)
  - The card has been analyzed for potential to impact our System Security Plan (SSP) and if necessary, and SCR has been submitted to the FedRAMP JAB.
  - Any necessary research stories or spikes have been completed.
  - The card has WSJF values.
- Backlog (when the feature is basically well-understood at a high level and awaits squad-level attention)
  - The card includes a rough (implementation-agnostic) description of what we're after and what benefits we hypothesize it will deliver.
  - The card includes any existing or potential metrics we could track to demonstrate we're delivering that benefit.
  - The card points to any relevant design/research artifacts from the Analysis phase. That's it! Any more detail than that should appear in stories that get parented onto the feature.
- Implementing (while implementation is in progress)
  - It should be possible to find the set of stories related to the feature.
  - The feature is tracked against the Program Increment (PI) where we suspect it'll be delivered.
  - If customer-facing, the feature is published on the public roadmap in the quarter where we suspect it'll be delivered.
- Validating (while they are being evaluated as delivering their intended benefit, open to customer feedback)
  - We are confident that we are delivering the intended benefit and that we are seeing any key metrics change.
- Done (when they are confirmed as meeting their target, and no longer a focus)
