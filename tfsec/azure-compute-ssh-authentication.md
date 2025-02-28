Pattern: Password authentication in use instead of SSH keys

Issue: -

## Description

Access to instances should be authenticated using SSH keys. Removing the option of password authentication enforces more secure methods while removing the risks inherent with passwords.

**Resolution**: Use SSH keys for authentication.

## Examples

Example of **incorrect** code:

```terraform
resource "azurerm_virtual_machine" "bad_example" {
	os_profile_linux_config {
		disable_password_authentication = false
	}
}
```

Example of **correct** code:

```terraform
resource "azurerm_virtual_machine" "good_example" {
	os_profile_linux_config {
		disable_password_authentication = true
	}
}
```