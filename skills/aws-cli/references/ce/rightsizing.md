# Rightsizing

### 6.1 `get-rightsizing-recommendation`

Gets rightsizing recommendations for EC2 instances, identifying instances that are underutilized and recommending modifications or terminations. **Paginated.**

**Synopsis:**
```bash
aws ce get-rightsizing-recommendation \
    --service <value> \
    [--filter <value>] \
    [--configuration <value>] \
    [--page-size <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service` | **Yes** | string | -- | Only valid value: `AmazonEC2` |
| `--filter` | No | structure | None | Filter by `LINKED_ACCOUNT`, `REGION`, `RIGHTSIZING_TYPE`. OR and NOT unsupported |
| `--configuration` | No | structure | None | Recommendation configuration |
| `--page-size` | No | integer | None | Items per API call |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Configuration Structure:**
```json
{
    "RecommendationTarget": "SAME_INSTANCE_FAMILY|CROSS_INSTANCE_FAMILY",
    "BenefitsConsidered": true|false
}
```

- `RecommendationTarget`: Whether to consider instances from same family only or cross-family
- `BenefitsConsidered`: Whether to factor in RI/Savings Plans discounts

**Output Schema:**
```json
{
    "Metadata": {
        "RecommendationId": "string",
        "GenerationTimestamp": "string",
        "LookbackPeriodInDays": "SEVEN_DAYS|THIRTY_DAYS|SIXTY_DAYS",
        "AdditionalMetadata": "string"
    },
    "Summary": {
        "TotalRecommendationCount": "string",
        "EstimatedTotalMonthlySavingsAmount": "string",
        "SavingsCurrencyCode": "string",
        "SavingsPercentage": "string"
    },
    "RightsizingRecommendations": [
        {
            "AccountId": "string",
            "CurrentInstance": {
                "ResourceId": "string",
                "InstanceName": "string",
                "Tags": [],
                "ResourceDetails": {
                    "EC2ResourceDetails": {
                        "HourlyOnDemandRate": "string",
                        "InstanceType": "string",
                        "Platform": "string",
                        "Region": "string",
                        "Sku": "string",
                        "Memory": "string",
                        "NetworkPerformance": "string",
                        "Storage": "string",
                        "Vcpu": "string"
                    }
                },
                "ResourceUtilization": {
                    "EC2ResourceUtilization": {
                        "MaxCpuUtilizationPercentage": "string",
                        "MaxMemoryUtilizationPercentage": "string",
                        "MaxStorageUtilizationPercentage": "string",
                        "EBSResourceUtilization": {
                            "EbsReadOpsPerSecond": "string",
                            "EbsWriteOpsPerSecond": "string",
                            "EbsReadBytesPerSecond": "string",
                            "EbsWriteBytesPerSecond": "string"
                        },
                        "DiskResourceUtilization": {
                            "DiskReadOpsPerSecond": "string",
                            "DiskWriteOpsPerSecond": "string",
                            "DiskReadBytesPerSecond": "string",
                            "DiskWriteBytesPerSecond": "string"
                        },
                        "NetworkResourceUtilization": {
                            "NetworkInBytesPerSecond": "string",
                            "NetworkOutBytesPerSecond": "string",
                            "NetworkPacketsInPerSecond": "string",
                            "NetworkPacketsOutPerSecond": "string"
                        }
                    }
                },
                "ReservationCoveredHoursInLookbackPeriod": "string",
                "SavingsPlansCoveredHoursInLookbackPeriod": "string",
                "OnDemandHoursInLookbackPeriod": "string",
                "TotalRunningHoursInLookbackPeriod": "string",
                "MonthlyCost": "string",
                "CurrencyCode": "string"
            },
            "RightsizingType": "TERMINATE|MODIFY",
            "ModifyRecommendationDetail": {
                "TargetInstances": [
                    {
                        "EstimatedMonthlyCost": "string",
                        "EstimatedMonthlySavings": "string",
                        "CurrencyCode": "string",
                        "DefaultTargetInstance": "boolean",
                        "ResourceDetails": {
                            "EC2ResourceDetails": {}
                        },
                        "ExpectedResourceUtilization": {
                            "EC2ResourceUtilization": {}
                        },
                        "PlatformDifferences": [
                            "HYPERVISOR|NETWORK_INTERFACE|STORAGE_INTERFACE|INSTANCE_STORE_AVAILABILITY|VIRTUALIZATION_TYPE"
                        ]
                    }
                ]
            },
            "TerminateRecommendationDetail": {
                "EstimatedMonthlySavings": "string",
                "CurrencyCode": "string"
            },
            "FindingReasonCodes": [
                "CPU_OVER_PROVISIONED|CPU_UNDER_PROVISIONED|MEMORY_OVER_PROVISIONED|MEMORY_UNDER_PROVISIONED|EBS_THROUGHPUT_OVER_PROVISIONED|EBS_THROUGHPUT_UNDER_PROVISIONED|EBS_IOPS_OVER_PROVISIONED|EBS_IOPS_UNDER_PROVISIONED|NETWORK_BANDWIDTH_OVER_PROVISIONED|NETWORK_BANDWIDTH_UNDER_PROVISIONED|NETWORK_PPS_OVER_PROVISIONED|NETWORK_PPS_UNDER_PROVISIONED|DISK_IOPS_OVER_PROVISIONED|DISK_IOPS_UNDER_PROVISIONED|DISK_THROUGHPUT_OVER_PROVISIONED|DISK_THROUGHPUT_UNDER_PROVISIONED"
            ]
        }
    ],
    "NextPageToken": "string",
    "Configuration": {
        "RecommendationTarget": "SAME_INSTANCE_FAMILY|CROSS_INSTANCE_FAMILY",
        "BenefitsConsidered": "boolean"
    }
}
```
