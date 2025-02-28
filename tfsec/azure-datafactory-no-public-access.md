Pattern: Data Factory should have public access disabled, the default is enabled

Issue: -

## Description

Data Factory has public access set to true by default.

Disabling public network access is applicable only to the self-hosted integration runtime, not to Azure Integration Runtime and SQL Server Integration Services (SSIS) Integration Runtime.

**Resolution**: Set public access to disabled for Data Factory.

## Examples

Example of **incorrect** code:

```terraform
resource "azurerm_data_factory" "bad_example" {
  name                = "example"
  location            = azurerm_resource_group.example.location
  resource_group_name = azurerm_resource_group.example.name
}
```

Example of **correct** code:

```terraform
resource "azurerm_data_factory" "good_example" {
  name                = "example"
  location            = azurerm_resource_group.example.location
  resource_group_name = azurerm_resource_group.example.name
  public_network_enabled = false
}
```