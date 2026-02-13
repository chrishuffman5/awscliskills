# AWS CLI v2 — Pricing

## Overview

Complete reference for all `aws pricing` subcommands in AWS CLI v2. Covers querying AWS service pricing data, discovering available services and their attributes, retrieving product pricing details, and downloading bulk price list files.

## Quick Reference — Common Workflows

### List all available services
```bash
aws pricing describe-services --region us-east-1
```

### Get attributes for a service
```bash
aws pricing describe-services \
  --service-code AmazonEC2 \
  --format-version aws_v1 \
  --region us-east-1
```

### Get attribute values (e.g., available regions for EC2)
```bash
aws pricing get-attribute-values \
  --service-code AmazonEC2 \
  --attribute-name location \
  --region us-east-1
```

### Query product pricing with filters
```bash
aws pricing get-products \
  --service-code AmazonEC2 \
  --filters Type=TERM_MATCH,Field=instanceType,Value=m5.xlarge \
             Type=TERM_MATCH,Field=location,Value="US East (N. Virginia)" \
  --format-version aws_v1 \
  --region us-east-1
```

### List available price lists
```bash
aws pricing list-price-lists \
  --service-code AmazonEC2 \
  --effective-date 2025-01-01 \
  --currency-code USD \
  --region us-east-1
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Pricing | [`pricing.md`](pricing.md) | describe-services, get-attribute-values, get-products, list-price-lists, get-price-list-file-url |
