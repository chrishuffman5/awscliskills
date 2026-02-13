# AWS CLI v2 — CloudWatch Synthetics

## Overview

Complete reference for all `aws synthetics` subcommands in AWS CLI v2. Covers canary monitoring (create, update, start, stop, delete, dry run), canary groups, runtime version management, and tagging. CloudWatch Synthetics lets you create canaries -- configurable scripts that run on a schedule to monitor your endpoints and APIs.

## Quick Reference — Common Workflows

### Create a canary
```bash
aws synthetics create-canary \
  --name my-canary \
  --artifact-s3-location s3://my-bucket/canary-artifacts \
  --execution-role-arn arn:aws:iam::123456789012:role/canary-role \
  --schedule Expression="rate(5 minutes)" \
  --code Handler=index.handler,ZipFile=fileb://canary.zip \
  --runtime-version syn-nodejs-puppeteer-9.0
```

### List canaries
```bash
aws synthetics describe-canaries
```

### Start a canary
```bash
aws synthetics start-canary --name my-canary
```

### Stop a canary
```bash
aws synthetics stop-canary --name my-canary
```

### Get canary runs
```bash
aws synthetics get-canary-runs --name my-canary --max-results 10
```

### Create a group and associate a canary
```bash
aws synthetics create-group --name my-group
aws synthetics associate-resource --group-identifier my-group \
  --resource-arn arn:aws:synthetics:us-east-1:123456789012:canary:my-canary
```

### Describe runtime versions
```bash
aws synthetics describe-runtime-versions
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Canaries | [`canaries.md`](canaries.md) | create-canary, delete-canary, get-canary, describe-canaries, update-canary, start-canary, stop-canary, start-canary-dry-run, get-canary-runs, describe-canaries-last-run, describe-runtime-versions |
| Groups | [`groups.md`](groups.md) | create-group, delete-group, get-group, list-groups, associate-resource, disassociate-resource, list-group-resources, list-associated-groups |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
