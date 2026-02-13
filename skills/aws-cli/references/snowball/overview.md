# AWS CLI v2 — Snow Family (Snowball)

## Overview

Complete reference for all `aws snowball` subcommands in AWS CLI v2. Covers Snow Family job and cluster management, shipping addresses, device manifests and unlock codes, long-term pricing, compatible images, pickup locations, and service versions. The Snow Family includes Snowcone, Snowball Edge, and Snowball devices for offline data transfer and edge computing.

## Quick Reference — Common Workflows

### Create a shipping address
```bash
aws snowball create-address \
  --address Name="John Doe",Company="Acme Corp",Street1="123 Main St",City="Seattle",StateOrProvince="WA",Country="US",PostalCode="98101",PhoneNumber="206-555-0100"
```

### Create an import job
```bash
aws snowball create-job \
  --job-type IMPORT \
  --snowball-type EDGE \
  --address-id ADID12345678-1234-1234-1234-123456789012 \
  --resources 'S3Resources=[{BucketArn=arn:aws:s3:::my-bucket}]' \
  --role-arn arn:aws:iam::123456789012:role/SnowballRole \
  --kms-key-arn arn:aws:kms:us-east-1:123456789012:key/key-id \
  --shipping-option SECOND_DAY
```

### Describe a job and check status
```bash
aws snowball describe-job --job-id JID12345678-1234-1234-1234-123456789012
aws snowball describe-job --job-id JID12345678-1234-1234-1234-123456789012 \
  --query 'JobMetadata.JobState' --output text
```

### Get manifest and unlock code for a device
```bash
aws snowball get-job-manifest --job-id JID12345678-1234-1234-1234-123456789012
aws snowball get-job-unlock-code --job-id JID12345678-1234-1234-1234-123456789012
```

### Create a cluster of Snow devices
```bash
aws snowball create-cluster \
  --job-type LOCAL_USE \
  --snowball-type EDGE \
  --address-id ADID12345678-1234-1234-1234-123456789012 \
  --shipping-option SECOND_DAY \
  --on-device-service-configuration 'S3OnDeviceService={StorageLimit=10,StorageUnit=TB}'
```

### Create a return shipping label
```bash
aws snowball create-return-shipping-label \
  --job-id JID12345678-1234-1234-1234-123456789012 \
  --shipping-option NEXT_DAY
```

### Set up long-term pricing
```bash
aws snowball create-long-term-pricing \
  --long-term-pricing-type OneYear \
  --snowball-type EDGE \
  --is-long-term-pricing-auto-renew
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Jobs | [`jobs.md`](jobs.md) | create-job, describe-job, update-job, cancel-job, list-jobs, get-job-manifest, get-job-unlock-code, get-software-updates, update-job-shipment-state |
| Clusters | [`clusters.md`](clusters.md) | create-cluster, describe-cluster, update-cluster, cancel-cluster, list-clusters, list-cluster-jobs |
| Addresses | [`addresses.md`](addresses.md) | create-address, describe-address, describe-addresses, list-pickup-locations |
| Pricing & Shipping | [`pricing-shipping.md`](pricing-shipping.md) | create-long-term-pricing, update-long-term-pricing, list-long-term-pricing, create-return-shipping-label, describe-return-shipping-label |
| Compatibility | [`compatibility.md`](compatibility.md) | get-snowball-usage, list-compatible-images, list-service-versions |
