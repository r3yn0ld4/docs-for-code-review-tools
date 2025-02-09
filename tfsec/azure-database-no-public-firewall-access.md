Pattern: Enabled public access for database firewall

Issue: -

## Description

Azure services can be allowed access through the firewall using a start and end IP address of 0.0.0.0. No other end ip address should be combined with a start of 0.0.0.0

**Resolution**: Don't use wide ip ranges for the sql firewall.

## Examples

Example of **incorrect** code:

```terraform
resource "azurerm_sql_firewall_rule" "bad_example" {
  name                = "bad_rule"
  resource_group_name = azurerm_resource_group.example.name
  server_name         = azurerm_sql_server.example.name
  start_ip_address    = "0.0.0.0"
  end_ip_address      = "255.255.255.255"
}

resource "azurerm_postgresql_firewall_rule" "bad_example" {
  name                = "bad_example"
  resource_group_name = azurerm_resource_group.example.name
  server_name         = azurerm_postgresql_server.example.name
  start_ip_address    = "0.0.0.0"
  end_ip_address      = "255.255.255.255"
}
```

Example of **correct** code:

```terraform
resource "azurerm_sql_firewall_rule" "good_example" {
  name                = "good_rule"
  resource_group_name = azurerm_resource_group.example.name
  server_name         = azurerm_sql_server.example.name
  start_ip_address    = "0.0.0.0"
  end_ip_address      = "0.0.0.0"
}
```