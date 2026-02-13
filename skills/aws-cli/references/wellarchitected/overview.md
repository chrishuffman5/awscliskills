# AWS CLI v2 — Well-Architected

## Overview

Complete reference for all `aws wellarchitected` subcommands in AWS CLI v2. Covers workload management, lens reviews and answers, milestones, profiles, review templates, share invitations, consolidated reports, check summaries, and global settings for the AWS Well-Architected Framework.

## Quick Reference — Common Workflows

### Create a workload
```bash
aws wellarchitected create-workload \
  --workload-name "MyWebApp" \
  --description "Production web application" \
  --environment PRODUCTION \
  --aws-regions us-east-1 us-west-2 \
  --review-owner "team@example.com" \
  --lenses wellarchitected serverless
```

### Get a lens review summary
```bash
aws wellarchitected get-lens-review \
  --workload-id a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4 \
  --lens-alias wellarchitected
```

### List improvement recommendations
```bash
aws wellarchitected list-lens-review-improvements \
  --workload-id a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4 \
  --lens-alias wellarchitected \
  --pillar-id operationalExcellence
```

### Create a milestone
```bash
aws wellarchitected create-milestone \
  --workload-id a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4 \
  --milestone-name "Q1-2026 Review"
```

### Share a workload
```bash
aws wellarchitected create-workload-share \
  --workload-id a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4 \
  --shared-with "123456789012" \
  --permission-type CONTRIBUTOR
```

### Get consolidated report
```bash
aws wellarchitected get-consolidated-report \
  --format PDF --include-shared-resources
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Workloads | [`workloads.md`](workloads.md) | create-workload, delete-workload, get-workload, list-workloads, update-workload, create-workload-share, delete-workload-share, list-workload-shares, update-workload-share |
| Lenses | [`lenses.md`](lenses.md) | import-lens, export-lens, delete-lens, get-lens, list-lenses, create-lens-version, get-lens-version-difference, associate-lenses, disassociate-lenses, create-lens-share, delete-lens-share, list-lens-shares |
| Reviews | [`reviews.md`](reviews.md) | get-lens-review, list-lens-reviews, update-lens-review, get-lens-review-report, list-lens-review-improvements, upgrade-lens-review |
| Answers | [`answers.md`](answers.md) | get-answer, list-answers, update-answer |
| Milestones | [`milestones.md`](milestones.md) | create-milestone, get-milestone, list-milestones |
| Profiles | [`profiles.md`](profiles.md) | create-profile, delete-profile, get-profile, list-profiles, update-profile, get-profile-template, create-profile-share, delete-profile-share, list-profile-shares, list-profile-notifications, upgrade-profile-version, associate-profiles, disassociate-profiles |
| Review Templates | [`review-templates.md`](review-templates.md) | create-review-template, delete-review-template, get-review-template, list-review-templates, update-review-template, get-review-template-answer, list-review-template-answers, update-review-template-answer, get-review-template-lens-review, update-review-template-lens-review, upgrade-review-template-lens-review, create-template-share, delete-template-share, list-template-shares |
| Share Invitations | [`share-invitations.md`](share-invitations.md) | list-share-invitations, update-share-invitation |
| Checks & Reports | [`checks-reports.md`](checks-reports.md) | list-check-details, list-check-summaries, get-consolidated-report, list-notifications |
| Settings | [`settings.md`](settings.md) | get-global-settings, update-global-settings, update-integration |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
