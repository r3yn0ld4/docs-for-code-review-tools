Pattern: EKS should have the encryption of secrets enabled

Issue: -

## Description

EKS cluster resources should have the encryption_config block set with protection of the secrets resource.

**Resolution**: Enable encryption of EKS secrets.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_eks_cluster" "bad_example" {
    name = "bad_example_cluster"

    role_arn = var.cluster_arn
    vpc_config {
        endpoint_public_access = false
    }
}
```

Example of **correct** code:

```terraform
resource "aws_eks_cluster" "good_example" {
    encryption_config {
        resources = [ "secrets" ]
        provider {
            key_arn = var.kms_arn
        }
    }

    name = "good_example_cluster"
    role_arn = var.cluster_arn
    vpc_config {
        endpoint_public_access = false
    }
}
```