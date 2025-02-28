Pattern: ECR Repository should use customer managed keys to allow more control

Issue: -

## Description

Images in the ECR repository are encrypted by default using AWS managed encryption keys. To increase control of the encryption and control the management of factors like key rotation, use a Customer Managed Key.

**Resolution**: Use customer managed keys.

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
resource "aws_kms_key" "ecr_kms" {
	enable_key_rotation = true
}

resource "aws_ecr_repository" "good_example" {
	name                 = "bar"
	image_tag_mutability = "MUTABLE"
  
	image_scanning_configuration {
	  scan_on_push = true
	}

	encryption_configuration {
		encryption_type = "KMS"
		kms_key = aws_kms_key.ecr_kms.key_id
	}
  }
```