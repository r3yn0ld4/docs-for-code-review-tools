Pattern: Disabled DNSSEC for Cloud DNS

Issue: -

## Description

DNSSEC authenticates DNS responses, preventing MITM attacks and impersonation.

**Resolution**: Enable DNSSEC.

## Examples

Example of **incorrect** code:

```terraform
resource "google_dns_managed_zone" "bad_example" {
  name        = "example-zone"
  dns_name    = "example-${random_id.rnd.hex}.com."
  description = "Example DNS zone"
  labels = {
    foo = "bar"
  }
  dnssec_config {
    state = "off"
  }
}

resource "random_id" "rnd" {
  byte_length = 4
}
```

Example of **correct** code:

```terraform
resource "google_dns_managed_zone" "good_example" {
  name        = "example-zone"
  dns_name    = "example-${random_id.rnd.hex}.com."
  description = "Example DNS zone"
  labels = {
    foo = "bar"
  }
  dnssec_config {
    state = "on"
  }
}

resource "random_id" "rnd" {
  byte_length = 4
}
```