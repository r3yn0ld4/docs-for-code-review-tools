Pattern: S3 Access block should block public policy

Issue: -

## Description

S3 bucket policy should have block public policy to prevent users from PUTing a policy that enable public access.

**Resolution**: Prevent policies that allow public access being PUT.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_s3_bucket_public_access_block" "bad_example" {
	bucket = aws_s3_bucket.example.id
}

resource "aws_s3_bucket_public_access_block" "bad_example" {
	bucket = aws_s3_bucket.example.id
  
	block_public_policy = false
}
```

Example of **correct** code:

```terraform
resource "aws_s3_bucket_public_access_block" "good_example" {
	bucket = aws_s3_bucket.example.id
  
	block_public_policy = true
}
```