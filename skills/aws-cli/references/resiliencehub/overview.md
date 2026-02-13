# AWS CLI v2 — Resilience Hub

## Overview

Complete reference for all `aws resiliencehub` subcommands in AWS CLI v2. Covers application resilience management including apps, app versions, app components, resources, resiliency policies, assessments, recommendations (alarms, SOPs, tests), resource grouping, metrics export, and recommendation templates.

## Quick Reference — Common Workflows

### Create an application
```bash
aws resiliencehub create-app \
  --name my-resilient-app \
  --description "Production application" \
  --assessment-schedule Daily
```

### Create a resiliency policy
```bash
aws resiliencehub create-resiliency-policy \
  --policy-name critical-policy \
  --tier Critical \
  --policy 'Software={rpoInSecs=3600,rtoInSecs=3600},Hardware={rpoInSecs=86400,rtoInSecs=86400},AZ={rpoInSecs=86400,rtoInSecs=86400}'
```

### Start an assessment
```bash
aws resiliencehub start-app-assessment \
  --app-arn arn:aws:resiliencehub:us-east-1:123456789012:app/app-id \
  --app-version release \
  --assessment-name weekly-assessment
```

### Describe an assessment
```bash
aws resiliencehub describe-app-assessment \
  --assessment-arn arn:aws:resiliencehub:us-east-1:123456789012:app-assessment/assessment-id
```

### List alarm recommendations
```bash
aws resiliencehub list-alarm-recommendations \
  --assessment-arn arn:aws:resiliencehub:us-east-1:123456789012:app-assessment/assessment-id
```

### Import resources to draft app version
```bash
aws resiliencehub import-resources-to-draft-app-version \
  --app-arn arn:aws:resiliencehub:us-east-1:123456789012:app/app-id \
  --source-arns arn:aws:cloudformation:us-east-1:123456789012:stack/my-stack/guid
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Apps | [`apps.md`](apps.md) | create-app, delete-app, describe-app, list-apps, update-app, publish-app-version, describe-app-version, list-app-versions, update-app-version |
| App Components | [`app-components.md`](app-components.md) | create-app-version-app-component, delete-app-version-app-component, describe-app-version-app-component, list-app-version-app-components, update-app-version-app-component |
| App Resources | [`app-resources.md`](app-resources.md) | create-app-version-resource, delete-app-version-resource, describe-app-version-resource, list-app-version-resources, update-app-version-resource, add-draft-app-version-resource-mappings, remove-draft-app-version-resource-mappings, list-app-version-resource-mappings, import-resources-to-draft-app-version, describe-draft-app-version-resources-import-status, describe-app-version-resources-resolution-status, resolve-app-version-resources, describe-app-version-template, put-draft-app-version-template, list-app-input-sources, delete-app-input-source, list-unsupported-app-version-resources |
| Assessments | [`assessments.md`](assessments.md) | start-app-assessment, delete-app-assessment, describe-app-assessment, list-app-assessments, list-app-assessment-compliance-drifts, list-app-assessment-resource-drifts |
| Recommendations | [`recommendations.md`](recommendations.md) | list-alarm-recommendations, list-sop-recommendations, list-test-recommendations, list-app-component-compliances, list-app-component-recommendations, batch-update-recommendation-status, create-recommendation-template, delete-recommendation-template, list-recommendation-templates |
| Resiliency Policies | [`resiliency-policies.md`](resiliency-policies.md) | create-resiliency-policy, delete-resiliency-policy, describe-resiliency-policy, list-resiliency-policies, update-resiliency-policy, list-suggested-resiliency-policies |
| Resource Grouping | [`resource-grouping.md`](resource-grouping.md) | start-resource-grouping-recommendation-task, describe-resource-grouping-recommendation-task, list-resource-grouping-recommendations, accept-resource-grouping-recommendations, reject-resource-grouping-recommendations |
| Metrics | [`metrics.md`](metrics.md) | start-metrics-export, describe-metrics-export, list-metrics |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
