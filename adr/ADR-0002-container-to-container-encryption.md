# Container-to-Container encryption

There are three main options here, the third having many sub-options:

## Note:
The upstream took on the native HTTPS support, so we're relying on that.

## Wait for native HTTPS support
Asking about c2c encryption in Cloud Foundry community channels has opened up some
conversations about offering this natively. We do not have a firm commitment or
timeline for adoption, but if/when adopted, this would just happen natively, no
configuration required.
[Issue here](https://github.com/cloudfoundry/diego-release/issues/588)

## Out-and-back
Once we finish internet-to-container encryption (~weeks), users could use external
routes, secured with api keys and/or route services to provide access control.

## In-container encryption termination
Since the internal network allows TCP connections (rather than HTTP only), users
can implement encryption in-container. There are two sets of options to consider:

### Single- vs multi- process

- *Single-process*: terminate TLS by configuring HTTPS listeners for whatever web
  server the app runs (e.g. jetty, uwsgi, etc)
- *Multi-process*: If an application doesn’t support HTTPS listeners, users could
  terminate TLS in-container by adding Nginx to your application using the
  multi-buildpack feature combined with the Nginx buildpack

### Certificate source
There are a few potential sources for the certificates used for in-container encryption:
- *Self-managed*: Users manage their own certificates. This means either using
  self-signed certificates (not useful for identity verification) or managing
  provisioning certificates signed by a trusted certificate authority.
- *Current identity certificates*: Containers are currently provided certificates
  signed by a platform-trusted authority. These certificates do not have Subject
  Alternative Names (SANs) users’ applications would know, so the certificates
  would not be useful for identity verification
- *Improved identity certificates*: Cloud Foundry could add internal routes as
  Subject Alternative Names (SANS) to container certificates. Cloud.gov has laid
  out what we believe to be needed here in
  [this ticket](https://github.com/cloudfoundry/diego-release/issues/587)
