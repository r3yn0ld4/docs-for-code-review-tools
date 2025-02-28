Pattern: Ensure RBAC is enabled on AKS clusters

Issue: -

## Description

Using Kubernetes role-based access control (RBAC), you can grant users, groups, and service accounts access to only the resources they need.

**Resolution**: Enable RBAC.

## Examples

Example of **incorrect** code:

```terraform
resource "azurerm_kubernetes_cluster" "bad_example" {
	role_based_access_control {
		enabled = false
	}
}
```

Example of **correct** code:

```terraform
resource "azurerm_kubernetes_cluster" "good_example" {
	role_based_access_control {
		enabled = true
	}
}
```