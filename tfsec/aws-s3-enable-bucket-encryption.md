Pattern: Unencrypted S3 bucket

Issue: -

## Description

S3 Buckets should be encrypted with customer managed KMS keys and not default AWS managed keys, in order to allow granular control over access to specific buckets.

**Resolution**: Configure bucket encryption.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_s3_bucket" "bad_example" {
  bucket = "mybucket"
}
```

Example of **correct** code:

```terraform
resource "aws_s3_bucket" "good_example" {
  bucket = "mybucket"

  server_side_encryption_configuration {
    rule {
      apply_server_side_encryption_by_default {
        kms_master_key_id = "arn"
        sse_algorithm     = "aws:kms"
      }
    }
  }
}
```