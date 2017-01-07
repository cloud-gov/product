# Reading List

## 
### cloud.gov
- [ ] Read [the team onboarding document](https://github.com/18F/cg-product/blob/master/Onboarding.md) for more context about cloud.gov
- [ ] Read the ["What is it?"](https://docs.google.com/presentation/d/1nCcti3dXG9TVGW3OqaWtnf96oXX8U8SBTM_WePFO_dg/edit#slide=id.p) presentation for a rundown of what cloud.gov is and does
- [ ] Read through [the Introduction section of docs.cloud.gov](https://docs.cloud.gov/) for a broader understanding of cloud.gov, especially as we present it to potential customers/users
- [ ] Read the [January 2016 cloud.gov "Executive Business Case" document](https://docs.google.com/document/d/138OcG0Lt6gr9J0wM0TzzPNyTROmYAwfLIDujtweiwGw/edit#) for greater context about cloud.gov's potential impact in government
- [ ] Check out the [roadmap](https://18f.aha.io/products/CGP/feature_cards) to get a high-level view of recently-completed, in-progress, and upcoming features
- [ ] Read the [Delivery Process document](https://github.com/18F/cg-product/blob/master/DeliveryProcess.md) to learn about how we work

### Required items for all team members

These items help us fulfill security and compliance requirements (including for FedRAMP). If you get stuck, or if these requirements are confusing, ask for help from your buddy or in a cloud.gov channel.

- [ ] Read the [18F Security Policies and Procedures](https://github.com/18F/compliance-docs). These documents (which are mostly quite short) explain the high-level policies and procedures we must comply with while running cloud.gov.
- [ ] Read and understand our policy about [protecting sensitive information](https://github.com/18F/open-source-policy/blob/master/practice.md#protecting-sensitive-information) in the context of maintaining the vast majority of our documentation in public.
- [ ] Read the [Incident Response Guide](https://docs.cloud.gov/ops/security-ir/).
- [ ] Read the [Contingency Plan](https://docs.cloud.gov/ops/contingency-plan/).
- [ ] Read the [Continuous Monitoring Strategy](https://cloud.gov/docs/ops/continuous-monitoring/), particularly the [cloud.gov team responsibilities](https://cloud.gov/docs/ops/continuous-monitoring/#cloud-gov-team).
- [ ] Read the [Configuration Management Plan](https://docs.cloud.gov/ops/configuration-management/).
- [ ] Read our [sharing secret keys](https://cloud.gov/docs/ops/secrets/#sharing-secret-keys) policy.
- [ ] Review the [18F requirements for password management](https://handbook.18f.gov/password-requirements/).
- [ ] Review the [18F open source policy guidance about protecting sensitive information](https://github.com/18F/open-source-policy/blob/master/practice.md#protecting-sensitive-information).


### Cloud Operations (Atlas & AgentQ)
#### Comprehensive 
- [ ] Read the System Security Plan (the latest version lives on [Google Drive](https://drive.google.com/drive/u/0/folders/0B6fPl5s12igNX3JwR2xFZVpmek0); look for "cloud.gov System Security Plan (SSP)" as a `.docx` file). All of it is useful, but the document is huge -- of particular note for onboarding:
   - Section 9: System Description
   - Section 10: System Environment
- [ ] Learn about [Cloud Foundry](https://www.cloudfoundry.org/): 
   - [ ] Watch [Build Your Own Private Cloud Foundry](https://www.youtube.com/watch?v=v85r4Hy3jbs) to learn about running Cloud Foundry
   - [ ] Complete this [tutorial for Cloud Foundry](https://pivotal.io/platform/pcf-tutorials/getting-started-with-pivotal-cloud-foundry/introduction) (either lightly adapt for cloud.gov sandbox or simply complete as written)
- [ ] Learn about [BOSH](http://bosh.io/): 
   - [ ] Watch this [video](https://www.youtube.com/watch?v=2jpN1mSPZ4Q)
   - [ ] Complete this [tutorial for BOSH](https://mariash.github.io/learn-bosh/)
   - [ ] Examine [our provisioning procedures](https://github.com/18F/cg-provision)
   - [ ] Read [this](http://events.linuxfoundation.org/sites/events/files/slides/seven-stages-of-bosh.pdf) for levity
- [ ] Get to know how UAA is deployed/integrated -- document forthcoming
- [ ] Learn about [Concourse](https://concourse.ci/) and try a [tutorial](https://github.com/starkandwayne/concourse-tutorial)
- [ ] Check out our [staging](https://ci-stage.cloud.gov/) and [production](https://ci.cloud.gov) Concourse instances, and take a look at some of [our pipelines](https://github.com/18F?utf8=%E2%9C%93&query=cg-deploy)
- [ ] Get familiar with our AWS setup
   - Read about our [AWS accounts](https://cloud.gov/docs/ops/aws-accounts/) and [onboarding](https://cloud.gov/docs/ops/aws-onboarding/)
   - Read about the [AWS CLI](https://aws.amazon.com/cli/) 
- [ ] Get familiar with [Terraform](https://www.terraform.io/) by going through the [getting started guide](https://www.terraform.io/intro/getting-started/install.html)
- [ ] Read about how the team [manages secrets](https://cloud.gov/docs/ops/secrets/)
- [ ] Read about Cloud Foundry [services from a user perspective](http://docs.cloudfoundry.org/devguide/services/)
- [ ] Read about [implementing services](http://docs.cloudfoundry.org/services/)
- [ ] Take a look at [our existing brokers](https://github.com/18F?utf8=%E2%9C%93&query=broker)
#### Day-to-day
- [ ] Review the [daily maintenance tasks](https://cloud.gov/docs/ops/maintenance-list/)
- [ ] Review the boards for [Atlas](https://github.com/18F/cg-product#boards?labels=Atlas) and [AgentQ](https://github.com/18F/cg-product#boards?labels=AgentQ)

#### Navigator

- [ ] Review the main [front end board](https://github.com/18F/cg-dashboard/pulls#boards?repos=55727091,39210774,49169967,40567233&labels=Navigator&showPRs=false) (ensure to filter by the "Navigator" label)
- [ ] Review the primary cloud.gov sites: [the dashboard](https://dashboard.cloud.gov/#/), [main landing page](https://cloud.gov/), and [documentation](https://docs.cloud.gov/).
- [ ] Review [dashboard contributing guide](https://github.com/18F/cg-dashboard/blob/master/CONTRIBUTING.md) and [cg-style standards](https://github.com/18F/cg-style/blob/master/documentation/frontend_standards.md) which help frame what we're looking for in code review
- [ ] Review the [design principles wiki](https://github.com/18F/cg-product/wiki) which explains the thinking behind the product and where that thinking comes from
- [ ] Review the [design resource request document](https://docs.google.com/document/d/1s96VP6PB7fbc8g_GwgAZ1hCPmew-J35ZOJx772c1AZ4/edit) if you haven’t already to get a sense of your role on the project
- [ ] Review the [design principles doc](https://docs.google.com/spreadsheets/d/14Y3RKaLUt6RPX5w13iz7oaSCpojEQ-Wqjnd8Ie_VkCc/edit#gid=259774738) to get a sense of how the cloud.gov team feels about the product
- [ ] Review the [comparative analysis](https://github.com/18F/cg-product/wiki/Comparative-landscape-and-heuristics) to get a sense of other vendors and their dashboards.
- [ ] Review the [cg-style styleguide](https://pages.18f.gov/cg-style/) to get a sense of the global cloud.gov visual style.
- [ ] Review the [US Web Design Standards](https://standards.usa.gov/) as cg-style was built from it.
- [ ] Review the dashboard: current [prod](https://dashboard.cloud.gov/#/), [master](https://dashboard-master.apps.cloud.gov/#/) and [staging](https://dashboard-staging.apps.cloud.gov/#/)

#### HighBar
- [ ] Read through the description of [Compliance Toolkit](https://github.com/18F/compliance-toolkit/#readme)
- [ ] Watch [Handling FISMA Faster and Better](https://www.youtube.com/watch?v=T1S52B1-NT4) for important context and background on the federal regulatory context in which cloud.gov operates.
- [ ] Do a cursory read of [Before You Ship](https://pages.18f.gov/before-you-ship/)
- [ ] Read [the intro to Compliance Masonry](https://github.com/opencontrol/compliance-masonry#readme)

