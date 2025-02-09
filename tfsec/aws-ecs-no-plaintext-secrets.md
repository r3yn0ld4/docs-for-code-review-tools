Pattern: Task definition defines sensitive environment variable(s)

Issue: -

## Description

You should not make secrets available to a user in plaintext in any scenario. Secrets can instead be pulled from a secure secret storage system by the service requiring them.

**Resolution**: Use secrets for the task definition.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_ecs_task_definition" "bad_example" {
  container_definitions = <<EOF
[
  {
    "name": "my_service",
    "essential": true,
    "memory": 256,
    "environment": [
      { "name": "ENVIRONMENT", "value": "development" },
      { "name": "DATABASE_PASSWORD", "value": "oh no D:"}
    ]
  }
]
EOF

}
```

Example of **correct** code:

```terraform
resource "aws_ecs_task_definition" "good_example" {
  container_definitions = <<EOF
[
  {
    "name": "my_service",
    "essential": true,
    "memory": 256,
    "environment": [
      { "name": "ENVIRONMENT", "value": "development" }
    ]
  }
]
EOF

}
```