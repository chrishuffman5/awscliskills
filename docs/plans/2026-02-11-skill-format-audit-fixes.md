# Skill Format Audit Fixes — Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Fix 4 audit issues found across all 16 AWS CLI service skills to align with skill-creator best practices.

**Architecture:** Each skill gets the same 4 transformations applied: expand frontmatter description with "when to use" triggers, move `reference.md` into a `references/` subdirectory, add grep search patterns to SKILL.md, and remove the redundant `## When to Use` body section. All 16 skills are independent so work can be parallelized.

**Tech Stack:** Git, Markdown editing

---

## Background

An audit of all 16 service skills against the `.agents/skills/skill-creator` guidelines found 4 systemic issues:

| # | Issue | Severity | Description |
|---|-------|----------|-------------|
| 1 | Description lacks "when to use" triggers | Critical | The `description` field in YAML frontmatter is the primary triggering mechanism. All our skills have terse descriptions and put trigger info in a `## When to Use` body section that isn't read until AFTER triggering. |
| 2 | `reference.md` not in `references/` subdirectory | Critical | Skill-creator specifies reference files belong in `references/`. All 16 skills have `reference.md` at the skill root. |
| 3 | Missing grep search patterns for large references | High | For references >10k words, SKILL.md should include grep patterns to help Claude find specific content. 12 of 16 files exceed 10k words. |
| 4 | Redundant `## When to Use` in body | Medium | Once Issue 1 is fixed (triggers in description), the body section is duplicative and wastes tokens. |

### Reference file sizes (words)

| Skill | Words | >10k? |
|-------|------:|:-----:|
| aws-cli-cloudwatch | 12,578 | YES |
| aws-cli-s3 | 12,026 | YES |
| aws-cli-route53 | 11,597 | YES |
| aws-cli-cloudfront | 11,354 | YES |
| aws-cli-rds | 11,319 | YES |
| aws-cli-ecs | 11,168 | YES |
| aws-cli-iam | 10,272 | YES |
| aws-cli-lambda | 10,086 | YES |
| aws-cli-ec2 | 10,092 | YES |
| aws-cli-dynamodb | 9,763 | NO |
| aws-cli-elbv2 | 8,097 | NO |
| aws-cli-kms | 7,623 | NO |
| aws-cli-ecr | 6,103 | NO |
| aws-cli-sns | 5,605 | NO |
| aws-cli-sqs | 4,153 | NO |
| aws-cli-secretsmanager | 3,887 | NO |

**Decision:** Add grep patterns to ALL 16 skills for consistency, regardless of size.

---

## Transformation Spec (applies to every skill)

### Fix 1: Expand frontmatter description

**Before:**
```yaml
description: Use when working with AWS ECS commands — clusters, services, tasks, task definitions, container instances, capacity providers, deployments
```

**After:**
```yaml
description: Use when working with AWS ECS commands — clusters, services, tasks, task definitions, container instances, capacity providers, deployments. Use this skill when creating or managing ECS clusters, deploying and updating ECS services, running standalone or scheduled tasks, registering task definitions, managing container instances (EC2 launch type), configuring capacity providers, or monitoring deployments and service events.
```

**Pattern:** Append the "When to Use" bullet points as a comma-separated sentence starting with "Use this skill when" to the existing description. Keep it as a single `description:` value.

### Fix 2: Move reference.md → references/reference.md

```bash
mkdir -p skills/aws-cli-<service>/references
git mv skills/aws-cli-<service>/reference.md skills/aws-cli-<service>/references/reference.md
```

### Fix 3: Replace "Full Command Reference" section with grep patterns

**Before:**
```markdown
## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**After (example for ECS):**
```markdown
## Full Command Reference

See [`references/reference.md`](references/reference.md) for all commands, flags, and JSON output schemas.

**Grep patterns for quick lookup:**
- Command details: `grep -n "^### " references/reference.md` — lists all commands
- Specific command: `grep -n "create-service" references/reference.md`
- Required params: `grep -B2 -A10 "Required Parameters" references/reference.md`
- Output schema: `grep -B2 -A20 "JSON Output" references/reference.md`
- Section headers: `grep -n "^## " references/reference.md` — lists all sections
```

The grep patterns are identical for all 16 skills (they all follow the same reference.md structure) except the example command in the "Specific command" line, which should use a representative command for that service.

### Fix 4: Remove `## When to Use` section

Delete the entire `## When to Use` section (header + bullet list) from the body.

---

## Per-Skill Data

Each task below needs the service-specific "When to Use" content to merge into the description, and a representative command for the grep example. Here is the data for all 16 skills:

### aws-cli-ecs
- **When to Use content:** creating or managing ECS clusters, deploying and updating ECS services, running standalone or scheduled tasks, registering and managing task definitions, managing container instances (EC2 launch type), configuring capacity providers and auto scaling, monitoring deployments and service events
- **Grep example command:** `create-service`

### aws-cli-ec2
- **When to Use content:** launching or managing EC2 instances for ECS container instances, creating VPC networking (VPCs, subnets, internet gateways, NAT gateways, route tables), configuring security groups for ECS traffic, finding ECS-optimized AMIs, creating launch templates for ECS auto scaling, managing auto scaling groups for ECS capacity providers
- **Grep example command:** `run-instances`

### aws-cli-ecr
- **When to Use content:** creating or managing ECR repositories, pushing/pulling container images, setting up lifecycle policies for image cleanup, configuring image scanning, authenticating Docker to ECR (get-login-password), managing registry-level settings (replication, pull-through cache)
- **Grep example command:** `create-repository`

### aws-cli-s3
- **When to Use content:** creating or managing S3 buckets, uploading/downloading/copying/syncing objects, configuring bucket policies/ACLs/access points, setting up lifecycle rules for storage class transitions and expiration, enabling versioning, configuring static website hosting, generating presigned URLs, managing multipart uploads, setting up cross-region replication, configuring server-side encryption
- **Grep example command:** `put-object`

### aws-cli-rds
- **When to Use content:** creating or managing RDS DB instances (MySQL, PostgreSQL, MariaDB, Oracle, SQL Server), creating or managing Aurora DB clusters, taking and restoring snapshots, configuring parameter groups and option groups, setting up DB subnet groups, creating read replicas, managing automated backups and point-in-time recovery, configuring event subscriptions, managing RDS Proxy
- **Grep example command:** `create-db-instance`

### aws-cli-route53
- **When to Use content:** creating or managing hosted zones (public and private), creating/updating/deleting DNS records, setting up alias records pointing to AWS resources (ALB, CloudFront, S3), configuring health checks for failover, implementing routing policies (weighted, latency-based, geolocation, failover), registering or transferring domain names, managing DNSSEC signing, configuring query logging
- **Grep example command:** `change-resource-record-sets`

### aws-cli-iam
- **When to Use content:** creating IAM users/groups/roles, writing and attaching IAM policies (managed and inline), creating instance profiles for EC2 instances, creating ECS task execution roles and task roles, managing access keys and signing certificates, configuring MFA devices, setting up OIDC or SAML identity providers, managing service-linked roles, generating credential reports
- **Grep example command:** `create-role`

### aws-cli-cloudwatch
- **When to Use content:** publishing custom metrics or retrieving metric data, creating and managing CloudWatch alarms (simple and composite), building CloudWatch dashboards, creating and managing log groups and log streams, querying logs with CloudWatch Logs Insights, setting up metric filters, configuring subscription filters, setting retention policies, monitoring ECS service health via metrics and alarms
- **Grep example command:** `put-metric-alarm`

### aws-cli-elbv2
- **When to Use content:** creating ALBs or NLBs for ECS service traffic, configuring target groups (IP or instance type) for ECS services, setting up listeners with HTTP/HTTPS/TLS rules, configuring path-based or host-based routing rules, managing SSL/TLS certificates on load balancers, configuring health checks, setting up sticky sessions, enabling access logging
- **Grep example command:** `create-load-balancer`

### aws-cli-lambda
- **When to Use content:** creating or managing Lambda functions, deploying function code (zip or container image), invoking functions (sync or async), managing Lambda layers, configuring event source mappings (SQS, Kinesis, DynamoDB Streams, Kafka), creating and managing aliases and versions, configuring provisioned concurrency, setting up function URLs, managing resource-based policies, configuring code signing
- **Grep example command:** `create-function`

### aws-cli-dynamodb
- **When to Use content:** creating or managing DynamoDB tables, performing CRUD operations on items, querying tables and indexes, scanning tables with filters, managing Global Secondary Indexes, configuring DynamoDB Streams, creating and restoring backups, setting up global tables, configuring TTL, running transactional reads and writes, batch operations, importing/exporting data to/from S3
- **Grep example command:** `create-table`

### aws-cli-kms
- **When to Use content:** creating and managing KMS keys (symmetric, asymmetric, HMAC), encrypting and decrypting data, signing and verifying digital signatures, managing key policies and grants, creating and managing key aliases, configuring automatic key rotation, setting up multi-region keys, managing custom key stores, importing external key material
- **Grep example command:** `create-key`

### aws-cli-sns
- **When to Use content:** creating and managing SNS topics (standard and FIFO), subscribing endpoints (email, SQS, Lambda, HTTP/HTTPS, SMS), publishing messages, configuring subscription filter policies, setting up dead-letter queues, managing mobile push notification platform applications, sending SMS messages, configuring CloudWatch alarm notification targets
- **Grep example command:** `create-topic`

### aws-cli-sqs
- **When to Use content:** creating and managing SQS queues (standard and FIFO), sending/receiving/deleting messages, configuring dead-letter queues (redrive policies), setting visibility timeout and message retention, configuring long polling, setting queue access policies, using SQS as a Lambda event source trigger, decoupling microservices in ECS architectures
- **Grep example command:** `create-queue`

### aws-cli-cloudfront
- **When to Use content:** creating and managing CloudFront distributions, configuring S3 or ALB origins, setting up cache behaviors and TTLs, creating invalidations, writing and deploying CloudFront Functions, configuring origin access control (OAC) for S3, setting up custom domains with SSL certificates, managing cache/origin request policies, configuring continuous deployment, setting up real-time logging
- **Grep example command:** `create-distribution`

### aws-cli-secretsmanager
- **When to Use content:** storing and retrieving secrets (database credentials, API keys, tokens), configuring automatic secret rotation with Lambda, managing secret versions and staging labels, setting up cross-region replication, configuring resource-based policies for cross-account access, batch-retrieving multiple secrets, restoring deleted secrets, injecting secrets into ECS task definitions
- **Grep example command:** `create-secret`

---

## Task Execution

### Task 1: Fix aws-cli-ecs

**Files:**
- Modify: `skills/aws-cli-ecs/SKILL.md`
- Move: `skills/aws-cli-ecs/reference.md` → `skills/aws-cli-ecs/references/reference.md`

**Step 1: Create references/ directory and move reference.md**
```bash
mkdir -p skills/aws-cli-ecs/references
git mv skills/aws-cli-ecs/reference.md skills/aws-cli-ecs/references/reference.md
```

**Step 2: Edit SKILL.md — expand description**

Replace the frontmatter `description` with:
```yaml
description: Use when working with AWS ECS commands — clusters, services, tasks, task definitions, container instances, capacity providers, deployments. Use this skill when creating or managing ECS clusters, deploying and updating ECS services, running standalone or scheduled tasks, registering and managing task definitions, managing container instances (EC2 launch type), configuring capacity providers and auto scaling, or monitoring deployments and service events.
```

**Step 3: Edit SKILL.md — remove "When to Use" section**

Delete lines 12-20 (the `## When to Use` header and its bullet list).

**Step 4: Edit SKILL.md — replace "Full Command Reference" section**

Replace:
```markdown
## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

With:
```markdown
## Full Command Reference

See [`references/reference.md`](references/reference.md) for all commands, flags, and JSON output schemas.

**Grep patterns for quick lookup:**
- Command details: `grep -n "^### " references/reference.md` — lists all commands
- Specific command: `grep -n "create-service" references/reference.md`
- Required params: `grep -B2 -A10 "Required Parameters" references/reference.md`
- Output schema: `grep -B2 -A20 "JSON Output" references/reference.md`
- Section headers: `grep -n "^## " references/reference.md` — lists all sections
```

**Step 5: Commit**
```bash
git add skills/aws-cli-ecs/
git commit -m "fix(aws-cli-ecs): align skill format with skill-creator best practices"
```

---

### Tasks 2–16: Fix remaining skills

Each follows the identical 5-step pattern from Task 1, substituting the per-skill data from the "Per-Skill Data" section above. The tasks are:

| Task | Skill | Grep Example Command |
|------|-------|---------------------|
| 2 | aws-cli-ec2 | `run-instances` |
| 3 | aws-cli-ecr | `create-repository` |
| 4 | aws-cli-s3 | `put-object` |
| 5 | aws-cli-rds | `create-db-instance` |
| 6 | aws-cli-route53 | `change-resource-record-sets` |
| 7 | aws-cli-iam | `create-role` |
| 8 | aws-cli-cloudwatch | `put-metric-alarm` |
| 9 | aws-cli-elbv2 | `create-load-balancer` |
| 10 | aws-cli-lambda | `create-function` |
| 11 | aws-cli-dynamodb | `create-table` |
| 12 | aws-cli-kms | `create-key` |
| 13 | aws-cli-sns | `create-topic` |
| 14 | aws-cli-sqs | `create-queue` |
| 15 | aws-cli-cloudfront | `create-distribution` |
| 16 | aws-cli-secretsmanager | `create-secret` |

Each task follows the same 5 steps:
1. `mkdir -p` + `git mv` to move reference.md → references/reference.md
2. Expand frontmatter description (append "Use this skill when..." from Per-Skill Data)
3. Remove `## When to Use` section from body
4. Replace `## Full Command Reference` section with grep patterns (using the example command from the table)
5. `git add` + `git commit`

---

### Task 17: Update router and CLAUDE.md references

**Files:**
- Modify: `skills/aws-cli/SKILL.md` — no changes needed (router doesn't reference `reference.md`)
- Modify: `CLAUDE.md` — update skill hierarchy to show `references/reference.md` instead of `reference.md`
- Modify: `README.md` — update skill file format section

**Step 1: Edit CLAUDE.md**

In the Repository Architecture section, update the skill directory tree from:
```
  aws-cli-ecs/          # ECS reference (full coverage)
    SKILL.md
    reference.md
```
To:
```
  aws-cli-ecs/          # ECS reference (full coverage)
    SKILL.md
    references/
      reference.md
```

Apply this pattern to all 16 service skills in the tree.

**Step 2: Edit README.md**

Update the "Skill File Format" section from:
```
skills/aws-cli-<service>/
  SKILL.md          # YAML frontmatter (name, description) + overview + common workflows
  reference.md      # Complete command reference: every subcommand, all flags, JSON output schemas
```
To:
```
skills/aws-cli-<service>/
  SKILL.md              # YAML frontmatter (name, description) + overview + common workflows
  references/
    reference.md        # Complete command reference: every subcommand, all flags, JSON output schemas
```

Update the descriptions under both **SKILL.md** and **reference.md** to match.

**Step 3: Commit**
```bash
git add CLAUDE.md README.md
git commit -m "docs: update CLAUDE.md and README.md for references/ directory structure"
```

---

### Task 18: Push to remote

```bash
git push
```

---

## Parallelization Strategy

Tasks 1–16 are fully independent (each skill is a separate directory). They can all be executed in parallel by Agent Teams.

Task 17 depends on Tasks 1–16 completing (to ensure all moves are done before documenting).

Task 18 depends on Task 17.

**Recommended execution:**
- Batch 1: Tasks 1–16 (parallel, via Agent Teams — up to 5 agents, each handling ~3 skills)
- Batch 2: Task 17 (leader handles directly)
- Batch 3: Task 18 (leader handles directly)
