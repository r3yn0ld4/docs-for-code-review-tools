Pattern: Legacy client authentication methods utilized

Issue: -

## Description

It is recommended to use Serivce Accounts and OAuth as authentication methods for accessing the master in the container cluster. 

Basic authentication should be disabled by explicitly unsetting the `username` and `password` on the `master_auth` block.

**Resolution**: Use service account or OAuth for authentication.

## Examples

Example of **incorrect** code:

```terraform
resource "google_container_cluster" "bad_example" {
}

resource "google_container_cluster" "gke" {
	master_auth {
	    username = ""
	    password = ""
		client_certificate_config {
			issue_client_certificate = true
	    }
	}
}
```

Example of **correct** code:

```terraform
resource "google_container_cluster" "good_example" {
	master_auth {
	    username = ""
	    password = ""
	}
}
```