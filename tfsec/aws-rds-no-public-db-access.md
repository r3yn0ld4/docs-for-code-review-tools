Pattern: A database resource is marked as publicly accessible

Issue: -

## Description

Database resources should not publicly available. You should limit all access to the minimum that is required for your application to function.

**Resolution**: Set the database to not be publically accessible.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_db_instance" "bad_example" {
	publicly_accessible = true
}
```

Example of **correct** code:

```terraform
resource "aws_db_instance" "good_example" {
	publicly_accessible = false
}
```