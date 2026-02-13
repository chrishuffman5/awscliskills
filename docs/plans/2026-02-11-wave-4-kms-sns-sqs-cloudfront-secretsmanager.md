# Wave 4: KMS, SNS, SQS, CloudFront, Secrets Manager Skills

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Add 5 more AWS CLI reference skills (KMS, SNS, SQS, CloudFront, Secrets Manager) to the skill library, bringing total coverage to 16 services.

**Architecture:** Each service gets a `skills/aws-cli-<service>/` directory with `SKILL.md` (YAML frontmatter + overview + common workflows) and `reference.md` (exhaustive command reference with all flags, types, defaults, JSON output schemas). The router skill `skills/aws-cli/SKILL.md` service index is updated with all 5 new entries. Use `skills/aws-cli-ecr/` as the format template.

**Tech Stack:** Static Markdown, AWS CLI v2 documentation, YAML frontmatter for Claude skill metadata

---

## Service Selection Rationale

| Service | Why | CLI Namespace |
|---------|-----|---------------|
| KMS | Encryption key management — used by S3, RDS, EBS, Lambda, Secrets Manager, and ECS for data encryption | `aws kms` |
| SNS | Notification fan-out — CloudWatch alarm targets, event-driven architectures, push notifications | `aws sns` |
| SQS | Message queuing — decoupling services, Lambda event sources, task queues, dead-letter queues | `aws sqs` |
| CloudFront | CDN — S3/ALB origins, edge caching, custom domains with Route 53 + ACM | `aws cloudfront` |
| Secrets Manager | Secret storage — RDS credentials, API keys, ECS task secrets with auto-rotation | `aws secretsmanager` |

---

## Task 1: Create KMS SKILL.md

**Files:**
- Create: `skills/aws-cli-kms/SKILL.md`

**Step 1: Create the SKILL.md file**

```markdown
---
name: aws-cli-kms
description: Use when working with AWS KMS commands — encryption keys, key policies, grants, aliases, encryption/decryption, key rotation, multi-region keys, custom key stores
---

# AWS CLI v2 — KMS (Key Management Service)

## Overview

Complete reference for all `aws kms` subcommands in AWS CLI v2. Covers symmetric and asymmetric key creation, key policies, grants, aliases, encrypt/decrypt/sign/verify operations, automatic key rotation, multi-region keys, custom key stores (CloudHSM), and key material import.

## When to Use

- Creating and managing KMS keys (symmetric, asymmetric, HMAC)
- Encrypting and decrypting data
- Signing and verifying digital signatures
- Managing key policies and grants
- Creating and managing key aliases
- Configuring automatic key rotation
- Setting up multi-region keys
- Managing custom key stores (CloudHSM-backed)
- Importing external key material

## Quick Reference — Common Workflows

### Create a symmetric encryption key
```bash
aws kms create-key --description "My encryption key" \
  --key-usage ENCRYPT_DECRYPT --key-spec SYMMETRIC_DEFAULT
aws kms create-alias --alias-name alias/my-key --target-key-id <key-id>
```

### Encrypt and decrypt data
```bash
aws kms encrypt --key-id alias/my-key --plaintext fileb://plaintext.txt \
  --output text --query CiphertextBlob | base64 --decode > encrypted.bin
aws kms decrypt --ciphertext-blob fileb://encrypted.bin \
  --output text --query Plaintext | base64 --decode > decrypted.txt
```

### Generate a data key for envelope encryption
```bash
aws kms generate-data-key --key-id alias/my-key --key-spec AES_256
```

### Enable automatic key rotation
```bash
aws kms enable-key-rotation --key-id <key-id>
aws kms get-key-rotation-status --key-id <key-id>
```

### List all keys and aliases
```bash
aws kms list-keys --query 'Keys[].KeyId'
aws kms list-aliases --query 'Aliases[].{Alias:AliasName,Key:TargetKeyId}'
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Keys | create-key, describe-key, list-keys, enable-key, disable-key, schedule/cancel-key-deletion | Key lifecycle |
| Cryptographic Ops | encrypt, decrypt, re-encrypt, generate-data-key, generate-data-key-without-plaintext, generate-random, sign, verify, generate-mac, verify-mac | Data operations |
| Key Policies | get/put-key-policy, list-key-policies | Access control |
| Grants | create-grant, list-grants, list-retirable-grants, retire-grant, revoke-grant | Delegated access |
| Aliases | create-alias, delete-alias, list-aliases, update-alias | Friendly names |
| Rotation | enable/disable-key-rotation, get-key-rotation-status, rotate-key-on-demand | Key rotation |
| Multi-Region | replicate-key, update-primary-region | Cross-region keys |
| Custom Key Stores | create/delete/describe/update/connect/disconnect-custom-key-store | CloudHSM-backed |
| Import Key Material | get-parameters-for-import, import-key-material, delete-imported-key-material | External keys |
| Tags | tag-resource, untag-resource, list-resource-tags | Resource tagging |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-kms/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-kms`

**Step 3: Commit**

```bash
git add skills/aws-cli-kms/SKILL.md
git commit -m "feat: add KMS skill overview (SKILL.md)"
```

---

## Task 2: Create KMS reference.md

**Files:**
- Create: `skills/aws-cli-kms/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-kms/reference.md` with the complete KMS command reference. Structure:

1. Version header citing AWS CLI v2 docs source URL
2. Table of Contents with numbered sections
3. Quick Reference table of ALL `aws kms` subcommands (command | category | description)
4. Grouped sections:
   - **Keys**: `create-key`, `describe-key`, `list-keys`, `enable-key`, `disable-key`, `schedule-key-deletion`, `cancel-key-deletion`, `update-key-description`, `get-key-policy`, `put-key-policy`, `list-key-policies`
   - **Cryptographic Operations**: `encrypt`, `decrypt`, `re-encrypt`, `generate-data-key`, `generate-data-key-without-plaintext`, `generate-data-key-pair`, `generate-data-key-pair-without-plaintext`, `generate-random`, `sign`, `verify`, `generate-mac`, `verify-mac`, `derive-shared-secret`
   - **Grants**: `create-grant`, `list-grants`, `list-retirable-grants`, `retire-grant`, `revoke-grant`
   - **Aliases**: `create-alias`, `delete-alias`, `list-aliases`, `update-alias`
   - **Key Rotation**: `enable-key-rotation`, `disable-key-rotation`, `get-key-rotation-status`, `rotate-key-on-demand`, `list-key-rotations`
   - **Multi-Region Keys**: `replicate-key`, `update-primary-region`
   - **Custom Key Stores**: `create-custom-key-store`, `delete-custom-key-store`, `describe-custom-key-stores`, `update-custom-key-store`, `connect-custom-key-store`, `disconnect-custom-key-store`
   - **Import Key Material**: `get-parameters-for-import`, `import-key-material`, `delete-imported-key-material`
   - **Tags**: `tag-resource`, `untag-resource`, `list-resource-tags`

5. Each command: description, required params table, optional params table, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/kms/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-kms/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-kms/reference.md
git commit -m "feat: add KMS complete command reference"
```

---

## Task 3: Create SNS SKILL.md

**Files:**
- Create: `skills/aws-cli-sns/SKILL.md`

**Step 1: Create the SKILL.md file**

```markdown
---
name: aws-cli-sns
description: Use when working with AWS SNS commands — topics, subscriptions, publishing messages, SMS, platform applications, push notifications, FIFO topics, message filtering
---

# AWS CLI v2 — SNS (Simple Notification Service)

## Overview

Complete reference for all `aws sns` subcommands in AWS CLI v2. Covers topic management, subscription configuration (email, SQS, Lambda, HTTP, SMS), message publishing, message filtering, FIFO topics, platform applications for mobile push, and SMS messaging.

## When to Use

- Creating and managing SNS topics (standard and FIFO)
- Subscribing endpoints (email, SQS queues, Lambda functions, HTTP/HTTPS, SMS)
- Publishing messages to topics
- Configuring subscription filter policies
- Setting up dead-letter queues for failed deliveries
- Managing mobile push notification platform applications
- Sending SMS messages
- Configuring CloudWatch alarm notification targets

## Quick Reference — Common Workflows

### Create topic and subscribe
```bash
aws sns create-topic --name my-topic
aws sns subscribe --topic-arn arn:aws:sns:us-east-1:123456789012:my-topic \
  --protocol email --notification-endpoint user@example.com
```

### Publish a message
```bash
aws sns publish --topic-arn arn:aws:sns:us-east-1:123456789012:my-topic \
  --subject "Alert" --message "Something happened"
```

### Subscribe SQS queue to SNS topic
```bash
aws sns subscribe --topic-arn arn:aws:sns:us-east-1:123456789012:my-topic \
  --protocol sqs --notification-endpoint arn:aws:sqs:us-east-1:123456789012:my-queue
```

### Subscribe Lambda function
```bash
aws sns subscribe --topic-arn arn:aws:sns:us-east-1:123456789012:my-topic \
  --protocol lambda --notification-endpoint arn:aws:lambda:us-east-1:123456789012:function:my-func
```

### Set subscription filter policy
```bash
aws sns set-subscription-attributes --subscription-arn arn:aws:sns:... \
  --attribute-name FilterPolicy --attribute-value '{"event_type":["order_placed"]}'
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Topics | create, delete, list, get/set-attributes | Topic lifecycle |
| Subscriptions | subscribe, unsubscribe, confirm, list, get/set-attributes | Endpoint management |
| Publishing | publish, publish-batch | Message delivery |
| Platform Applications | create, delete, get/set/list platform-application, create/delete/get/set/list platform-endpoint | Mobile push |
| SMS | set/get/check-if-phone-number-is-opted-out, list-phone-numbers-opted-out, create/delete/list/get origination-identity | SMS messaging |
| Tags | tag-resource, untag-resource, list-tags-for-resource | Resource tagging |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-sns/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-sns`

**Step 3: Commit**

```bash
git add skills/aws-cli-sns/SKILL.md
git commit -m "feat: add SNS skill overview (SKILL.md)"
```

---

## Task 4: Create SNS reference.md

**Files:**
- Create: `skills/aws-cli-sns/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-sns/reference.md`. Structure:

1. Version header citing AWS CLI v2 docs
2. Table of Contents with numbered sections
3. Quick Reference table of all `aws sns` subcommands
4. Grouped sections:
   - **Topics**: `create-topic`, `delete-topic`, `list-topics`, `get-topic-attributes`, `set-topic-attributes`
   - **Subscriptions**: `subscribe`, `unsubscribe`, `confirm-subscription`, `list-subscriptions`, `list-subscriptions-by-topic`, `get-subscription-attributes`, `set-subscription-attributes`
   - **Publishing**: `publish`, `publish-batch`
   - **Platform Applications**: `create-platform-application`, `delete-platform-application`, `get-platform-application-attributes`, `set-platform-application-attributes`, `list-platform-applications`
   - **Platform Endpoints**: `create-platform-endpoint`, `delete-endpoint`, `get-endpoint-attributes`, `set-endpoint-attributes`, `list-endpoints-by-platform-application`
   - **SMS**: `set-sms-attributes`, `get-sms-attributes`, `check-if-phone-number-is-opted-out`, `list-phone-numbers-opted-out`, `opt-in-phone-number`, `create-sms-sandbox-phone-number`, `delete-sms-sandbox-phone-number`, `list-sms-sandbox-phone-numbers`, `verify-sms-sandbox-phone-number`, `get-sms-sandbox-account-status`
   - **Origination Identities**: `create-platform-application` origination numbers, `list-origination-numbers`
   - **Data Protection**: `put-data-protection-policy`, `get-data-protection-policy`
   - **Tags**: `tag-resource`, `untag-resource`, `list-tags-for-resource`

5. Each command: description, required params, optional params, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/sns/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-sns/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-sns/reference.md
git commit -m "feat: add SNS complete command reference"
```

---

## Task 5: Create SQS SKILL.md

**Files:**
- Create: `skills/aws-cli-sqs/SKILL.md`

**Step 1: Create the SKILL.md file**

```markdown
---
name: aws-cli-sqs
description: Use when working with AWS SQS commands — standard and FIFO queues, messages, dead-letter queues, visibility timeout, long polling, message attributes, queue policies
---

# AWS CLI v2 — SQS (Simple Queue Service)

## Overview

Complete reference for all `aws sqs` subcommands in AWS CLI v2. Covers standard and FIFO queue management, sending and receiving messages, dead-letter queues, visibility timeout configuration, long polling, message attributes, queue policies, and purging.

## When to Use

- Creating and managing SQS queues (standard and FIFO)
- Sending, receiving, and deleting messages
- Configuring dead-letter queues (redrive policies)
- Setting visibility timeout and message retention
- Configuring long polling for cost-efficient message consumption
- Setting queue access policies
- Using SQS as a Lambda event source trigger
- Decoupling microservices in ECS architectures

## Quick Reference — Common Workflows

### Create a standard queue
```bash
aws sqs create-queue --queue-name my-queue \
  --attributes VisibilityTimeout=60,MessageRetentionPeriod=345600
```

### Create a FIFO queue
```bash
aws sqs create-queue --queue-name my-queue.fifo \
  --attributes FifoQueue=true,ContentBasedDeduplication=true
```

### Send and receive messages
```bash
aws sqs send-message --queue-url https://sqs.us-east-1.amazonaws.com/123456789012/my-queue \
  --message-body '{"task":"process-order","id":42}'
aws sqs receive-message --queue-url https://sqs.us-east-1.amazonaws.com/123456789012/my-queue \
  --max-number-of-messages 10 --wait-time-seconds 20
```

### Delete a message after processing
```bash
aws sqs delete-message --queue-url https://sqs... --receipt-handle <handle>
```

### Configure dead-letter queue
```bash
aws sqs set-queue-attributes --queue-url https://sqs... \
  --attributes '{"RedrivePolicy":"{\"deadLetterTargetArn\":\"arn:aws:sqs:us-east-1:123456789012:my-dlq\",\"maxReceiveCount\":\"3\"}"}'
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Queues | create, delete, list, get-url, get/set-attributes, purge | Queue lifecycle |
| Messages | send, send-batch, receive, delete, delete-batch, change-visibility, change-visibility-batch | Message operations |
| Dead-Letter | start/cancel-message-move-task, list-message-move-tasks | DLQ redrive |
| Tags | tag-queue, untag-queue, list-queue-tags | Resource tagging |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-sqs/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-sqs`

**Step 3: Commit**

```bash
git add skills/aws-cli-sqs/SKILL.md
git commit -m "feat: add SQS skill overview (SKILL.md)"
```

---

## Task 6: Create SQS reference.md

**Files:**
- Create: `skills/aws-cli-sqs/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-sqs/reference.md`. Structure:

1. Version header citing AWS CLI v2 docs
2. Table of Contents with numbered sections
3. Quick Reference table of all `aws sqs` subcommands
4. Grouped sections:
   - **Queues**: `create-queue`, `delete-queue`, `list-queues`, `get-queue-url`, `get-queue-attributes`, `set-queue-attributes`, `purge-queue`, `list-dead-letter-source-queues`
   - **Messages**: `send-message`, `send-message-batch`, `receive-message`, `delete-message`, `delete-message-batch`, `change-message-visibility`, `change-message-visibility-batch`
   - **Dead-Letter Queue Redrive**: `start-message-move-task`, `cancel-message-move-task`, `list-message-move-tasks`
   - **Permissions**: `add-permission`, `remove-permission`
   - **Tags**: `tag-queue`, `untag-queue`, `list-queue-tags`

5. Each command: description, required params, optional params, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/sqs/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-sqs/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-sqs/reference.md
git commit -m "feat: add SQS complete command reference"
```

---

## Task 7: Create CloudFront SKILL.md

**Files:**
- Create: `skills/aws-cli-cloudfront/SKILL.md`

**Step 1: Create the SKILL.md file**

```markdown
---
name: aws-cli-cloudfront
description: Use when working with AWS CloudFront commands — distributions, origins, cache behaviors, invalidations, functions, origin access control, signed URLs, continuous deployment
---

# AWS CLI v2 — CloudFront (Content Delivery Network)

## Overview

Complete reference for all `aws cloudfront` subcommands in AWS CLI v2. Covers distribution management, origin configuration (S3, ALB, custom), cache behavior settings, invalidations, CloudFront Functions, Lambda@Edge associations, origin access control (OAC), signed URLs/cookies, continuous deployment (staging distributions), and real-time logs.

## When to Use

- Creating and managing CloudFront distributions
- Configuring S3 or ALB origins
- Setting up cache behaviors and TTLs
- Creating invalidations to purge cached content
- Writing and deploying CloudFront Functions
- Configuring origin access control (OAC) for S3
- Setting up custom domains with SSL certificates (ACM)
- Managing cache policies and origin request policies
- Configuring continuous deployment with staging distributions
- Setting up real-time logging

## Quick Reference — Common Workflows

### Create a distribution with S3 origin
```bash
aws cloudfront create-distribution --distribution-config file://dist-config.json
```

### Create an invalidation
```bash
aws cloudfront create-invalidation --distribution-id E1234 \
  --paths '/*'
aws cloudfront wait invalidation-completed --distribution-id E1234 --id I1234
```

### List distributions
```bash
aws cloudfront list-distributions \
  --query 'DistributionList.Items[].{Id:Id,Domain:DomainName,Status:Status}'
```

### Get distribution config (for updates)
```bash
aws cloudfront get-distribution-config --id E1234
# Edit the config, then update:
aws cloudfront update-distribution --id E1234 --distribution-config file://updated.json --if-match <ETag>
```

### Create a CloudFront Function
```bash
aws cloudfront create-function --name my-func --function-config '{
  "Comment":"URL rewrite","Runtime":"cloudfront-js-2.0"
}' --function-code fileb://function.js
aws cloudfront publish-function --name my-func --if-match <ETag>
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Distributions | create, delete, get, list, update, get-config | Distribution lifecycle |
| Invalidations | create, get, list | Cache purging |
| Functions | create, delete, describe, get, list, publish, test, update | Edge compute |
| Cache Policies | create, delete, get, list, update | Caching configuration |
| Origin Request Policies | create, delete, get, list, update | Origin forwarding |
| Response Headers Policies | create, delete, get, list, update | Security headers |
| Origin Access Control | create, delete, get, list, update | S3 OAC |
| Continuous Deployment | create, delete, get, list, update | Staging distributions |
| Key Groups & Public Keys | create, delete, get, list, update | Signed URL keys |
| Real-Time Logs | create, delete, get, list, update | Streaming logs |
| Tags | tag-resource, untag-resource, list-tags-for-resource | Resource tagging |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-cloudfront/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-cloudfront`

**Step 3: Commit**

```bash
git add skills/aws-cli-cloudfront/SKILL.md
git commit -m "feat: add CloudFront skill overview (SKILL.md)"
```

---

## Task 8: Create CloudFront reference.md

**Files:**
- Create: `skills/aws-cli-cloudfront/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-cloudfront/reference.md`. Structure:

1. Version header citing AWS CLI v2 docs
2. Table of Contents with numbered sections
3. Quick Reference table of all `aws cloudfront` subcommands
4. Grouped sections:
   - **Distributions**: `create-distribution`, `delete-distribution`, `get-distribution`, `get-distribution-config`, `list-distributions`, `update-distribution`, `list-distributions-by-web-acl-id`
   - **Invalidations**: `create-invalidation`, `get-invalidation`, `list-invalidations`
   - **Functions**: `create-function`, `delete-function`, `describe-function`, `get-function`, `list-functions`, `publish-function`, `test-function`, `update-function`
   - **Cache Policies**: `create-cache-policy`, `delete-cache-policy`, `get-cache-policy`, `get-cache-policy-config`, `list-cache-policies`, `update-cache-policy`
   - **Origin Request Policies**: `create-origin-request-policy`, `delete-origin-request-policy`, `get-origin-request-policy`, `get-origin-request-policy-config`, `list-origin-request-policies`, `update-origin-request-policy`
   - **Response Headers Policies**: `create-response-headers-policy`, `delete-response-headers-policy`, `get-response-headers-policy`, `get-response-headers-policy-config`, `list-response-headers-policies`, `update-response-headers-policy`
   - **Origin Access Control**: `create-origin-access-control`, `delete-origin-access-control`, `get-origin-access-control`, `get-origin-access-control-config`, `list-origin-access-controls`, `update-origin-access-control`
   - **Cloud Front OAI (legacy)**: `create-cloud-front-origin-access-identity`, `delete-cloud-front-origin-access-identity`, `get-cloud-front-origin-access-identity`, `list-cloud-front-origin-access-identities`, `update-cloud-front-origin-access-identity`
   - **Continuous Deployment**: `create-continuous-deployment-policy`, `delete-continuous-deployment-policy`, `get-continuous-deployment-policy`, `list-continuous-deployment-policies`, `update-continuous-deployment-policy`, `update-distribution-with-staging-config`
   - **Key Groups**: `create-key-group`, `delete-key-group`, `get-key-group`, `get-key-group-config`, `list-key-groups`, `update-key-group`
   - **Public Keys**: `create-public-key`, `delete-public-key`, `get-public-key`, `get-public-key-config`, `list-public-keys`, `update-public-key`
   - **Real-Time Logs**: `create-realtime-log-config`, `delete-realtime-log-config`, `get-realtime-log-config`, `list-realtime-log-configs`, `update-realtime-log-config`
   - **Monitoring Subscriptions**: `create-monitoring-subscription`, `delete-monitoring-subscription`, `get-monitoring-subscription`
   - **Field-Level Encryption**: `create-field-level-encryption-config`, `create-field-level-encryption-profile`, etc.
   - **Tags**: `tag-resource`, `untag-resource`, `list-tags-for-resource`
   - **Wait Commands**: `distribution-deployed`, `invalidation-completed`, `streaming-distribution-deployed`

5. Each command: description, required params, optional params, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/cloudfront/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-cloudfront/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-cloudfront/reference.md
git commit -m "feat: add CloudFront complete command reference"
```

---

## Task 9: Create Secrets Manager SKILL.md

**Files:**
- Create: `skills/aws-cli-secretsmanager/SKILL.md`

**Step 1: Create the SKILL.md file**

```markdown
---
name: aws-cli-secretsmanager
description: Use when working with AWS Secrets Manager commands — secrets, versions, rotation, replication, resource policies, batch retrieval
---

# AWS CLI v2 — Secrets Manager

## Overview

Complete reference for all `aws secretsmanager` subcommands in AWS CLI v2. Covers secret creation and retrieval, version management, automatic rotation with Lambda, cross-region replication, resource-based policies, and batch secret retrieval.

## When to Use

- Storing and retrieving secrets (database credentials, API keys, tokens)
- Configuring automatic secret rotation with Lambda
- Managing secret versions and staging labels
- Setting up cross-region secret replication
- Configuring resource-based policies for cross-account access
- Batch-retrieving multiple secrets
- Restoring deleted secrets within the recovery window
- Injecting secrets into ECS task definitions

## Quick Reference — Common Workflows

### Create a secret
```bash
aws secretsmanager create-secret --name my-db-creds \
  --secret-string '{"username":"admin","password":"s3cret"}'
```

### Retrieve a secret value
```bash
aws secretsmanager get-secret-value --secret-id my-db-creds \
  --query SecretString --output text
```

### Rotate a secret with Lambda
```bash
aws secretsmanager rotate-secret --secret-id my-db-creds \
  --rotation-lambda-arn arn:aws:lambda:us-east-1:123456789012:function:rotate-creds \
  --rotation-rules AutomaticallyAfterDays=30
```

### Update a secret value
```bash
aws secretsmanager update-secret --secret-id my-db-creds \
  --secret-string '{"username":"admin","password":"n3wS3cret"}'
```

### Replicate secret to another region
```bash
aws secretsmanager replicate-secret-to-regions --secret-id my-db-creds \
  --add-replica-regions Region=eu-west-1
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Secrets | create, delete, describe, get-value, list, put-value, restore, update | Secret lifecycle |
| Rotation | rotate-secret, cancel-rotate-secret | Automatic rotation |
| Versions | get-secret-value (with version), list-secret-version-ids, update-secret-version-stage | Version management |
| Replication | replicate-to-regions, remove-regions-from-replication, stop-replication-to-replica | Multi-region |
| Policies | get/put/delete/validate resource-policy | Access control |
| Batch | batch-get-secret-value | Bulk retrieval |
| Random Password | get-random-password | Password generation |
| Tags | tag-resource, untag-resource | Resource tagging |

## Full Command Reference

See `reference.md` in this skill directory for the complete reference with all commands, flags, and output schemas.
```

**Step 2: Verify**

Run: `head -5 skills/aws-cli-secretsmanager/SKILL.md`
Expected: YAML frontmatter with `name: aws-cli-secretsmanager`

**Step 3: Commit**

```bash
git add skills/aws-cli-secretsmanager/SKILL.md
git commit -m "feat: add Secrets Manager skill overview (SKILL.md)"
```

---

## Task 10: Create Secrets Manager reference.md

**Files:**
- Create: `skills/aws-cli-secretsmanager/reference.md`

**Step 1: Create the reference.md file**

Write `skills/aws-cli-secretsmanager/reference.md`. Structure:

1. Version header citing AWS CLI v2 docs
2. Table of Contents with numbered sections
3. Quick Reference table of all `aws secretsmanager` subcommands
4. Grouped sections:
   - **Secret Lifecycle**: `create-secret`, `delete-secret`, `describe-secret`, `list-secrets`, `update-secret`, `restore-secret`, `put-secret-value`
   - **Secret Retrieval**: `get-secret-value`, `batch-get-secret-value`
   - **Versions**: `list-secret-version-ids`, `update-secret-version-stage`
   - **Rotation**: `rotate-secret`, `cancel-rotate-secret`
   - **Replication**: `replicate-secret-to-regions`, `remove-regions-from-replication`, `stop-replication-to-replica`
   - **Resource Policies**: `get-resource-policy`, `put-resource-policy`, `delete-resource-policy`, `validate-resource-policy`
   - **Random Password**: `get-random-password`
   - **Tags**: `tag-resource`, `untag-resource`

5. Each command: description, required params, optional params, JSON output schema

**Data source:** Author from https://docs.aws.amazon.com/cli/latest/reference/secretsmanager/

**Step 2: Verify**

Run: `head -30 skills/aws-cli-secretsmanager/reference.md`
Expected: Version header, table of contents

**Step 3: Commit**

```bash
git add skills/aws-cli-secretsmanager/reference.md
git commit -m "feat: add Secrets Manager complete command reference"
```

---

## Task 11: Update router skill service index with all 5 new services

**Files:**
- Modify: `skills/aws-cli/SKILL.md:2` (description frontmatter)
- Modify: `skills/aws-cli/SKILL.md:14-27` (Service Index table)

**Step 1: Update YAML frontmatter description**

Append `, KMS, SNS, SQS, CloudFront, Secrets Manager` to the description.

**Step 2: Add 5 new rows to Service Index table**

Append after the DynamoDB row:
```markdown
| KMS | `aws-cli-kms` | Encryption keys, key policies, grants, aliases, encrypt/decrypt, key rotation, multi-region |
| SNS | `aws-cli-sns` | Topics, subscriptions, publishing, SMS, platform applications, message filtering |
| SQS | `aws-cli-sqs` | Standard and FIFO queues, messages, dead-letter queues, visibility timeout, long polling |
| CloudFront | `aws-cli-cloudfront` | Distributions, origins, cache behaviors, invalidations, functions, origin access control |
| Secrets Manager | `aws-cli-secretsmanager` | Secrets, versions, rotation, replication, resource policies, batch retrieval |
```

**Step 3: Commit**

```bash
git add skills/aws-cli/SKILL.md
git commit -m "feat: add KMS, SNS, SQS, CloudFront, Secrets Manager to router service index"
```

---

## Task 12: Update CLAUDE.md and README.md with new services

**Files:**
- Modify: `CLAUDE.md` (skill hierarchy tree + service list)
- Modify: `README.md` (Available Skills table)

**Step 1: Add new entries to CLAUDE.md skill hierarchy tree**

Add after the `aws-cli-dynamodb/` entry:
```
  aws-cli-kms/            # KMS reference (keys, encryption, grants, rotation)
    SKILL.md
    reference.md
  aws-cli-sns/            # SNS reference (topics, subscriptions, publishing)
    SKILL.md
    reference.md
  aws-cli-sqs/            # SQS reference (queues, messages, DLQ)
    SKILL.md
    reference.md
  aws-cli-cloudfront/     # CloudFront reference (distributions, invalidations, functions)
    SKILL.md
    reference.md
  aws-cli-secretsmanager/ # Secrets Manager reference (secrets, rotation, replication)
    SKILL.md
    reference.md
```

Update the service list in "How Skills Work" to include all 16 services.

**Step 2: Add new rows to README.md Available Skills table**

Append 5 rows after DynamoDB:
```markdown
| KMS | `aws-cli-kms` | Encryption keys, key policies, grants, aliases, encrypt/decrypt, key rotation, multi-region |
| SNS | `aws-cli-sns` | Topics, subscriptions, publishing, SMS, platform applications, message filtering |
| SQS | `aws-cli-sqs` | Standard and FIFO queues, messages, dead-letter queues, visibility timeout, long polling |
| CloudFront | `aws-cli-cloudfront` | Distributions, origins, cache behaviors, invalidations, functions, origin access control |
| Secrets Manager | `aws-cli-secretsmanager` | Secrets, versions, rotation, replication, resource policies, batch retrieval |
```

**Step 3: Commit**

```bash
git add CLAUDE.md README.md
git commit -m "docs: update CLAUDE.md and README.md with wave 4 services"
```

---

## Dependency Summary

```
Task 1 (KMS SKILL.md)        → Task 2 (KMS reference.md)
Task 3 (SNS SKILL.md)        → Task 4 (SNS reference.md)
Task 5 (SQS SKILL.md)        → Task 6 (SQS reference.md)
Task 7 (CF SKILL.md)         → Task 8 (CF reference.md)
Task 9 (SM SKILL.md)         → Task 10 (SM reference.md)
Tasks 2,4,6,8,10              → Task 11 (update router)
Task 11                       → Task 12 (update CLAUDE.md + README.md)
```

Tasks 1-2, 3-4, 5-6, 7-8, and 9-10 can all run **in parallel** (each service is independent). Task 11 depends on all services being complete. Task 12 is last.
