Pattern: RDS encryption has not been enabled at a DB Instance level

Issue: -

## Description

Encryption should be enabled for an RDS Database instances. 

When enabling encryption by setting the kms_key_id.

**Resolution**: Enable encryption for RDS clusters and instances.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_db_instance" "bad_example" {
	
}
```

Example of **correct** code:

```terraform
resource "aws_db_instance" "good_example" {
	storage_encrypted  = true
}
```