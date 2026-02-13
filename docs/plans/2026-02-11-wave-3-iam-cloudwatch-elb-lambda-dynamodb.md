# Wave 3: IAM, CloudWatch, ELBv2, Lambda, DynamoDB Skills

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Add 5 more AWS CLI reference skills (IAM, CloudWatch, ELBv2, Lambda, DynamoDB) to the skill library, bringing total coverage to 11 services.

**Architecture:** Each service gets a `skills/aws-cli-<service>/` directory with `SKILL.md` (YAML frontmatter + overview + common workflows) and `reference.md` (exhaustive command reference with all flags, types, defaults, JSON output schemas). The router skill `skills/aws-cli/SKILL.md` service index is updated with all 5 new entries. Use `skills/aws-cli-ecr/` as the format template.

**Tech Stack:** Static Markdown, AWS CLI v2 documentation, YAML frontmatter for Claude skill metadata

---

## Service Selection Rationale

| Service | Why | CLI Namespace |
|---------|-----|---------------|
| IAM | Foundational — roles, policies, instance profiles required by every other service (especially ECS task roles) | `aws iam` |
| CloudWatch | Observability — logs, metrics, alarms for ECS services and all infrastructure | `aws cloudwatch` + `aws logs` |
| ELBv2 | Traffic routing — ALBs/NLBs are how traffic reaches ECS services | `aws elbv2` |
| Lambda | Serverless compute — top-3 most used AWS service | `aws lambda` |
| DynamoDB | NoSQL database — top-5 most used AWS service, common ECS backend | `aws dynamodb` |

---

## Task 1: Create IAM SKILL.md

**Files:**
- Create: `skills/aws-cli-iam/SKILL.md`

**Step 1: Create the SKILL.md file**

```markdown
---
name: aws-cli-iam
description: Use when working with AWS IAM commands — users, groups, roles, policies, instance profiles, access keys, MFA, service-linked roles, OIDC/SAML providers
---

# AWS CLI v2 — IAM (Identity and Access Management)

## Overview

Complete reference for all `aws iam` subcommands in AWS CLI v2. Covers user and group management, role creation and assumption, policy authoring and attachment, instance profiles for EC2/ECS, access key rotation, MFA configuration, and identity providers (OIDC, SAML).

## When to Use

- Creating IAM users, groups, and roles
- Writing and attaching IAM policies (managed and inline)
- Creating instance profiles for EC2 instances (ECS container instances)
- Creating ECS task execution roles and task roles
- Managing access keys and signing certificates
- Configuring MFA devices
- Setting up OIDC or SAML identity providers
- Managing service-linked roles
- Generating credential reports and access advisor data

## Quick Reference — Common Workflows

### Create a role for ECS tasks
```bash
aws iam create-role --role-name ecsTaskRole \
  --assume-role-policy-document '{
    "Version":"2012-10-17",
    "Statement":[{"Effect":"Allow","Principal":{"Service":"ecs-tasks.amazonaws.com"},"Action":"sts:AssumeRole"}]
  }'
aws iam attach-role-policy --role-name ecsTaskRole \
  --policy-arn arn:aws:iam::aws:policy/service-role/AmazonECSTaskExecutionRolePolicy
```

### Create instance profile for ECS EC2 instances
```bash
aws iam create-instance-profile --instance-profile-name ecsInstanceProfile
aws iam add-role-to-instance-profile --instance-profile-name ecsInstanceProfile --role-name ecsInstanceRole
```

### Create a policy and attach to role
```bash
aws iam create-policy --policy-name my-policy --policy-document file://policy.json
aws iam attach-role-policy --role-name my-role --policy-arn arn:aws:iam::123456789012:policy/my-policy
```

### List and rotate access keys
```bash
aws iam list-access-keys --user-name my-user
aws iam create-access-key --user-name my-user
aws iam delete-access-key --user-name my-user --access-key-id AKIA...
```

### Get account authorization details
```bash
aws iam get-account-authorization-details --filter Role --query 'RoleDetailList[].{Name:RoleName,Arn:Arn}'
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Users | create, delete, get, list, update, tag/untag | User lifecycle |
| Groups | create, delete, get, list, add/remove user | Group membership |
| Roles | create, delete, get, list, update, tag/untag | Role management |
| Policies | create, delete, get, list, create-version, set-default-version | Managed policies |
| Policy Attachment | attach/detach role/user/group policy, list attached/entities | Binding policies |
| Inline Policies | put/get/delete role/user/group policy, list role/user/group policies | Embedded policies |
| Instance Profiles | create, delete, get, list, add/remove role | EC2/ECS instance profiles |
| Access Keys | create, delete, list, update, get-last-used | Credential management |
| MFA | create/delete/deactivate/enable/list virtual MFA, resync | Multi-factor auth |
| Identity Providers | create/delete/get/list/update OIDC and SAML providers | Federation |
| Service-Linked Roles | create, delete, get-deletion-status | AWS-managed roles |
| Account | get-account-summary, get-account-authorization-details, generate-credential-report, get-credential-report | Account audit |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-iam/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-iam`

**Step 3: Commit**

```bash
git add skills/aws-cli-iam/SKILL.md
git commit -m "feat: add IAM skill overview (SKILL.md)"
```

---

## Task 2: Create IAM reference.md

**Files:**
- Create: `skills/aws-cli-iam/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-iam/reference.md` with the complete IAM command reference. Structure:

1. Version header citing AWS CLI v2 docs source URL
2. Table of Contents with numbered sections
3. Quick Reference table of ALL `aws iam` subcommands (command | category | description)
4. Grouped sections:
   - **Users**: `create-user`, `delete-user`, `get-user`, `list-users`, `update-user`, `tag-user`, `untag-user`, `list-user-tags`
   - **Groups**: `create-group`, `delete-group`, `get-group`, `list-groups`, `update-group`, `add-user-to-group`, `remove-user-from-group`, `list-groups-for-user`
   - **Roles**: `create-role`, `delete-role`, `get-role`, `list-roles`, `update-role`, `update-role-description`, `update-assume-role-policy`, `tag-role`, `untag-role`, `list-role-tags`
   - **Managed Policies**: `create-policy`, `delete-policy`, `get-policy`, `list-policies`, `create-policy-version`, `delete-policy-version`, `get-policy-version`, `list-policy-versions`, `set-default-policy-version`
   - **Policy Attachment**: `attach-role-policy`, `detach-role-policy`, `attach-user-policy`, `detach-user-policy`, `attach-group-policy`, `detach-group-policy`, `list-attached-role-policies`, `list-attached-user-policies`, `list-attached-group-policies`, `list-entities-for-policy`
   - **Inline Policies**: `put-role-policy`, `get-role-policy`, `delete-role-policy`, `list-role-policies`, `put-user-policy`, `get-user-policy`, `delete-user-policy`, `list-user-policies`, `put-group-policy`, `get-group-policy`, `delete-group-policy`, `list-group-policies`
   - **Instance Profiles**: `create-instance-profile`, `delete-instance-profile`, `get-instance-profile`, `list-instance-profiles`, `list-instance-profiles-for-role`, `add-role-to-instance-profile`, `remove-role-from-instance-profile`, `tag-instance-profile`, `untag-instance-profile`
   - **Access Keys**: `create-access-key`, `delete-access-key`, `list-access-keys`, `update-access-key`, `get-access-key-last-used`
   - **Login Profiles**: `create-login-profile`, `delete-login-profile`, `get-login-profile`, `update-login-profile`
   - **MFA**: `create-virtual-mfa-device`, `delete-virtual-mfa-device`, `enable-mfa-device`, `deactivate-mfa-device`, `list-virtual-mfa-devices`, `list-mfa-devices`, `resync-mfa-device`
   - **Signing Certificates**: `upload-signing-certificate`, `delete-signing-certificate`, `list-signing-certificates`, `update-signing-certificate`
   - **SSH Public Keys**: `upload-ssh-public-key`, `delete-ssh-public-key`, `get-ssh-public-key`, `list-ssh-public-keys`, `update-ssh-public-key`
   - **Server Certificates**: `upload-server-certificate`, `delete-server-certificate`, `get-server-certificate`, `list-server-certificates`, `update-server-certificate`
   - **OIDC Providers**: `create-open-id-connect-provider`, `delete-open-id-connect-provider`, `get-open-id-connect-provider`, `list-open-id-connect-providers`, `update-open-id-connect-provider-thumbprint`, `add-client-id-to-open-id-connect-provider`, `remove-client-id-from-open-id-connect-provider`
   - **SAML Providers**: `create-saml-provider`, `delete-saml-provider`, `get-saml-provider`, `list-saml-providers`, `update-saml-provider`
   - **Service-Linked Roles**: `create-service-linked-role`, `delete-service-linked-role`, `get-service-linked-role-deletion-status`
   - **Account & Reporting**: `get-account-summary`, `get-account-authorization-details`, `generate-credential-report`, `get-credential-report`, `get-account-password-policy`, `update-account-password-policy`, `delete-account-password-policy`, `create-account-alias`, `delete-account-alias`, `list-account-aliases`
   - **Policy Simulation**: `simulate-principal-policy`, `simulate-custom-policy`
   - **Tags**: `tag-user`, `untag-user`, `tag-role`, `untag-role`, `tag-policy`, `untag-policy`, `tag-instance-profile`, `untag-instance-profile`, etc.

5. Each command: description, required params table, optional params table, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/iam/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-iam/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-iam/reference.md
git commit -m "feat: add IAM complete command reference"
```

---

## Task 3: Create CloudWatch SKILL.md

**Files:**
- Create: `skills/aws-cli-cloudwatch/SKILL.md`

**Step 1: Create the SKILL.md file**

```markdown
---
name: aws-cli-cloudwatch
description: Use when working with AWS CloudWatch and CloudWatch Logs commands — metrics, alarms, dashboards, log groups, log streams, metric filters, insights queries, anomaly detection
---

# AWS CLI v2 — CloudWatch (Monitoring & Logs)

## Overview

Complete reference for `aws cloudwatch` (metrics, alarms, dashboards) and `aws logs` (CloudWatch Logs) subcommands in AWS CLI v2. Covers metric publishing and retrieval, alarm configuration, composite alarms, dashboard management, log group/stream operations, metric filters, Logs Insights queries, and subscription filters.

## When to Use

- Publishing custom metrics or retrieving metric data
- Creating and managing CloudWatch alarms (simple and composite)
- Building CloudWatch dashboards
- Creating and managing log groups and log streams
- Querying logs with CloudWatch Logs Insights
- Setting up metric filters to extract metrics from logs
- Configuring subscription filters to stream logs to Lambda/Kinesis/S3
- Setting retention policies on log groups
- Monitoring ECS service health via metrics and alarms

## Quick Reference — Common Workflows

### Create an alarm on ECS service CPU
```bash
aws cloudwatch put-metric-alarm --alarm-name ecs-high-cpu \
  --metric-name CPUUtilization --namespace AWS/ECS \
  --dimensions Name=ClusterName,Value=my-cluster Name=ServiceName,Value=my-service \
  --statistic Average --period 300 --threshold 80 \
  --comparison-operator GreaterThanThreshold --evaluation-periods 2 \
  --alarm-actions arn:aws:sns:us-east-1:123456789012:my-topic
```

### Query logs with Insights
```bash
aws logs start-query --log-group-name /ecs/my-service \
  --start-time $(date -d '1 hour ago' +%s) --end-time $(date +%s) \
  --query-string 'fields @timestamp, @message | filter @message like /ERROR/ | sort @timestamp desc | limit 20'
aws logs get-query-results --query-id <query-id>
```

### Create a log group with retention
```bash
aws logs create-log-group --log-group-name /ecs/my-service
aws logs put-retention-policy --log-group-name /ecs/my-service --retention-in-days 30
```

### Get metric statistics
```bash
aws cloudwatch get-metric-statistics --namespace AWS/ECS \
  --metric-name MemoryUtilization --dimensions Name=ClusterName,Value=my-cluster \
  --start-time 2026-02-11T00:00:00Z --end-time 2026-02-11T12:00:00Z \
  --period 3600 --statistics Average Maximum
```

### Tail logs in real time
```bash
aws logs tail /ecs/my-service --follow --since 10m
```

## Covered Command Groups

| Group | Commands | CLI Service |
|-------|----------|-------------|
| Metrics | put-metric-data, get-metric-data, get-metric-statistics, list-metrics | `aws cloudwatch` |
| Alarms | put-metric-alarm, put-composite-alarm, describe-alarms, delete-alarms, set-alarm-state, enable/disable-alarm-actions | `aws cloudwatch` |
| Dashboards | put-dashboard, get-dashboard, list-dashboards, delete-dashboards | `aws cloudwatch` |
| Anomaly Detection | put-anomaly-detector, describe-anomaly-detectors, delete-anomaly-detector | `aws cloudwatch` |
| Log Groups | create, delete, describe, put-retention-policy, tag/untag | `aws logs` |
| Log Streams | create, delete, describe | `aws logs` |
| Log Events | put, get, filter, tail | `aws logs` |
| Metric Filters | put, describe, delete | `aws logs` |
| Subscription Filters | put, describe, delete | `aws logs` |
| Logs Insights | start-query, stop-query, get-query-results, describe-queries | `aws logs` |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-cloudwatch/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-cloudwatch`

**Step 3: Commit**

```bash
git add skills/aws-cli-cloudwatch/SKILL.md
git commit -m "feat: add CloudWatch skill overview (SKILL.md)"
```

---

## Task 4: Create CloudWatch reference.md

**Files:**
- Create: `skills/aws-cli-cloudwatch/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-cloudwatch/reference.md` covering both `aws cloudwatch` and `aws logs`. Structure:

1. Version header citing AWS CLI v2 docs
2. Table of Contents with numbered sections
3. Quick Reference table of all subcommands for both namespaces
4. Grouped sections:
   - **Metrics (`aws cloudwatch`)**: `put-metric-data`, `get-metric-data`, `get-metric-statistics`, `list-metrics`, `get-metric-stream`, `put-metric-stream`, `delete-metric-stream`, `list-metric-streams`, `start-metric-streams`, `stop-metric-streams`
   - **Alarms (`aws cloudwatch`)**: `put-metric-alarm`, `put-composite-alarm`, `describe-alarms`, `describe-alarms-for-metric`, `describe-alarm-history`, `delete-alarms`, `set-alarm-state`, `enable-alarm-actions`, `disable-alarm-actions`
   - **Dashboards (`aws cloudwatch`)**: `put-dashboard`, `get-dashboard`, `list-dashboards`, `delete-dashboards`
   - **Anomaly Detection (`aws cloudwatch`)**: `put-anomaly-detector`, `describe-anomaly-detectors`, `delete-anomaly-detector`
   - **Insight Rules (`aws cloudwatch`)**: `put-insight-rule`, `describe-insight-rules`, `delete-insight-rules`, `enable-insight-rules`, `disable-insight-rules`, `get-insight-rule-report`
   - **Tags (`aws cloudwatch`)**: `tag-resource`, `untag-resource`, `list-tags-for-resource`
   - **Log Groups (`aws logs`)**: `create-log-group`, `delete-log-group`, `describe-log-groups`, `put-retention-policy`, `delete-retention-policy`, `tag-log-group`, `untag-log-group`, `list-tags-log-group`, `associate-kms-key`, `disassociate-kms-key`
   - **Log Streams (`aws logs`)**: `create-log-stream`, `delete-log-stream`, `describe-log-streams`
   - **Log Events (`aws logs`)**: `put-log-events`, `get-log-events`, `filter-log-events`, `tail`
   - **Metric Filters (`aws logs`)**: `put-metric-filter`, `describe-metric-filters`, `delete-metric-filter`
   - **Subscription Filters (`aws logs`)**: `put-subscription-filter`, `describe-subscription-filters`, `delete-subscription-filter`
   - **Destinations (`aws logs`)**: `put-destination`, `put-destination-policy`, `describe-destinations`, `delete-destination`
   - **Logs Insights (`aws logs`)**: `start-query`, `stop-query`, `get-query-results`, `describe-queries`, `get-log-record`
   - **Export Tasks (`aws logs`)**: `create-export-task`, `describe-export-tasks`, `cancel-export-task`
   - **Resource Policies (`aws logs`)**: `put-resource-policy`, `describe-resource-policies`, `delete-resource-policy`
   - **Log Data Protection (`aws logs`)**: `put-data-protection-policy`, `get-data-protection-policy`, `delete-data-protection-policy`
   - **Query Definitions (`aws logs`)**: `put-query-definition`, `describe-query-definitions`, `delete-query-definition`

5. Each command: description, required params, optional params, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/cloudwatch/ and https://docs.aws.amazon.com/cli/latest/reference/logs/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-cloudwatch/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-cloudwatch/reference.md
git commit -m "feat: add CloudWatch complete command reference"
```

---

## Task 5: Create ELBv2 SKILL.md

**Files:**
- Create: `skills/aws-cli-elbv2/SKILL.md`

**Step 1: Create the SKILL.md file**

```markdown
---
name: aws-cli-elbv2
description: Use when working with AWS Elastic Load Balancing v2 commands — Application Load Balancers (ALB), Network Load Balancers (NLB), target groups, listeners, rules, health checks
---

# AWS CLI v2 — ELBv2 (Elastic Load Balancing v2)

## Overview

Complete reference for all `aws elbv2` subcommands in AWS CLI v2. Covers Application Load Balancers (ALB), Network Load Balancers (NLB), Gateway Load Balancers (GWLB), target groups, listeners, listener rules, health checks, SSL certificates, and WAF integration.

## When to Use

- Creating ALBs or NLBs for ECS service traffic
- Configuring target groups (IP or instance type) for ECS services
- Setting up listeners with HTTP/HTTPS/TLS rules
- Configuring path-based or host-based routing rules
- Managing SSL/TLS certificates on load balancers
- Configuring health checks for target groups
- Setting up sticky sessions
- Enabling access logging

## Quick Reference — Common Workflows

### Create ALB for ECS
```bash
aws elbv2 create-load-balancer --name my-alb --type application \
  --subnets subnet-aaa subnet-bbb --security-groups sg-xxx
```

### Create target group (IP type for awsvpc network mode)
```bash
aws elbv2 create-target-group --name my-tg --protocol HTTP --port 80 \
  --vpc-id vpc-xxx --target-type ip \
  --health-check-path /health --health-check-interval-seconds 30
```

### Create HTTPS listener with default action
```bash
aws elbv2 create-listener --load-balancer-arn arn:aws:elasticloadbalancing:... \
  --protocol HTTPS --port 443 \
  --certificates CertificateArn=arn:aws:acm:... \
  --default-actions Type=forward,TargetGroupArn=arn:aws:elasticloadbalancing:...
```

### Create path-based routing rule
```bash
aws elbv2 create-rule --listener-arn arn:aws:elasticloadbalancing:... \
  --conditions Field=path-pattern,Values='/api/*' \
  --actions Type=forward,TargetGroupArn=arn:aws:elasticloadbalancing:... \
  --priority 10
```

### Describe target health
```bash
aws elbv2 describe-target-health --target-group-arn arn:aws:elasticloadbalancing:...
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Load Balancers | create, delete, describe, modify, set-subnets, set-security-groups, set-ip-address-type | ALB/NLB/GWLB lifecycle |
| Target Groups | create, delete, describe, modify, register/deregister targets, describe-target-health | Target management |
| Listeners | create, delete, describe, modify | Listener configuration |
| Rules | create, delete, describe, modify, set-rule-priorities | Routing rules |
| Certificates | add, remove, describe listener certificates | SSL/TLS management |
| Attributes | describe/modify load-balancer-attributes, describe/modify target-group-attributes | Feature configuration |
| Tags | add-tags, remove-tags, describe-tags | Resource tagging |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-elbv2/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-elbv2`

**Step 3: Commit**

```bash
git add skills/aws-cli-elbv2/SKILL.md
git commit -m "feat: add ELBv2 skill overview (SKILL.md)"
```

---

## Task 6: Create ELBv2 reference.md

**Files:**
- Create: `skills/aws-cli-elbv2/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-elbv2/reference.md`. Structure:

1. Version header citing AWS CLI v2 docs
2. Table of Contents with numbered sections
3. Quick Reference table of all `aws elbv2` subcommands
4. Grouped sections:
   - **Load Balancers**: `create-load-balancer`, `delete-load-balancer`, `describe-load-balancers`, `modify-load-balancer-attributes`, `describe-load-balancer-attributes`, `set-subnets`, `set-security-groups`, `set-ip-address-type`
   - **Target Groups**: `create-target-group`, `delete-target-group`, `describe-target-groups`, `modify-target-group`, `modify-target-group-attributes`, `describe-target-group-attributes`, `register-targets`, `deregister-targets`, `describe-target-health`
   - **Listeners**: `create-listener`, `delete-listener`, `describe-listeners`, `modify-listener`
   - **Rules**: `create-rule`, `delete-rule`, `describe-rules`, `modify-rule`, `set-rule-priorities`
   - **Certificates**: `add-listener-certificates`, `remove-listener-certificates`, `describe-listener-certificates`
   - **SSL Policies**: `describe-ssl-policies`
   - **Account Limits**: `describe-account-limits`
   - **Tags**: `add-tags`, `remove-tags`, `describe-tags`
   - **Trust Stores**: `create-trust-store`, `delete-trust-store`, `describe-trust-stores`, `modify-trust-store`, `get-trust-store-ca-certificates-bundle`, `describe-trust-store-associations`, `describe-trust-store-revocations`, `add-trust-store-revocations`, `remove-trust-store-revocations`

5. Each command: description, required params, optional params, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/elbv2/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-elbv2/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-elbv2/reference.md
git commit -m "feat: add ELBv2 complete command reference"
```

---

## Task 7: Create Lambda SKILL.md

**Files:**
- Create: `skills/aws-cli-lambda/SKILL.md`

**Step 1: Create the SKILL.md file**

```markdown
---
name: aws-cli-lambda
description: Use when working with AWS Lambda commands — functions, layers, event source mappings, aliases, versions, concurrency, URLs, code signing
---

# AWS CLI v2 — Lambda (Serverless Compute)

## Overview

Complete reference for all `aws lambda` subcommands in AWS CLI v2. Covers function creation and management, deployment packages, layers, event source mappings, aliases, versions, provisioned concurrency, function URLs, code signing, and permissions.

## When to Use

- Creating or managing Lambda functions
- Deploying function code (zip or container image)
- Invoking functions (sync or async)
- Managing Lambda layers
- Configuring event source mappings (SQS, Kinesis, DynamoDB Streams, Kafka)
- Creating and managing aliases and versions
- Configuring provisioned concurrency
- Setting up function URLs for HTTP access
- Managing resource-based policies (permissions)
- Configuring code signing

## Quick Reference — Common Workflows

### Create a function from zip
```bash
aws lambda create-function --function-name my-func \
  --runtime python3.12 --handler index.handler \
  --role arn:aws:iam::123456789012:role/lambda-role \
  --zip-file fileb://function.zip
```

### Create a function from container image
```bash
aws lambda create-function --function-name my-func \
  --package-type Image \
  --code ImageUri=123456789012.dkr.ecr.us-east-1.amazonaws.com/my-app:latest \
  --role arn:aws:iam::123456789012:role/lambda-role
```

### Update function code
```bash
aws lambda update-function-code --function-name my-func --zip-file fileb://function.zip
aws lambda wait function-updated --function-name my-func
```

### Invoke a function
```bash
aws lambda invoke --function-name my-func --payload '{"key":"value"}' output.json
cat output.json
```

### Add an SQS event source
```bash
aws lambda create-event-source-mapping --function-name my-func \
  --event-source-arn arn:aws:sqs:us-east-1:123456789012:my-queue \
  --batch-size 10
```

### Publish version and create alias
```bash
aws lambda publish-version --function-name my-func --description "v1"
aws lambda create-alias --function-name my-func --name prod --function-version 1
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Functions | create, delete, get, list, update-code, update-configuration, wait | Function lifecycle |
| Invocation | invoke, invoke-async | Running functions |
| Layers | publish, get, list, delete, list-versions, get-policy, add/remove-permission | Shared code layers |
| Event Source Mappings | create, delete, get, list, update | Trigger configuration |
| Aliases | create, delete, get, list, update | Traffic routing |
| Versions | publish-version, list-versions-by-function | Immutable snapshots |
| Concurrency | put/get/delete provisioned-concurrency, put/get/delete function-concurrency | Scaling config |
| Function URLs | create, delete, get, update | HTTP endpoints |
| Permissions | add-permission, remove-permission, get-policy | Resource policies |
| Code Signing | create/update/get/list/delete code-signing-config | Signing configuration |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-lambda/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-lambda`

**Step 3: Commit**

```bash
git add skills/aws-cli-lambda/SKILL.md
git commit -m "feat: add Lambda skill overview (SKILL.md)"
```

---

## Task 8: Create Lambda reference.md

**Files:**
- Create: `skills/aws-cli-lambda/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-lambda/reference.md`. Structure:

1. Version header citing AWS CLI v2 docs
2. Table of Contents with numbered sections
3. Quick Reference table of all `aws lambda` subcommands
4. Grouped sections:
   - **Functions**: `create-function`, `delete-function`, `get-function`, `get-function-configuration`, `list-functions`, `update-function-code`, `update-function-configuration`, `update-function-event-invoke-config`, `put-function-event-invoke-config`, `get-function-event-invoke-config`, `delete-function-event-invoke-config`, `list-function-event-invoke-configs`
   - **Invocation**: `invoke`, `invoke-async` (deprecated)
   - **Layers**: `publish-layer-version`, `get-layer-version`, `get-layer-version-by-arn`, `list-layers`, `list-layer-versions`, `delete-layer-version`, `get-layer-version-policy`, `add-layer-version-permission`, `remove-layer-version-permission`
   - **Event Source Mappings**: `create-event-source-mapping`, `delete-event-source-mapping`, `get-event-source-mapping`, `list-event-source-mappings`, `update-event-source-mapping`
   - **Aliases**: `create-alias`, `delete-alias`, `get-alias`, `list-aliases`, `update-alias`
   - **Versions**: `publish-version`, `list-versions-by-function`
   - **Concurrency**: `put-function-concurrency`, `get-function-concurrency`, `delete-function-concurrency`, `put-provisioned-concurrency-config`, `get-provisioned-concurrency-config`, `delete-provisioned-concurrency-config`, `list-provisioned-concurrency-configs`
   - **Function URLs**: `create-function-url-config`, `delete-function-url-config`, `get-function-url-config`, `update-function-url-config`, `list-function-url-configs`
   - **Permissions**: `add-permission`, `remove-permission`, `get-policy`
   - **Code Signing**: `create-code-signing-config`, `update-code-signing-config`, `get-code-signing-config`, `list-code-signing-configs`, `delete-code-signing-config`, `get-function-code-signing-config`, `put-function-code-signing-config`, `delete-function-code-signing-config`
   - **Tags**: `tag-resource`, `untag-resource`, `list-tags`
   - **Account**: `get-account-settings`

5. Each command: description, required params, optional params, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/lambda/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-lambda/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-lambda/reference.md
git commit -m "feat: add Lambda complete command reference"
```

---

## Task 9: Create DynamoDB SKILL.md

**Files:**
- Create: `skills/aws-cli-dynamodb/SKILL.md`

**Step 1: Create the SKILL.md file**

```markdown
---
name: aws-cli-dynamodb
description: Use when working with AWS DynamoDB commands — tables, items, indexes, queries, scans, streams, backups, global tables, TTL, transactions
---

# AWS CLI v2 — DynamoDB (NoSQL Database)

## Overview

Complete reference for all `aws dynamodb` subcommands in AWS CLI v2. Covers table management, item CRUD operations, queries and scans, secondary indexes (GSI/LSI), DynamoDB Streams, on-demand and provisioned capacity, backups and restore, global tables, TTL, transactions, and batch operations.

## When to Use

- Creating or managing DynamoDB tables
- Performing CRUD operations on items (put, get, update, delete)
- Querying tables and indexes
- Scanning tables with filters
- Managing Global Secondary Indexes (GSI)
- Configuring DynamoDB Streams
- Creating and restoring backups
- Setting up global tables for multi-region
- Configuring TTL (time to live)
- Running transactional reads and writes
- Batch read/write operations
- Importing/exporting table data to/from S3

## Quick Reference — Common Workflows

### Create a table
```bash
aws dynamodb create-table --table-name my-table \
  --attribute-definitions AttributeName=pk,AttributeType=S AttributeName=sk,AttributeType=S \
  --key-schema AttributeName=pk,KeyType=HASH AttributeName=sk,KeyType=RANGE \
  --billing-mode PAY_PER_REQUEST
aws dynamodb wait table-exists --table-name my-table
```

### Put and get an item
```bash
aws dynamodb put-item --table-name my-table \
  --item '{"pk":{"S":"user#123"},"sk":{"S":"profile"},"name":{"S":"Alice"}}'
aws dynamodb get-item --table-name my-table \
  --key '{"pk":{"S":"user#123"},"sk":{"S":"profile"}}'
```

### Query by partition key
```bash
aws dynamodb query --table-name my-table \
  --key-condition-expression "pk = :pk AND begins_with(sk, :prefix)" \
  --expression-attribute-values '{":pk":{"S":"user#123"},":prefix":{"S":"order#"}}'
```

### Batch write
```bash
aws dynamodb batch-write-item --request-items file://batch.json
```

### Enable TTL
```bash
aws dynamodb update-time-to-live --table-name my-table \
  --time-to-live-specification Enabled=true,AttributeName=ttl
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Tables | create, delete, describe, list, update | Table lifecycle |
| Items | put, get, update, delete | Single-item CRUD |
| Query & Scan | query, scan | Read operations |
| Batch | batch-write-item, batch-get-item | Multi-item operations |
| Transactions | transact-write-items, transact-get-items | ACID transactions |
| Indexes | update-table (GSI changes), describe-table | Secondary indexes |
| Streams | describe-stream, get-records, get-shard-iterator, list-streams | Change data capture |
| Backups | create-backup, delete-backup, describe-backup, list-backups, restore-table-from-backup | Point-in-time |
| PITR | describe/update-continuous-backups, restore-table-to-point-in-time | Continuous backups |
| Global Tables | create, describe, list, update global-table | Multi-region |
| TTL | describe/update-time-to-live | Item expiration |
| Import/Export | import-table, describe-import, list-imports, export-table-to-point-in-time, describe-export, list-exports | S3 integration |
| Tags | tag-resource, untag-resource, list-tags-of-resource | Resource tagging |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-dynamodb/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-dynamodb`

**Step 3: Commit**

```bash
git add skills/aws-cli-dynamodb/SKILL.md
git commit -m "feat: add DynamoDB skill overview (SKILL.md)"
```

---

## Task 10: Create DynamoDB reference.md

**Files:**
- Create: `skills/aws-cli-dynamodb/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-dynamodb/reference.md`. Structure:

1. Version header citing AWS CLI v2 docs
2. Table of Contents with numbered sections
3. Quick Reference table of all `aws dynamodb` subcommands
4. Grouped sections:
   - **Tables**: `create-table`, `delete-table`, `describe-table`, `list-tables`, `update-table`, `describe-table-replica-auto-scaling`, `update-table-replica-auto-scaling`
   - **Items**: `put-item`, `get-item`, `update-item`, `delete-item`
   - **Query & Scan**: `query`, `scan`
   - **Batch Operations**: `batch-write-item`, `batch-get-item`, `batch-execute-statement`
   - **Transactions**: `transact-write-items`, `transact-get-items`, `execute-transaction`
   - **PartiQL**: `execute-statement`, `batch-execute-statement`, `execute-transaction`
   - **Streams (`aws dynamodbstreams`)**: `describe-stream`, `get-records`, `get-shard-iterator`, `list-streams`
   - **Backups**: `create-backup`, `delete-backup`, `describe-backup`, `list-backups`, `restore-table-from-backup`
   - **Continuous Backups (PITR)**: `describe-continuous-backups`, `update-continuous-backups`, `restore-table-to-point-in-time`
   - **Global Tables**: `create-global-table`, `describe-global-table`, `list-global-tables`, `update-global-table`, `describe-global-table-settings`, `update-global-table-settings`
   - **TTL**: `describe-time-to-live`, `update-time-to-live`
   - **Import/Export**: `import-table`, `describe-import`, `list-imports`, `export-table-to-point-in-time`, `describe-export`, `list-exports`
   - **Endpoints**: `describe-endpoints`
   - **Limits**: `describe-limits`
   - **Contributor Insights**: `describe-contributor-insights`, `update-contributor-insights`, `list-contributor-insights`
   - **Kinesis Streaming**: `describe-kinesis-streaming-destination`, `enable-kinesis-streaming-destination`, `disable-kinesis-streaming-destination`
   - **Tags**: `tag-resource`, `untag-resource`, `list-tags-of-resource`

5. Each command: description, required params, optional params, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/dynamodb/ and https://docs.aws.amazon.com/cli/latest/reference/dynamodbstreams/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-dynamodb/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-dynamodb/reference.md
git commit -m "feat: add DynamoDB complete command reference"
```

---

## Task 11: Update router skill service index with all 5 new services

**Files:**
- Modify: `skills/aws-cli/SKILL.md:2` (description frontmatter)
- Modify: `skills/aws-cli/SKILL.md:14-21` (Service Index table)

**Step 1: Update YAML frontmatter description**

Change to:
```yaml
description: Use when working with any AWS CLI v2 commands — provides general CLI conventions and routes to per-service reference skills for ECS, EC2, ECR, S3, RDS, Route 53, IAM, CloudWatch, ELBv2, Lambda, DynamoDB
```

**Step 2: Add 5 new rows to Service Index table**

Append after the Route 53 row:
```markdown
| IAM | `aws-cli-iam` | Users, groups, roles, policies, instance profiles, access keys, MFA, identity providers |
| CloudWatch | `aws-cli-cloudwatch` | Metrics, alarms, dashboards, log groups, log streams, metric filters, Insights queries |
| ELBv2 | `aws-cli-elbv2` | ALBs, NLBs, target groups, listeners, rules, health checks, SSL certificates |
| Lambda | `aws-cli-lambda` | Functions, layers, event source mappings, aliases, versions, concurrency, URLs |
| DynamoDB | `aws-cli-dynamodb` | Tables, items, indexes, queries, scans, streams, backups, global tables, TTL |
```

**Step 3: Commit**

```bash
git add skills/aws-cli/SKILL.md
git commit -m "feat: add IAM, CloudWatch, ELBv2, Lambda, DynamoDB to router service index"
```

---

## Task 12: Update CLAUDE.md with new services

**Files:**
- Modify: `CLAUDE.md` (skill hierarchy tree + service list in "How Skills Work")

**Step 1: Add new entries to skill hierarchy tree**

Add after the `aws-cli-route53/` entry:
```
  aws-cli-iam/            # IAM reference (users, roles, policies, instance profiles)
    SKILL.md
    reference.md
  aws-cli-cloudwatch/     # CloudWatch reference (cloudwatch + logs)
    SKILL.md
    reference.md
  aws-cli-elbv2/          # ELBv2 reference (ALB, NLB, target groups, listeners)
    SKILL.md
    reference.md
  aws-cli-lambda/         # Lambda reference (functions, layers, events)
    SKILL.md
    reference.md
  aws-cli-dynamodb/       # DynamoDB reference (tables, items, streams)
    SKILL.md
    reference.md
```

**Step 2: Update the service list in "How Skills Work"**

Update the parenthetical list to include all 11 services.

**Step 3: Commit**

```bash
git add CLAUDE.md
git commit -m "docs: update CLAUDE.md with wave 3 services"
```

---

## Dependency Summary

```
Task 1 (IAM SKILL.md)        → Task 2 (IAM reference.md)
Task 3 (CW SKILL.md)         → Task 4 (CW reference.md)
Task 5 (ELBv2 SKILL.md)      → Task 6 (ELBv2 reference.md)
Task 7 (Lambda SKILL.md)     → Task 8 (Lambda reference.md)
Task 9 (DynamoDB SKILL.md)   → Task 10 (DynamoDB reference.md)
Tasks 2,4,6,8,10              → Task 11 (update router)
Task 11                       → Task 12 (update CLAUDE.md)
```

Tasks 1-2, 3-4, 5-6, 7-8, and 9-10 can all run **in parallel** (each service is independent). Task 11 depends on all services being complete. Task 12 is last.
