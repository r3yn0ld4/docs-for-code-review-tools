Pattern: EKS Clusters should have cluster control plane logging turned on

Issue: -

## Description

By default cluster control plane logging is not turned on. Logging is available for audit, api, authenticator, controllerManager and scheduler. All logging should be turned on for cluster control plane.

**Resolution**: Enable logging for the EKS control plane.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_eks_cluster" "bad_example" {
    encryption_config {
        resources = [ "secrets" ]
        provider {
            key_arn = var.kms_arn
        }
    }

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

	enabled_cluster_log_types = ["api", "authenticator", "audit", "scheduler", "controllerManager"]

    name = "good_example_cluster"
    role_arn = var.cluster_arn
    vpc_config {
        endpoint_public_access = false
    }
}
```