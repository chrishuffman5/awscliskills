# AWS CLI v2 — Security Lake

## Overview

Complete reference for all `aws securitylake` subcommands in AWS CLI v2. Amazon Security Lake automatically centralizes security data from AWS environments, SaaS providers, on-premises sources, and cloud sources into a purpose-built data lake stored in your account. Security Lake uses the Open Cybersecurity Schema Framework (OCSF) to normalize and combine security data, making it easier to analyze, investigate, and respond to security events.

## Quick Reference — Common Workflows

### Create a data lake in a region
```bash
aws securitylake create-data-lake \
  --configurations '[{"region":"us-east-1","encryptionConfiguration":{"kmsKeyId":"S3_MANAGED_KEY"},"lifecycleConfiguration":{"expiration":{"days":365}}}]' \
  --meta-store-manager-role-arn arn:aws:iam::123456789012:role/AmazonSecurityLakeMetaStoreManager
```

### Enable AWS log sources
```bash
aws securitylake create-aws-log-source \
  --sources '[{"regions":["us-east-1"],"sourceName":"VPC_FLOW","sourceVersion":"2.0"}]'
```

### Create a custom log source
```bash
aws securitylake create-custom-log-source \
  --source-name my-custom-source \
  --source-version "1.0" \
  --configuration '{"crawlerConfiguration":{"roleArn":"arn:aws:iam::123456789012:role/CrawlerRole"},"providerIdentity":{"externalId":"ext123","principal":"123456789012"}}' \
  --event-classes '["FILE_ACTIVITY","NETWORK_ACTIVITY"]'
```

### Create a subscriber with S3 access
```bash
aws securitylake create-subscriber \
  --access-types "S3" \
  --sources '[{"awsLogSource":{"sourceName":"VPC_FLOW","sourceVersion":"2.0"}}]' \
  --subscriber-name my-subscriber \
  --subscriber-identity '{"principal":"123456789012","externalId":"ext123"}'
```

### List data lakes across regions
```bash
aws securitylake list-data-lakes --regions us-east-1 us-west-2
```

### Set up subscriber notification
```bash
aws securitylake create-subscriber-notification \
  --subscriber-id 1234abcd-12ab-34cd-56ef-1234567890ab \
  --configuration '{"httpsNotificationConfiguration":{"endpoint":"https://example.com/notify","targetRoleArn":"arn:aws:iam::123456789012:role/NotifyRole"}}'
```

### Register delegated administrator for organization
```bash
aws securitylake register-data-lake-delegated-administrator \
  --account-id 123456789012
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Data Lake | [`data-lake.md`](data-lake.md) | create-data-lake, delete-data-lake, update-data-lake, list-data-lakes, create-data-lake-exception-subscription, delete-data-lake-exception-subscription, get-data-lake-exception-subscription, update-data-lake-exception-subscription, list-data-lake-exceptions, get-data-lake-sources, create-data-lake-organization-configuration, delete-data-lake-organization-configuration, get-data-lake-organization-configuration, register-data-lake-delegated-administrator, deregister-data-lake-delegated-administrator |
| Log Sources | [`log-sources.md`](log-sources.md) | create-aws-log-source, delete-aws-log-source, create-custom-log-source, delete-custom-log-source, list-log-sources |
| Subscribers | [`subscribers.md`](subscribers.md) | create-subscriber, delete-subscriber, get-subscriber, update-subscriber, list-subscribers, create-subscriber-notification, delete-subscriber-notification, update-subscriber-notification |
| Organization & Tags | [`organization-tags.md`](organization-tags.md) | tag-resource, untag-resource, list-tags-for-resource |
