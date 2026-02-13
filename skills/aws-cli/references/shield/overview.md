# AWS CLI v2 — Shield (AWS Shield Advanced)

## Overview

Complete reference for all `aws shield` subcommands in AWS CLI v2. Covers Shield Advanced subscription management, resource protection, attack detection and description, DDoS Response Team (DRT) access configuration, proactive engagement, application-layer automatic response, and tagging.

## Quick Reference — Common Workflows

### Subscribe to Shield Advanced
```bash
aws shield create-subscription
```

### Protect a resource
```bash
aws shield create-protection \
  --name "CloudFront-Protection" \
  --resource-arn arn:aws:cloudfront::123456789012:distribution/E198WC25FXOWY8
```

### List all protections
```bash
aws shield list-protections
```

### Create a protection group
```bash
aws shield create-protection-group \
  --protection-group-id my-group \
  --aggregation SUM \
  --pattern ALL
```

### Describe a detected attack
```bash
aws shield describe-attack --attack-id a1b2c3d4-5678-90ab-cdef-EXAMPLE11111
```

### List recent attacks
```bash
aws shield list-attacks \
  --start-time '{"FromInclusive":"2024-01-01T00:00:00Z"}' \
  --end-time '{"ToExclusive":"2024-02-01T00:00:00Z"}'
```

### Grant DRT access
```bash
aws shield associate-drt-role \
  --role-arn arn:aws:iam::123456789012:role/DrtRole
aws shield associate-drt-log-bucket \
  --log-bucket flow-logs-for-website-lb
```

### Enable proactive engagement
```bash
aws shield associate-proactive-engagement-details \
  --emergency-contact-list 'EmailAddress=security@example.com,PhoneNumber=+15555555555,ContactNotes=Security team'
aws shield enable-proactive-engagement
```

### Enable automatic application-layer DDoS mitigation
```bash
aws shield enable-application-layer-automatic-response \
  --resource-arn arn:aws:elasticloadbalancing:us-east-1:123456789012:loadbalancer/app/my-alb/1234567890abcdef \
  --action 'Block={}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Subscription | [`subscription.md`](subscription.md) | create-subscription, describe-subscription, update-subscription, get-subscription-state |
| Protections | [`protections.md`](protections.md) | create-protection, delete-protection, describe-protection, list-protections, create-protection-group, delete-protection-group, describe-protection-group, list-protection-groups, update-protection-group, list-resources-in-protection-group |
| Attacks | [`attacks.md`](attacks.md) | describe-attack, describe-attack-statistics, list-attacks |
| DRT Access | [`drt-access.md`](drt-access.md) | associate-drt-role, disassociate-drt-role, associate-drt-log-bucket, disassociate-drt-log-bucket, describe-drt-access |
| Proactive Engagement | [`proactive-engagement.md`](proactive-engagement.md) | enable-proactive-engagement, disable-proactive-engagement, associate-proactive-engagement-details, describe-emergency-contact-settings, update-emergency-contact-settings, associate-health-check, disassociate-health-check |
| Automatic Response | [`automatic-response.md`](automatic-response.md) | enable-application-layer-automatic-response, disable-application-layer-automatic-response, update-application-layer-automatic-response |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
