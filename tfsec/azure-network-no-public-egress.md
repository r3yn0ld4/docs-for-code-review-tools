Pattern: An outbound network security rule allows traffic to /0

Issue: -

## Description

Network security rules should not use very broad subnets.

Where possible, segments should be broken into smaller subnets.

**Resolution**: Set a more restrictive cidr range.

## Examples

Example of **incorrect** code:

```terraform
resource "azurerm_network_security_rule" "bad_example" {
	direction = "Outbound"
	destination_address_prefix = "0.0.0.0/0"
	access = "Allow"
}
```

Example of **correct** code:

```terraform
resource "azurerm_network_security_rule" "good_example" {
	direction = "Outbound"
	destination_address_prefix = "10.0.0.0/16"
	access = "Allow"
}
```