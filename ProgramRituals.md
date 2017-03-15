
# Program Rituals and Practices

## Scaled Agile Framework (SAFe)

Managing a small team for a short project can be challenging and require practices, discipline, and experience to run effectively.

When the team size and project duration expand, new sets of practices are required to both coordinate the efforts of a larger team (often broken down into smaller squads) and regularly set, evaluate, and reset objectives over a period of time to ensure cross-team collaboration and that the team regularly prioritizes the highest-value work while adapting to change, including shifts in business context, personnel churn, and other factors that may influence capacity and priorities.

On cloud.gov, which has now run for several years with a team size varying from nine to twenty-five members, we use a subset of [Scaled Agile Framework (SAFe)](http://www.scaledagileframework.com/guidance-essential-safe/) practices with other agile techniques to help meet these needs:
 
## Planning Increment (PI)

On cloud.gov, a planning increment (also known elsewhere as a [program increment](http://www.scaledagileframework.com/program-increment/)) is a macro cadence for building and validating system components. The PI is composed of approximately five to six sprints where the program team selects a maximum of ten high-level features on which to work. The PI basically matches a quarterly calendar so is both useful for higher-level roadmapping and also giving the team enough (but not too much) time to make progress against these features before reevaluating and beginning a new increment.


### Planning Increment (PI) planning

Each PI begins with a PI planning session, which is typically conducted over the course of two days with sessions for both the entire team and also squad breakouts. During these, the teams discuss the prioritized features for a given PI, including interdependencies and some implementation details along with risks and a plan for mitigating these. By the end of PI planning, the team should have at least a rough roadmap for each sprint within the PI and, ideally, enough groundwork completed to promptly start the first sprint. 

Of course, these plans may change over the course of the PI as business context shifts and the team learns more about their work, but the team should leave PI planning with clear next steps as well as opportunities to raise any ideas, questions, or concerns.


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

## Mid-PI check-ins (50%, 75%)

Twice per PI (once halfway through and another at the three-quarter mark), the product team conducts a check-in meeting to review progress and begin to discuss features might make sense for the subsequent PI. These meetings are open to the entire team but require the participation of product and business leads.

If the PI is going slowly, features may be de-scoped or reprioritized in anticipation of the next PI planning meeting. If the PI is proceeding well, the team may pull in additional high-level features to the current increment. 

Looking ahead at the following PI, the team reviews the product backlog, which includes preliminary backlogs for the next couple increments as well as additional items contained in squad-specific backlogs. As the team sets priorities and gains clarity on the direction for the following PI, they may front-load several time-boxed research stories or technical spikes in the last couple sprints of the current PI so more information, such as analysis, design comps, or proofs-of-concept, are available during the next PI planning meeting so squads can make more informed decisions as they plan their work.


## Innovation and Planning (IP) Sprint

Once per program increment, we conduct the Innovation and Planning sprint. This sprint starts with seven days of decompression time for the team, and ends with a day for holding a stakeholder review (the "Inspect" session) and a program-wide retrospective to discuss what changes the team wants to make (the "Adapt" session). Finally, the IP sprint includes the two days needed for planning for the following PI (see "PI Planning" above). 

### Innovation time

The first seven days are intended for the team to take a break from working on features and decompress, have some fun, and possibly learn or experiment. The individual team members select what they want to work on, rather than the collective decision-making process led by the product manager during a typical working sprint. The only requirements are that:

 - The work is feasibly related to cloud.gov
 - Team members articulate, in advance, what they’re going to try to accomplish
 - Team members present what they learned (even if they failed) to the whole team at the end of the sprint

The benefits of this are threefold. First, the team is able to refresh, reset, and come to the next PI with renewed focus and perspective. Second, the team has an opportunity to do some work that will benefit the project but typically may be difficult to prioritize during a regular working sprint – taking training, developing new skills, paying down bothersome tech debt, or prototyping a feature they really care about. Third, the entire team is similarly disengaged from the backlog so it's easier to do this work without the constant pull of teammates who are focused on a shared sprint goal.

Team members can also keep advancing features, but the IP sprint leaves the decisions to team members, not product managers.  Team members can also collaborate with each other on IP sprint work, but it’s not at all required. 

The outcome of Innovation time is presented at the tail end of the Inspect session; see below.

### Inspect session (usually 1-2 hours)

This is a all-program demo session where the team's output for the PI are presented in a summarized form for the broadest possible set of stakeholders (higher-ups and neighboring teams at 18F, but also representatives from key customers). The presentation should cover: New and changed features, progress on key metrics, user-experience changes, etc. The results are compared against the PI objectives set for the program during PI planning and together we make an assessment of whether the intended objective was met. At the end of this session, prototypes and learnings from the Innovation time are presented, lightning-talk style. (Depending on the content, some outcomes may be presented after external stakeholders leave.) Once all external stakeholders are dismissed, team members representing the 18F Products and Platforms Business Unit also give an update on business metrics for cloud.gov as a whole for the remaining internal stakeholders.

### Adapt session (usually 1 hour)

This is the PI-cadence, all-program retrospective (as opposed to squad retrospectives, which occur once per sprint, typically immediately after Sprint Review). Here, the team reflects on the entire Planning Increment and identifies actions for improvements going forward. These program-level improvements are tracked for visibility and follow-through over the course of the next PI.

### PI Planning

Fresh from the presentation and feedback of the Inspect and Adapt sessions, the last two days of the PI are spent running the PI planning session for the next PI (see "PI Planning" above).
