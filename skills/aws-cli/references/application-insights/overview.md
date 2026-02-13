# AWS CLI v2 — Application Insights

## Overview

Complete reference for all `aws application-insights` subcommands in AWS CLI v2. Covers application monitoring, component management, log pattern configuration, problem detection, observation analysis, and workload management for Amazon CloudWatch Application Insights.

## Quick Reference — Common Workflows

### Create an application for monitoring
```bash
aws application-insights create-application \
  --resource-group-name my-resource-group \
  --ops-center-enabled \
  --ops-item-sns-topic-arn arn:aws:sns:us-east-1:123456789012:my-topic
```

### List and describe applications
```bash
aws application-insights list-applications
aws application-insights describe-application \
  --resource-group-name my-resource-group
```

### List and configure components
```bash
aws application-insights list-components \
  --resource-group-name my-resource-group
aws application-insights describe-component-configuration-recommendation \
  --resource-group-name my-resource-group \
  --component-name my-component --tier SQL_SERVER
```

### View problems and observations
```bash
aws application-insights list-problems \
  --resource-group-name my-resource-group
aws application-insights describe-problem --problem-id p-12345
aws application-insights describe-problem-observations --problem-id p-12345
```

### Create a custom log pattern
```bash
aws application-insights create-log-pattern \
  --resource-group-name my-resource-group \
  --pattern-set-name my-pattern-set \
  --pattern-name my-pattern \
  --pattern "ERROR.*OutOfMemory" --rank 1
```

### Manage workloads
```bash
aws application-insights add-workload \
  --resource-group-name my-resource-group \
  --component-name my-component \
  --workload-configuration '{"Tier":"SQL_SERVER","WorkloadName":"my-db"}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Applications | [`applications.md`](applications.md) | create-application, delete-application, describe-application, list-applications, update-application |
| Components | [`components.md`](components.md) | create-component, delete-component, describe-component, list-components, update-component, describe-component-configuration, describe-component-configuration-recommendation, update-component-configuration |
| Log Patterns | [`log-patterns.md`](log-patterns.md) | create-log-pattern, delete-log-pattern, describe-log-pattern, list-log-patterns, update-log-pattern, list-log-pattern-sets |
| Problems | [`problems.md`](problems.md) | describe-problem, list-problems, update-problem, describe-problem-observations, describe-observation, list-configuration-history |
| Workloads | [`workloads.md`](workloads.md) | add-workload, remove-workload, describe-workload, list-workloads, update-workload |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
