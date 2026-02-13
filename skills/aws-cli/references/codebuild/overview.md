# AWS CLI v2 — CodeBuild

## Overview

Complete reference for all `aws codebuild` subcommands in AWS CLI v2. Covers build project management, build execution, build batches, report groups, reports, source credentials, webhooks, compute fleets, and resource tagging.

## Quick Reference — Common Workflows

### Create a build project
```bash
aws codebuild create-project --name my-project \
  --source type=CODECOMMIT,location=https://git-codecommit.us-east-1.amazonaws.com/v1/repos/my-repo \
  --artifacts type=S3,location=my-bucket,path=builds \
  --environment type=LINUX_CONTAINER,computeType=BUILD_GENERAL1_SMALL,image=aws/codebuild/amazonlinux2-x86_64-standard:4.0 \
  --service-role arn:aws:iam::123456789012:role/codebuild-role
```

### Start a build
```bash
aws codebuild start-build --project-name my-project
```

### Start a build with overrides
```bash
aws codebuild start-build --project-name my-project \
  --source-version main \
  --environment-variables-override name=ENV_VAR,value=my-value,type=PLAINTEXT
```

### List builds for a project
```bash
aws codebuild list-builds-for-project --project-name my-project \
  --sort-order DESCENDING --query 'ids[0:5]'
```

### Get build details
```bash
aws codebuild batch-get-builds --ids my-project:build-id
```

### Stop a running build
```bash
aws codebuild stop-build --id my-project:build-id
```

### Import source credentials (GitHub PAT)
```bash
aws codebuild import-source-credentials \
  --server-type GITHUB \
  --auth-type PERSONAL_ACCESS_TOKEN \
  --token my-pat-token
```

### Create a webhook for automatic builds
```bash
aws codebuild create-webhook --project-name my-project \
  --filter-groups '[[{"type":"EVENT","pattern":"PUSH"},{"type":"HEAD_REF","pattern":"^refs/heads/main$"}]]'
```

### Start a build batch
```bash
aws codebuild start-build-batch --project-name my-project \
  --buildspec-override file://buildspec-batch.yml
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Projects | [`projects.md`](projects.md) | create-project, delete-project, batch-get-projects, list-projects, update-project |
| Builds | [`builds.md`](builds.md) | start-build, stop-build, retry-build, batch-get-builds, list-builds, list-builds-for-project |
| Build Batches | [`build-batches.md`](build-batches.md) | start-build-batch, stop-build-batch, retry-build-batch, delete-build-batch, describe-build-batches (batch-get-build-batches), list-build-batches, list-build-batches-for-project |
| Report Groups | [`report-groups.md`](report-groups.md) | create-report-group, delete-report-group, batch-get-report-groups, list-report-groups, update-report-group |
| Reports | [`reports.md`](reports.md) | batch-get-reports, delete-report, describe-test-cases, list-reports, list-reports-for-report-group |
| Source Credentials | [`source-credentials.md`](source-credentials.md) | import-source-credentials, delete-source-credentials, list-source-credentials |
| Webhooks | [`webhooks.md`](webhooks.md) | create-webhook, delete-webhook, update-webhook |
| Fleets | [`fleets.md`](fleets.md) | create-fleet, delete-fleet, batch-get-fleets, list-fleets, update-fleet |
| Tags | [`tags.md`](tags.md) | tag-resource (codebuild), untag-resource (codebuild), list-tags-for-resource (codebuild, via batch-get) |
