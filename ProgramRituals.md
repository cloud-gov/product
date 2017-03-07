
# Program Rituals and Practices

## Scaled Agile Framework (SAFe)

Managing a small team for a short project can be challenging and require practices, discipline, and experience to run effectively.

When the team size and project duration expand, new sets of practices are required to both coordinate the efforts of a larger team (often broken down into a subset of teams) and regularly set, evaluate, and reset objectives over a period of time to insure cross-team collaboration and that the team regularly prioritizes the highest-value work while adapting to change, including shifts in business context, personnel churn, and other factors that may influence capacity and priorities.

On cloud.gov, which has now run for several years with a team size varying from twelve to eighteen members, we use a set of [Scaled Agile Framework (SAFe)](http://www.scaledagileframework.com/guidance-essential-safe/) practices with other Agile techniques to help meet these needs:
 
## Planning Increment (PI)


## Planning Increment (PI) planning

Each PI begins with a PI planning session, which is typically conducted over the course of two days with sessions for both the entire team and also squad breakouts. During these, the teams discuss the prioritized features for a given PI, including interdependencies and some implementation details along with risks and a plan for mitigating these. By the end of PI planning, the team should have at least a rough roadmap for each sprint within the PI and, ideally, enough groundwork completed to promptly start the first sprint. 

Of course, these plans may change over the course of the PI as business context shifts and the team learns more about their work, but the team should leave PI planning with clear next steps as well as opportunities to raise any ideas, questions, or concerns.


### Planning artifacts

Key recordable outcomes of PI planning should include:
 - PI objectives and risks for each squad
 - PI objectives and risks for the whole program (ideally these get plopped into the "Inspect" presentation template as a first draft for that meeting immediately after PI planning ends) 

These often take the form of:
 - Prioritized high-level features (Aha! and Favro)
 - Backlog of epics and related stories (Favro)
 - Planning Mural (Mural.ly)


## Program-level standup

In order to share progress, highlight dependencies, and resolve obstacles, we conduct a fifteen-minute program-level standup including all team members four days per week (with the fifth day up to squads/Business Unit to decide if/how they want to meet and share). The goal is to provide visibility into progress and impediments. The meeting is timeboxed to fifteen minutes, though followups may often be scheduled immediately afterwards to address problems that may have been identified. 


## Sprint review / System demo

The sprint review (or [System Demo](http://www.scaledagileframework.com/system-demo/) in SAFe terms) is a bi-weekly, once-per-sprint opportunity to catch up on what was accomplished across all product sub-streams in the cycle that was just concluded. The intended audience are key stakeholders, as well as anyone who may be curious about new activity that may be unable or not interested in following day-to-day work.

During the meeting, squads walk through a presentation deck that list significant features shipped during the sprint, including visible demonstration of what was accomplished (e.g. artifacts written, features running in production or staging, or comps for upcoming designs). The team members responsible for the work being demonstrated generally present it. 

Additionally, team members also briefly highlight any significant work-in-progress that is likely to be completed in the next sprint and unlikely to be abandoned. As these materials are presented, stakeholders are encouraged to give feedback. 


## Inspect and Adapt sessions

This is the PI-cadence, all-program retrospective (as opposed to squad retrospectives, which occur once per sprint, typically immediately after Sprint Review). Here, the team reflects on the entire Planning Increment and identifies actions for improvements going forward. 


## Mid-PI check-ins (50%, 75%)

Twice per PI (once halfway through and another at the three-quarter mark), the product team conducts a check-in meeting to review progress and begin to discuss features might make sense for the subsequent PI. These meetings are open to the entire team but require the participation of product and business leads.

If the PI is going slowly, features may be de-scoped or reprioritized in anticipation of the next PI planning meeting. If the PI is proceeding well, the team may pull in additional high-level features to the current increment. 

Looking ahead at the following PI, the team reviews the product backlog, which includes preliminary backlogs for the next couple increments as well as additional items contained in squad-specific backlogs. As the team sets priorities and gains clarity on the direction for the following PI, they may front-load several time-boxed research stories or technical spikes in the last couple sprints of the current PI so more information, such as analysis, design comps, or proofs-of-concept, are available during the next PI planning meeting so squads can make more informed decisions as they plan their work.


## Innovation and Planning (IP) Sprint

Once per program increment, we conduct the Innovation and Planning sprint, which includes three days for stakeholder review, a program-wide retrospective to discuss what changes the team wants to make, and PI planning. 

The remaining seven days is intended for the team to take a break from working on features and decompress, have some fun, and possibly learn or experiment. The individual team members select what they want to work on, rather than the collective decision-making process, led by the product manager, during a typical working sprint. The only requirements are that:


 - The work is feasibly related to cloud.gov
 - Team members articulate, in advance, what they’re going to try to accomplish
 - Team members present what they learned (even if they failed) to the whole team at the end of the sprint

The benefits of this are twofold – first, the team is able to refresh, reset, and come to the next PI with renewed focus and perspective. Second, the team has an opportunity to do some work that will benefit the project but typically may be difficult to prioritize during a regular working sprint – taking training, developing new skills, paying down bothersome tech debt, or prototyping a feature they really care about. 

Team members can also keep advancing features, but the IP sprint leaves the decisions to team members, not product managers. Team members can also collaborate with each other on IP sprint work, but it’s not at all required. 


