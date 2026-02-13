# AWS CLI v2 — SSM Incidents (Incident Manager) + SSM Contacts

## Overview

Complete reference for `aws ssm-incidents` and `aws ssm-contacts` subcommands in AWS CLI v2. This is a merged reference covering both services. SSM Incidents manages incident response plans, incidents, timeline events, and replication sets. SSM Contacts manages contacts, contact channels, engagements, and on-call rotations.

## Quick Reference — Common Workflows

### Create a replication set
```bash
aws ssm-incidents create-replication-set \
  --regions '{"us-east-1":{"sseKmsKeyId":"DefaultKey"}}'
```

### Create a response plan
```bash
aws ssm-incidents create-response-plan \
  --name "critical-incident-plan" \
  --incident-template '{"title":"Critical Incident","impact":1}'
```

### Start an incident
```bash
aws ssm-incidents start-incident --response-plan-arn \
  arn:aws:ssm-incidents:us-east-1:123456789012:response-plan/critical-incident-plan
```

### Create a contact
```bash
aws ssm-contacts create-contact --alias "oncall-engineer" \
  --display-name "On-Call Engineer" --type PERSONAL \
  --plan '{"Stages":[]}'
```

### Create a contact channel
```bash
aws ssm-contacts create-contact-channel --contact-id \
  arn:aws:ssm-contacts:us-east-1:123456789012:contact/oncall-engineer \
  --name "Email" --type EMAIL \
  --delivery-address '{"SimpleAddress":"engineer@example.com"}'
```

### Start an engagement
```bash
aws ssm-contacts start-engagement \
  --contact-id arn:aws:ssm-contacts:us-east-1:123456789012:contact/oncall-engineer \
  --sender "ssm-incidents" --subject "Critical alert" --content "Service is down"
```

### Create a rotation
```bash
aws ssm-contacts create-rotation --name "weekly-rotation" \
  --contact-ids arn:aws:ssm-contacts:us-east-1:123456789012:contact/eng1 \
    arn:aws:ssm-contacts:us-east-1:123456789012:contact/eng2 \
  --time-zone-id "America/New_York" \
  --recurrence '{"MonthlySettings":[],"WeeklySettings":[{"DayOfWeek":"MON","HandOffTime":{"HourOfDay":9,"MinuteOfHour":0}}],"NumberOfOnCalls":1,"RecurrenceMultiplier":1}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Response Plans | [`response-plans.md`](response-plans.md) | create-response-plan, delete-response-plan, get-response-plan, list-response-plans, update-response-plan |
| Incidents | [`incidents.md`](incidents.md) | start-incident, get-incident-record, delete-incident-record, update-incident-record, list-incident-records, update-deletion-protection |
| Incident Findings | [`incident-findings.md`](incident-findings.md) | batch-get-incident-findings, list-incident-findings |
| Related Items | [`related-items.md`](related-items.md) | list-related-items, update-related-items |
| Timeline Events | [`timeline-events.md`](timeline-events.md) | create-timeline-event, delete-timeline-event, get-timeline-event, list-timeline-events, update-timeline-event |
| Replication Sets | [`replication-sets.md`](replication-sets.md) | create-replication-set, delete-replication-set, get-replication-set, list-replication-sets, update-replication-set |
| Resource Policies | [`resource-policies.md`](resource-policies.md) | get-resource-policies, put-resource-policy, delete-resource-policy |
| Contacts | [`contacts.md`](contacts.md) | create-contact, delete-contact, get-contact, list-contacts, update-contact, get-contact-policy, put-contact-policy |
| Contact Channels | [`contact-channels.md`](contact-channels.md) | create-contact-channel, delete-contact-channel, get-contact-channel, list-contact-channels, update-contact-channel, activate-contact-channel, deactivate-contact-channel, send-activation-code |
| Engagements | [`engagements.md`](engagements.md) | start-engagement, stop-engagement, describe-engagement, list-engagements, accept-page, describe-page, list-pages-by-contact, list-pages-by-engagement, list-page-receipts, list-page-resolutions |
| Rotations | [`rotations.md`](rotations.md) | create-rotation, delete-rotation, get-rotation, list-rotations, update-rotation, create-rotation-override, delete-rotation-override, get-rotation-override, list-rotation-overrides, list-rotation-shifts, list-preview-rotation-shifts |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait-for-replication-set-active, wait-for-replication-set-deleted |
