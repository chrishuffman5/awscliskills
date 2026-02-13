# Consolidate Into Single Skill — Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Merge all 16 service skills into the single `aws-cli` router skill so users get everything with one `cp -r` and Claude Code only indexes one skill.

**Architecture:** Move each service's reference files into `skills/aws-cli/references/<service>/`, convert each service SKILL.md body into an `overview.md`, update the router SKILL.md with a new description and service index pointing to overview files, delete the 16 separate `skills/aws-cli-*` directories.

**Tech Stack:** Git, Markdown, Agent Teams with Haiku model

---

## Current State

```
skills/
  aws-cli/                    # Router skill (SKILL.md only)
  aws-cli-ecs/                # 16 separate service skills
    SKILL.md                  # Frontmatter + overview + workflows + command ref table
    references/
      index.md                # Quick ref table + global options
      clusters.md             # Per-command-group files
      services.md
      ...
  aws-cli-ec2/
  ... (16 total)
```

## Target State

```
skills/
  aws-cli/                    # Single unified skill
    SKILL.md                  # Router + general conventions (updated description + service index)
    references/
      ecs/
        overview.md           # Service overview + common workflows + command ref table
        index.md              # Quick ref table + global options
        clusters.md           # Per-command-group files (unchanged)
        services.md
        ...
      ec2/
        overview.md
        index.md
        instances.md
        ...
      ... (16 service subdirectories)
```

## Per-Service File Counts

| Service | Group Files | +index.md | +overview.md | Total |
|---------|------------|-----------|-------------|-------|
| ecs | 13 | 1 | 1 | 15 |
| ec2 | 7 | 1 | 1 | 9 |
| ecr | 7 | 1 | 1 | 9 |
| s3 | 5 | 1 | 1 | 7 |
| rds | 11 | 1 | 1 | 13 |
| route53 | 9 | 1 | 1 | 11 |
| iam | 21 | 1 | 1 | 23 |
| cloudwatch | 20 | 1 | 1 | 22 |
| elbv2 | 10 | 1 | 1 | 12 |
| lambda | 14 | 1 | 1 | 16 |
| dynamodb | 18 | 1 | 1 | 20 |
| kms | 9 | 1 | 1 | 11 |
| sns | 11 | 1 | 1 | 13 |
| sqs | 5 | 1 | 1 | 7 |
| cloudfront | 18 | 1 | 1 | 20 |
| secretsmanager | 8 | 1 | 1 | 10 |

---

## Transformation Spec

For each of the 16 services, an agent performs these steps:

### Step 1: Create target directory

```bash
mkdir -p skills/aws-cli/references/<service>
```

### Step 2: Move reference files

```bash
git mv skills/aws-cli-<service>/references/*.md skills/aws-cli/references/<service>/
```

This moves all group files AND index.md in one command.

### Step 3: Create overview.md from SKILL.md body

Read `skills/aws-cli-<service>/SKILL.md`. Strip the YAML frontmatter (lines 1-4, the `---` delimiters and content between them). Write the remaining body to `skills/aws-cli/references/<service>/overview.md`.

The overview.md should also have its internal reference links updated from `references/` to `./` since the overview is now inside the references directory. For example:
- `[`references/index.md`](references/index.md)` → `[`index.md`](index.md)`
- `[`clusters.md`](references/clusters.md)` → `[`clusters.md`](clusters.md)`

### Step 4: Delete old service skill directory

```bash
git rm -r skills/aws-cli-<service>/
```

### Step 5: Commit

```bash
git add skills/aws-cli/references/<service>/ skills/aws-cli-<service>/
git commit -m "refactor: consolidate aws-cli-<service> into aws-cli skill

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>"
```

---

## Task Execution

### Task 0: Push current state

```bash
git status
git push
```

### Tasks 1-4: Migrate services (parallel, 4 Haiku agents)

| Agent | Services |
|-------|----------|
| merge-1 | ecs, ec2, ecr, s3 |
| merge-2 | rds, route53, iam, cloudwatch |
| merge-3 | elbv2, lambda, dynamodb, kms |
| merge-4 | sns, sqs, cloudfront, secretsmanager |

Each agent follows the Transformation Spec above for each of its 4 services.

### Task 5: Update SKILL.md (leader)

**File:** `skills/aws-cli/SKILL.md`

**Step 1: Update frontmatter description**

Replace the current description with:
```yaml
description: >-
  Use when working with any AWS CLI v2 commands. Covers general CLI conventions
  (output formats, --query, pagination, waiters) and provides per-service
  references for ECS, EC2, ECR, S3, RDS, Route 53, IAM, CloudWatch, ELBv2,
  Lambda, DynamoDB, KMS, SNS, SQS, CloudFront, and Secrets Manager. Use this
  skill for any task involving AWS resource creation, management, querying,
  or teardown via the CLI.
```

**Step 2: Update overview text**

Replace:
```markdown
Router skill for AWS CLI v2. Contains general conventions shared across all services. For command-specific reference, load the per-service skill.
```
With:
```markdown
Unified AWS CLI v2 reference skill. Contains general conventions shared across all services plus per-service command references. Read the service overview for the AWS service you are working with.
```

**Step 3: Update service index table**

Replace:
```markdown
| Service | Skill | Scope |
|---------|-------|-------|
| ECS | `aws-cli-ecs` | Clusters, services, tasks, ... |
```
With:
```markdown
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
```

**Step 4: Update instruction line**

Replace:
```markdown
**REQUIRED:** Load the per-service skill for the AWS service you are working with.
```
With:
```markdown
**REQUIRED:** Read the overview file for the AWS service you are working with.
```

**Step 5: Commit**
```bash
git add skills/aws-cli/SKILL.md
git commit -m "refactor: update aws-cli SKILL.md as unified single skill

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>"
```

### Task 6: Update CLAUDE.md and README.md (leader)

**CLAUDE.md changes:**
- Update skill hierarchy tree to show single `aws-cli/` directory with `references/<service>/` subdirectories
- Update "How Skills Work" section to describe single-skill architecture
- Update "Adding a New Service Skill" instructions

**README.md changes:**
- Simplify "Adding Skills to Your Project" — one `cp -r` command
- Remove Option 2 (cherry-picking individual services) or simplify it
- Update "Skill File Format" section
- Update "What gets loaded" section

**Commit:**
```bash
git add CLAUDE.md README.md
git commit -m "docs: update CLAUDE.md and README.md for single-skill architecture

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>"
```

### Task 7: Push to remote

```bash
git push
```

---

## Parallelization

- Tasks 1-4: Fully independent (separate source directories). Run all 4 Haiku agents in parallel.
- Task 5: Depends on Tasks 1-4 (service index table points to moved files). Leader handles.
- Task 6: Depends on Task 5. Leader handles.
- Task 7: Depends on Task 6. Leader handles.

## Expected Outcome

- 1 skill directory instead of 17
- Single frontmatter indexed by Claude Code (vs 17 before)
- Same progressive disclosure: SKILL.md → overview.md → group files
- One `cp -r skills/aws-cli your-project/skills/` to install
- Token cost per query unchanged (still loads only the groups needed)
