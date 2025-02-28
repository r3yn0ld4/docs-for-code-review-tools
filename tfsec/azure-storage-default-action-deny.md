Pattern: The default action on Storage account network rules should be set to deny

Issue: -

## Description

The default_action for network rules should come into effect when no other rules are matched.

The default action should be set to Deny.

**Resolution**: Set network rules to deny.

## Examples

Example of **incorrect** code:

```terraform
resource "azurerm_storage_account_network_rules" "bad_example" {
  
  default_action             = "Allow"
  ip_rules                   = ["127.0.0.1"]
  virtual_network_subnet_ids = [azurerm_subnet.test.id]
  bypass                     = ["Metrics"]
}
```

Example of **correct** code:

```terraform
resource "azurerm_storage_account_network_rules" "good_example" {
  
  default_action             = "Deny"
  ip_rules                   = ["127.0.0.1"]
  virtual_network_subnet_ids = [azurerm_subnet.test.id]
  bypass                     = ["Metrics"]
}
```