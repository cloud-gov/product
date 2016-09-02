# Make cloud.gov words consistent

Do you ever write cloud.gov outage updates, dev docs, compliance docs, or other words about cloud.gov? Do you want to...

* ...write helpful info that helps our readers trust us?
* ...never wonder again how to capitalize cloud.gov, BOSH, or GitHub?

OK, follow this guide!

Consistency helps cloud.gov look trustworthy and reliable, and it reduces potential reader confusion.

**You should add things too:** Just make a pull request and assign it to @brittag.

For additional helpful background knowledge about writing well for cloud.gov users, see the [18F Content Guide](https://pages.18f.gov/content-guide/), including its [content principles](https://pages.18f.gov/content-guide/content-principles/).

## Use these exact strings for tricky product names, abbreviations, and team names

Use these exact strings (keeping this spelling, capitalization, punctuation, and spacing):

* **18F**
* **Amazon Web Services**
* **BOSH**
* **CircleCI**
* **Cloud Foundry**
* **cloud.gov** (always lowercase, even at the beginning of a sentence)
* **CloudWatch**
* **Concourse**
* **Dashboard** (formerly *Deck* or *Console*)
* **EC2**
* **ElastiCache**
* **Elasticsearch**
* **ELK**
* **FedRAMP**
* FISMA levels are **Low**, **Moderate** (not *Medium*), and **High**.
* **Git**
* **GitHub**
* **GovCloud**
* **Information Systems Security Officer** (or **ISSO**)
* **Information Systems Security Manager** (or **ISSM**)
* **Infrastructure as a Service** (or **IaaS**)
* **iptables**
* **Kibana**
* **Loggregator**
* **Logstash**
* **New Relic**
* **OAuth**
* **Platform as a Service** (or **PaaS**)
* **StatusPage**
* **Virtual Private Cloud**
* **YAML**
* **Zendesk**

## Use these non-case-sensitive strings for words with tricky spacing and punctuation

These words should be lowercased in the middle of a sentence and capitalized at the beginning of a sentence, but use this exact spacing and punctuation.

* **email**
* **federal**
* **internet**
* **jump box**
* **one-time authentication code** (this is good to use instead of *one time code* or *one-time registration code*)
* **role-based access control**
* **third-party credentials**
* **timestamp**
* **website**

## Use active voice instead of passive voice

Use active voice, especially when you're writing technical explanations. For example: *"the subject did something"*, such as *"the cluster recorded the data"*.

If you write sentences in passive voice (*"something was done"*), such as *"the data was recorded"*, your sentence is hiding important technical information: what did the action? What recorded the data? If you write *something was done by the thing*, revise it to say *the thing did something*.

Using active voice is important for outage reports and postmortems. If we write with passive voice, this can sound like we're not taking full responsibility for our actions and mistakes.

Active voice is also important for documentation (including compliance documentation). When you state which part of the system is doing which action, this helps readers understand how the system works.

## Use contractions and friendly language

Use contractions. Write ordinary straightforward explanations; rewrite stiff or formal phrasing.

## Spell out abbreviations and acronyms early and often

Spell out abbreviations and acronyms the first time you use a term on a page or in a section of a long document.

If you're not sure whether an acronym or abbreviation is a first use (such as if you're writing a section in YAML to use with Compliance Masonry), spell it out. There's no harm in writing out abbreviations an extra time; it'll make up for all the government documents everywhere that have too many unexplained abbreviations.

## Working on our compliance documentation?

*This section is a work in progress.*

### How to keep roles consistent

Capitalize roles throughout the document to help readers understand that you're talking about specific roles rather than just groups of people in general. For example, "Authorizing Official", "Cloud Operations", and "Information Systems Security Officer".

In control descriptions (under "Responsible Roles"):
* List roles with commas, for example "System Owner, Cloud Operations". Don't include "and".
* List roles that can be singular, such as "Authorizing Official", as singular (even if the actual role is occupied by multiple people).

### Customer responsibilities

Write “**Customer Responsibility**” in bold whenever we want to indicate that something is a customer responsibility (not “Client Application” or other titles).
