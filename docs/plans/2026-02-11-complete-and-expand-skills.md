# Complete Original Plan & Expand AWS CLI Skills

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Complete the missing ECS skill from the original plan, then add S3, RDS, and Route 53 service skills.

**Architecture:** Each service gets a `skills/aws-cli-<service>/` directory containing `SKILL.md` (YAML frontmatter + overview + common workflows) and `reference.md` (exhaustive command reference with all flags, types, defaults, and JSON output schemas). The router skill `skills/aws-cli/SKILL.md` service index table is updated for each new service.

**Tech Stack:** Static Markdown, AWS CLI v2 documentation, YAML frontmatter for Claude skill metadata

**Existing patterns to follow:** Use `skills/aws-cli-ecr/` as the template — match its SKILL.md structure (frontmatter, Overview, When to Use, Quick Reference workflows, Full Command Reference pointer) and its reference.md structure (version header, Table of Contents, Quick Reference table of all subcommands, then grouped sections with flag tables and JSON output schemas).

---

## Phase A: Complete Original Plan (ECS)

### Task 1: Create ECS SKILL.md

**Files:**
- Create: `skills/aws-cli-ecs/SKILL.md`

**Step 1: Create the SKILL.md file**

Write `skills/aws-cli-ecs/SKILL.md` with this structure:

```markdown
---
name: aws-cli-ecs
description: Use when working with AWS ECS commands — clusters, services, tasks, task definitions, container instances, capacity providers, deployments
---

# AWS CLI v2 — ECS (Elastic Container Service)

## Overview

Complete reference for all `aws ecs` subcommands in AWS CLI v2. Covers cluster management, service orchestration, task execution, task definition registration, container instance management, and capacity providers.

## When to Use

- Creating or managing ECS clusters
- Deploying and updating ECS services
- Running standalone tasks or scheduled tasks
- Registering and managing task definitions
- Managing container instances (EC2 launch type)
- Configuring capacity providers and auto scaling
- Monitoring deployments and service events

## Quick Reference — Common Workflows

### Create a cluster
```bash
aws ecs create-cluster --cluster-name my-cluster \
  --capacity-providers my-asg-cp \
  --default-capacity-provider-strategy capacityProvider=my-asg-cp,weight=1
```

### Register a task definition
```bash
aws ecs register-task-definition --cli-input-json file://task-def.json
```

### Create a service
```bash
aws ecs create-service --cluster my-cluster --service-name my-service \
  --task-definition my-task:1 --desired-count 2 \
  --launch-type EC2
```

### Run a standalone task
```bash
aws ecs run-task --cluster my-cluster --task-definition my-task:1 \
  --count 1 --launch-type EC2
```

### Update service (deploy new task def revision)
```bash
aws ecs update-service --cluster my-cluster --service-name my-service \
  --task-definition my-task:2
aws ecs wait services-stable --cluster my-cluster --services my-service
```

### List container instances and drain
```bash
aws ecs list-container-instances --cluster my-cluster --query 'containerInstanceArns'
aws ecs update-container-instances-state --cluster my-cluster \
  --container-instances arn:aws:ecs:... --status DRAINING
```

### Create capacity provider linked to ASG
```bash
aws ecs create-capacity-provider --name my-asg-cp \
  --auto-scaling-group-provider autoScalingGroupArn=arn:aws:autoscaling:...,managedScaling={status=ENABLED,targetCapacity=80},managedTerminationProtection=ENABLED
```

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify the file exists and looks correct**

Run: `cat skills/aws-cli-ecs/SKILL.md | head -5`
Expected: YAML frontmatter with `name: aws-cli-ecs`

**Step 3: Commit**

```bash
git add skills/aws-cli-ecs/SKILL.md
git commit -m "feat: add ECS skill overview (SKILL.md)"
```

---

### Task 2: Create ECS reference.md

**Files:**
- Create: `skills/aws-cli-ecs/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-ecs/reference.md` with the complete ECS command reference. Follow the ECR reference.md format exactly:

1. Version header citing AWS CLI v2 docs
2. Table of Contents with numbered sections
3. Quick Reference table of ALL `aws ecs` subcommands (command | category | description)
4. Grouped sections covering every command group:
   - **Clusters**: `create-cluster`, `delete-cluster`, `describe-clusters`, `list-clusters`, `update-cluster`, `update-cluster-settings`, `put-cluster-capacity-providers`
   - **Services**: `create-service`, `delete-service`, `describe-services`, `list-services`, `update-service`, `update-service-primary-task-set`
   - **Tasks**: `run-task`, `start-task`, `stop-task`, `describe-tasks`, `list-tasks`
   - **Task Definitions**: `register-task-definition`, `deregister-task-definition`, `describe-task-definition`, `list-task-definitions`, `list-task-definition-families`, `delete-task-definitions`
   - **Container Instances**: `register-container-instance`, `deregister-container-instance`, `describe-container-instances`, `list-container-instances`, `update-container-instances-state`, `update-container-agent`
   - **Capacity Providers**: `create-capacity-provider`, `delete-capacity-provider`, `describe-capacity-providers`, `update-capacity-provider`
   - **Task Sets**: `create-task-set`, `delete-task-set`, `describe-task-sets`, `update-task-set`
   - **Account Settings**: `list-account-settings`, `put-account-setting`, `put-account-setting-default`, `delete-account-setting`
   - **Tags**: `tag-resource`, `untag-resource`, `list-tags-for-resource`
   - **Service Deployments**: `list-service-deployments`, `describe-service-deployments`, `describe-service-revisions`, `list-service-revisions`
   - **Attributes**: `put-attributes`, `delete-attributes`, `list-attributes`
   - **Execute Command**: `execute-command`, `update-cluster` (executeCommandConfiguration)

5. Each command entry must include:
   - Description (1-2 sentences)
   - Required parameters table (Parameter | Type | Description)
   - Optional parameters table (Parameter | Type | Description)
   - JSON output schema showing the response structure

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/ecs/

**Step 2: Verify the file structure**

Run: `head -30 skills/aws-cli-ecs/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-ecs/reference.md
git commit -m "feat: add ECS complete command reference"
```

---

### Task 3: Update router skill with ECS entry verification

**Files:**
- Modify: `skills/aws-cli/SKILL.md:16-18` (Service Index table)

**Step 1: Verify ECS is already in the service index**

Read `skills/aws-cli/SKILL.md` and check the Service Index table. The original plan already included ECS in the router, so confirm it has:

```
| ECS | `aws-cli-ecs` | Clusters, services, tasks, task definitions, container instances, capacity providers |
```

If it's already there (it is in the current file), no edit needed. If missing, add it.

**Step 2: Commit (only if changes were made)**

```bash
git add skills/aws-cli/SKILL.md
git commit -m "fix: ensure ECS entry in router service index"
```

---

## Phase B: Add Popular AWS Service Skills

### Task 4: Create S3 SKILL.md

**Files:**
- Create: `skills/aws-cli-s3/SKILL.md`

**Step 1: Create the SKILL.md file**

Write `skills/aws-cli-s3/SKILL.md` following the established pattern:

```markdown
---
name: aws-cli-s3
description: Use when working with AWS S3 commands — buckets, objects, storage classes, lifecycle rules, versioning, website hosting, presigned URLs, multipart uploads
---

# AWS CLI v2 — S3 (Simple Storage Service)

## Overview

Complete reference for `aws s3` (high-level) and `aws s3api` (low-level) subcommands in AWS CLI v2. Covers bucket management, object operations, storage classes, lifecycle rules, versioning, access policies, encryption, website hosting, and transfer acceleration.

## When to Use

- Creating or managing S3 buckets
- Uploading, downloading, copying, or syncing objects
- Configuring bucket policies, ACLs, and access points
- Setting up lifecycle rules for storage class transitions and expiration
- Enabling versioning and managing object versions
- Configuring static website hosting
- Generating presigned URLs for temporary access
- Managing multipart uploads
- Setting up cross-region replication
- Configuring server-side encryption

## Quick Reference — Common Workflows

### Create bucket and upload
```bash
aws s3 mb s3://my-bucket --region us-east-1
aws s3 cp local-file.txt s3://my-bucket/path/
aws s3 sync ./local-dir s3://my-bucket/prefix/ --delete
```

### Download and list objects
```bash
aws s3 ls s3://my-bucket/prefix/ --recursive
aws s3 cp s3://my-bucket/path/file.txt ./local-file.txt
aws s3 sync s3://my-bucket/prefix/ ./local-dir
```

### Generate presigned URL
```bash
aws s3 presign s3://my-bucket/path/file.txt --expires-in 3600
```

### Set bucket policy
```bash
aws s3api put-bucket-policy --bucket my-bucket --policy file://policy.json
```

### Enable versioning
```bash
aws s3api put-bucket-versioning --bucket my-bucket --versioning-configuration Status=Enabled
```

### Configure lifecycle rule
```bash
aws s3api put-bucket-lifecycle-configuration --bucket my-bucket --lifecycle-configuration file://lifecycle.json
```

## Covered Command Groups

| Group | Commands | CLI Service |
|-------|----------|-------------|
| High-Level | cp, mv, rm, sync, ls, mb, rb, presign, website | `aws s3` |
| Buckets | create, delete, head, list, get/put policy, versioning, lifecycle, encryption, logging, cors, website, acl, replication, accelerate, tagging | `aws s3api` |
| Objects | get, put, delete, copy, head, list-objects-v2, restore, select, presign, multipart uploads | `aws s3api` |
| Access Points | create, delete, get, list access points and policies | `aws s3control` |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-s3/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-s3`

**Step 3: Commit**

```bash
git add skills/aws-cli-s3/SKILL.md
git commit -m "feat: add S3 skill overview (SKILL.md)"
```

---

### Task 5: Create S3 reference.md

**Files:**
- Create: `skills/aws-cli-s3/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-s3/reference.md` with the complete S3 command reference. Structure:

1. Version header citing AWS CLI v2 docs
2. Table of Contents with numbered sections
3. Quick Reference table of all subcommands for both `aws s3` and `aws s3api`
4. Grouped sections:
   - **High-Level Commands (`aws s3`)**: `cp`, `mv`, `rm`, `sync`, `ls`, `mb`, `rb`, `presign`, `website`
   - **Bucket Management (`aws s3api`)**: `create-bucket`, `delete-bucket`, `head-bucket`, `list-buckets`, `get-bucket-location`
   - **Bucket Configuration**: `put/get-bucket-policy`, `put/get-bucket-versioning`, `put/get-bucket-lifecycle-configuration`, `put/get-bucket-encryption`, `put/get-bucket-logging`, `put/get-bucket-cors`, `put/get-bucket-website`, `put/get-bucket-acl`, `put/get-bucket-replication`, `put/get-bucket-accelerate-configuration`, `put/get-bucket-tagging`, `put/get-bucket-notification-configuration`, `get-bucket-policy-status`, `put/get-public-access-block`
   - **Object Operations**: `get-object`, `put-object`, `delete-object`, `delete-objects`, `copy-object`, `head-object`, `list-objects-v2`, `restore-object`, `select-object-content`, `get/put-object-acl`, `get/put-object-tagging`, `get-object-attributes`
   - **Multipart Uploads**: `create-multipart-upload`, `upload-part`, `upload-part-copy`, `complete-multipart-upload`, `abort-multipart-upload`, `list-multipart-uploads`, `list-parts`
   - **Tags**: `get/put/delete-bucket-tagging`, `get/put/delete-object-tagging`

5. Each command: description, required params, optional params, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/s3/ and https://docs.aws.amazon.com/cli/latest/reference/s3api/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-s3/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-s3/reference.md
git commit -m "feat: add S3 complete command reference"
```

---

### Task 6: Create RDS SKILL.md

**Files:**
- Create: `skills/aws-cli-rds/SKILL.md`

**Step 1: Create the SKILL.md file**

Write `skills/aws-cli-rds/SKILL.md`:

```markdown
---
name: aws-cli-rds
description: Use when working with AWS RDS commands — DB instances, clusters (Aurora), snapshots, parameter groups, subnet groups, read replicas, automated backups, event subscriptions
---

# AWS CLI v2 — RDS (Relational Database Service)

## Overview

Complete reference for all `aws rds` subcommands in AWS CLI v2. Covers DB instance lifecycle, Aurora clusters, snapshots, parameter groups, subnet groups, read replicas, automated backups, security, monitoring, and event subscriptions.

## When to Use

- Creating or managing RDS DB instances (MySQL, PostgreSQL, MariaDB, Oracle, SQL Server)
- Creating or managing Aurora DB clusters
- Taking and restoring snapshots
- Configuring parameter groups and option groups
- Setting up DB subnet groups for VPC networking
- Creating read replicas
- Managing automated backups and point-in-time recovery
- Configuring event subscriptions and notifications
- Managing RDS Proxy

## Quick Reference — Common Workflows

### Create a DB instance
```bash
aws rds create-db-instance --db-instance-identifier my-db \
  --db-instance-class db.t3.medium --engine postgres \
  --master-username admin --master-user-password secret \
  --allocated-storage 20 --vpc-security-group-ids sg-xxx \
  --db-subnet-group-name my-subnet-group
```

### Create an Aurora cluster
```bash
aws rds create-db-cluster --db-cluster-identifier my-aurora \
  --engine aurora-postgresql --master-username admin \
  --master-user-password secret --vpc-security-group-ids sg-xxx \
  --db-subnet-group-name my-subnet-group
aws rds create-db-instance --db-instance-identifier my-aurora-instance-1 \
  --db-cluster-identifier my-aurora --db-instance-class db.r6g.large \
  --engine aurora-postgresql
```

### Take a snapshot
```bash
aws rds create-db-snapshot --db-instance-identifier my-db --db-snapshot-identifier my-snap
aws rds wait db-snapshot-available --db-snapshot-identifier my-snap
```

### Create read replica
```bash
aws rds create-db-instance-read-replica --db-instance-identifier my-replica \
  --source-db-instance-identifier my-db --db-instance-class db.t3.medium
```

### Modify instance (apply immediately)
```bash
aws rds modify-db-instance --db-instance-identifier my-db \
  --db-instance-class db.t3.large --apply-immediately
aws rds wait db-instance-available --db-instance-identifier my-db
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| DB Instances | create, delete, describe, modify, reboot, start, stop | Instance lifecycle |
| DB Clusters | create, delete, describe, modify, failover, start, stop | Aurora clusters |
| Snapshots | create, delete, describe, copy, restore, share | Instance & cluster snapshots |
| Parameter Groups | create, delete, describe, modify, reset | Engine configuration |
| Subnet Groups | create, delete, describe, modify | VPC networking |
| Option Groups | create, delete, describe, modify, copy | Engine-specific features |
| Event Subscriptions | create, delete, describe, modify | SNS notifications |
| Automated Backups | describe, delete, start/stop replication | Backup management |
| Proxies | create, delete, describe, modify | RDS Proxy |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-rds/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-rds`

**Step 3: Commit**

```bash
git add skills/aws-cli-rds/SKILL.md
git commit -m "feat: add RDS skill overview (SKILL.md)"
```

---

### Task 7: Create RDS reference.md

**Files:**
- Create: `skills/aws-cli-rds/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-rds/reference.md` with the complete RDS command reference. Structure:

1. Version header citing AWS CLI v2 docs
2. Table of Contents with numbered sections
3. Quick Reference table of all `aws rds` subcommands
4. Grouped sections:
   - **DB Instances**: `create-db-instance`, `delete-db-instance`, `describe-db-instances`, `modify-db-instance`, `reboot-db-instance`, `start-db-instance`, `stop-db-instance`, `create-db-instance-read-replica`, `promote-read-replica`, `switchover-read-replica`
   - **DB Clusters (Aurora)**: `create-db-cluster`, `delete-db-cluster`, `describe-db-clusters`, `modify-db-cluster`, `failover-db-cluster`, `start-db-cluster`, `stop-db-cluster`, `create-db-cluster-endpoint`, `describe-db-cluster-endpoints`
   - **Snapshots**: `create-db-snapshot`, `delete-db-snapshot`, `describe-db-snapshots`, `copy-db-snapshot`, `restore-db-instance-from-db-snapshot`, `create-db-cluster-snapshot`, `delete-db-cluster-snapshot`, `describe-db-cluster-snapshots`, `copy-db-cluster-snapshot`, `restore-db-cluster-from-snapshot`
   - **Parameter Groups**: `create-db-parameter-group`, `delete-db-parameter-group`, `describe-db-parameter-groups`, `describe-db-parameters`, `modify-db-parameter-group`, `reset-db-parameter-group`, `create-db-cluster-parameter-group`, `describe-db-cluster-parameters`, `modify-db-cluster-parameter-group`
   - **Subnet Groups**: `create-db-subnet-group`, `delete-db-subnet-group`, `describe-db-subnet-groups`, `modify-db-subnet-group`
   - **Option Groups**: `create-option-group`, `delete-option-group`, `describe-option-groups`, `describe-option-group-options`, `modify-option-group`, `copy-option-group`
   - **Event Subscriptions**: `create-event-subscription`, `delete-event-subscription`, `describe-event-subscriptions`, `modify-event-subscription`, `describe-events`, `describe-event-categories`
   - **Automated Backups**: `describe-db-instance-automated-backups`, `delete-db-instance-automated-backup`, `start-db-instance-automated-backups-replication`, `stop-db-instance-automated-backups-replication`
   - **RDS Proxy**: `create-db-proxy`, `delete-db-proxy`, `describe-db-proxies`, `modify-db-proxy`, `register-db-proxy-targets`, `deregister-db-proxy-targets`, `describe-db-proxy-targets`, `describe-db-proxy-target-groups`
   - **Security**: `describe-db-security-groups`, `describe-certificates`, `modify-certificates`
   - **Maintenance**: `describe-pending-maintenance-actions`, `apply-pending-maintenance-action`, `describe-db-engine-versions`, `describe-orderable-db-instance-options`
   - **Tags**: `add-tags-to-resource`, `remove-tags-from-resource`, `list-tags-for-resource`

5. Each command: description, required params, optional params, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/rds/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-rds/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-rds/reference.md
git commit -m "feat: add RDS complete command reference"
```

---

### Task 8: Create Route 53 SKILL.md

**Files:**
- Create: `skills/aws-cli-route53/SKILL.md`

**Step 1: Create the SKILL.md file**

Write `skills/aws-cli-route53/SKILL.md`:

```markdown
---
name: aws-cli-route53
description: Use when working with AWS Route 53 commands — hosted zones, DNS records, health checks, routing policies, domain registration, traffic policies, query logging
---

# AWS CLI v2 — Route 53 (DNS Service)

## Overview

Complete reference for `aws route53` and `aws route53domains` subcommands in AWS CLI v2. Covers hosted zone management, DNS record operations (A, AAAA, CNAME, MX, TXT, NS, SOA, SRV, alias), health checks, routing policies (simple, weighted, latency, failover, geolocation, multivalue), domain registration, and traffic flow.

## When to Use

- Creating or managing hosted zones (public and private)
- Creating, updating, or deleting DNS records
- Setting up alias records pointing to AWS resources (ALB, CloudFront, S3)
- Configuring health checks for failover
- Implementing routing policies (weighted, latency-based, geolocation, failover)
- Registering or transferring domain names
- Managing DNSSEC signing
- Configuring query logging

## Quick Reference — Common Workflows

### Create a hosted zone
```bash
aws route53 create-hosted-zone --name example.com --caller-reference $(date +%s)
```

### Create an A record
```bash
aws route53 change-resource-record-sets --hosted-zone-id Z123 \
  --change-batch '{
    "Changes":[{
      "Action":"UPSERT",
      "ResourceRecordSet":{
        "Name":"app.example.com",
        "Type":"A",
        "TTL":300,
        "ResourceRecords":[{"Value":"1.2.3.4"}]
      }
    }]
  }'
```

### Create alias record pointing to ALB
```bash
aws route53 change-resource-record-sets --hosted-zone-id Z123 \
  --change-batch '{
    "Changes":[{
      "Action":"UPSERT",
      "ResourceRecordSet":{
        "Name":"app.example.com",
        "Type":"A",
        "AliasTarget":{
          "HostedZoneId":"Z35SXDOTRQ7X7K",
          "DNSName":"my-alb-123.us-east-1.elb.amazonaws.com",
          "EvaluateTargetHealth":true
        }
      }
    }]
  }'
```

### List records in a hosted zone
```bash
aws route53 list-resource-record-sets --hosted-zone-id Z123 \
  --query 'ResourceRecordSets[].{Name:Name,Type:Type,TTL:TTL}'
```

### Create a health check
```bash
aws route53 create-health-check --caller-reference $(date +%s) \
  --health-check-config '{
    "Type":"HTTPS",
    "FullyQualifiedDomainName":"app.example.com",
    "Port":443,
    "RequestInterval":30,
    "FailureThreshold":3
  }'
```

## Covered Command Groups

| Group | Commands | CLI Service |
|-------|----------|-------------|
| Hosted Zones | create, delete, get, list, update, associate/disassociate VPC | `aws route53` |
| Records | change-resource-record-sets, list-resource-record-sets, test-dns-answer | `aws route53` |
| Health Checks | create, delete, get, list, update, get-status | `aws route53` |
| Traffic Policies | create, delete, get, list, update, create/get/list policy instances | `aws route53` |
| DNSSEC | enable/disable-hosted-zone-dnssec, get-dnssec | `aws route53` |
| Query Logging | create, delete, list query logging configs | `aws route53` |
| Domain Registration | register, transfer, renew, check-availability, get/update details | `aws route53domains` |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-route53/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-route53`

**Step 3: Commit**

```bash
git add skills/aws-cli-route53/SKILL.md
git commit -m "feat: add Route 53 skill overview (SKILL.md)"
```

---

### Task 9: Create Route 53 reference.md

**Files:**
- Create: `skills/aws-cli-route53/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-route53/reference.md` with the complete Route 53 command reference. Structure:

1. Version header citing AWS CLI v2 docs
2. Table of Contents with numbered sections
3. Quick Reference table of all subcommands for both `aws route53` and `aws route53domains`
4. Grouped sections:
   - **Hosted Zones (`aws route53`)**: `create-hosted-zone`, `delete-hosted-zone`, `get-hosted-zone`, `list-hosted-zones`, `list-hosted-zones-by-name`, `update-hosted-zone-comment`, `get-hosted-zone-count`, `create-hosted-zone-dnssec-signing`, `associate-vpc-with-hosted-zone`, `disassociate-vpc-from-hosted-zone`, `list-hosted-zones-by-vpc`
   - **Records**: `change-resource-record-sets` (UPSERT/CREATE/DELETE actions for all record types: A, AAAA, CNAME, MX, TXT, NS, SOA, SRV, CAA, alias), `list-resource-record-sets`, `test-dns-answer`, `get-change` (poll for INSYNC)
   - **Health Checks**: `create-health-check`, `delete-health-check`, `get-health-check`, `list-health-checks`, `update-health-check`, `get-health-check-status`, `get-health-check-last-failure-reason`, `get-health-check-count`
   - **Traffic Policies**: `create-traffic-policy`, `delete-traffic-policy`, `get-traffic-policy`, `list-traffic-policies`, `update-traffic-policy-comment`, `create-traffic-policy-version`, `list-traffic-policy-versions`, `create-traffic-policy-instance`, `delete-traffic-policy-instance`, `get-traffic-policy-instance`, `list-traffic-policy-instances`, `update-traffic-policy-instance`
   - **DNSSEC**: `enable-hosted-zone-dnssec`, `disable-hosted-zone-dnssec`, `get-dnssec`, `create-key-signing-key`, `delete-key-signing-key`, `activate-key-signing-key`, `deactivate-key-signing-key`
   - **Query Logging**: `create-query-logging-config`, `delete-query-logging-config`, `get-query-logging-config`, `list-query-logging-configs`
   - **Reusable Delegation Sets**: `create-reusable-delegation-set`, `delete-reusable-delegation-set`, `get-reusable-delegation-set`, `list-reusable-delegation-sets`
   - **Domain Registration (`aws route53domains`)**: `register-domain`, `transfer-domain`, `renew-domain`, `check-domain-availability`, `check-domain-transferability`, `get-domain-detail`, `list-domains`, `update-domain-nameservers`, `update-domain-contact`, `enable-domain-auto-renew`, `disable-domain-auto-renew`, `enable-domain-transfer-lock`, `disable-domain-transfer-lock`, `get-operation-detail`, `list-operations`, `list-prices`
   - **Tags**: `change-tags-for-resource`, `list-tags-for-resource`, `list-tags-for-resources`

5. Each command: description, required params, optional params, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/route53/ and https://docs.aws.amazon.com/cli/latest/reference/route53domains/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-route53/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-route53/reference.md
git commit -m "feat: add Route 53 complete command reference"
```

---

### Task 10: Update router skill service index with all new services

**Files:**
- Modify: `skills/aws-cli/SKILL.md:14-19` (Service Index table)
- Modify: `skills/aws-cli/SKILL.md:2` (description — add new services)

**Step 1: Update the YAML frontmatter description**

Change the `description` line to include new services:

```yaml
description: Use when working with any AWS CLI v2 commands — provides general CLI conventions and routes to per-service reference skills for ECS, EC2, ECR, S3, RDS, Route 53
```

**Step 2: Update the Service Index table**

Replace the existing 3-row table with:

```markdown
| Service | Skill | Scope |
|---------|-------|-------|
| ECS | `aws-cli-ecs` | Clusters, services, tasks, task definitions, container instances, capacity providers |
| EC2 | `aws-cli-ec2` | Instances, VPCs, subnets, security groups, key pairs, AMIs, launch templates, auto scaling |
| ECR | `aws-cli-ecr` | Repositories, images, lifecycle policies, scanning, authentication, registry |
| S3 | `aws-cli-s3` | Buckets, objects, storage classes, lifecycle, versioning, website hosting, presigned URLs |
| RDS | `aws-cli-rds` | DB instances, Aurora clusters, snapshots, parameter groups, subnet groups, replicas, proxies |
| Route 53 | `aws-cli-route53` | Hosted zones, DNS records, health checks, routing policies, domain registration |
```

**Step 3: Commit**

```bash
git add skills/aws-cli/SKILL.md
git commit -m "feat: add S3, RDS, Route 53 to router service index"
```

---

### Task 11: Update CLAUDE.md with new services

**Files:**
- Modify: `CLAUDE.md` (skill hierarchy diagram and "Adding a New Service Skill" section)

**Step 1: Update the skill hierarchy tree**

Update the tree in CLAUDE.md to include the new service directories (`aws-cli-ecs`, `aws-cli-s3`, `aws-cli-rds`, `aws-cli-route53`) following the existing format.

**Step 2: Commit**

```bash
git add CLAUDE.md
git commit -m "docs: update CLAUDE.md with expanded service list"
```

---

## Dependency Summary

```
Task 1 (ECS SKILL.md) → Task 2 (ECS reference.md) → Task 3 (verify router)
Task 4 (S3 SKILL.md)  → Task 5 (S3 reference.md)
Task 6 (RDS SKILL.md) → Task 7 (RDS reference.md)
Task 8 (R53 SKILL.md) → Task 9 (R53 reference.md)
Tasks 3,5,7,9 → Task 10 (update router)
Task 10 → Task 11 (update CLAUDE.md)
```

Tasks 1-2, 4-5, 6-7, and 8-9 can run in parallel (each service is independent). Task 10 depends on all reference files being complete. Task 11 is last.
