Pattern: Storage containers in blob storage mode should not have public access

Issue: -

## Description

Storage container public access should be off. It can be configured for blobs only, containers and blobs or off entirely. The default is off, with no public access.

Explicitly overriding publicAccess to anything other than off should be avoided.

**Resolution**: Disable public access to storage containers.

## Examples

Example of **incorrect** code:

```terraform
resource "azure_storage_container" "bad_example" {
	name                  = "terraform-container-storage"
	container_access_type = "blob"
	
	properties = {
		"publicAccess" = "blob"
	}
}
```

Example of **correct** code:

```terraform
resource "azure_storage_container" "good_example" {
	name                  = "terraform-container-storage"
	container_access_type = "blob"
	
	properties = {
		"publicAccess" = "off"
	}
}
```