Pattern: RDS Cluster and RDS instance should have backup retention longer than default 1 day

Issue: -

## Description

RDS backup retention for clusters defaults to 1 day, this may not be enough to identify and respond to an issue. Backup retention periods should be set to a period that is a balance on cost and limiting risk.

**Resolution**: Explicitly set the retention period to greater than the default.

## Examples

Example of **incorrect** code:

```terraform
resource "aws_db_instance" "bad_example" {
	allocated_storage    = 10
	engine               = "mysql"
	engine_version       = "5.7"
	instance_class       = "db.t3.micro"
	name                 = "mydb"
	username             = "foo"
	password             = "foobarbaz"
	parameter_group_name = "default.mysql5.7"
	skip_final_snapshot  = true
}

resource "aws_rds_cluster" "bad_example" {
	cluster_identifier      = "aurora-cluster-demo"
	engine                  = "aurora-mysql"
	engine_version          = "5.7.mysql_aurora.2.03.2"
	availability_zones      = ["us-west-2a", "us-west-2b", "us-west-2c"]
	database_name           = "mydb"
	master_username         = "foo"
	master_password         = "bar"
	preferred_backup_window = "07:00-09:00"
  }
```

Example of **correct** code:

```terraform
resource "aws_rds_cluster" "good_example" {
	cluster_identifier      = "aurora-cluster-demo"
	engine                  = "aurora-mysql"
	engine_version          = "5.7.mysql_aurora.2.03.2"
	availability_zones      = ["us-west-2a", "us-west-2b", "us-west-2c"]
	database_name           = "mydb"
	master_username         = "foo"
	master_password         = "bar"
	backup_retention_period = 5
	preferred_backup_window = "07:00-09:00"
  }

  resource "aws_db_instance" "good_example" {
	allocated_storage    = 10
	engine               = "mysql"
	engine_version       = "5.7"
	instance_class       = "db.t3.micro"
	name                 = "mydb"
	username             = "foo"
	password             = "foobarbaz"
	parameter_group_name = "default.mysql5.7"
	backup_retention_period = 5
	skip_final_snapshot  = true
}
```