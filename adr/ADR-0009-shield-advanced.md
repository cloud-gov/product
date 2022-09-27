# CloudFront and Shield Advanced

## Why

To mitigate the impact of DDoS attacks, we want to enable AWS Shield Advanced, Amazon's DDoS protection product. Shield Advanced is not available in GovCloud and cannot protect GovCloud load balancers from a Commercial account. To use it, we will create CloudFront distributions in our Commercial AWS account in front of all platform load balancers, and enable Shield Advanced on CloudFront.

## Background: How CloudFront and Shield Advanced Work

[CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) is AWS's Content Delivery Network (CDN) product. It is comprised of a globally distributed network of edge locations and is meant to speed up content delivery by serving cached content from locations geographically close to users. CloudFront distributions tell CloudFront which origin servers to use and are associated with a domain name.

[Shield Advanced](https://docs.aws.amazon.com/waf/latest/developerguide/ddos-advanced-summary.html) is a tier of AWS Shield, a DDoS protection service. Shield Advanced automatically creates Web Application Firewall (WAF) rules in response to changing traffic to block requests that are part of a DDoS attack. Shield Advanced can be enabled on [certain AWS resource types](https://docs.aws.amazon.com/waf/latest/developerguide/ddos-advanced-summary-protected-resources.html), including CloudFront distributions.

## Implementation

The following only applies to our production environment. All other environments are not available on the public internet and cannot be targeted by DDoS attacks.

```mermaid
graph TD
    subgraph b["blank"]
        style b fill:none,stroke:none,color:#fff
        classDef s fill:#ecffec,stroke:#73d893
        classDef cf fill:#ffffec,stroke:#d8d893

        s1[Shield Protection 1]:::s --> cf1
        cf1[CloudFront Distribution 1]:::cf --> alb1[ALB 1]

        s2[Shield Protection 2]:::s --> cf2
        cf2[CloudFront Distribution 2]:::cf --> alb2[ALB 2]

        s3[Shield Protection 3]:::s --> cf3
        cf3[CloudFront Distribution 3]:::cf --> alb3[ALB 3]
    end

    sg1[Shield Protection Group] --> cf1 & cf2 & cf3
    style sg1 fill:#ffecec,stroke:#d87393
```

We will use Terraform in `cg-provision` to do the following:

* Create CloudFront distributions in front of all internet-facing load balancers.
    * Use the [aws_cloudfront_distribution](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/cloudfront_distribution) Terraform resource.
    * See also the [aws_lb](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/lb) resource and [aws_elb](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/elb) resource.
        * We mostly use ALBs, except for four "classic" ELBs. Three of those are internal.
    * A single distribution can point to [up to 25 origins](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-overview.html), so we may not need one distribution per LB.
    * A single AWS account has a default quota of [200 distributions](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cloudfront-limits.html#limits-web-distributions).
* Enable Shield Advanced on the new CloudFront distributions.
    * Use the [aws_shield_protection](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/shield_protection) resource. One per protected resource (CloudFront distribution, in this case).
    * Add a [aws_shield_protection_group](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/shield_protection_group) resource so traffic is analyzed across all resources.
* Change DNS to reference CloudFront distributions instead of the load balancers.
    * Relevant resource type is [aws_route53_record](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record).

Notes:

* Even though the final implementation will only be run in production, it's possible we could implement the change in the development environment to test it.
    * I'm not sure if we can do this, since that environment is not exposed to the internet.
    * If not: I plan to enable CloudFront alongside the current system, leaving existing DNS as-is, and test with the CloudFront-generated domains before switching DNS.

## Open Questions

* CloudFront is currently in the `external` environment. Would the new distributions also be there? Are resources in this environment treated as outside the security boundary?
* Can we put this protection in front of our customers' applications? What if they are using a CDN themselves?
