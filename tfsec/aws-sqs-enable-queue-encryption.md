Pattern: Unencrypted SQS queue

Issue: -

## Description

Queues should be encrypted with customer managed KMS keys and not default AWS managed keys, in order to allow granular control over access to specific queues.

**Resolution**: Turn on SQS Queue encryption.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_sqs_queue" "bad_example" {
	# no key specified
}
```

Example of **correct** code:

```terraform
resource "aws_sqs_queue" "good_example" {
	kms_master_key_id = "/blah"
}
```