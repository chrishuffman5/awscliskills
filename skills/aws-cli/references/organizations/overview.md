# AWS CLI v2 — Organizations

## Overview

Complete reference for all `aws organizations` subcommands in AWS CLI v2. Covers organization management, account creation and management, organizational units (OUs), policies (service control policies, tag policies, backup policies, AI services opt-out policies), handshakes, delegated administrators, and service access management.

## Quick Reference — Common Workflows

### Create an organization

```bash
aws organizations create-organization --feature-set ALL
```

### Create an organizational unit

```bash
aws organizations create-organizational-unit \
  --parent-id r-abc1 \
  --name Production
```

### Create a member account

```bash
aws organizations create-account \
  --email new-account@example.com \
  --account-name "New Account" \
  --role-name OrganizationAccountAccessRole
```

### Move an account to an OU

```bash
aws organizations move-account \
  --account-id 123456789012 \
  --source-parent-id r-abc1 \
  --destination-parent-id ou-abc1-def23456
```

### Create and attach a service control policy

```bash
aws organizations create-policy \
  --name DenyS3Delete \
  --type SERVICE_CONTROL_POLICY \
  --content file://deny-s3-delete.json \
  --description "Deny S3 object deletion"

aws organizations attach-policy \
  --policy-id p-abc12345 \
  --target-id ou-abc1-def23456
```

### List all accounts

```bash
aws organizations list-accounts \
  --query 'Accounts[].{Id:Id,Name:Name,Email:Email,Status:Status}' \
  --output table
```

### Enable a service for organization integration

```bash
aws organizations enable-aws-service-access \
  --service-principal config.amazonaws.com
```

### Register a delegated administrator

```bash
aws organizations register-delegated-administrator \
  --account-id 123456789012 \
  --service-principal config.amazonaws.com
```

### Invite an existing account

```bash
aws organizations invite-account-to-organization \
  --target Id=123456789012,Type=ACCOUNT \
  --notes "Please join our organization"
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Organization | [`organization.md`](organization.md) | create-organization, delete-organization, describe-organization, enable-all-features, leave-organization, list-roots |
| Accounts | [`accounts.md`](accounts.md) | create-account, create-gov-cloud-account, close-account, describe-account, describe-create-account-status, list-accounts, list-accounts-for-parent, list-create-account-status, move-account, remove-account-from-organization, invite-account-to-organization |
| Organizational Units | [`organizational-units.md`](organizational-units.md) | create-organizational-unit, delete-organizational-unit, describe-organizational-unit, list-organizational-units-for-parent, list-children, list-parents, update-organizational-unit |
| Policies | [`policies.md`](policies.md) | create-policy, delete-policy, describe-policy, update-policy, list-policies, list-policies-for-target, list-targets-for-policy, attach-policy, detach-policy, describe-effective-policy, enable-policy-type, disable-policy-type |
| Handshakes | [`handshakes.md`](handshakes.md) | accept-handshake, cancel-handshake, decline-handshake, describe-handshake, list-handshakes-for-account, list-handshakes-for-organization |
| Delegated Admin | [`delegated-admin.md`](delegated-admin.md) | register-delegated-administrator, deregister-delegated-administrator, list-delegated-administrators, list-delegated-services-for-account |
| Service Access | [`service-access.md`](service-access.md) | enable-aws-service-access, disable-aws-service-access, list-aws-service-access-for-organization |
| Resource Policy | [`responsibility-transfer.md`](responsibility-transfer.md) | put-resource-policy, delete-resource-policy, describe-resource-policy |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
