Pattern: AWS Classic resource usage

Issue: -

## Description

AWS Classic resources run in a shared environment with infrastructure owned by other AWS customers. You should run
resources in a VPC instead.

**Resolution**: Switch to VPC resources.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_db_security_group" "bad_example" {
  # ...
}
```

Example of **correct** code:

```terraform
resource "aws_security_group" "good_example" {
  # ...
}
```