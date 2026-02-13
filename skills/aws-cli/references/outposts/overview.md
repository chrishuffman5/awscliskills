# AWS CLI v2 — Outposts

## Overview

Complete reference for all `aws outposts` subcommands in AWS CLI v2. Covers Outpost management, site configuration, order tracking, catalog item lookups, capacity task management, asset inventory, connection details, and billing information. AWS Outposts extends AWS infrastructure, services, APIs, and tools to customer premises for a consistent hybrid experience.

## Quick Reference — Common Workflows

### Create an Outpost
```bash
aws outposts create-outpost \
  --name my-outpost \
  --site-id os-1234567890abcdef0 \
  --availability-zone us-east-1a \
  --tags Key=Environment,Value=Production
```

### List all Outposts
```bash
aws outposts list-outposts --query 'Outposts[].{Name:Name,Id:OutpostId,Status:LifeCycleStatus}'
```

### Get Outpost details
```bash
aws outposts get-outpost --outpost-id op-1234567890abcdef0
```

### Create a site
```bash
aws outposts create-site --name my-site \
  --operating-address AddressLine1="123 Main St",City="Seattle",StateOrRegion="WA",PostalCode="98101",CountryCode="US"
```

### List catalog items
```bash
aws outposts list-catalog-items --query 'CatalogItems[].{ItemId:CatalogItemId,PowerKva:PowerKva}'
```

### Create an order
```bash
aws outposts create-order --outpost-identifier op-1234567890abcdef0 \
  --line-items CatalogItemId=oci-1234567890abcdef0,Quantity=1 \
  --payment-option ALL_UPFRONT \
  --payment-term THREE_YEARS
```

### Start a capacity task
```bash
aws outposts start-capacity-task --outpost-identifier op-1234567890abcdef0 \
  --instance-pools InstanceType=m5.xlarge,Count=4
```

### List assets on an Outpost
```bash
aws outposts list-assets --outpost-identifier op-1234567890abcdef0 \
  --query 'Assets[].{Id:AssetId,Type:AssetType,Status:ComputeAttributes.HostId}'
```

### Get connection information
```bash
aws outposts get-connection --connection-id conn-1234567890abcdef0
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Outposts | [`outposts.md`](outposts.md) | create-outpost, get-outpost, list-outposts, update-outpost, delete-outpost, get-outpost-instance-types, get-outpost-supported-instance-types |
| Sites | [`sites.md`](sites.md) | create-site, get-site, list-sites, update-site, delete-site, get-site-address, update-site-address, update-site-rack-physical-properties |
| Orders | [`orders.md`](orders.md) | create-order, get-order, list-orders |
| Capacity | [`capacity.md`](capacity.md) | start-capacity-task, get-capacity-task, list-capacity-tasks, cancel-capacity-task |
| Assets | [`assets.md`](assets.md) | list-assets, get-outpost-instance-types |
| Connections & Tags | [`connections-tags.md`](connections-tags.md) | start-connection, get-connection, list-catalog-items, list-tags-for-resource, tag-resource, untag-resource |
