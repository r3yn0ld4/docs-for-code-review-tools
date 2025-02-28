Pattern: Load balancers should drop invalid headers

Issue: -

## Description

Passing unknown or invalid headers through to the target poses a potential risk of compromise. 

By setting drop_invalid_header_fields to true, anything that doe not conform to well known, defined headers will be removed by the load balancer.

**Resolution**: Set drop_invalid_header_fields to true.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_alb" "bad_example" {
	name               = "bad_alb"
	internal           = false
	load_balancer_type = "application"
	
	access_logs {
	  bucket  = aws_s3_bucket.lb_logs.bucket
	  prefix  = "test-lb"
	  enabled = true
	}
  
	drop_invalid_header_fields = false
  }
```

Example of **correct** code:

```terraform
resource "aws_alb" "good_example" {
	name               = "good_alb"
	internal           = false
	load_balancer_type = "application"
	
	access_logs {
	  bucket  = aws_s3_bucket.lb_logs.bucket
	  prefix  = "test-lb"
	  enabled = true
	}
  
	drop_invalid_header_fields = true
  }
```