# AWS CLI v2 — Resource Groups

## Overview

Complete reference for all `aws resource-groups` subcommands in AWS CLI v2. Covers resource group creation and management, tag-based and CloudFormation stack-based resource queries, group configuration, tag sync tasks, and account-level settings. AWS Resource Groups lets you organize AWS resources into logical groups for bulk management, monitoring, and automation.

## Quick Reference — Common Workflows

### Create a tag-based resource group
```bash
aws resource-groups create-group --name my-prod-group \
  --resource-query '{"Type":"TAG_FILTERS_1_0","Query":"{\"ResourceTypeFilters\":[\"AWS::AllSupported\"],\"TagFilters\":[{\"Key\":\"Environment\",\"Values\":[\"Production\"]}]}"}'
```

### Create a CloudFormation stack-based group
```bash
aws resource-groups create-group --name my-stack-group \
  --resource-query '{"Type":"CLOUDFORMATION_STACK_1_0","Query":"{\"ResourceTypeFilters\":[\"AWS::AllSupported\"],\"StackIdentifier\":\"arn:aws:cloudformation:us-east-1:123456789012:stack/my-stack/guid\"}"}'
```

### List all resource groups
```bash
aws resource-groups list-groups \
  --query 'GroupIdentifiers[].{Name:GroupName,Arn:GroupArn}'
```

### Get group details
```bash
aws resource-groups get-group --group-name my-prod-group
```

### List resources in a group
```bash
aws resource-groups list-group-resources --group my-prod-group \
  --query 'Resources[].{Arn:Identifier.ResourceArn,Type:Identifier.ResourceType}'
```

### Search for resources matching a query
```bash
aws resource-groups search-resources \
  --resource-query '{"Type":"TAG_FILTERS_1_0","Query":"{\"ResourceTypeFilters\":[\"AWS::EC2::Instance\"],\"TagFilters\":[{\"Key\":\"Environment\",\"Values\":[\"Production\"]}]}"}'
```

### Update a group's resource query
```bash
aws resource-groups update-group-query --group-name my-prod-group \
  --resource-query '{"Type":"TAG_FILTERS_1_0","Query":"{\"ResourceTypeFilters\":[\"AWS::EC2::Instance\"],\"TagFilters\":[{\"Key\":\"Environment\",\"Values\":[\"Production\",\"Staging\"]}]}"}'
```

### Get account settings
```bash
aws resource-groups get-account-settings
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Groups | [`groups.md`](groups.md) | create-group, get-group, list-groups, update-group, delete-group, list-group-resources |
| Queries & Configuration | [`queries-configuration.md`](queries-configuration.md) | get-group-query, update-group-query, search-resources, get-group-configuration, put-group-configuration, group-resources, ungroup-resources, list-grouping-statuses |
| Tag Sync | [`tag-sync.md`](tag-sync.md) | start-tag-sync-task, get-tag-sync-task, list-tag-sync-tasks, cancel-tag-sync-task |
| Tags & Settings | [`tags-settings.md`](tags-settings.md) | tag, untag, get-tags, get-account-settings, update-account-settings |
