Pattern: An ingress Network ACL rule allows ALL ports from /0

Issue: -

## Description

Opening up ACLs to the public internet is potentially dangerous. You should restrict access to IP addresses or ranges that explicitly require it where possible, and ensure that you specify required ports.

**Resolution**: Set a more restrictive cidr range.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_network_acl_rule" "bad_example" {
  egress         = false
  protocol       = "all"
  rule_action    = "allow"
  cidr_block     = "0.0.0.0/0"
}
```

Example of **correct** code:

```terraform
resource "aws_network_acl_rule" "good_example" {
  egress         = false
  protocol       = "tcp"
  from_port      = 22
  to_port        = 22
  rule_action    = "allow"
  cidr_block     = "0.0.0.0/0"
}
```