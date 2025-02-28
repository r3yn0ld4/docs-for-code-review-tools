Pattern: Unencrypted compute disk

Issue: -

## Description

By default, Compute Engine encrypts all data at rest. Compute Engine handles and manages this encryption for you without any additional actions on your part.

If the `disk_encryption_key` block is included in the resource declaration then it *must* include a `raw_key` or `kms_key_self_link`.

To use the default offering of Google managed keys, do not include a `disk_encryption_key` block at all.

**Resolution**: Enable encrytion for compute disks.

## Examples

Example of **incorrect** code:

```terraform
resource "google_compute_disk" "bad_example" {
	# ... 
	disk_encryption_key {}
	# ...
}
```

Example of **correct** code:

```terraform
resource "google_compute_disk" "good_example" {
	disk_encryption_key {
		kms_key_self_link = "something"
	}
}

resource "google_compute_disk" "good_example" {
	disk_encryption_key {
		raw_key = "something"
	}
}
```