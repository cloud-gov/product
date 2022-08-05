# Git commit signing and validation

## Why

To stay secure and complaint, we want to validate that our code came from
a trusted identity and was not tampered with in-flight.

## How commit signing works

When you sign a commit, your private key signs a checksum of the commit contents.
Anything which receives the commit and also has access to the corresponding public
key can verify that the commit contents have not been altered in any way, either
in authorship or otherwise.

## Implementation

### Prerequisites

- All cloud.gov platform operators [sign commits using GPG](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification#gpg-commit-signature-verification)
- All cloud.gov platform repos are [configured to require signed commits for merging
to the default branch using Allstar](https://github.com/cloud-gov/.allstar)
- Concourse has access to secrets backend (Credhub) containing all of the GPG public
keys for platform operators. We also include the [GPG public key for commits made
via the Github UI](https://github.com/web-flow.gpg) (including PR merges) so that
those commits are trusted.

### Concourse config

The Concourse git resource [supports commit validation](https://github.com/concourse/git-resource/blob/f103729fe58117d542b74a6fefbe5360e5e3f625/README.md?plain=1#L91-L100)
out of the box. All we need to do is turn it on and feed it some keys. To do this,
we should add platform operator keys to a global variable in a Concourse credential
store, then reference that variable in all of our pipeline configs for git resources
[as seen here](https://github.com/cloud-gov/cg-provision/blob/6dfe35b24c9591b62ccf55df004ebeb7b7cc67b8/ci/pipeline.yml#L1337).

### On-/off-boarding

When a new platform operator is added, they'll generate cloud.gov-specific PGP keys.
We'll add the public key to the list of trusted keys, and they'll configure git
to sign their commits.

When an operator leaves the team, we'll remove their key from the trusted keys.
This shouldn't affect any pipelines, since our pipelines generally only run
responding to new commits. As needed, we can push new commits/signatures to
get pipelines going again.

### External contributors

External contributors may not have PGP commit signing configured for GitHub. Even
if they do have it configured, their PGP key would not be in the set of trusted
keys for platform operators.

In order to merge external contributions, a platform operator should:

1. Create a new feature branch off of the main branch (e.g. `feature-foo`)
1. Target the PR of external contribution at the new feature branch
1. After PR review, merge the external contribution to the new feature branch
1. Rebase the feature branch to the main branch so that the rebased commits will
be signed
1. Create a PR to merge the feature branch to the main branch

### Local validation

Since only members of the platform operations team can push to our repos and signed
commits are going to be required for all repos, there should be no risk of team members
pulling down problematic code.

## Open questions

### Netlify CMS

[Netlify CMS is integrated with the `cg-site`](https://github.com/cloud-gov/cg-site/tree/master/admin)
repo and will make commits on the repo to add content that was created in the UI.
Netlify doesn't support signing these commits.

As a workaround, we can pull the branches that Netlify has made commits on and rebase
them so that the commits are signed.

But long term, should we deprecate support for Netlify?
