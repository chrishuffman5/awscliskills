# AWS CLI v2 — CodeCommit

## Overview

Complete reference for all `aws codecommit` subcommands in AWS CLI v2. Covers repository management, branch operations, commits and file operations, pull requests, approval rules, merge operations, comments, and triggers for AWS CodeCommit Git-based source control.

> **Note:** AWS CodeCommit is no longer accepting new customers as of July 2024. Existing customers can continue to use the service.

## Quick Reference — Common Workflows

### Create a repository
```bash
aws codecommit create-repository --repository-name my-repo \
  --repository-description "My application repository"
```

### List and describe repositories
```bash
aws codecommit list-repositories
aws codecommit get-repository --repository-name my-repo
```

### Create a branch
```bash
aws codecommit create-branch --repository-name my-repo \
  --branch-name feature-branch --commit-id abc123def456
```

### Create a pull request
```bash
aws codecommit create-pull-request --title "Add new feature" \
  --targets repositoryName=my-repo,sourceReference=feature-branch,destinationReference=main
```

### Merge a pull request
```bash
aws codecommit merge-pull-request-by-squash \
  --pull-request-id 42 --repository-name my-repo
```

### Create a commit with file changes
```bash
aws codecommit create-commit --repository-name my-repo \
  --branch-name main --parent-commit-id abc123 \
  --put-files '[{"filePath":"README.md","fileContent":"SGVsbG8="}]'
```

### Set up repository triggers
```bash
aws codecommit put-repository-triggers --repository-name my-repo \
  --triggers '[{"name":"my-trigger","destinationArn":"arn:aws:sns:us-east-1:123456789012:my-topic","events":["all"],"branches":["main"]}]'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Repositories | [`repositories.md`](repositories.md) | create-repository, delete-repository, get-repository, list-repositories, batch-get-repositories, update-repository-description, update-repository-name |
| Branches | [`branches.md`](branches.md) | create-branch, delete-branch, get-branch, list-branches, update-default-branch |
| Commits & Files | [`commits-files.md`](commits-files.md) | create-commit, get-commit, batch-get-commits, get-differences, get-blob, get-file, get-folder, put-file, delete-file |
| Pull Requests | [`pull-requests.md`](pull-requests.md) | create-pull-request, get-pull-request, list-pull-requests, update-pull-request-title, update-pull-request-description, update-pull-request-status, describe-pull-request-events, evaluate-pull-request-approval-rules |
| Approval Rules | [`approval-rules.md`](approval-rules.md) | create-approval-rule-template, delete-approval-rule-template, get-approval-rule-template, list-approval-rule-templates, update-approval-rule-template-content, associate-approval-rule-template-with-repository, disassociate-approval-rule-template-from-repository, list-associated-approval-rule-templates-for-repository, list-repositories-for-approval-rule-template |
| Merges | [`merges.md`](merges.md) | get-merge-options, get-merge-conflicts, get-merge-commit, merge-branches-by-fast-forward, merge-branches-by-squash, merge-branches-by-three-way, merge-pull-request-by-fast-forward, merge-pull-request-by-squash, merge-pull-request-by-three-way |
| Comments | [`comments.md`](comments.md) | post-comment-for-compared-commit, post-comment-for-pull-request, post-comment-reply, get-comment, get-comments-for-compared-commit, get-comments-for-pull-request, update-comment, delete-comment-content |
| Triggers | [`triggers.md`](triggers.md) | get-repository-triggers, put-repository-triggers, test-repository-triggers |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
