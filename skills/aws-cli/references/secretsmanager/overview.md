
# AWS CLI v2 — Secrets Manager

## Overview

Complete reference for all `aws secretsmanager` subcommands in AWS CLI v2. Covers secret creation and retrieval, version management, automatic rotation with Lambda, cross-region replication, resource-based policies, and batch secret retrieval.

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

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Secret Lifecycle | [`secret-lifecycle.md`](secret-lifecycle.md) | create-secret, delete-secret, describe-secret, list-secrets, update-secret, restore-secret, put-secret-value |
| Secret Retrieval | [`secret-retrieval.md`](secret-retrieval.md) | get-secret-value, batch-get-secret-value |
| Versions | [`versions.md`](versions.md) | list-secret-version-ids, update-secret-version-stage |
| Rotation | [`rotation.md`](rotation.md) | rotate-secret, cancel-rotate-secret |
| Replication | [`replication.md`](replication.md) | replicate-secret-to-regions, remove-regions-from-replication, stop-replication-to-replica |
| Resource Policies | [`resource-policies.md`](resource-policies.md) | get-resource-policy, put-resource-policy, delete-resource-policy, validate-resource-policy |
| Random Password | [`random-password.md`](random-password.md) | get-random-password |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource |
