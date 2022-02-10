# Idiomatic Bosh Building

## Why

Currently, we keep some data in S3 that Bosh expects to live in S3 - namely the `.final_builds` and 
`releases` directories. The `.final_builds` directory maps blobstore IDs to and version identifiers -
it's generated and used by bosh at different points during development and release cutting. The 
`releases` directory maps blobs and packages in the `.final_builds` directory to versioned releases.

Keeping these in S3 has the avantage that our CI system can interact with them without having to commit
to git. It has the downside that we need to interact with these S3 files manually when we make certain 
categories of changes to a release. It's also very unusual in the bosh community, so hard for folks to
understand without interaction.

## The Plan

We should start tracking both of these directories in git. We can track the `.final_builds` directory
without tracking the `releases` directory, but cannot track `releases` without tracking `.final_builds`

We'll move one release at a time, removing them from the bosh-releases pipeline and updating them, 
to track these directories.

The challenge is that we need to let CI commit, but we can't let it commit to our protected
branches. In a perfect world, this is pretty easy:

1. CI checks out repo
2. CI creates a branch
3. CI commits the the changes
4. CI creates a PR 
5. a human reviews and merges the PR

Where this gets complicated is in the time between PR creation and merging.
If another release gets cut, then CI will either 
- end up with merge conflicts (if we reuse the same branch) 
- create a new release with the same version identifier (if we don't reuse the branch)
- other things we haven't realized yet

Plausible options to prevent this:
- check for open PRs and fail the build if any exist
- don't try to prevent it, and rely instead on operational fixing, at least initially
- others?


## Other Considerations

- we discussed and decided _not_ to provide our releases via GitHub, because it likely has
  licensing complications we don't want to deal with
- we should stop building all our bosh releases in a single pipeline, and instead build them
  either where they're used, or in their own dedicated pipelines with testing
