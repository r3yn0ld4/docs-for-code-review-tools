Pattern: AWS ES Domain should have logging enabled

Issue: -

## Description

AWS ES domain should have logging enabled by default.

**Resolution**: Enable logging for ElasticSearch domains.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_elasticsearch_domain" "example" {
  // other config

  // One of the log_publishing_options has to be AUDIT_LOGS
  log_publishing_options {
    cloudwatch_log_group_arn = aws_cloudwatch_log_group.example.arn
    log_type                 = "INDEX_SLOW_LOGS"
  }
}
```

Example of **correct** code:

```terraform
resource "aws_elasticsearch_domain" "example" {
  // other config

  // At minimum we should have AUDIT_LOGS enabled
  log_publishing_options {
    cloudwatch_log_group_arn = aws_cloudwatch_log_group.example.arn
    log_type                 = "AUDIT_LOGS"
  }
}
```