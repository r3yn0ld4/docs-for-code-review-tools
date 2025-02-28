Pattern: Kinesis stream is unencrypted

Issue: -

## Description

Kinesis streams should be encrypted to ensure sensitive data is kept private. Additionally, non-default KMS keys should be used so granularity of access control can be ensured.

**Resolution**: Enable in transit encryption.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_kinesis_stream" "bad_example" {
	encryption_type = "NONE"
}
```

Example of **correct** code:

```terraform
resource "aws_kinesis_stream" "good_example" {
	encryption_type = "KMS"
	kms_key_id = "my/special/key"
}
```