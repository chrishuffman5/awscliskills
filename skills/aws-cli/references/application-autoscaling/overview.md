# AWS CLI v2 — Application Auto Scaling

## Overview

Complete reference for all `aws application-autoscaling` subcommands in AWS CLI v2. Covers scalable target registration, scaling policy management (target tracking, step scaling, predictive scaling), scheduled actions, scaling activity monitoring, and resource tagging. Application Auto Scaling provides unified auto scaling for AWS services including ECS, DynamoDB, Lambda, RDS, ElastiCache, Neptune, SageMaker, EMR, AppStream, EC2 Spot Fleets, Comprehend, Kafka, Cassandra, and custom resources.

## Quick Reference — Common Workflows

### Register an ECS service for auto scaling
```bash
aws application-autoscaling register-scalable-target \
    --service-namespace ecs \
    --scalable-dimension ecs:service:DesiredCount \
    --resource-id service/my-cluster/my-service \
    --min-capacity 2 \
    --max-capacity 10

aws application-autoscaling put-scaling-policy \
    --service-namespace ecs \
    --scalable-dimension ecs:service:DesiredCount \
    --resource-id service/my-cluster/my-service \
    --policy-name cpu-target-tracking \
    --policy-type TargetTrackingScaling \
    --target-tracking-scaling-policy-configuration \
        '{"TargetValue":75.0,"PredefinedMetricSpecification":{"PredefinedMetricType":"ECSServiceAverageCPUUtilization"},"ScaleOutCooldown":300,"ScaleInCooldown":300}'
```

### Set up DynamoDB table auto scaling
```bash
aws application-autoscaling register-scalable-target \
    --service-namespace dynamodb \
    --scalable-dimension dynamodb:table:ReadCapacityUnits \
    --resource-id table/my-table \
    --min-capacity 5 \
    --max-capacity 100

aws application-autoscaling put-scaling-policy \
    --service-namespace dynamodb \
    --scalable-dimension dynamodb:table:ReadCapacityUnits \
    --resource-id table/my-table \
    --policy-name read-capacity-tracking \
    --policy-type TargetTrackingScaling \
    --target-tracking-scaling-policy-configuration \
        '{"TargetValue":70.0,"PredefinedMetricSpecification":{"PredefinedMetricType":"DynamoDBReadCapacityUtilization"}}'
```

### Create a scheduled scaling action
```bash
aws application-autoscaling put-scheduled-action \
    --service-namespace ecs \
    --scalable-dimension ecs:service:DesiredCount \
    --resource-id service/my-cluster/my-service \
    --scheduled-action-name scale-up-morning \
    --schedule "cron(0 8 * * ? *)" \
    --timezone "America/New_York" \
    --scalable-target-action MinCapacity=5,MaxCapacity=20
```

### Check scaling activities
```bash
aws application-autoscaling describe-scaling-activities \
    --service-namespace ecs \
    --resource-id service/my-cluster/my-service \
    --query 'ScalingActivities[].{Time:StartTime,Status:StatusCode,Cause:Cause}'
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Scalable Targets | [scalable-targets.md](scalable-targets.md) | `register-scalable-target`, `deregister-scalable-target`, `describe-scalable-targets` |
| Scaling Policies | [scaling-policies.md](scaling-policies.md) | `put-scaling-policy`, `delete-scaling-policy`, `describe-scaling-policies`, `describe-scaling-activities`, `get-predictive-scaling-forecast` |
| Scheduled Actions | [scheduled-actions.md](scheduled-actions.md) | `put-scheduled-action`, `delete-scheduled-action`, `describe-scheduled-actions` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
