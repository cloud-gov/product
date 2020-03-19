## Rules

- **Abide by [the TTS Code of Conduct]({{site.baseurl}}/code-of-conduct).** If you see anyone violating our Code of Conduct, see the reporting section.

- **Do not grant Admin rights to anyone but TTS staff.**

- **Do not store sensitive information in GitHub**, including environment variables, private configuration data, or sensitive information about the public (including but not limited to PII). In the event that such variables or configuration data is pushed to a GitHub repository accidentally, even momentarily, consider it compromised and revoke or change the credentials immediately. Do not delete the commit itself. Then immediately follow the directions on the [incident response handbook page]({{site.baseurl}}/security-incidents). If you're unsure how to protect this information, consult with Infrastructure on GitHub or in the [#admins-github](https://gsa-tts.slack.com/messages/admins-github/) channel in Slack. Some projects use [Citadel](https://github.com/poise/citadel) to store secrets. Also refer to the [TTS Handbook page on sensitive information]({{site.baseurl}}/sensitive-information) and [guidance on sensitive information in our open source policy.](https://github.com/18F/open-source-policy/blob/master/practice.md#protecting-sensitive-information)

  - To help you not commit sensitive information to Github, [please read about Git
    Seekrets]({{site.baseurl}}/sensitive-information#git-seekret).

- **Ask TTS Tech Portfolio before integrating a service with GitHub.** Many websites offer the option to "Sign in with GitHub" and may further request permission to access your "personal user data." Providing this level of access can not only share your public or private email address, but it can also grant the ability to access TTS private repositories. For this reason, we ask that all organization members refrain from authorizing integrations and request any desired integrations through an TTS Tech Portfolio issue.

- **Ask TTS Tech Portfolio before creating private repositories.** We pay GitHub for the ability to create private repositories and need to bill clients for repositories created on their behalf. Before you do anything, drop into [#admins-github](https://gsa-tts.slack.com/messages/admins-github) and explain what you'd like to do and why. Be sure to include a link in your repo README to a document that explains why it is private. (See the **Exceptions** section of the [18F Open Source policy](https://18f.gsa.gov/open-source-policy/).)

- **You do not need approval to create public repositories.**

- **Ask TTS Tech Portfolio before deleting repositories.** As a government team, we can’t delete repositories without TTS Tech Portfolio first reviewing them for information that they may need to retain/archive (including issues, pull request comments, commit history, and other information). If you want to delete a repository, go to [#admins-github](https://gsa-tts.slack.com/messages/admins-github/) and explain what you'd like to do and why, and wait for approval before deleting it.

- **You do not need approval to transfer a repository.** In some cases, it may make sense to transfer a repository to a client. The person performing the transfer will need to be a member of both organizations. After transferring the repository to the client's organization, create a fork of it in the 18F organization. This is so that:
  - We have a record of the repository in our GitHub organization
  - We have a copy of the code, should the decide to delete the transferred repository, make it private, etc.
