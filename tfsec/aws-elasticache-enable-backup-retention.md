Pattern: Redis cluster should be backup retention turned on

Issue: -

## Description

Redis clusters should have a snapshot retention time to ensure that they are backed up and can be restored if required.

**Resolution**: Configure snapshot retention for redis cluster.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_elasticache_cluster" "bad_example" {
	cluster_id           = "cluster-example"
	engine               = "redis"
	node_type            = "cache.m4.large"
	num_cache_nodes      = 1
	parameter_group_name = "default.redis3.2"
	engine_version       = "3.2.10"
	port                 = 6379
}
```

Example of **correct** code:

```terraform
resource "aws_elasticache_cluster" "good_example" {
	cluster_id           = "cluster-example"
	engine               = "redis"
	node_type            = "cache.m4.large"
	num_cache_nodes      = 1
	parameter_group_name = "default.redis3.2"
	engine_version       = "3.2.10"
	port                 = 6379

	snapshot_retention_limit = 5
}
```