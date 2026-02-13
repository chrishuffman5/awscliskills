
# AWS CLI v2 — SNS (Simple Notification Service)

## Overview

Complete reference for all `aws sns` subcommands in AWS CLI v2. Covers topic management, subscription configuration (email, SQS, Lambda, HTTP, SMS), message publishing, message filtering, FIFO topics, platform applications for mobile push, and SMS messaging.

## Quick Reference — Common Workflows

### Create topic and subscribe
```bash
aws sns create-topic --name my-topic
aws sns subscribe --topic-arn arn:aws:sns:us-east-1:123456789012:my-topic \
  --protocol email --notification-endpoint user@example.com
```

### Publish a message
```bash
aws sns publish --topic-arn arn:aws:sns:us-east-1:123456789012:my-topic \
  --subject "Alert" --message "Something happened"
```

### Subscribe SQS queue to SNS topic
```bash
aws sns subscribe --topic-arn arn:aws:sns:us-east-1:123456789012:my-topic \
  --protocol sqs --notification-endpoint arn:aws:sqs:us-east-1:123456789012:my-queue
```

### Subscribe Lambda function
```bash
aws sns subscribe --topic-arn arn:aws:sns:us-east-1:123456789012:my-topic \
  --protocol lambda --notification-endpoint arn:aws:lambda:us-east-1:123456789012:function:my-func
```

### Set subscription filter policy
```bash
aws sns set-subscription-attributes --subscription-arn arn:aws:sns:... \
  --attribute-name FilterPolicy --attribute-value '{"event_type":["order_placed"]}'
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Topics | create, delete, list, get/set-attributes | Topic lifecycle |
| Subscriptions | subscribe, unsubscribe, confirm, list, get/set-attributes | Endpoint management |
| Publishing | publish, publish-batch | Message delivery |
| Platform Applications | create, delete, get/set/list platform-application, create/delete/get/set/list platform-endpoint | Mobile push |
| SMS | set/get/check-if-phone-number-is-opted-out, list-phone-numbers-opted-out, create/delete/list/get origination-identity | SMS messaging |
| Tags | tag-resource, untag-resource, list-tags-for-resource | Resource tagging |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Topics | [`topics.md`](topics.md) | create-topic, delete-topic, list-topics, get-topic-attributes, set-topic-attributes |
| Subscriptions | [`subscriptions.md`](subscriptions.md) | subscribe, unsubscribe, confirm-subscription, list-subscriptions, list-subscriptions-by-topic, get-subscription-attributes, set-subscription-attributes |
| Publishing | [`publishing.md`](publishing.md) | publish, publish-batch |
| Permissions | [`permissions.md`](permissions.md) | add-permission, remove-permission |
| Platform Applications | [`platform-applications.md`](platform-applications.md) | create-platform-application, delete-platform-application, get-platform-application-attributes, set-platform-application-attributes, list-platform-applications |
| Platform Endpoints | [`platform-endpoints.md`](platform-endpoints.md) | create-platform-endpoint, delete-endpoint, get-endpoint-attributes, set-endpoint-attributes, list-endpoints-by-platform-application |
| SMS | [`sms.md`](sms.md) | get-sms-attributes, set-sms-attributes, check-if-phone-number-is-opted-out, list-phone-numbers-opted-out, opt-in-phone-number |
| SMS Sandbox | [`sms-sandbox.md`](sms-sandbox.md) | get-sms-sandbox-account-status, create-sms-sandbox-phone-number, verify-sms-sandbox-phone-number, delete-sms-sandbox-phone-number, list-sms-sandbox-phone-numbers |
| Origination Numbers | [`origination-numbers.md`](origination-numbers.md) | list-origination-numbers |
| Data Protection | [`data-protection.md`](data-protection.md) | put-data-protection-policy, get-data-protection-policy |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
