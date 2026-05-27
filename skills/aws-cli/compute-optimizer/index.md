# AWS CLI v2 -- Compute Optimizer Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/compute-optimizer/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `get-enrollment-status` | Enrollment | Get account enrollment status |
| `get-enrollment-statuses-for-organization` | Enrollment | Get enrollment statuses across organization |
| `update-enrollment-status` | Enrollment | Enroll or unenroll an account |
| `get-ec2-instance-recommendations` | Recommendations | Get EC2 instance recommendations |
| `get-ec2-recommendation-projected-metrics` | Recommendations | Get projected metrics for EC2 recommendations |
| `get-auto-scaling-group-recommendations` | Recommendations | Get Auto Scaling group recommendations |
| `get-ebs-volume-recommendations` | Recommendations | Get EBS volume recommendations |
| `get-lambda-function-recommendations` | Recommendations | Get Lambda function recommendations |
| `get-ecs-service-recommendations` | Recommendations | Get ECS service recommendations |
| `get-ecs-service-projected-metrics` | Recommendations | Get projected metrics for ECS services |
| `get-rds-database-recommendations` | Recommendations | Get RDS database recommendations |
| `get-rds-database-recommendation-projected-metrics` | Recommendations | Get projected metrics for RDS |
| `get-idle-recommendations` | Recommendations | Get idle resource recommendations |
| `get-recommendation-summaries` | Recommendations | Get summary of recommendations by resource type |
| `describe-recommendation-export-jobs` | Recommendations | Describe recommendation export jobs |
| `export-ec2-instance-recommendations` | Exports | Export EC2 recommendations to S3 |
| `export-auto-scaling-group-recommendations` | Exports | Export ASG recommendations to S3 |
| `export-ebs-volume-recommendations` | Exports | Export EBS recommendations to S3 |
| `export-lambda-function-recommendations` | Exports | Export Lambda recommendations to S3 |
| `export-ecs-service-recommendations` | Exports | Export ECS service recommendations to S3 |
| `export-rds-database-recommendations` | Exports | Export RDS recommendations to S3 |
| `export-idle-recommendations` | Exports | Export idle resource recommendations to S3 |
| `get-effective-recommendation-preferences` | Preferences | Get effective preferences for a resource |
| `get-recommendation-preferences` | Preferences | Get recommendation preferences |
| `put-recommendation-preferences` | Preferences | Set recommendation preferences |
| `delete-recommendation-preferences` | Preferences | Delete recommendation preferences |

---

## Global Options

These options are available on ALL `aws compute-optimizer` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Finding Classifications

| Finding | Description |
|---------|-------------|
| `Underprovisioned` | Resource is underprovisioned and may experience performance issues |
| `Overprovisioned` | Resource is overprovisioned and could be downsized to save costs |
| `Optimized` | Resource is well-matched to workload |
| `NotOptimized` | Resource could benefit from optimization |

### Recommendation Resource Types

| Type | Description |
|------|-------------|
| `Ec2Instance` | EC2 instances |
| `AutoScalingGroup` | Auto Scaling groups |
| `EbsVolume` | EBS volumes |
| `LambdaFunction` | Lambda functions |
| `EcsService` | ECS services on Fargate |
| `RdsDBInstance` | RDS DB instances |
| `IdleResource` | Idle resources (EC2, EBS, ELB, RDS, etc.) |

### Export File Formats

| Format | Description |
|--------|-------------|
| `Csv` | Comma-separated values |

### Enhanced Infrastructure Metrics

When enabled, Compute Optimizer analyzes metrics over a 3-month period (instead of the default 14 days) for better recommendations. Requires opt-in.

### Recommendation Preferences Scope

| Scope | Description |
|-------|-------------|
| `Organization` | Apply to entire organization |
| `AccountId` | Apply to a specific account |
| `ResourceArn` | Apply to a specific resource |
