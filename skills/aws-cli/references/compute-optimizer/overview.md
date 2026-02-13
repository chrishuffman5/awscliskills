# AWS CLI v2 — Compute Optimizer

## Overview

Complete reference for all `aws compute-optimizer` subcommands in AWS CLI v2. Covers resource optimization recommendations for EC2 instances, EBS volumes, Lambda functions, Auto Scaling groups, ECS services on Fargate, RDS DB instances, and idle resources. Also covers enrollment, recommendation exports, and recommendation preferences.

## Quick Reference — Common Workflows

### Enroll an account in Compute Optimizer

```bash
aws compute-optimizer update-enrollment-status --status Active
```

### Get enrollment status

```bash
aws compute-optimizer get-enrollment-status
```

### Get EC2 instance recommendations

```bash
aws compute-optimizer get-ec2-instance-recommendations \
  --instance-arns arn:aws:ec2:us-east-1:123456789012:instance/i-1234567890abcdef0 \
  --query 'instanceRecommendations[].{Instance:instanceArn,Finding:finding,Options:recommendationOptions[0].instanceType}'
```

### Get Auto Scaling group recommendations

```bash
aws compute-optimizer get-auto-scaling-group-recommendations \
  --query 'autoScalingGroupRecommendations[].{ASG:autoScalingGroupName,Finding:finding}'
```

### Get EBS volume recommendations

```bash
aws compute-optimizer get-ebs-volume-recommendations \
  --query 'volumeRecommendations[].{Volume:volumeArn,Finding:finding,Options:volumeRecommendationOptions[0]}'
```

### Get Lambda function recommendations

```bash
aws compute-optimizer get-lambda-function-recommendations \
  --query 'lambdaFunctionRecommendations[].{Function:functionArn,Finding:finding,MemoryCurrent:currentMemorySize}'
```

### Export EC2 recommendations to S3

```bash
aws compute-optimizer export-ec2-instance-recommendations \
  --s3-destination-config bucket=my-optimizer-exports,keyPrefix=ec2 \
  --file-format Csv
```

### Get recommendation summaries

```bash
aws compute-optimizer get-recommendation-summaries \
  --query 'recommendationSummaries[].{Type:recommendationResourceType,Savings:savingsOpportunity}' \
  --output table
```

### Set recommendation preferences for an organization

```bash
aws compute-optimizer put-recommendation-preferences \
  --resource-type Ec2Instance \
  --scope name=Organization,value=o-abc12345 \
  --enhanced-infrastructure-metrics Active
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Enrollment | [`enrollment.md`](enrollment.md) | get-enrollment-status, get-enrollment-statuses-for-organization, update-enrollment-status |
| Recommendations | [`recommendations.md`](recommendations.md) | get-ec2-instance-recommendations, get-ec2-recommendation-projected-metrics, get-auto-scaling-group-recommendations, get-ebs-volume-recommendations, get-lambda-function-recommendations, get-ecs-service-recommendations, get-ecs-service-projected-metrics, get-rds-database-recommendations, get-rds-database-recommendation-projected-metrics, get-idle-recommendations, get-recommendation-summaries, describe-recommendation-export-jobs |
| Exports | [`exports.md`](exports.md) | export-ec2-instance-recommendations, export-auto-scaling-group-recommendations, export-ebs-volume-recommendations, export-lambda-function-recommendations, export-ecs-service-recommendations, export-rds-database-recommendations, export-idle-recommendations |
| Preferences | [`preferences.md`](preferences.md) | get-effective-recommendation-preferences, get-recommendation-preferences, put-recommendation-preferences, delete-recommendation-preferences |
