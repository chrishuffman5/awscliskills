# AWS CLI v2 — ECR (Elastic Container Registry)

## Overview

Complete reference for all `aws ecr` subcommands in AWS CLI v2. Covers repository management, image operations, lifecycle policies, scanning, authentication, and registry configuration.

## Quick Reference — Common Workflows

### Authenticate Docker to ECR
```bash
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <account-id>.dkr.ecr.us-east-1.amazonaws.com
```

### Create repo, build, tag, push
```bash
aws ecr create-repository --repository-name my-app --image-tag-mutability IMMUTABLE
docker build -t my-app .
docker tag my-app:latest <account-id>.dkr.ecr.us-east-1.amazonaws.com/my-app:latest
docker push <account-id>.dkr.ecr.us-east-1.amazonaws.com/my-app:latest
```

### List images in a repo
```bash
aws ecr describe-images --repository-name my-app --query 'imageDetails[].{Tag:imageTags[0],Pushed:imagePushedAt,Size:imageSizeInBytes}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Repository Management | [`repository-management.md`](repository-management.md) | create-repository, delete-repository, describe-repositories, put-image-tag-mutability, set-repository-policy, get-repository-policy, delete-repository-policy |
| Image Management | [`image-management.md`](image-management.md) | batch-get-image, batch-delete-image, describe-images, list-images, put-image, batch-check-layer-availability |
| Image Scanning | [`image-scanning.md`](image-scanning.md) | describe-image-scan-findings, start-image-scan, put-image-scanning-configuration |
| Lifecycle Policies | [`lifecycle-policies.md`](lifecycle-policies.md) | get-lifecycle-policy, put-lifecycle-policy, delete-lifecycle-policy, start-lifecycle-policy-preview, get-lifecycle-policy-preview |
| Authentication | [`authentication.md`](authentication.md) | get-authorization-token, get-login-password |
| Registry Management | [`registry-management.md`](registry-management.md) | describe-registry, put-registry-policy, get-registry-policy, delete-registry-policy, put-registry-scanning-configuration, get-registry-scanning-configuration, put-replication-configuration, describe-pull-through-cache-rules, create-pull-through-cache-rule, delete-pull-through-cache-rule |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
