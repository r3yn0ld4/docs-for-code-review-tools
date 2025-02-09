Pattern: aws_instance should activate session tokens for Instance Metadata Service

Issue: -

## Description

IMDS v2 (Instance Metadata Service) introduced session authentication tokens which improve security when talking to IMDS.
By default `aws_instance` resource sets IMDS session auth tokens to be optional. 
To fully protect IMDS you need to enable session tokens by using `metadata_options` block and its `http_tokens` variable set to `required`.

**Resolution**: Enable HTTP token requirement for IMDS.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_instance" "bad_example" {
  ami           = "ami-005e54dee72cc1d00"
  instance_type = "t2.micro"
}
```

Example of **correct** code:

```terraform
resource "aws_instance" "good_example" {
  ami           = "ami-005e54dee72cc1d00"
  instance_type = "t2.micro"
  metadata_options {
	http_tokens = "required"
  }	
}
```