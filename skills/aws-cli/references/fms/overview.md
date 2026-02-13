# AWS CLI v2 — Firewall Manager (FMS)

## Overview

Complete reference for all `aws fms` subcommands in AWS CLI v2. Covers administrator account management, security policy creation and enforcement, apps and protocols lists, resource sets, third-party firewall integration, notification channels, and tagging.

## Quick Reference — Common Workflows

### Set up Firewall Manager administrator
```bash
aws fms associate-admin-account --admin-account 123456789012
```

### Create a WAFv2 security policy
```bash
aws fms put-policy --cli-input-json file://wafv2-policy.json
```

### List all policies
```bash
aws fms list-policies
```

### Get policy details
```bash
aws fms get-policy --policy-id a1b2c3d4-5678-90ab-cdef-EXAMPLE11111
```

### Check compliance for a member account
```bash
aws fms get-compliance-detail \
  --policy-id a1b2c3d4-5678-90ab-cdef-EXAMPLE11111 \
  --member-account 123456789012
```

### Create a resource set
```bash
aws fms put-resource-set \
  --resource-set 'Name=my-resource-set,ResourceTypeList=AWS::EC2::Instance'
```

### Set up notification channel
```bash
aws fms put-notification-channel \
  --sns-topic-arn arn:aws:sns:us-east-1:123456789012:fms-notifications \
  --sns-role-name arn:aws:iam::123456789012:role/FMSNotificationRole
```

### Create an apps list
```bash
aws fms put-apps-list --apps-list 'ListName=my-apps,AppsList=[{AppName=web,Protocol=TCP,Port=443}]'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Admin | [`admin.md`](admin.md) | associate-admin-account, disassociate-admin-account, get-admin-account, get-admin-scope, put-admin-account, list-admin-accounts-for-organization, list-admins-managing-account |
| Policies | [`policies.md`](policies.md) | put-policy, get-policy, delete-policy, list-policies, get-compliance-detail, list-compliance-status, get-violation-details, get-protection-status, list-member-accounts, list-discovered-resources |
| Apps & Protocols | [`apps-protocols.md`](apps-protocols.md) | put-apps-list, get-apps-list, delete-apps-list, list-apps-lists, put-protocols-list, get-protocols-list, delete-protocols-list, list-protocols-lists |
| Resource Sets | [`resource-sets.md`](resource-sets.md) | put-resource-set, get-resource-set, delete-resource-set, list-resource-sets, list-resource-set-resources, batch-associate-resource, batch-disassociate-resource |
| Third-Party Firewalls | [`third-party.md`](third-party.md) | associate-third-party-firewall, disassociate-third-party-firewall, get-third-party-firewall-association-status, list-third-party-firewall-firewall-policies |
| Notifications & Tags | [`notifications-tags.md`](notifications-tags.md) | put-notification-channel, get-notification-channel, delete-notification-channel, tag-resource, untag-resource, list-tags-for-resource |
