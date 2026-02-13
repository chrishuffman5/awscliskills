# AWS CLI Skills for Claude Code

A unified AWS CLI v2 reference skill for [Claude Code](https://claude.ai/code). Provides comprehensive command references — flags, types, defaults, and JSON output schemas — for 31 AWS services, sourced from official AWS documentation.

## Covered Services

| Service | Reference | Scope |
|---------|-----------|-------|
| ECS | `references/ecs/` | Clusters, services, tasks, task definitions, container instances, capacity providers |
| EC2 | `references/ec2/` | Instances, VPCs, subnets, security groups, key pairs, AMIs, launch templates, auto scaling |
| ECR | `references/ecr/` | Repositories, images, lifecycle policies, scanning, authentication, registry |
| S3 | `references/s3/` | Buckets, objects, storage classes, lifecycle, versioning, website hosting, presigned URLs |
| RDS | `references/rds/` | DB instances, Aurora clusters, snapshots, parameter groups, subnet groups, replicas, proxies |
| Route 53 | `references/route53/` | Hosted zones, DNS records, health checks, routing policies, domain registration |
| IAM | `references/iam/` | Users, groups, roles, policies, instance profiles, access keys, MFA, identity providers |
| CloudWatch | `references/cloudwatch/` | Metrics, alarms, dashboards, log groups, log streams, metric filters, Insights queries |
| ELBv2 | `references/elbv2/` | ALBs, NLBs, target groups, listeners, rules, health checks, SSL certificates |
| Lambda | `references/lambda/` | Functions, layers, event source mappings, aliases, versions, concurrency, URLs |
| DynamoDB | `references/dynamodb/` | Tables, items, indexes, queries, scans, streams, backups, global tables, TTL |
| KMS | `references/kms/` | Encryption keys, key policies, grants, aliases, encrypt/decrypt, key rotation, multi-region |
| SNS | `references/sns/` | Topics, subscriptions, publishing, SMS, platform applications, message filtering |
| SQS | `references/sqs/` | Standard and FIFO queues, messages, dead-letter queues, visibility timeout, long polling |
| CloudFront | `references/cloudfront/` | Distributions, origins, cache behaviors, invalidations, functions, origin access control |
| Secrets Manager | `references/secretsmanager/` | Secrets, versions, rotation, replication, resource policies, batch retrieval |
| API Gateway | `references/apigateway/` | REST APIs, HTTP APIs, resources, methods, stages, authorizers, API keys, usage plans |
| Step Functions | `references/stepfunctions/` | State machines, executions, activities, map runs, versions |
| Cognito | `references/cognito/` | User pools, user pool clients, users, groups, identity providers, identity pools, MFA |
| SES v2 | `references/sesv2/` | Email identities, configuration sets, contact lists, templates, sending, suppression |
| EventBridge | `references/eventbridge/` | Event buses, rules, targets, archives, replays, connections, API destinations, pipes |
| Systems Manager | `references/ssm/` | Parameter Store, documents, Run Command, Session Manager, patch baselines, state manager |
| ACM | `references/acm/` | Certificates, import/export, validation, tags, account configuration |
| STS | `references/sts/` | Assume role, session tokens, federation, caller identity |
| CloudTrail | `references/cloudtrail/` | Trails, event selectors, event data stores, queries, channels, imports |
| EFS | `references/efs/` | File systems, mount targets, access points, replication, lifecycle |
| ElastiCache | `references/elasticache/` | Clusters, replication groups, parameter groups, snapshots, users, serverless |
| WAF v2 | `references/wafv2/` | Web ACLs, rule groups, IP sets, regex pattern sets, logging |
| CodeBuild | `references/codebuild/` | Projects, builds, build batches, report groups, source credentials, webhooks, fleets |
| CodeDeploy | `references/codedeploy/` | Applications, deployment groups, deployments, deployment configs, revisions |
| CodePipeline | `references/codepipeline/` | Pipelines, stages, actions, action types, webhooks |

## Adding the Skill to Your Project

Claude Code loads skills from a `skills/` directory in your project root. Copy the single `aws-cli` skill directory into your project:

```bash
# From your project root
cp -r /path/to/awscliskills/skills/aws-cli skills/
```

That's it — one directory gives you all 31 services.

### Alternative: Git subtree (stays synced with updates)

```bash
git subtree add --prefix=skills/aws-cli https://github.com/chrishuffman5/awscliskills.git main --squash
```

### What gets loaded

- Claude Code reads `SKILL.md` and uses the YAML frontmatter (`name`, `description`) to decide when the skill is relevant to your current task.
- `SKILL.md` contains general CLI conventions (output formats, `--query`, pagination, waiters) and a service index table pointing to per-service overview files.
- Each service has a `references/<service>/` directory with an `overview.md` (service overview + workflows + command reference table), `index.md` (quick reference), and per-command-group files (e.g., `clusters.md`, `services.md`).
- Progressive disclosure: `SKILL.md` → `overview.md` → group files. Claude only loads the specific command groups needed, reducing token cost by ~70-80%.

## Skill File Format

```
skills/aws-cli/
  SKILL.md                        # General CLI conventions + service index table
  references/
    ecs/                          # One directory per service
      overview.md                 # Service overview + common workflows + command ref table
      index.md                    # Quick reference table + global options
      clusters.md                 # Per-command-group reference files
      services.md
      tasks.md
      ...
    ec2/
    ecr/
    ... (31 service directories)
```

**SKILL.md** contains:
- YAML frontmatter with `name` and `description` (used by Claude Code for skill matching)
- General CLI conventions (output formats, `--query`, pagination, waiters)
- Service index table mapping each service to its `overview.md`

**references/\<service\>/overview.md** contains:
- Service overview
- Quick reference with common workflow examples
- Covered command groups table
- Command reference table mapping each group to its reference file

**references/\<service\>/index.md** contains:
- Quick reference table of all subcommands
- Global options reference

**references/\<service\>/\<group\>.md** files each contain:
- All commands in that group with:
  - Description
  - Required parameters table (parameter, type, description)
  - Optional parameters table (parameter, type, default, description)
  - JSON output schema

This split structure means Claude only loads the specific command groups needed for a task, reducing token cost by ~70-80% compared to loading a monolithic reference file.
