<a name="definition-of-done"></a>
<a name="grooming"></a>
**Moved content:** Looking for information related to CM-4, CM-9, CM-11, or SC-18? To find information about the [Definition of Done](StoryLifecycle.md#definition-of-done) and [the story grooming process](StoryLifecycle.md#grooming), see [the Story Lifecycle](StoryLifecycle.md).

---

# Delivery process

The cloud.gov team applies a subset of [the Scaled Agile Framework](http://www.scaledagileframework.com/) (SAFe) to guide its program structure, as described in [Essential SAFe](http://www.scaledagileframework.com/essential-safe/). We set goals and prioritize work in three month periods called "program increments," or PIs, and practice a number of SAFe rituals around this quarterly cadence.

To manage our day-to-day work, we practice Scrumban, which means we practice [Kanban](http://blog.crisp.se/2009/06/26/henrikkniberg/1246053060000) around cardwall-style boards that track work from left-to-right as it is identified, prioritized, explored, delivered, and demonstrated. We augment Kanban with a subset of Scrum activities: 

- a rapid (15-minute vidconf) or asynchronous (in Slack) daily standup per squad to communicate about the status of work on the board
- bi-weekly sprint demos for stakeholders and colleagues of each squad's recent work
- bi-weekly retrospectives for each squad
- occasional higher-level planning and grooming sessions
 
## Squads
We've structured our team into two squads, each centered around a different [theme](https://github.com/18F/cg-product#sub-teamsthemes-of-work), and generally working on features under that theme:

- Platform (formerly Atlas/AgentQ):
  - Adam Kendall, Josh Carp, Steve Harms, Tim Spencer (Bret Mogilefsky, PM)
  - Comm channels: #cg-platform, #cg-services, #cg-platform-news
  - Skills involved:
    - Atlas: SRE skills like Terraform, BOSH, etc.
    - AgentQ: Clojure, Ruby, Golang, Python, Bash; Linux, Infrastructure, Networking, Automation; Monitoring
   - [Board view](https://cm-jira.usa.gov/secure/RapidBoard.jspa?rapidView=1926&projectKey=CG&quickFilter=8141)

- Customer:
  - Peter Burkholder, Phoebe Espiritu (Bret Mogilefsky, PM)
  - Comm channel: #cg-customer, #cg-nav-news
  - Skills involved: UX research, UI design, service design, content strategy, communications, front-end dev, Python, Ruby, Go, Networking
  - [Board view](https://cm-jira.usa.gov/secure/RapidBoard.jspa?projectKey=CG&rapidView=1929)

## Business Unit
cloud.gov's business unit (BU) focuses on business strategy and development, ensuring customer support gets handled, making sure we meet compliance requirements and other mandatory reporting requirements, and [related work](https://docs.google.com/document/d/18jU3jb6pWEo430LN77G8ucuW7IW0bKP9ljnYSyQU13c/edit#heading=h.tjv8u8lx3c02). Currently, the BU consists of Shashank Khandelwal (Acting Director) and Britta Gustafson (Acting Deputy Director). Their comms channels are #cg-business and #cg-bizops, with compliance work (formerly called HighBar) in #cg-compliance.

## Kanban process

Kanban basically says cards go through a set of states (represented columns on a board), but it doesn't say much about what the cards represent or how the states are defined. Here's what they mean to us.

### Cards on squad boards

Cards on our boards typically capture and track a bug, raw task, or Story. Bugs and tasks are what they sound like. **Stories** represent tactical increments of individually-valuable work deliverable by a squad within a single iteration.

[What's the lifecycle and "definition-of-done" for stories?](StoryLifecycle.md)

### Cards on program boards

**Features** are roadmap-worthy changes in product capabilities tracked against regular milestones... big stuff that's worth planning and announcing on a regular basis.

[What's the lifecycle and "definition-of-done" for features?](FeatureLifecycle.md)

### WIP Limits

If you see a number after a column name, that's a work-in-progress (WIP) limit. That means we expect to see no more than that number of cards in the column at a time. If you want to move a card right into a column that's already at its WIP limit, first figure out how to help move one of the existing cards out to the right! If the next column is also at its WIP limit, that's your cue to keep working your way over to the right, asking "how can I help?" when you encounter something being worked on for which there's space to move.

In general we use WIP limits to gate how much time and effort we put into grooming cards when we haven't got capacity to do them yet, and to gate how many things we're trying to do at once so that we focus on finishing existing work before starting new work. We don't want individuals to be responsible for more than one or two cards in progress at a time, and we like people to collaborate and pair up to get work done, so our WIP limit for cards actually getting development attention is set intentionally low to encourage this!

