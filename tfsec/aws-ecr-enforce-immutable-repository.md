Pattern: ECR images tags shouldn't be mutable

Issue: -

## Description

ECR images should be set to IMMUTABLE to prevent code injection through image mutation.

This can be done by setting `image_tab_mutability` to `IMMUTABLE`

**Resolution**: Only use immutable images in ECR.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_ecr_repository" "bad_example" {
  name                 = "bar"
  image_tag_mutability = "MUTABLE"

  image_scanning_configuration {
    scan_on_push = true
  }
}
```

Example of **correct** code:

```terraform
resource "aws_ecr_repository" "good_example" {
  name                 = "bar"
  image_tag_mutability = "IMMUTABLE"

  image_scanning_configuration {
    scan_on_push = true
  }
}
```