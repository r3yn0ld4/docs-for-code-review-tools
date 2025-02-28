Pattern: Unencrypted Elasticache Replication Group

Issue: -

## Description

You should ensure your Elasticache data is encrypted at rest to help prevent sensitive information from being read by unauthorised users.

**Resolution**: Enable encryption for replication group.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_elasticache_replication_group" "bad_example" {
        replication_group_id = "foo"
        replication_group_description = "my foo cluster"

        at_rest_encryption_enabled = false
}
```

Example of **correct** code:

```terraform
resource "aws_elasticache_replication_group" "good_example" {
        replication_group_id = "foo"
        replication_group_description = "my foo cluster"

        at_rest_encryption_enabled = true
}
```