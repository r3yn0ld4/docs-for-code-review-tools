Pattern: Ensure AKS logging to Azure Monitoring is Configured

Issue: -

## Description

Ensure AKS logging to Azure Monitoring is configured for containers to monitor the performance of workloads.

**Resolution**: Enable logging for AKS.

## Examples

Example of **incorrect** code:

```terraform
resource "azurerm_kubernetes_cluster" "bad_example" {
    addon_profile {}
}
```

Example of **correct** code:

```terraform
resource "azurerm_kubernetes_cluster" "good_example" {
    addon_profile {
		oms_agent {
			enabled = true
		}
	}
}
```