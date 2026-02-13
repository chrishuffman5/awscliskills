# AWS CLI v2 — Marketplace Catalog

## Overview

Complete reference for all `aws marketplace-catalog` subcommands in AWS CLI v2. Covers entity management (products, offers, resale authorizations), change set operations for modifying entities, resource-based policies, and tagging. The Marketplace Catalog API enables programmatic management of AWS Marketplace listings.

## Quick Reference — Common Workflows

### List all SaaS products
```bash
aws marketplace-catalog list-entities \
  --catalog AWSMarketplace \
  --entity-type SaaSProduct
```

### Describe an entity
```bash
aws marketplace-catalog describe-entity \
  --catalog AWSMarketplace \
  --entity-id prod-1234567890abc
```

### Start a change set to update a product
```bash
aws marketplace-catalog start-change-set \
  --catalog AWSMarketplace \
  --change-set-name "UpdateProductDescription" \
  --change-set '[{"ChangeType":"UpdateInformation","Entity":{"Type":"AmiProduct@1.0","Identifier":"prod-1234567890abc"},"DetailsDocument":{"ProductTitle":"My Updated Product"}}]'
```

### Check change set status
```bash
aws marketplace-catalog describe-change-set \
  --catalog AWSMarketplace \
  --change-set-id cs-1234567890abc
```

### Cancel a pending change set
```bash
aws marketplace-catalog cancel-change-set \
  --catalog AWSMarketplace \
  --change-set-id cs-1234567890abc
```

### Set a resource policy on an entity
```bash
aws marketplace-catalog put-resource-policy \
  --resource-arn arn:aws:aws-marketplace:us-east-1:123456789012:AWSMarketplace/Entity/prod-abc \
  --policy '{"Version":"2012-10-17","Statement":[{"Effect":"Allow","Principal":{"AWS":"arn:aws:iam::987654321098:root"},"Action":"aws-marketplace:DescribeEntity","Resource":"*"}]}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Entities | [`entities.md`](entities.md) | describe-entity, list-entities, batch-describe-entities |
| Change Sets | [`change-sets.md`](change-sets.md) | start-change-set, cancel-change-set, describe-change-set, list-change-sets |
| Resource Policies | [`resource-policies.md`](resource-policies.md) | get-resource-policy, put-resource-policy, delete-resource-policy |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
