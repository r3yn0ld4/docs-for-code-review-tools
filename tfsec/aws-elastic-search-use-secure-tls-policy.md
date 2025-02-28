Pattern: Elasticsearch domain endpoint is using outdated TLS policy

Issue: -

## Description

You should not use outdated/insecure TLS versions for encryption. You should be using TLS v1.2+.

**Resolution**: Use the most modern TLS/SSL policies available.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_elasticsearch_domain" "bad_example" {
  domain_name = "domain-foo"

  domain_endpoint_options {
    enforce_https = true
    tls_security_policy = "Policy-Min-TLS-1-0-2019-07"
  }
}
```

Example of **correct** code:

```terraform
resource "aws_elasticsearch_domain" "good_example" {
  domain_name = "domain-foo"

  domain_endpoint_options {
    enforce_https = true
    tls_security_policy = "Policy-Min-TLS-1-2-2019-07"
  }
}
```