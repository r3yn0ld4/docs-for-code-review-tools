Pattern: It is AWS best practice to not use the default VPC for workflows

Issue: -

## Description

Default VPC does not have a lot of the critical security features that standard VPC comes with, new resources should not be created in the default VPC and it should not be present in the Terraform.

**Resolution**: Create a non-default vpc for resources to be created in.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_default_vpc" "default" {
	tags = {
	  Name = "Default VPC"
	}
  }
```

Example of **correct** code:

```terraform
# no aws default vpc present
```