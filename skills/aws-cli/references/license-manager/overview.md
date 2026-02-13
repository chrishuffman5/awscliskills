# AWS CLI v2 — License Manager

## Overview

Complete reference for `aws license-manager`, `aws license-manager-linux-subscriptions`, and `aws license-manager-user-subscriptions` subcommands in AWS CLI v2. Covers license configurations, license creation and distribution via grants, license checkout and consumption, tokens, conversion tasks, report generators, license asset groups and rulesets, Linux subscription tracking, and user-based subscription management for Microsoft products on EC2.

## Quick Reference — Common Workflows

### Create a license configuration
```bash
aws license-manager create-license-configuration \
  --name my-license-config \
  --license-counting-type vCPU \
  --license-count 100 \
  --license-count-hard-limit
```

### Create a grant for a license
```bash
aws license-manager create-grant \
  --client-token "unique-token-123" \
  --grant-name "MyGrant" \
  --license-arn arn:aws:license-manager::123456789012:license/lic-abc123 \
  --principals arn:aws:iam::987654321098:root \
  --home-region us-east-1 \
  --allowed-operations CheckoutLicense CheckInLicense
```

### Check out a license
```bash
aws license-manager checkout-license \
  --product-sku my-product-sku \
  --checkout-type PROVISIONAL \
  --key-fingerprint abc123fingerprint \
  --entitlements Name=FeatureA,Unit=Count,Value=1 \
  --client-token "unique-token-456"
```

### Register a Linux subscription provider (RHEL)
```bash
aws license-manager-linux-subscriptions register-subscription-provider \
  --subscription-provider-source RedHat \
  --secret-arn arn:aws:secretsmanager:us-east-1:123456789012:secret:rhel-token
```

### Register an identity provider for user subscriptions
```bash
aws license-manager-user-subscriptions register-identity-provider \
  --identity-provider '{"ActiveDirectoryIdentityProvider":{"DirectoryId":"d-1234567890"}}' \
  --product VISUAL_STUDIO_ENTERPRISE
```

### Get service settings
```bash
aws license-manager get-service-settings
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| License Configurations | [`license-configurations.md`](license-configurations.md) | create-license-configuration, delete-license-configuration, get-license-configuration, list-license-configurations, update-license-configuration, list-license-configurations-for-organization, list-usage-for-license-configuration, list-associations-for-license-configuration, list-failures-for-license-configuration-operations, update-license-specifications-for-resource, list-license-specifications-for-resource, list-resource-inventory |
| Licenses | [`licenses.md`](licenses.md) | create-license, delete-license, get-license, list-licenses, create-license-version, list-license-versions, get-license-usage, check-in-license, checkout-license, checkout-borrow-license, extend-license-consumption, list-received-licenses, list-received-licenses-for-organization |
| Grants | [`grants.md`](grants.md) | create-grant, delete-grant, get-grant, create-grant-version, list-distributed-grants, list-received-grants, list-received-grants-for-organization, accept-grant, reject-grant |
| Tokens | [`tokens.md`](tokens.md) | create-token, delete-token, list-tokens, get-access-token |
| License Asset Groups | [`license-asset-groups.md`](license-asset-groups.md) | create-license-asset-group, delete-license-asset-group, get-license-asset-group, list-license-asset-groups, update-license-asset-group, list-assets-for-license-asset-group, create-license-asset-ruleset, delete-license-asset-ruleset, get-license-asset-ruleset, list-license-asset-rulesets, update-license-asset-ruleset |
| Conversion & Reports | [`conversion-reports.md`](conversion-reports.md) | create-license-conversion-task-for-resource, get-license-conversion-task, list-license-conversion-tasks, create-license-manager-report-generator, delete-license-manager-report-generator, get-license-manager-report-generator, list-license-manager-report-generators, update-license-manager-report-generator |
| Service Settings | [`service-settings.md`](service-settings.md) | get-service-settings, update-service-settings |
| Linux Subscriptions | [`linux-subscriptions.md`](linux-subscriptions.md) | list-linux-subscriptions, list-linux-subscription-instances, register-subscription-provider, deregister-subscription-provider, get-registered-subscription-provider, list-registered-subscription-providers, get-service-settings, update-service-settings |
| User Subscriptions | [`user-subscriptions.md`](user-subscriptions.md) | register-identity-provider, deregister-identity-provider, list-identity-providers, update-identity-provider-settings, associate-user, disassociate-user, list-user-associations, list-instances, list-product-subscriptions, start-product-subscription, stop-product-subscription, create-license-server-endpoint, delete-license-server-endpoint, list-license-server-endpoints |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource (all three namespaces) |
