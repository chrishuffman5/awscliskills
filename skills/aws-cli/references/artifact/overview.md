# AWS CLI v2 — Artifact (artifact)

## Overview

Complete reference for all `aws artifact` subcommands in AWS CLI v2. Covers compliance report management, agreement management, and account settings. AWS Artifact provides on-demand access to AWS compliance reports and agreements. Use these commands to list available compliance reports, download reports (after accepting terms), manage customer agreements, and configure notification settings.

## Quick Reference — Common Workflows

### List all available compliance reports
```bash
aws artifact list-reports
```

### Get metadata for a specific report
```bash
aws artifact get-report-metadata \
  --report-id report-abc123def456gh78
```

### List all versions of a report
```bash
aws artifact list-report-versions \
  --report-id report-abc123def456gh78
```

### Accept terms and download a report
```bash
# Step 1: Get the term token
aws artifact get-term-for-report \
  --report-id report-abc123def456gh78

# Step 2: Download the report using the term token
aws artifact get-report \
  --report-id report-abc123def456gh78 \
  --term-token <term-token-from-step-1>
```

### List customer agreements
```bash
aws artifact list-customer-agreements
```

### Get account settings
```bash
aws artifact get-account-settings
```

### Update notification subscription
```bash
aws artifact put-account-settings \
  --notification-subscription-status SUBSCRIBED
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Reports | [`reports.md`](reports.md) | list-reports, get-report-metadata, get-report, get-term-for-report, list-report-versions |
| Agreements & Settings | [`agreements-settings.md`](agreements-settings.md) | list-customer-agreements, get-account-settings, put-account-settings |
