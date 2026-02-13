# AWS CLI v2 — AWS Health

## Overview

Complete reference for all `aws health` subcommands in AWS CLI v2. Covers Health event discovery, event details, affected entities and accounts, event aggregates, and organizational Health service access. Requires a Business, Enterprise On-Ramp, or Enterprise Support plan from AWS Support.

## Quick Reference — Common Workflows

### List open Health events
```bash
aws health describe-events \
  --filter "eventStatusCodes=open" \
  --region us-east-1
```

### Get event details
```bash
aws health describe-event-details \
  --event-arns "arn:aws:health:us-east-1::event/EC2/AWS_EC2_OPERATIONAL_ISSUE/AWS_EC2_OPERATIONAL_ISSUE_EXAMPLE" \
  --region us-east-1
```

### List affected entities for an event
```bash
aws health describe-affected-entities \
  --filter "eventArns=arn:aws:health:us-east-1::event/EC2/EC2_INSTANCE_RETIREMENT_SCHEDULED/EXAMPLE" \
  --region us-east-1
```

### Get event type counts by category
```bash
aws health describe-event-aggregates \
  --aggregate-field eventTypeCategory \
  --region us-east-1
```

### Enable organizational Health view
```bash
aws health enable-health-service-access-for-organization \
  --region us-east-1
```

### List organization-wide Health events
```bash
aws health describe-events-for-organization \
  --filter "eventStatusCodes=open" \
  --region us-east-1
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Events | [`events.md`](events.md) | describe-events, describe-event-details, describe-event-types, describe-event-aggregates |
| Affected Entities | [`affected-entities.md`](affected-entities.md) | describe-affected-entities, describe-entity-aggregates |
| Organization Events | [`organization-events.md`](organization-events.md) | describe-events-for-organization, describe-event-details-for-organization, describe-affected-entities-for-organization, describe-affected-accounts-for-organization, describe-entity-aggregates-for-organization |
| Organization Access | [`organization-access.md`](organization-access.md) | enable-health-service-access-for-organization, disable-health-service-access-for-organization, describe-health-service-status-for-organization |
