Pattern: Ensure AKS has an API Server Authorized IP Ranges enabled

Issue: -

## Description

The API server is the central way to interact with and manage a cluster. To improve cluster security and minimize attacks, the API server should only be accessible from a limited set of IP address ranges.

**Resolution**: Limit the access to the API server to a limited IP range.

## Examples

Example of **incorrect** code:

```terraform
resource "azurerm_kubernetes_cluster" "bad_example" {

}
```

Example of **correct** code:

```terraform
resource "azurerm_kubernetes_cluster" "good_example" {
    api_server_authorized_ip_ranges = [
		"1.2.3.4/32"
	]
}
```