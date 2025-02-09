Pattern: ECR repository has image scans disabled

Issue: -

## Description

Repository image scans should be enabled to ensure vulnerable software can be discovered and remediated as soon as possible.

**Resolution**: Enable ECR image scanning.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_ecr_repository" "bad_example" {
  name                 = "bar"
  image_tag_mutability = "MUTABLE"

  image_scanning_configuration {
    scan_on_push = false
  }
}
```

Example of **correct** code:

```terraform
resource "aws_ecr_repository" "good_example" {
  name                 = "bar"
  image_tag_mutability = "MUTABLE"

  image_scanning_configuration {
    scan_on_push = true
  }
}
```