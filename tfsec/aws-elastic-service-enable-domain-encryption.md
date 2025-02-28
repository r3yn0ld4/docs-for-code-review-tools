Pattern: Elasticsearch domain isn't encrypted at rest

Issue: -

## Description

You should ensure your Elasticsearch data is encrypted at rest to help prevent sensitive information from being read by unauthorised users.

**Resolution**: Enable ElasticSearch domain encryption.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_elasticsearch_domain" "bad_example" {
  domain_name = "domain-foo"

  encrypt_at_rest {
    enabled = false
  }
}
```

Example of **correct** code:

```terraform
resource "aws_elasticsearch_domain" "good_example" {
  domain_name = "domain-foo"

  encrypt_at_rest {
    enabled = true
  }
}
```