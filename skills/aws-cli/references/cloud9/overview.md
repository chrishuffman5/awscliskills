# AWS CLI v2 — Cloud9 (Cloud IDE)

## Overview

Complete reference for all `aws cloud9` subcommands in AWS CLI v2. Covers cloud-based IDE environment management, environment membership, and tagging. Note: AWS Cloud9 is no longer available to new customers. Existing customers can continue to use the service.

## Quick Reference — Common Workflows

### Create an EC2 environment
```bash
aws cloud9 create-environment-ec2 \
  --name my-dev-env \
  --instance-type t3.small \
  --image-id amazonlinux-2023-x86_64 \
  --automatic-stop-time-minutes 30
```

### List all environments
```bash
aws cloud9 list-environments
```

### Describe environments
```bash
aws cloud9 describe-environments --environment-ids env-id-1 env-id-2
```

### Add a member to an environment
```bash
aws cloud9 create-environment-membership \
  --environment-id abc123 \
  --user-arn arn:aws:iam::123456789012:user/jsmith \
  --permissions read-write
```

### Update a member's permissions
```bash
aws cloud9 update-environment-membership \
  --environment-id abc123 \
  --user-arn arn:aws:iam::123456789012:user/jsmith \
  --permissions read-only
```

### Delete an environment
```bash
aws cloud9 delete-environment --environment-id abc123
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Environments | [`environments.md`](environments.md) | create-environment-ec2, delete-environment, describe-environments, list-environments, update-environment, describe-environment-status |
| Memberships | [`memberships.md`](memberships.md) | create-environment-membership, delete-environment-membership, describe-environment-memberships, update-environment-membership |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
