Pattern: Shielded GKE nodes not enabled

Issue: -

## Description

CIS GKE Benchmark Recommendation: 6.5.5. Ensure Shielded GKE Nodes are Enabled

Shielded GKE Nodes provide strong, verifiable node identity and integrity to increase the security of GKE nodes and should be enabled on all GKE clusters.

**Resolution**: Enable node shielding.

## Examples

Example of **incorrect** code:

```terraform
resource "google_container_cluster" "bad_example" {
	enable_shielded_nodes = "false"
}
```

Example of **correct** code:

```terraform
resource "google_container_cluster" "good_example" {
	enable_shielded_nodes = "true"
}
```