# AWS CLI v2 — CodeGuru (Code Reviews + Security Scanning)

## Overview

Complete reference for `aws codeguru-reviewer` and `aws codeguru-security` subcommands in AWS CLI v2. CodeGuru Reviewer provides automated code reviews powered by machine learning. CodeGuru Security provides automated security scanning for code vulnerabilities. Note: CodeGuru Security reached end of support in November 2025.

## Quick Reference — Common Workflows

### Associate a repository for code reviews
```bash
aws codeguru-reviewer associate-repository \
  --repository 'CodeCommit={Name=my-repo}' \
  --tags Environment=production
```

### Create a code review
```bash
aws codeguru-reviewer create-code-review \
  --name my-review \
  --repository-association-arn arn:aws:codeguru-reviewer:us-east-1:123456789012:association:uuid \
  --type 'RepositoryAnalysis={RepositoryHead={BranchName=main}}'
```

### List recommendations for a code review
```bash
aws codeguru-reviewer list-recommendations \
  --code-review-arn arn:aws:codeguru-reviewer:us-east-1:123456789012:code-review:uuid
```

### Provide feedback on a recommendation
```bash
aws codeguru-reviewer put-recommendation-feedback \
  --code-review-arn arn:aws:codeguru-reviewer:us-east-1:123456789012:code-review:uuid \
  --recommendation-id rec-id \
  --reactions ThumbsUp
```

### Create a security scan
```bash
aws codeguru-security create-scan \
  --scan-name my-scan \
  --resource-id '{"ScanName":"my-scan"}' \
  --scan-type Standard \
  --analysis-type Security
```

### Get security findings
```bash
aws codeguru-security get-findings \
  --scan-name my-scan \
  --status Open
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Repositories | [`repositories.md`](repositories.md) | associate-repository, disassociate-repository, describe-repository-association, list-repository-associations |
| Code Reviews | [`code-reviews.md`](code-reviews.md) | create-code-review, describe-code-review, list-code-reviews |
| Recommendations | [`recommendations.md`](recommendations.md) | list-recommendations, list-recommendation-feedback, describe-recommendation-feedback, put-recommendation-feedback |
| Security Scans | [`security-scans.md`](security-scans.md) | create-scan, get-scan, list-scans, create-upload-url |
| Security Findings | [`security-findings.md`](security-findings.md) | get-findings, batch-get-findings, list-findings-metrics, get-metrics-summary |
| Security Account | [`security-account.md`](security-account.md) | get-account-configuration, update-account-configuration |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait code-review-completed, wait repository-association-succeeded |
