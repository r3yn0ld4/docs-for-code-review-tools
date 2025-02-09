Pattern: EKS cluster should not have open CIDR range for public access

Issue: -

## Description

EKS Clusters have public access cidrs set to 0.0.0.0/0 by default which is wide open to the internet. This should be explicitly set to a more specific CIDR range

**Resolution**: Don't enable public access to EKS Clusters.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_eks_cluster" "bad_example" {
    // other config 

    name = "bad_example_cluster"
    role_arn = var.cluster_arn
    vpc_config {
        endpoint_public_access = true
    }
}
```

Example of **correct** code:

```terraform
resource "aws_eks_cluster" "good_example" {
    // other config 

    name = "good_example_cluster"
    role_arn = var.cluster_arn
    vpc_config {
        endpoint_public_access = true
        public_access_cidrs = ["10.2.0.0/8"]
    }
}
```