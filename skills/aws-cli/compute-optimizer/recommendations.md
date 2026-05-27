# Recommendations

### 2.1 `get-ec2-instance-recommendations`

Returns EC2 instance recommendations. **Paginated operation.**

**Synopsis:**
```bash
aws compute-optimizer get-ec2-instance-recommendations \
    [--instance-arns <value>] \
    [--filters <value>] \
    [--account-ids <value>] \
    [--recommendation-preferences <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arns` | No | list(string) | None | Specific instance ARNs (up to 1000) |
| `--filters` | No | list | None | Filter results. Shorthand: `name=Finding\|FindingReasonCodes\|RecommendationSourceType\|InferredWorkloadTypes,values=string,string ...` |
| `--account-ids` | No | list(string) | None | Account IDs (for organization-level queries) |
| `--recommendation-preferences` | No | structure | None | Preferences override. Shorthand: `cpuVendorArchitectures=string,string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "instanceRecommendations": [
        {
            "instanceArn": "string",
            "accountId": "string",
            "instanceName": "string",
            "currentInstanceType": "string",
            "finding": "Underprovisioned|Overprovisioned|Optimized|NotOptimized",
            "findingReasonCodes": ["string"],
            "utilizationMetrics": [
                {
                    "name": "Cpu|Memory|EBS_READ_OPS_PER_SECOND|EBS_WRITE_OPS_PER_SECOND|EBS_READ_BYTES_PER_SECOND|EBS_WRITE_BYTES_PER_SECOND|DISK_READ_OPS_PER_SECOND|DISK_WRITE_OPS_PER_SECOND|DISK_READ_BYTES_PER_SECOND|DISK_WRITE_BYTES_PER_SECOND|NETWORK_IN_BYTES_PER_SECOND|NETWORK_OUT_BYTES_PER_SECOND|NETWORK_PACKETS_IN_PER_SECOND|NETWORK_PACKETS_OUT_PER_SECOND|GPU_PERCENTAGE|GPU_MEMORY_PERCENTAGE",
                    "statistic": "Maximum|Average",
                    "value": "double"
                }
            ],
            "lookBackPeriodInDays": "double",
            "recommendationOptions": [
                {
                    "instanceType": "string",
                    "projectedUtilizationMetrics": [],
                    "platformDifferences": ["string"],
                    "performanceRisk": "double",
                    "rank": "integer",
                    "savingsOpportunity": {
                        "savingsOpportunityPercentage": "double",
                        "estimatedMonthlySavings": {
                            "currency": "USD",
                            "value": "double"
                        }
                    },
                    "migrationEffort": "VeryLow|Low|Medium|High"
                }
            ],
            "recommendationSources": [
                {
                    "recommendationSourceArn": "string",
                    "recommendationSourceType": "string"
                }
            ],
            "lastRefreshTimestamp": "timestamp",
            "currentPerformanceRisk": "VeryLow|Low|Medium|High",
            "effectiveRecommendationPreferences": {},
            "inferredWorkloadTypes": ["string"],
            "idle": "True|False",
            "tags": [
                {
                    "key": "string",
                    "value": "string"
                }
            ]
        }
    ],
    "nextToken": "string",
    "errors": [
        {
            "identifier": "string",
            "code": "string",
            "message": "string"
        }
    ]
}
```

---

### 2.2 `get-ec2-recommendation-projected-metrics`

Returns the projected utilization metrics for an EC2 instance recommendation.

**Synopsis:**
```bash
aws compute-optimizer get-ec2-recommendation-projected-metrics \
    --instance-arn <value> \
    --stat <value> \
    --period <value> \
    --start-time <value> \
    --end-time <value> \
    [--recommendation-preferences <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the EC2 instance |
| `--stat` | **Yes** | string | -- | Statistic: `Maximum` or `Average` |
| `--period` | **Yes** | integer | -- | Granularity in seconds (60, 300, 3600, 86400) |
| `--start-time` | **Yes** | timestamp | -- | Start time for projected metrics |
| `--end-time` | **Yes** | timestamp | -- | End time for projected metrics |
| `--recommendation-preferences` | No | structure | None | Preferences override |

**Output Schema:**
```json
{
    "recommendedOptionProjectedMetrics": [
        {
            "recommendedInstanceType": "string",
            "rank": "integer",
            "projectedMetrics": [
                {
                    "name": "string",
                    "timestamps": ["timestamp"],
                    "values": ["double"]
                }
            ]
        }
    ]
}
```

---

### 2.3 `get-auto-scaling-group-recommendations`

Returns Auto Scaling group recommendations. **Paginated operation.**

**Synopsis:**
```bash
aws compute-optimizer get-auto-scaling-group-recommendations \
    [--auto-scaling-group-arns <value>] \
    [--filters <value>] \
    [--account-ids <value>] \
    [--recommendation-preferences <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-arns` | No | list(string) | None | Specific ASG ARNs |
| `--filters` | No | list | None | Filter results |
| `--account-ids` | No | list(string) | None | Account IDs |
| `--recommendation-preferences` | No | structure | None | Preferences override |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "autoScalingGroupRecommendations": [
        {
            "accountId": "string",
            "autoScalingGroupArn": "string",
            "autoScalingGroupName": "string",
            "finding": "Underprovisioned|Overprovisioned|Optimized|NotOptimized",
            "utilizationMetrics": [],
            "lookBackPeriodInDays": "double",
            "currentConfiguration": {
                "desiredCapacity": "integer",
                "minSize": "integer",
                "maxSize": "integer",
                "instanceType": "string"
            },
            "recommendationOptions": [
                {
                    "configuration": {
                        "desiredCapacity": "integer",
                        "minSize": "integer",
                        "maxSize": "integer",
                        "instanceType": "string"
                    },
                    "projectedUtilizationMetrics": [],
                    "performanceRisk": "double",
                    "rank": "integer",
                    "savingsOpportunity": {},
                    "migrationEffort": "VeryLow|Low|Medium|High"
                }
            ],
            "lastRefreshTimestamp": "timestamp",
            "currentPerformanceRisk": "string",
            "inferredWorkloadTypes": ["string"]
        }
    ],
    "nextToken": "string",
    "errors": []
}
```

---

### 2.4 `get-ebs-volume-recommendations`

Returns EBS volume recommendations. **Paginated operation.**

**Synopsis:**
```bash
aws compute-optimizer get-ebs-volume-recommendations \
    [--volume-arns <value>] \
    [--filters <value>] \
    [--account-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--volume-arns` | No | list(string) | None | Specific EBS volume ARNs |
| `--filters` | No | list | None | Filter results |
| `--account-ids` | No | list(string) | None | Account IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "volumeRecommendations": [
        {
            "volumeArn": "string",
            "accountId": "string",
            "currentConfiguration": {
                "volumeType": "string",
                "volumeSize": "integer",
                "volumeBaselineIOPS": "integer",
                "volumeBurstIOPS": "integer",
                "volumeBaselineThroughput": "integer",
                "volumeBurstThroughput": "integer",
                "rootVolume": true|false
            },
            "finding": "Optimized|NotOptimized",
            "utilizationMetrics": [],
            "lookBackPeriodInDays": "double",
            "volumeRecommendationOptions": [
                {
                    "configuration": {
                        "volumeType": "string",
                        "volumeSize": "integer",
                        "volumeBaselineIOPS": "integer",
                        "volumeBurstIOPS": "integer",
                        "volumeBaselineThroughput": "integer",
                        "volumeBurstThroughput": "integer"
                    },
                    "performanceRisk": "double",
                    "rank": "integer",
                    "savingsOpportunity": {}
                }
            ],
            "lastRefreshTimestamp": "timestamp",
            "currentPerformanceRisk": "string",
            "tags": []
        }
    ],
    "nextToken": "string",
    "errors": []
}
```

---

### 2.5 `get-lambda-function-recommendations`

Returns Lambda function recommendations. **Paginated operation.**

**Synopsis:**
```bash
aws compute-optimizer get-lambda-function-recommendations \
    [--function-arns <value>] \
    [--filters <value>] \
    [--account-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-arns` | No | list(string) | None | Specific Lambda function ARNs |
| `--filters` | No | list | None | Filter results |
| `--account-ids` | No | list(string) | None | Account IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "lambdaFunctionRecommendations": [
        {
            "functionArn": "string",
            "functionVersion": "string",
            "accountId": "string",
            "currentMemorySize": "integer",
            "numberOfInvocations": "long",
            "utilizationMetrics": [
                {
                    "name": "Duration|Memory",
                    "statistic": "Maximum|Average",
                    "value": "double"
                }
            ],
            "lookbackPeriodInDays": "double",
            "lastRefreshTimestamp": "timestamp",
            "finding": "Optimized|NotOptimized|Unavailable",
            "findingReasonCodes": ["string"],
            "memorySizeRecommendationOptions": [
                {
                    "rank": "integer",
                    "memorySize": "integer",
                    "projectedUtilizationMetrics": [],
                    "savingsOpportunity": {}
                }
            ],
            "currentPerformanceRisk": "string",
            "tags": []
        }
    ],
    "nextToken": "string"
}
```

---

### 2.6 `get-ecs-service-recommendations`

Returns ECS service (Fargate) recommendations. **Paginated operation.**

**Synopsis:**
```bash
aws compute-optimizer get-ecs-service-recommendations \
    [--service-arns <value>] \
    [--filters <value>] \
    [--account-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arns` | No | list(string) | None | Specific ECS service ARNs |
| `--filters` | No | list | None | Filter results |
| `--account-ids` | No | list(string) | None | Account IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ecsServiceRecommendations": [
        {
            "serviceArn": "string",
            "accountId": "string",
            "currentServiceConfiguration": {
                "memory": "integer",
                "cpu": "integer",
                "containerConfigurations": [
                    {
                        "containerName": "string",
                        "memorySizeConfiguration": {
                            "memory": "integer",
                            "memoryReservation": "integer"
                        },
                        "cpu": "integer"
                    }
                ],
                "autoScalingConfiguration": "TargetTrackingScalingCpu|TargetTrackingScalingMemory|None",
                "taskDefinitionArn": "string"
            },
            "utilizationMetrics": [],
            "lookbackPeriodInDays": "double",
            "launchType": "EC2|Fargate",
            "lastRefreshTimestamp": "timestamp",
            "finding": "Optimized|Underprovisioned|Overprovisioned",
            "findingReasonCodes": ["string"],
            "serviceRecommendationOptions": [
                {
                    "memory": "integer",
                    "cpu": "integer",
                    "savingsOpportunity": {},
                    "projectedUtilizationMetrics": [],
                    "containerRecommendations": []
                }
            ],
            "currentPerformanceRisk": "string",
            "tags": []
        }
    ],
    "nextToken": "string",
    "errors": []
}
```

---

### 2.7 `get-ecs-service-projected-metrics`

Returns projected metrics for an ECS service recommendation.

**Synopsis:**
```bash
aws compute-optimizer get-ecs-service-projected-metrics \
    --service-arn <value> \
    --stat <value> \
    --period <value> \
    --start-time <value> \
    --end-time <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arn` | **Yes** | string | -- | ARN of the ECS service |
| `--stat` | **Yes** | string | -- | Statistic: `Maximum` or `Average` |
| `--period` | **Yes** | integer | -- | Granularity in seconds |
| `--start-time` | **Yes** | timestamp | -- | Start time |
| `--end-time` | **Yes** | timestamp | -- | End time |

**Output Schema:**
```json
{
    "recommendedOptionProjectedMetrics": [
        {
            "projectedMetrics": [
                {
                    "name": "string",
                    "timestamps": ["timestamp"],
                    "upperBoundValues": ["double"],
                    "lowerBoundValues": ["double"]
                }
            ]
        }
    ]
}
```

---

### 2.8 `get-rds-database-recommendations`

Returns RDS DB instance recommendations. **Paginated operation.**

**Synopsis:**
```bash
aws compute-optimizer get-rds-database-recommendations \
    [--resource-arns <value>] \
    [--filters <value>] \
    [--account-ids <value>] \
    [--recommendation-preferences <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arns` | No | list(string) | None | Specific RDS instance ARNs |
| `--filters` | No | list | None | Filter results |
| `--account-ids` | No | list(string) | None | Account IDs |
| `--recommendation-preferences` | No | structure | None | Preferences override |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "rdsDBRecommendations": [
        {
            "resourceArn": "string",
            "accountId": "string",
            "engine": "string",
            "engineVersion": "string",
            "currentDBInstanceClass": "string",
            "currentStorageConfiguration": {
                "storageType": "string",
                "allocatedStorage": "integer",
                "iops": "integer",
                "maxAllocatedStorage": "integer",
                "storageThroughput": "integer"
            },
            "idle": "True|False",
            "finding": "Optimized|Underprovisioned|Overprovisioned",
            "findingReasonCodes": ["string"],
            "instanceRecommendationOptions": [
                {
                    "dbInstanceClass": "string",
                    "projectedUtilizationMetrics": [],
                    "performanceRisk": "double",
                    "rank": "integer",
                    "savingsOpportunity": {}
                }
            ],
            "storageRecommendationOptions": [
                {
                    "storageConfiguration": {},
                    "rank": "integer",
                    "savingsOpportunity": {}
                }
            ],
            "utilizationMetrics": [],
            "lastRefreshTimestamp": "timestamp",
            "lookbackPeriodInDays": "double",
            "tags": []
        }
    ],
    "nextToken": "string",
    "errors": []
}
```

---

### 2.9 `get-rds-database-recommendation-projected-metrics`

Returns projected metrics for an RDS DB instance recommendation.

**Synopsis:**
```bash
aws compute-optimizer get-rds-database-recommendation-projected-metrics \
    --resource-arn <value> \
    --stat <value> \
    --period <value> \
    --start-time <value> \
    --end-time <value> \
    [--recommendation-preferences <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the RDS DB instance |
| `--stat` | **Yes** | string | -- | Statistic: `Maximum` or `Average` |
| `--period` | **Yes** | integer | -- | Granularity in seconds |
| `--start-time` | **Yes** | timestamp | -- | Start time |
| `--end-time` | **Yes** | timestamp | -- | End time |
| `--recommendation-preferences` | No | structure | None | Preferences override |

**Output Schema:**
```json
{
    "recommendedOptionProjectedMetrics": [
        {
            "recommendedDBInstanceClass": "string",
            "rank": "integer",
            "projectedMetrics": [
                {
                    "name": "string",
                    "timestamps": ["timestamp"],
                    "values": ["double"]
                }
            ]
        }
    ]
}
```

---

### 2.10 `get-idle-recommendations`

Returns recommendations for idle resources. **Paginated operation.**

**Synopsis:**
```bash
aws compute-optimizer get-idle-recommendations \
    [--resource-arns <value>] \
    [--filters <value>] \
    [--account-ids <value>] \
    [--order-by <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arns` | No | list(string) | None | Specific resource ARNs |
| `--filters` | No | list | None | Filter results |
| `--account-ids` | No | list(string) | None | Account IDs |
| `--order-by` | No | structure | None | Sort results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "idleRecommendations": [
        {
            "resourceArn": "string",
            "resourceId": "string",
            "resourceType": "string",
            "accountId": "string",
            "finding": "Idle",
            "findingDescription": "string",
            "savingsOpportunity": {
                "savingsOpportunityPercentage": "double",
                "estimatedMonthlySavings": {
                    "currency": "USD",
                    "value": "double"
                }
            },
            "utilizationMetrics": [],
            "lookBackPeriodInDays": "double",
            "lastRefreshTimestamp": "timestamp",
            "tags": []
        }
    ],
    "nextToken": "string",
    "errors": []
}
```

---

### 2.11 `get-recommendation-summaries`

Returns a summary of recommendations by resource type. **Paginated operation.**

**Synopsis:**
```bash
aws compute-optimizer get-recommendation-summaries \
    [--account-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-ids` | No | list(string) | None | Account IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "recommendationSummaries": [
        {
            "summaries": [
                {
                    "name": "Underprovisioned|Overprovisioned|Optimized|NotOptimized",
                    "value": "double",
                    "reasonCodeSummaries": []
                }
            ],
            "recommendationResourceType": "Ec2Instance|AutoScalingGroup|EbsVolume|LambdaFunction|EcsService|RdsDBInstance|IdleResource",
            "accountId": "string",
            "savingsOpportunity": {
                "savingsOpportunityPercentage": "double",
                "estimatedMonthlySavings": {
                    "currency": "USD",
                    "value": "double"
                }
            },
            "currentPerformanceRiskRatings": {
                "high": "long",
                "medium": "long",
                "low": "long",
                "veryLow": "long"
            },
            "inferredWorkloadSavings": []
        }
    ],
    "nextToken": "string"
}
```

---

### 2.12 `describe-recommendation-export-jobs`

Describes recommendation export jobs. **Paginated operation.**

**Synopsis:**
```bash
aws compute-optimizer describe-recommendation-export-jobs \
    [--job-ids <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-ids` | No | list(string) | None | Specific export job IDs |
| `--filters` | No | list | None | Filter by resource type or status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "recommendationExportJobs": [
        {
            "jobId": "string",
            "destination": {
                "s3": {
                    "bucket": "string",
                    "key": "string",
                    "metadataKey": "string"
                }
            },
            "resourceType": "Ec2Instance|AutoScalingGroup|EbsVolume|LambdaFunction|EcsService|RdsDBInstance|IdleResource",
            "status": "Queued|InProgress|Complete|Failed",
            "creationTimestamp": "timestamp",
            "lastUpdatedTimestamp": "timestamp",
            "failureReason": "string"
        }
    ],
    "nextToken": "string"
}
```
