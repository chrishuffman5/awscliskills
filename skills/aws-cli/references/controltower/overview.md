# AWS CLI v2 — Control Tower (controltower)

## Overview

Complete reference for all `aws controltower` subcommands in AWS CLI v2. Covers landing zone management, control (guardrail) enablement and lifecycle, baseline management, and tagging. AWS Control Tower provides a pre-configured multi-account environment with governance guardrails based on AWS best practices. All operations that modify resources (create, enable, disable, update, reset) are asynchronous and return an `operationIdentifier` that can be used to track progress.

## Quick Reference — Common Workflows

### Create a landing zone
```bash
aws controltower create-landing-zone \
  --landing-zone-version "3.0" \
  --manifest file://manifest.json
```

### Get landing zone details
```bash
aws controltower get-landing-zone \
  --landing-zone-identifier arn:aws:controltower:us-east-1:123456789012:landingzone/ABCDEFGHIJKL
```

### Update a landing zone
```bash
aws controltower update-landing-zone \
  --landing-zone-identifier arn:aws:controltower:us-east-1:123456789012:landingzone/ABCDEFGHIJKL \
  --landing-zone-version "3.1" \
  --manifest file://manifest.json
```

### Enable a control on an OU
```bash
aws controltower enable-control \
  --control-identifier arn:aws:controltower:us-east-1::control/AWS-GR_RESTRICT_ROOT_USER_ACCESS_KEYS \
  --target-identifier arn:aws:organizations::123456789012:ou/o-abcdef/ou-xyz-12345678
```

### List enabled controls
```bash
aws controltower list-enabled-controls \
  --target-identifier arn:aws:organizations::123456789012:ou/o-abcdef/ou-xyz-12345678
```

### Disable a control
```bash
aws controltower disable-control \
  --control-identifier arn:aws:controltower:us-east-1::control/AWS-GR_RESTRICT_ROOT_USER_ACCESS_KEYS \
  --target-identifier arn:aws:organizations::123456789012:ou/o-abcdef/ou-xyz-12345678
```

### Check operation status
```bash
aws controltower get-control-operation \
  --operation-identifier a1b2c3d4-5678-90ab-cdef-EXAMPLE11111
```

### Enable a baseline on an OU
```bash
aws controltower enable-baseline \
  --baseline-identifier arn:aws:controltower:us-east-1::baseline/ABCDEFGHIJKL \
  --baseline-version "1.0" \
  --target-identifier arn:aws:organizations::123456789012:ou/o-abcdef/ou-xyz-12345678
```

### List available baselines
```bash
aws controltower list-baselines
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Landing Zones | [`landing-zones.md`](landing-zones.md) | create-landing-zone, get-landing-zone, list-landing-zones, update-landing-zone, delete-landing-zone, reset-landing-zone, get-landing-zone-operation, list-landing-zone-operations |
| Controls | [`controls.md`](controls.md) | enable-control, disable-control, get-enabled-control, list-enabled-controls, reset-enabled-control, get-control-operation, list-control-operations |
| Baselines | [`baselines.md`](baselines.md) | enable-baseline, disable-baseline, get-baseline, get-enabled-baseline, list-baselines, list-enabled-baselines, update-enabled-baseline, reset-enabled-baseline, get-baseline-operation |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
