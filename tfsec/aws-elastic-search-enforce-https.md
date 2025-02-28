Pattern: Elasticsearch doesn't enforce HTTPS traffic

Issue: -

## Description

Plain HTTP is unencrypted and human-readable. This means that if a malicious actor was to eavesdrop on your connection, they would be able to see all of your data flowing back and forth.

You should use HTTPS, which is HTTP over an encrypted (TLS) connection, meaning eavesdroppers cannot read your traffic.

**Resolution**: Enforce the use of HTTPS for ElasticSearch.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_elasticsearch_domain" "bad_example" {
  domain_name = "domain-foo"

  domain_endpoint_options {
    enforce_https = false
  }
}
```

Example of **correct** code:

```terraform
resource "aws_elasticsearch_domain" "good_example" {
  domain_name = "domain-foo"

  domain_endpoint_options {
    enforce_https = true
  }
}
```