# Application Auto Scaling — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `register-scalable-target` | Register a scalable target with min/max capacity |
| `deregister-scalable-target` | Deregister a scalable target |
| `describe-scalable-targets` | Describe registered scalable targets |
| `put-scaling-policy` | Create or update a scaling policy |
| `delete-scaling-policy` | Delete a scaling policy |
| `describe-scaling-policies` | Describe scaling policies |
| `describe-scaling-activities` | Describe scaling activities and history |
| `get-predictive-scaling-forecast` | Get predictive scaling forecast data |
| `put-scheduled-action` | Create or update a scheduled scaling action |
| `delete-scheduled-action` | Delete a scheduled action |
| `describe-scheduled-actions` | Describe scheduled actions |
| `tag-resource` | Add tags to a scalable target |
| `untag-resource` | Remove tags from a scalable target |
| `list-tags-for-resource` | List tags for a scalable target |

## Global Options

All commands accept these options:

| Option | Description |
|--------|-------------|
| `--output` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | JMESPath query to filter output |
| `--region` | AWS region |
| `--profile` | Named credential profile |
| `--no-cli-pager` | Disable pager for output |
| `--cli-input-json` | Read parameters from JSON string |
| `--cli-input-yaml` | Read parameters from YAML string |
| `--generate-cli-skeleton` | Print JSON/YAML input skeleton |

## Common Service Namespaces

| Namespace | Service | Example Resource ID | Example Scalable Dimension |
|-----------|---------|--------------------|-----------------------------|
| `ecs` | ECS | `service/cluster/service` | `ecs:service:DesiredCount` |
| `dynamodb` | DynamoDB | `table/TableName` | `dynamodb:table:ReadCapacityUnits` |
| `rds` | Aurora | `cluster:my-cluster` | `rds:cluster:ReadReplicaCount` |
| `lambda` | Lambda | `function:my-func:prod` | `lambda:function:ProvisionedConcurrency` |
| `elasticache` | ElastiCache | `replication-group/my-rg` | `elasticache:replication-group:NodeGroups` |
| `ec2` | Spot Fleet | `spot-fleet-request/sfr-123` | `ec2:spot-fleet-request:TargetCapacity` |
| `sagemaker` | SageMaker | `endpoint/my-ep/variant/v1` | `sagemaker:variant:DesiredInstanceCount` |
| `kafka` | MSK | `arn:aws:kafka:...` | `kafka:broker-storage:VolumeSize` |
| `custom-resource` | Custom | `https://...` | `custom-resource:ResourceType:Property` |

## Common Patterns

### List all scalable targets for a service
```bash
aws application-autoscaling describe-scalable-targets \
    --service-namespace ecs \
    --query 'ScalableTargets[].{Resource:ResourceId,Min:MinCapacity,Max:MaxCapacity}'
```

### Check recent scaling activities
```bash
aws application-autoscaling describe-scaling-activities \
    --service-namespace ecs \
    --max-items 5 \
    --query 'ScalingActivities[].{Status:StatusCode,Description:Description,Time:StartTime}'
```

### Suspend all scaling for a target
```bash
aws application-autoscaling register-scalable-target \
    --service-namespace ecs \
    --scalable-dimension ecs:service:DesiredCount \
    --resource-id service/my-cluster/my-service \
    --suspended-state '{"DynamicScalingInSuspended":true,"DynamicScalingOutSuspended":true,"ScheduledScalingSuspended":true}'
```
