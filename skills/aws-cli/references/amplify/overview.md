# AWS CLI v2 — Amplify (Amplify Hosting)

## Overview

Complete reference for all `aws amplify` subcommands in AWS CLI v2. Covers app management, branch configuration, domain associations, backend environments, jobs, deployments, and webhooks for AWS Amplify Hosting.

## Quick Reference — Common Workflows

### Create an Amplify app
```bash
aws amplify create-app --name my-app \
  --repository https://github.com/user/repo \
  --oauth-token ghp_xxxxxxxxxxxx \
  --build-spec "version: 1\nfrontend:\n  phases:\n    build:\n      commands:\n        - npm run build"
```

### Create a branch
```bash
aws amplify create-branch --app-id d1234abcde \
  --branch-name main \
  --stage PRODUCTION \
  --enable-auto-build
```

### Start a deployment job
```bash
aws amplify start-job --app-id d1234abcde \
  --branch-name main \
  --job-type RELEASE
```

### Associate a custom domain
```bash
aws amplify create-domain-association --app-id d1234abcde \
  --domain-name example.com \
  --sub-domain-settings 'prefix="",branchName=main' \
  --sub-domain-settings 'prefix=www,branchName=main'
```

### Create a manual deployment
```bash
aws amplify create-deployment --app-id d1234abcde --branch-name main
# Upload files to the returned zipUploadUrl, then:
aws amplify start-deployment --app-id d1234abcde --branch-name main \
  --job-id job-id
```

### List apps
```bash
aws amplify list-apps --query 'apps[].{Name:name,Id:appId,Repository:repository}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Apps | [`apps.md`](apps.md) | create-app, delete-app, get-app, list-apps, update-app, generate-access-logs |
| Branches | [`branches.md`](branches.md) | create-branch, delete-branch, get-branch, list-branches, update-branch |
| Domains | [`domains.md`](domains.md) | create-domain-association, delete-domain-association, get-domain-association, list-domain-associations, update-domain-association |
| Jobs & Deployments | [`jobs-deployments.md`](jobs-deployments.md) | start-job, stop-job, get-job, list-jobs, delete-job, create-deployment, start-deployment, get-artifact-url, list-artifacts |
| Backend Environments | [`backend-environments.md`](backend-environments.md) | create-backend-environment, delete-backend-environment, get-backend-environment, list-backend-environments |
| Webhooks | [`webhooks.md`](webhooks.md) | create-webhook, delete-webhook, get-webhook, list-webhooks, update-webhook |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
