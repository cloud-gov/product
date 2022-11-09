# cloud.gov Pages Caching

## Why

Build time and error-free builds are the important drivers of customer satisfication when using cloud.gov Pages. Based on limited analysis of build logs, we see that installing build dependencies can take a significant portion of the total build time. Caching these dependendies could significantly reduce build time at the cost of additional storage and added code/build complexity. 

## Background

- Current builds on cloud.gov Pages take between 30 seconds to 13 minutes (5% to 95% percentile). Installing Node and Ruby dependencies can often take two or more minutes.
- Dependencies on Pages sites do not change often, except in cases of developer-led debugging.
- Developers might expect caching to be an available option given their familiarity with other CI tools.
- Less technical users would benefit from faster builds and are unlikely to change dependencies.
- Caching can create build errors and security risks if not handled correctly but generally speaking, build dependencies do not contain private information.

## Proposal

### MVP

We can create a simple caching implementation which will result in faster build times. We can then monitor and evaulate the build times and error rates going forward to seek additional improvements. A limited implementation could look like:
- Prior to installing build dependencies, create a cache key based on hashing the dependency lock files (`Gemfile.lock`, `package-lock.json`, and `yarn.lock`)
- Check a given location on S3 for a file with this name, if it's present, download it.
- If it isn't available, after installing, upload our build dependencies to a folder with the name of our cache key (which by definition is new)

Other considerations:
- This should be a configurable option but ON by default.
    - Discussion of the above point: Turning caching on by default is likely to decrease build time across the platform more significantly but could introduce more errors or user confusion. Off by default will likely have a minimal impact on build time but limit errors.
- The cache files should be stored in the site's existing S3 bucket. See [further consideration here](https://github.com/cloud-gov/pages-build-container/issues/377).


### Transition plan

1. Announce the change publicly in #cg-pages
2. Monitor build times and support tickets for caching-related errors
3. Look for other opportunities to cache additional portions of the build process.

### Acceptance tests

- [ ] Add unit tests in pages-build-container
- [ ] Confirm caching implementation with each type of lockfile on staging
- [ ] Monitor build times after production rollout
- [ ] Monitor support queue for cache errors
