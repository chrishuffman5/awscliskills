# AWS Resource Explorer CLI Reference

## Overview

AWS Resource Explorer enables cross-region resource search across your AWS account or organization. It maintains indexes of resources in each enabled Region and supports aggregator indexes that replicate data from all Regions into a single searchable view. Use views to scope and filter search results, and managed views for AWS service integrations.

## Quick Reference

### Enable Resource Explorer across regions
```bash
aws resource-explorer-2 create-resource-explorer-setup \
    --region-list us-east-1 us-west-2 eu-west-1 \
    --aggregator-regions us-east-1 \
    --view-name default-view
```

### Create a local index and promote to aggregator
```bash
# Create local index
aws resource-explorer-2 create-index --region us-east-1

# Promote to aggregator
aws resource-explorer-2 update-index-type \
    --arn arn:aws:resource-explorer-2:us-east-1:123456789012:index/EXAMPLE \
    --type AGGREGATOR
```

### Create a filtered view
```bash
aws resource-explorer-2 create-view \
    --view-name EC2-Only \
    --included-properties Name=tags \
    --filters FilterString="service:ec2"
```

### Set default view and search
```bash
aws resource-explorer-2 associate-default-view \
    --view-arn arn:aws:resource-explorer-2:us-east-1:123456789012:view/EC2-Only/EXAMPLE

aws resource-explorer-2 search \
    --query-string "tag:Environment=Production"
```

### Search for specific resource types
```bash
aws resource-explorer-2 search \
    --query-string "resourcetype:ec2:instance region:us-east-1"
```

### List all resources with filters
```bash
aws resource-explorer-2 list-resources \
    --filters FilterString="service:s3"
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Indexes | [indexes.md](indexes.md) | create-index, delete-index, get-index, list-indexes, update-index-type, list-indexes-for-members, get-service-index, list-service-indexes |
| Views | [views.md](views.md) | create-view, delete-view, get-view, list-views, update-view, batch-get-view, get-managed-view, list-managed-views, get-service-view, list-service-views, associate-default-view, disassociate-default-view, get-default-view |
| Search | [search.md](search.md) | search, list-resources, list-supported-resource-types |
| Setup | [setup.md](setup.md) | create-resource-explorer-setup, delete-resource-explorer-setup, get-resource-explorer-setup, get-account-level-service-configuration, list-streaming-access-for-services |
| Tags | [tags.md](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
