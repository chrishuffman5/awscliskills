---
name: aws-cli
description: >-
  AWS CLI v2 command reference for 190 AWS services. Covers CLI conventions
  (output formats, --query, pagination, waiters) and routes to per-service
  sub-skills with complete flags, types, defaults, and JSON output schemas.
  Use for any AWS resource management via the CLI.
---

# AWS CLI v2 Reference

Complete AWS CLI v2 command reference covering 190 services. Each service is a self-contained
sub-skill in its own folder, named after its `aws` CLI command. This top-level skill gives you the
CLI conventions plus a routing protocol — read only the one service you need, not the whole catalog.

## Routing — find the right service

Each service lives at `<aws-command>/SKILL.md`, where `<aws-command>` is the AWS CLI service name.
**If you already know the service, read its `SKILL.md` directly — do not load the full index.**

- `aws s3 …`        → [`s3/SKILL.md`](s3/SKILL.md)
- `aws ec2 …`       → [`ec2/SKILL.md`](ec2/SKILL.md)
- `aws dynamodb …`  → [`dynamodb/SKILL.md`](dynamodb/SKILL.md)
- `aws lambda …`    → [`lambda/SKILL.md`](lambda/SKILL.md)
- `aws iam …`       → [`iam/SKILL.md`](iam/SKILL.md)

Each service's `SKILL.md` has an overview, common workflows, and a command-group index. The
command-group files alongside it (e.g. `instances.md`, `vpc.md`) hold the full per-command flags,
types, defaults, and JSON output schemas.

**If you don't know the CLI name** (e.g. "which service gives me a CDN?", or you only know the
marketing name), read [`service-index.md`](service-index.md) — the full table of all 190 services
with friendly names, sub-skill paths, and scope.

### Non-obvious name → folder mappings

The folder is the `aws` command name, which sometimes differs from the marketing name:

| Service (marketing) | Folder / `aws` command |
|---|---|
| Cloud Map | `servicediscovery` |
| AWS Config | `configservice` |
| Private CA (ACM PCA) | `acm-pca` |
| Managed Grafana | `grafana` |
| Managed Prometheus | `amp` |
| Chime SDK | `chime` |
| ELB Classic | `elb` (ALB/NLB → `elbv2`) |
| Application Discovery | `discovery` |
| Cost Explorer | `ce` (Cost & Usage Report → `cur`) |
| CloudHSM | `cloudhsmv2` |
| SES v2 | `sesv2` |
| Lex v2 | `lex` |
| Resource Explorer | `resource-explorer-2` |
| Snow Family | `snowball` |
| Step Functions | `stepfunctions` |
| Systems Manager | `ssm` |
| EC2 Image Builder | `imagebuilder` |

For anything not listed, the folder matches the `aws <service>` subcommand. See
[`service-index.md`](service-index.md) for the complete list.

**REQUIRED:** Read the target service's `SKILL.md` before constructing commands for it.

## General CLI Conventions

### Output Formats

```bash
--output json    # Default. Full JSON response.
--output text    # Tab-delimited. Good for scripting with awk/cut.
--output table   # Human-readable table.
--output yaml    # YAML format.
```

### Filtering with --query (JMESPath)

```bash
# Single field
aws ecs describe-clusters --query 'clusters[0].clusterArn'

# Multiple fields
aws ec2 describe-instances --query 'Reservations[].Instances[].[InstanceId,State.Name]'

# Filter by value
aws ecs list-services --query 'serviceArns[?contains(@,`my-service`)]'

# Flatten nested arrays
aws ec2 describe-instances --query 'Reservations[].Instances[].InstanceId'
```

### Pagination

```bash
--no-paginate          # Disable automatic pagination (get first page only)
--max-items N          # Limit total items returned
--page-size N          # Items per API call (controls request size, not total)
--starting-token TOK   # Resume from previous NextToken
```

Most `list-*` and `describe-*` commands paginate automatically in CLI v2.

### Waiters

Wait for a resource to reach a specific state. Format: `aws <service> wait <waiter-name>`.

```bash
aws ecs wait services-stable --cluster my-cluster --services my-service
aws ecs wait tasks-running --cluster my-cluster --tasks arn:aws:ecs:...
aws ecs wait tasks-stopped --cluster my-cluster --tasks arn:aws:ecs:...
aws ec2 wait instance-running --instance-ids i-1234567890abcdef0
aws ec2 wait instance-terminated --instance-ids i-1234567890abcdef0
aws ec2 wait vpc-available --vpc-ids vpc-123
aws ec2 wait subnet-available --subnet-ids subnet-123
aws ec2 wait nat-gateway-available --nat-gateway-ids nat-123
```

Waiters poll at intervals and timeout after a set number of attempts. Use `--cli-read-timeout` and `--cli-connect-timeout` to adjust.

### Common Global Options

```bash
--region REGION        # Override default region
--profile PROFILE      # Use named profile from ~/.aws/config
--no-cli-pager         # Disable pager (useful in scripts)
--cli-input-json       # Read input from JSON file: --cli-input-json file://input.json
--cli-input-yaml       # Read input from YAML file
--generate-cli-skeleton # Output input skeleton (for building --cli-input-json files)
--debug                # Full debug logging
--dry-run              # Supported by some EC2 commands — validates without executing
```

### JSON Input Files

For commands with complex input, use `--cli-input-json`:

```bash
# Generate skeleton
aws ecs register-task-definition --generate-cli-skeleton output > task-def.json

# Edit the skeleton, then use it
aws ecs register-task-definition --cli-input-json file://task-def.json
```

### Error Handling in Scripts

```bash
# Check exit code
if aws ecs describe-clusters --clusters my-cluster --query 'clusters[0].status' --output text | grep -q ACTIVE; then
  echo "Cluster is active"
fi

# Capture errors
result=$(aws ecs create-service --cli-input-json file://service.json 2>&1) || {
  echo "Failed: $result"
  exit 1
}
```

### ARN Format

```
arn:aws:<service>:<region>:<account-id>:<resource-type>/<resource-name>
```

Examples:
- `arn:aws:ecs:us-east-1:123456789012:cluster/my-cluster`
- `arn:aws:ecs:us-east-1:123456789012:service/my-cluster/my-service`
- `arn:aws:ecs:us-east-1:123456789012:task-definition/my-task:1`
- `arn:aws:ecr:us-east-1:123456789012:repository/my-repo`

### Environment Variables

```bash
AWS_DEFAULT_REGION       # Default region
AWS_ACCESS_KEY_ID        # Access key
AWS_SECRET_ACCESS_KEY    # Secret key
AWS_SESSION_TOKEN        # Session token (temporary credentials)
AWS_PROFILE              # Named profile
AWS_DEFAULT_OUTPUT       # Default output format
```
