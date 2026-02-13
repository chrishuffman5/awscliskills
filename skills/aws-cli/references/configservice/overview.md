# AWS CLI v2 — Config (AWS Config)

## Overview

Complete reference for all `aws configservice` subcommands in AWS CLI v2. Covers configuration recording, Config rules, conformance packs, remediation actions, aggregators, resource evaluation, organization-level config management, delivery channels, retention, and advanced queries.

## Quick Reference — Common Workflows

### Start configuration recording

```bash
aws configservice put-configuration-recorder \
  --configuration-recorder name=default,roleARN=arn:aws:iam::123456789012:role/ConfigRole \
  --recording-group allSupported=true,includeGlobalResourceTypes=true

aws configservice put-delivery-channel \
  --delivery-channel name=default,s3BucketName=my-config-bucket,snsTopicARN=arn:aws:sns:us-east-1:123456789012:config-topic

aws configservice start-configuration-recorder --configuration-recorder-name default
```

### Create a managed Config rule

```bash
aws configservice put-config-rule --config-rule '{
  "ConfigRuleName": "required-tags",
  "Source": {
    "Owner": "AWS",
    "SourceIdentifier": "REQUIRED_TAGS"
  },
  "InputParameters": "{\"tag1Key\":\"Environment\"}",
  "Scope": {
    "ComplianceResourceTypes": ["AWS::EC2::Instance"]
  }
}'
```

### Check compliance status of a rule

```bash
aws configservice describe-compliance-by-config-rule \
  --config-rule-names required-tags \
  --query 'ComplianceByConfigRules[].Compliance.ComplianceType'
```

### Deploy a conformance pack

```bash
aws configservice put-conformance-pack \
  --conformance-pack-name my-pack \
  --template-s3-uri s3://my-bucket/conformance-pack-template.yaml \
  --delivery-s3-bucket my-config-delivery-bucket
```

### Set up an aggregator for multi-account/region

```bash
aws configservice put-configuration-aggregator \
  --configuration-aggregator-name my-aggregator \
  --organization-aggregation-source RoleArn=arn:aws:iam::123456789012:role/AWSConfigRole,AllAwsRegions=true
```

### Set up auto-remediation

```bash
aws configservice put-remediation-configurations --remediation-configurations '[{
  "ConfigRuleName": "required-tags",
  "TargetType": "SSM_DOCUMENT",
  "TargetId": "AWS-AddTagsToResource",
  "Automatic": true,
  "MaximumAutomaticAttempts": 5,
  "RetryAttemptSeconds": 60,
  "Parameters": {
    "RequiredTagKey": {"StaticValue": {"Values": ["Environment"]}},
    "RequiredTagValue": {"StaticValue": {"Values": ["production"]}}
  }
}]'
```

### Run an advanced query

```bash
aws configservice select-resource-config \
  --expression "SELECT resourceId, resourceType, tags WHERE resourceType = 'AWS::EC2::Instance'" \
  --query 'Results' --output table
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Config Rules | [`config-rules.md`](config-rules.md) | put-config-rule, delete-config-rule, describe-config-rules, describe-config-rule-evaluation-status, start-config-rules-evaluation, delete-evaluation-results, describe-compliance-by-config-rule, describe-compliance-by-resource, get-compliance-details-by-config-rule, get-compliance-details-by-resource, get-compliance-summary-by-config-rule, get-compliance-summary-by-resource-type, get-custom-rule-policy |
| Conformance Packs | [`conformance-packs.md`](conformance-packs.md) | put-conformance-pack, delete-conformance-pack, describe-conformance-packs, describe-conformance-pack-status, describe-conformance-pack-compliance, get-conformance-pack-compliance-details, get-conformance-pack-compliance-summary, list-conformance-pack-compliance-scores |
| Recorders | [`recorders.md`](recorders.md) | put-configuration-recorder, delete-configuration-recorder, describe-configuration-recorders, describe-configuration-recorder-status, start-configuration-recorder, stop-configuration-recorder |
| Delivery Channels | [`delivery-channels.md`](delivery-channels.md) | put-delivery-channel, delete-delivery-channel, describe-delivery-channels, describe-delivery-channel-status, deliver-config-snapshot |
| Remediation | [`remediation.md`](remediation.md) | put-remediation-configurations, delete-remediation-configuration, describe-remediation-configurations, put-remediation-exceptions, delete-remediation-exceptions, describe-remediation-exceptions, describe-remediation-execution-status, start-remediation-execution |
| Aggregators | [`aggregators.md`](aggregators.md) | put-configuration-aggregator, delete-configuration-aggregator, describe-configuration-aggregators, describe-configuration-aggregator-sources-status, put-aggregation-authorization, delete-aggregation-authorization, describe-aggregation-authorizations, describe-pending-aggregation-requests, delete-pending-aggregation-request, get-aggregate-compliance-details-by-config-rule, get-aggregate-config-rule-compliance-summary, get-aggregate-conformance-pack-compliance-summary, get-aggregate-discovered-resource-counts, get-aggregate-resource-config, batch-get-aggregate-resource-config, list-aggregate-discovered-resources, select-aggregate-resource-config |
| Resources | [`resources.md`](resources.md) | list-discovered-resources, get-discovered-resource-counts, get-resource-config-history, batch-get-resource-config, select-resource-config |
| Resource Evaluation | [`resource-evaluation.md`](resource-evaluation.md) | put-evaluations, put-external-evaluation, start-resource-evaluation, get-resource-evaluation-summary, list-resource-evaluations |
| Organization Config | [`organization-config.md`](organization-config.md) | put-organization-config-rule, delete-organization-config-rule, describe-organization-config-rules, describe-organization-config-rule-statuses, get-organization-config-rule-detailed-status, get-organization-custom-rule-policy, put-organization-conformance-pack, delete-organization-conformance-pack, describe-organization-conformance-packs, describe-organization-conformance-pack-statuses, get-organization-conformance-pack-detailed-status |
| Retention & Queries | [`retention-queries.md`](retention-queries.md) | put-retention-configuration, delete-retention-configuration, describe-retention-configurations, put-stored-query, delete-stored-query, get-stored-query, list-stored-queries |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
