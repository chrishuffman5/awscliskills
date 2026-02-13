# AWS CLI v2 — S3 Outposts

## Overview

Complete reference for all `aws s3outposts` subcommands in AWS CLI v2. Amazon S3 on Outposts delivers object storage to your on-premises AWS Outposts environment. This service manages S3 endpoint lifecycle for Outposts, allowing you to create, list, and delete endpoints that connect your Outpost to S3 storage.

## Quick Reference — Common Workflows

### Create an endpoint for an Outpost
```bash
aws s3outposts create-endpoint \
  --outpost-id op-0ab1c2d3e4f567890 \
  --subnet-id subnet-0123456789abcdef0 \
  --security-group-id sg-0123456789abcdef0
```

### Create an endpoint with customer-owned IP
```bash
aws s3outposts create-endpoint \
  --outpost-id op-0ab1c2d3e4f567890 \
  --subnet-id subnet-0123456789abcdef0 \
  --security-group-id sg-0123456789abcdef0 \
  --access-type CustomerOwnedIp \
  --customer-owned-ipv4-pool ipv4pool-coip-01234567890abcdef
```

### List all endpoints
```bash
aws s3outposts list-endpoints \
  --query 'Endpoints[*].[EndpointArn,OutpostsId,Status]' \
  --output table
```

### List Outposts with S3 provisioned
```bash
aws s3outposts list-outposts-with-s3 \
  --query 'Outposts[*].[OutpostId,CapacityInBytes]' \
  --output table
```

### List shared endpoints for an Outpost
```bash
aws s3outposts list-shared-endpoints \
  --outpost-id op-0ab1c2d3e4f567890
```

### Delete an endpoint
```bash
aws s3outposts delete-endpoint \
  --endpoint-id abcdef0123456789012 \
  --outpost-id op-0ab1c2d3e4f567890
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Endpoints | [`endpoints.md`](endpoints.md) | create-endpoint, delete-endpoint, list-endpoints, list-outposts-with-s3, list-shared-endpoints |
