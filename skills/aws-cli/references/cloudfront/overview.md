
# AWS CLI v2 — CloudFront (Content Delivery Network)

## Overview

Complete reference for all `aws cloudfront` subcommands in AWS CLI v2. Covers distribution management, origin configuration (S3, ALB, custom), cache behavior settings, invalidations, CloudFront Functions, Lambda@Edge associations, origin access control (OAC), signed URLs/cookies, continuous deployment (staging distributions), and real-time logs.

## Quick Reference — Common Workflows

### Create a distribution with S3 origin
```bash
aws cloudfront create-distribution --distribution-config file://dist-config.json
```

### Create an invalidation
```bash
aws cloudfront create-invalidation --distribution-id E1234 \
  --paths '/*'
aws cloudfront wait invalidation-completed --distribution-id E1234 --id I1234
```

### List distributions
```bash
aws cloudfront list-distributions \
  --query 'DistributionList.Items[].{Id:Id,Domain:DomainName,Status:Status}'
```

### Get distribution config (for updates)
```bash
aws cloudfront get-distribution-config --id E1234
# Edit the config, then update:
aws cloudfront update-distribution --id E1234 --distribution-config file://updated.json --if-match <ETag>
```

### Create a CloudFront Function
```bash
aws cloudfront create-function --name my-func --function-config '{
  "Comment":"URL rewrite","Runtime":"cloudfront-js-2.0"
}' --function-code fileb://function.js
aws cloudfront publish-function --name my-func --if-match <ETag>
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Distributions | create, delete, get, list, update, get-config | Distribution lifecycle |
| Invalidations | create, get, list | Cache purging |
| Functions | create, delete, describe, get, list, publish, test, update | Edge compute |
| Cache Policies | create, delete, get, list, update | Caching configuration |
| Origin Request Policies | create, delete, get, list, update | Origin forwarding |
| Response Headers Policies | create, delete, get, list, update | Security headers |
| Origin Access Control | create, delete, get, list, update | S3 OAC |
| Continuous Deployment | create, delete, get, list, update | Staging distributions |
| Key Groups & Public Keys | create, delete, get, list, update | Signed URL keys |
| Real-Time Logs | create, delete, get, list, update | Streaming logs |
| Tags | tag-resource, untag-resource, list-tags-for-resource | Resource tagging |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Distributions | [`distributions.md`](distributions.md) | create-distribution, create-distribution-with-tags, get-distribution, get-distribution-config, list-distributions, update-distribution, delete-distribution, list-distributions-by-web-acl-id, list-distributions-by-cache-policy-id, list-distributions-by-origin-request-policy-id, list-distributions-by-response-headers-policy-id, list-distributions-by-key-group, list-distributions-by-realtime-log-config, list-conflicting-aliases |
| Invalidations | [`invalidations.md`](invalidations.md) | create-invalidation, get-invalidation, list-invalidations |
| Functions | [`functions.md`](functions.md) | create-function, delete-function, describe-function, get-function, list-functions, publish-function, test-function, update-function |
| Cache Policies | [`cache-policies.md`](cache-policies.md) | create-cache-policy, get-cache-policy, get-cache-policy-config, list-cache-policies, update-cache-policy, delete-cache-policy |
| Origin Request Policies | [`origin-request-policies.md`](origin-request-policies.md) | create-origin-request-policy, get-origin-request-policy, get-origin-request-policy-config, list-origin-request-policies, update-origin-request-policy, delete-origin-request-policy |
| Response Headers Policies | [`response-headers-policies.md`](response-headers-policies.md) | create-response-headers-policy, get-response-headers-policy, get-response-headers-policy-config, list-response-headers-policies, update-response-headers-policy, delete-response-headers-policy |
| Origin Access Control | [`origin-access-control.md`](origin-access-control.md) | create-origin-access-control, get-origin-access-control, get-origin-access-control-config, list-origin-access-controls, update-origin-access-control, delete-origin-access-control |
| Origin Access Identity (Legacy) | [`origin-access-identity.md`](origin-access-identity.md) | create-cloud-front-origin-access-identity, get-cloud-front-origin-access-identity, get-cloud-front-origin-access-identity-config, list-cloud-front-origin-access-identities, update-cloud-front-origin-access-identity, delete-cloud-front-origin-access-identity |
| Continuous Deployment | [`continuous-deployment.md`](continuous-deployment.md) | create-continuous-deployment-policy, get-continuous-deployment-policy, get-continuous-deployment-policy-config, list-continuous-deployment-policies, update-continuous-deployment-policy, delete-continuous-deployment-policy, update-distribution-with-staging-config |
| Key Groups | [`key-groups.md`](key-groups.md) | create-key-group, get-key-group, get-key-group-config, list-key-groups, update-key-group, delete-key-group |
| Public Keys | [`public-keys.md`](public-keys.md) | create-public-key, get-public-key, get-public-key-config, list-public-keys, update-public-key, delete-public-key |
| Real-Time Logs | [`real-time-logs.md`](real-time-logs.md) | create-realtime-log-config, get-realtime-log-config, list-realtime-log-configs, update-realtime-log-config, delete-realtime-log-config |
| Key Value Stores | [`key-value-stores.md`](key-value-stores.md) | create-key-value-store, describe-key-value-store, list-key-value-stores, update-key-value-store, delete-key-value-store |
| Monitoring Subscriptions | [`monitoring-subscriptions.md`](monitoring-subscriptions.md) | create-monitoring-subscription, get-monitoring-subscription, delete-monitoring-subscription |
| Field-Level Encryption | [`field-level-encryption.md`](field-level-encryption.md) | create-field-level-encryption-config, create-field-level-encryption-profile, get-field-level-encryption, get-field-level-encryption-config, get-field-level-encryption-profile, get-field-level-encryption-profile-config, list-field-level-encryption-configs, list-field-level-encryption-profiles, update-field-level-encryption-config, update-field-level-encryption-profile, delete-field-level-encryption-config, delete-field-level-encryption-profile |
| Streaming Distributions (Legacy) | [`streaming-distributions.md`](streaming-distributions.md) | create-streaming-distribution, get-streaming-distribution, get-streaming-distribution-config, list-streaming-distributions, update-streaming-distribution, delete-streaming-distribution |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| Wait Commands | [`wait-commands.md`](wait-commands.md) | wait distribution-deployed, wait invalidation-completed, wait streaming-distribution-deployed |
