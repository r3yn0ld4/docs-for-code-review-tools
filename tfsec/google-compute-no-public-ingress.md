Pattern: An inbound firewall rule allows traffic from /0

Issue: -

## Description

Network security rules should not use very broad subnets.

Where possible, segments should be broken into smaller subnets and avoid using the `/0` subnet.

**Resolution**: Set a more restrictive cidr range.

## Examples

Example of **incorrect** code:

```terraform
resource "google_compute_firewall" "bad_example" {
	source_ranges = ["0.0.0.0/0"]
}
```

Example of **correct** code:

```terraform
resource "google_compute_firewall" "good_example" {
	source_ranges = ["1.2.3.4/32"]
}
```