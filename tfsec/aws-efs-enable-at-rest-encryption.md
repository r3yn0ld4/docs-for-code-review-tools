Pattern: EFS Encryption has not been enabled

Issue: -

## Description

If your organization is subject to corporate or regulatory policies that require encryption of data and metadata at rest, we recommend creating a file system that is encrypted at rest, and mounting your file system using encryption of data in transit.

**Resolution**: Enable encryption for EFS.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_efs_file_system" "bad_example" {
  name       = "bar"
  encrypted  = false
  kms_key_id = ""
}
```

Example of **correct** code:

```terraform
resource "aws_efs_file_system" "good_example" {
  name       = "bar"
  encrypted  = true
  kms_key_id = "my_kms_key"
}
```