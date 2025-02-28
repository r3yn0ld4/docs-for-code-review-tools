Pattern: Legacy metadata endpoints enabled

Issue: -

## Description

The Compute Engine instance metadata server exposes legacy v0.1 and v1beta1 endpoints, which do not enforce metadata query headers. 

This is a feature in the v1 APIs that makes it more difficult for a potential attacker to retrieve instance metadata. 

Unless specifically required, we recommend you disable these legacy APIs.

When setting the `metadata` block, the default value for `disable-legacy-endpoints` is set to true, they should not be explicitly enabled.

**Resolution**: Disable legacy metadata endpoints.

## Examples

Example of **incorrect** code:

```terraform
resource "google_container_cluster" "bad_example" {
	metadata {
    disable-legacy-endpoints = false
  }
}
```

Example of **correct** code:

```terraform
resource "google_container_cluster" "good_example" {
	metadata {
    disable-legacy-endpoints = true
  }
}
```