# AWS CLI v2 — Savings Plans

## Overview

Complete reference for all `aws savingsplans` subcommands in AWS CLI v2. Covers purchasing and managing Savings Plans, describing plan details and rates, browsing available offerings and offering rates, returning plans, and deleting queued plans.

## Quick Reference — Common Workflows

### Browse Savings Plans offerings
```bash
aws savingsplans describe-savings-plans-offerings \
  --plan-types Compute \
  --payment-options "No Upfront" \
  --product-type EC2
```

### Browse offering rates for a specific offering
```bash
aws savingsplans describe-savings-plans-offering-rates \
  --savings-plan-offering-ids abc12345-1234-1234-1234-123456789012
```

### Purchase a Savings Plan
```bash
aws savingsplans create-savings-plan \
  --savings-plan-offering-id abc12345-1234-1234-1234-123456789012 \
  --commitment "10.00" \
  --tags Environment=Production
```

### List active Savings Plans
```bash
aws savingsplans describe-savings-plans --states active
```

### Describe rates for a plan
```bash
aws savingsplans describe-savings-plan-rates \
  --savings-plan-id sp-12345678901234567
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Savings Plans | [`savings-plans.md`](savings-plans.md) | create-savings-plan, delete-queued-savings-plan, describe-savings-plans, describe-savings-plan-rates, return-savings-plan |
| Offerings | [`offerings.md`](offerings.md) | describe-savings-plans-offerings, describe-savings-plans-offering-rates |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
