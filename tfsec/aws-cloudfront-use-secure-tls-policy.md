Pattern: CloudFront distribution uses outdated SSL/TLS protocols

Issue: -

## Description

You should not use outdated/insecure TLS versions for encryption. You should be using TLS v1.2+.

**Resolution**: Use the most modern TLS/SSL policies available.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_cloudfront_distribution" "bad_example" {
  viewer_certificate {
    cloudfront_default_certificate = true
	minimum_protocol_version = "TLSv1.0"
  }
}
```

Example of **correct** code:

```terraform
resource "aws_cloudfront_distribution" "good_example" {
  viewer_certificate {
    cloudfront_default_certificate = true
	minimum_protocol_version = "TLSv1.2_2019"
  }
}
```