# AWS CLI v2 — Billing

## Overview

Complete reference for all `aws billing` subcommands in AWS CLI v2. Covers billing views for creating custom views of billing data, associating and managing source views, resource policies, and tagging. Billing views represent sets of billing data that can be filtered by linked accounts, tags, and cost categories.

## Quick Reference — Common Workflows

### List all billing views
```bash
aws billing list-billing-views \
  --region us-east-1
```

### Create a custom billing view
```bash
aws billing create-billing-view \
  --name "Engineering-View" \
  --description "Billing view for engineering accounts" \
  --source-views "arn:aws:billing::123456789012:billingview/primary" \
  --data-filter-expression '{"dimensions":{"key":"LINKED_ACCOUNT","values":["111111111111","222222222222"]}}' \
  --region us-east-1
```

### Get billing view details
```bash
aws billing get-billing-view \
  --arn arn:aws:billing::123456789012:billingview/Engineering-View \
  --region us-east-1
```

### Update a billing view
```bash
aws billing update-billing-view \
  --arn arn:aws:billing::123456789012:billingview/Engineering-View \
  --description "Updated engineering billing view" \
  --region us-east-1
```

### Associate source views
```bash
aws billing associate-source-views \
  --arn arn:aws:billing::123456789012:billingview/Aggregate-View \
  --source-views "arn:aws:billing::123456789012:billingview/source-1" \
  --region us-east-1
```

### Get resource policy
```bash
aws billing get-resource-policy \
  --resource-arn arn:aws:billing::123456789012:billingview/my-view \
  --region us-east-1
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Billing Views | [`billing-views.md`](billing-views.md) | create-billing-view, delete-billing-view, get-billing-view, list-billing-views, update-billing-view, associate-source-views, disassociate-source-views, list-source-views-for-billing-view, get-resource-policy |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
