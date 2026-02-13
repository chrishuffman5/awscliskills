---
name: aws-cli
description: >-
  Use when working with any AWS CLI v2 commands. Covers general CLI conventions
  (output formats, --query, pagination, waiters) and provides per-service
  references for ECS, EC2, ECR, S3, RDS, Route 53, IAM, CloudWatch, ELBv2,
  Lambda, DynamoDB, KMS, SNS, SQS, CloudFront, Secrets Manager, API Gateway,
  Step Functions, Cognito, SES v2, EventBridge, Systems Manager, ACM, STS,
  CloudTrail, EFS, ElastiCache, WAF v2, CodeBuild, CodeDeploy, CodePipeline,
  Cost Explorer, Budgets, Cost and Usage Report, Pricing, Savings Plans,
  Billing, Marketplace Catalog, License Manager, AWS Health,
  Payment Cryptography, Location Services, Resource Explorer, GameLift,
  Well-Architected, Resilience Hub, Resource Groups Tagging API, Config,
  Organizations, and Compute Optimizer.
  Use this skill for any task involving AWS resource creation, management,
  querying, or teardown via the CLI.
---

# AWS CLI v2 General Reference

## Overview

Unified AWS CLI v2 reference skill. Contains general conventions shared across all services plus per-service command references. Read the service overview for the AWS service you are working with.

## Service Index

| Service | Reference | Scope |
|---------|-----------|-------|
| ECS | [`ecs/overview.md`](references/ecs/overview.md) | Clusters, services, tasks, task definitions, container instances, capacity providers |
| EC2 | [`ec2/overview.md`](references/ec2/overview.md) | Instances, VPCs, subnets, security groups, key pairs, AMIs, launch templates, auto scaling |
| ECR | [`ecr/overview.md`](references/ecr/overview.md) | Repositories, images, lifecycle policies, scanning, authentication, registry |
| S3 | [`s3/overview.md`](references/s3/overview.md) | Buckets, objects, storage classes, lifecycle, versioning, website hosting, presigned URLs |
| RDS | [`rds/overview.md`](references/rds/overview.md) | DB instances, Aurora clusters, snapshots, parameter groups, subnet groups, replicas, proxies |
| Route 53 | [`route53/overview.md`](references/route53/overview.md) | Hosted zones, DNS records, health checks, routing policies, domain registration |
| IAM | [`iam/overview.md`](references/iam/overview.md) | Users, groups, roles, policies, instance profiles, access keys, MFA, identity providers |
| CloudWatch | [`cloudwatch/overview.md`](references/cloudwatch/overview.md) | Metrics, alarms, dashboards, log groups, log streams, metric filters, Insights queries |
| ELBv2 | [`elbv2/overview.md`](references/elbv2/overview.md) | ALBs, NLBs, target groups, listeners, rules, health checks, SSL certificates |
| Lambda | [`lambda/overview.md`](references/lambda/overview.md) | Functions, layers, event source mappings, aliases, versions, concurrency, URLs |
| DynamoDB | [`dynamodb/overview.md`](references/dynamodb/overview.md) | Tables, items, indexes, queries, scans, streams, backups, global tables, TTL |
| KMS | [`kms/overview.md`](references/kms/overview.md) | Encryption keys, key policies, grants, aliases, encrypt/decrypt, key rotation, multi-region |
| SNS | [`sns/overview.md`](references/sns/overview.md) | Topics, subscriptions, publishing, SMS, platform applications, message filtering |
| SQS | [`sqs/overview.md`](references/sqs/overview.md) | Standard and FIFO queues, messages, dead-letter queues, visibility timeout, long polling |
| CloudFront | [`cloudfront/overview.md`](references/cloudfront/overview.md) | Distributions, origins, cache behaviors, invalidations, functions, origin access control |
| Secrets Manager | [`secretsmanager/overview.md`](references/secretsmanager/overview.md) | Secrets, versions, rotation, replication, resource policies, batch retrieval |
| API Gateway | [`apigateway/overview.md`](references/apigateway/overview.md) | REST APIs, HTTP APIs, resources, methods, stages, authorizers, API keys, usage plans |
| Step Functions | [`stepfunctions/overview.md`](references/stepfunctions/overview.md) | State machines, executions, activities, map runs, versions |
| Cognito | [`cognito/overview.md`](references/cognito/overview.md) | User pools, user pool clients, users, groups, identity providers, identity pools, MFA |
| SES v2 | [`sesv2/overview.md`](references/sesv2/overview.md) | Email identities, configuration sets, contact lists, templates, sending, suppression |
| EventBridge | [`eventbridge/overview.md`](references/eventbridge/overview.md) | Event buses, rules, targets, archives, replays, connections, API destinations, pipes |
| Systems Manager | [`ssm/overview.md`](references/ssm/overview.md) | Parameter Store, documents, Run Command, Session Manager, patch baselines, state manager |
| ACM | [`acm/overview.md`](references/acm/overview.md) | Certificates, import/export, validation, tags, account configuration |
| STS | [`sts/overview.md`](references/sts/overview.md) | Assume role, session tokens, federation, caller identity |
| CloudTrail | [`cloudtrail/overview.md`](references/cloudtrail/overview.md) | Trails, event selectors, event data stores, queries, channels, imports |
| EFS | [`efs/overview.md`](references/efs/overview.md) | File systems, mount targets, access points, replication, lifecycle |
| ElastiCache | [`elasticache/overview.md`](references/elasticache/overview.md) | Clusters, replication groups, parameter groups, snapshots, users, serverless |
| WAF v2 | [`wafv2/overview.md`](references/wafv2/overview.md) | Web ACLs, rule groups, IP sets, regex pattern sets, logging |
| CodeBuild | [`codebuild/overview.md`](references/codebuild/overview.md) | Projects, builds, build batches, report groups, source credentials, webhooks, fleets |
| CodeDeploy | [`codedeploy/overview.md`](references/codedeploy/overview.md) | Applications, deployment groups, deployments, deployment configs, revisions |
| CodePipeline | [`codepipeline/overview.md`](references/codepipeline/overview.md) | Pipelines, stages, actions, action types, webhooks |
| Cost Explorer | [`ce/overview.md`](references/ce/overview.md) | Cost and usage, forecasts, anomalies, savings plans, reservations, rightsizing |
| Budgets | [`budgets/overview.md`](references/budgets/overview.md) | Budgets, budget actions, notifications, subscribers |
| Cost and Usage Report | [`cur/overview.md`](references/cur/overview.md) | Report definitions, S3 delivery |
| Pricing | [`pricing/overview.md`](references/pricing/overview.md) | Services, products, attribute values, price lists |
| Savings Plans | [`savingsplans/overview.md`](references/savingsplans/overview.md) | Savings plans, rates, offerings |
| Billing | [`billing/overview.md`](references/billing/overview.md) | Billing views, source views, resource policies |
| Marketplace Catalog | [`marketplace-catalog/overview.md`](references/marketplace-catalog/overview.md) | Entities, change sets, resource policies |
| License Manager | [`license-manager/overview.md`](references/license-manager/overview.md) | Licenses, grants, configurations, Linux subscriptions, user subscriptions |
| AWS Health | [`health/overview.md`](references/health/overview.md) | Events, affected entities, organization events |
| Payment Cryptography | [`payment-cryptography/overview.md`](references/payment-cryptography/overview.md) | Keys, encryption, PIN/MAC operations, card validation |
| Location Services | [`location/overview.md`](references/location/overview.md) | Maps, places, routes, geofences, trackers, API keys |
| Resource Explorer | [`resource-explorer-2/overview.md`](references/resource-explorer-2/overview.md) | Indexes, views, search, supported resource types |
| GameLift | [`gamelift/overview.md`](references/gamelift/overview.md) | Fleets, builds, game sessions, matchmaking, server groups |
| Well-Architected | [`wellarchitected/overview.md`](references/wellarchitected/overview.md) | Workloads, lenses, reviews, milestones, profiles |
| Resilience Hub | [`resiliencehub/overview.md`](references/resiliencehub/overview.md) | Apps, resiliency policies, assessments, recommendations |
| Resource Groups Tagging API | [`resourcegroupstaggingapi/overview.md`](references/resourcegroupstaggingapi/overview.md) | Cross-service tag management, resource discovery by tag, tag compliance reporting |
| Config | [`configservice/overview.md`](references/configservice/overview.md) | Config rules, conformance packs, recorders, delivery channels, remediation, aggregators, resource evaluation |
| Organizations | [`organizations/overview.md`](references/organizations/overview.md) | Organization management, accounts, OUs, policies (SCPs, tag, backup, AI opt-out), handshakes, delegated admin |
| Compute Optimizer | [`compute-optimizer/overview.md`](references/compute-optimizer/overview.md) | Resource optimization recommendations for EC2, EBS, Lambda, ASG, ECS, RDS, idle resources |

**REQUIRED:** Read the overview file for the AWS service you are working with.

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
