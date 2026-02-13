# AWS CLI v2 — Trusted Advisor (trustedadvisor + support)

## Overview

Complete reference for `aws trustedadvisor` and `aws support` subcommands in AWS CLI v2. Covers the TrustedAdvisor Public API for managing recommendations at account and organization levels, plus the Support API for managing support cases and classic Trusted Advisor check operations. The `aws trustedadvisor` namespace provides the newer API for listing checks, viewing recommendations, managing resource exclusions, and updating recommendation lifecycles. The `aws support` namespace provides support case management and the classic Trusted Advisor check interface (refresh, results, summaries). Both APIs require a Business, Enterprise On-Ramp, or Enterprise Support plan.

## Quick Reference — Common Workflows

### List all Trusted Advisor recommendations
```bash
aws trustedadvisor list-recommendations
```

### Get a specific recommendation with details
```bash
aws trustedadvisor get-recommendation \
  --recommendation-identifier arn:aws:trustedadvisor::123456789012:recommendation/55fa4d2e-bbb7-491a-833b-5773e9589578
```

### List recommendations filtered by pillar and status
```bash
aws trustedadvisor list-recommendations \
  --pillar security --status warning
```

### List resources flagged by a recommendation
```bash
aws trustedadvisor list-recommendation-resources \
  --recommendation-identifier arn:aws:trustedadvisor::123456789012:recommendation/55fa4d2e-bbb7-491a-833b-5773e9589578 \
  --status warning
```

### Dismiss a recommendation
```bash
aws trustedadvisor update-recommendation-lifecycle \
  --recommendation-identifier arn:aws:trustedadvisor::123456789012:recommendation/861c9c6e-f169-405a-8b59-537a8caccd7a \
  --lifecycle-stage dismissed \
  --update-reason "Not applicable to our environment" \
  --update-reason-code not_applicable
```

### List all available Trusted Advisor checks
```bash
aws trustedadvisor list-checks --pillar cost_optimizing
```

### List organization-level recommendations
```bash
aws trustedadvisor list-organization-recommendations --status warning
```

### Get classic Trusted Advisor check results (Support API)
```bash
aws support describe-trusted-advisor-checks --language en --region us-east-1
aws support describe-trusted-advisor-check-result --check-id "Pfx0RwqBli" --region us-east-1
```

### Refresh a classic Trusted Advisor check
```bash
aws support refresh-trusted-advisor-check --check-id "Pfx0RwqBli" --region us-east-1
aws support describe-trusted-advisor-check-refresh-statuses --check-ids "Pfx0RwqBli" --region us-east-1
```

### Create a support case
```bash
aws support create-case \
  --subject "Question about ECS service limits" \
  --communication-body "We need to increase our ECS task limit." \
  --service-code "general-info" \
  --severity-code "low" \
  --issue-type "technical" \
  --language "en"
```

### Describe and resolve a support case
```bash
aws support describe-cases --display-id "1234567890"
aws support resolve-case --case-id "case-12345678910-2013-c4c1d2bf33c5cf47"
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Recommendations | [`recommendations.md`](recommendations.md) | list-recommendations, get-recommendation, list-recommendation-resources, update-recommendation-lifecycle, batch-update-recommendation-resource-exclusion, list-checks |
| Organization Recommendations | [`organization-recommendations.md`](organization-recommendations.md) | list-organization-recommendations, get-organization-recommendation, list-organization-recommendation-accounts, list-organization-recommendation-resources, update-organization-recommendation-lifecycle |
| Support Cases | [`support-cases.md`](support-cases.md) | create-case, describe-cases, add-communication-to-case, describe-communications, resolve-case, describe-services, describe-severity-levels, describe-create-case-options, describe-supported-languages, add-attachments-to-set, describe-attachment |
| Support Trusted Advisor | [`support-trusted-advisor.md`](support-trusted-advisor.md) | describe-trusted-advisor-checks, describe-trusted-advisor-check-result, describe-trusted-advisor-check-summaries, describe-trusted-advisor-check-refresh-statuses, refresh-trusted-advisor-check |
