# Coverage & Tags

### 12.1 `list-coverage`

Lists coverage details for GuardDuty runtime monitoring. Returns information about monitored resources. **Paginated operation.**

**Synopsis:**
```bash
aws guardduty list-coverage \
    --detector-id <value> \
    [--filter-criteria <value>] \
    [--sort-criteria <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--filter-criteria` | No | structure | None | Criteria for filtering coverage results |
| `--sort-criteria` | No | structure | None | Sort criteria for results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Criteria Structure:**
```json
{
    "FilterCriterion": [
        {
            "CriterionKey": "ACCOUNT_ID|CLUSTER_NAME|RESOURCE_TYPE|COVERAGE_STATUS|ADDON_VERSION|MANAGEMENT_TYPE|EKS_CLUSTER_NAME|ECS_CLUSTER_NAME|AGENT_VERSION|INSTANCE_ID|CLUSTER_ARN",
            "FilterCondition": {
                "Equals": ["string"],
                "NotEquals": ["string"]
            }
        }
    ]
}
```

**Output Schema:**
```json
{
    "Resources": [
        {
            "ResourceId": "string",
            "DetectorId": "string",
            "AccountId": "string",
            "ResourceDetails": {
                "EksClusterDetails": {
                    "ClusterName": "string",
                    "CoveredNodes": "long",
                    "CompatibleNodes": "long",
                    "AddonDetails": {
                        "AddonVersion": "string",
                        "AddonStatus": "string"
                    },
                    "ManagementType": "AUTO_MANAGED|MANUAL|DISABLED"
                },
                "ResourceType": "EKS|ECS|EC2",
                "EcsClusterDetails": {
                    "ClusterName": "string",
                    "FargateDetails": {
                        "Issues": ["string"],
                        "ManagementType": "AUTO_MANAGED|MANUAL|DISABLED"
                    },
                    "ContainerInstanceDetails": {
                        "CoveredContainerInstances": "long",
                        "CompatibleContainerInstances": "long"
                    }
                },
                "Ec2InstanceDetails": {
                    "InstanceId": "string",
                    "InstanceType": "string",
                    "ClusterArn": "string",
                    "AgentDetails": {
                        "Version": "string"
                    },
                    "ManagementType": "AUTO_MANAGED|MANUAL|DISABLED"
                }
            },
            "CoverageStatus": "HEALTHY|UNHEALTHY",
            "Issue": "string",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 12.2 `get-coverage-statistics`

Retrieves aggregated statistics for GuardDuty coverage.

**Synopsis:**
```bash
aws guardduty get-coverage-statistics \
    --detector-id <value> \
    --statistics-type <value> \
    [--filter-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--statistics-type` | **Yes** | list(string) | -- | Statistics types: `COUNT_BY_RESOURCE_TYPE`, `COUNT_BY_COVERAGE_STATUS` |
| `--filter-criteria` | No | structure | None | Criteria for filtering coverage |

**Output Schema:**
```json
{
    "CoverageStatistics": {
        "CountByResourceType": {
            "string": "long"
        },
        "CountByCoverageStatus": {
            "string": "long"
        }
    }
}
```

---

### 12.3 `get-usage-statistics`

Lists Amazon GuardDuty usage statistics over the last 30 days.

**Synopsis:**
```bash
aws guardduty get-usage-statistics \
    --detector-id <value> \
    --usage-statistic-type <value> \
    --usage-criteria <value> \
    [--unit <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--usage-statistic-type` | **Yes** | string | -- | Statistic type: `SUM_BY_ACCOUNT`, `SUM_BY_DATA_SOURCE`, `SUM_BY_RESOURCE`, `TOP_RESOURCES`, `SUM_BY_FEATURES`, `TOP_ACCOUNTS_BY_FEATURE` |
| `--usage-criteria` | **Yes** | structure | -- | Criteria for filtering usage statistics |
| `--unit` | No | string | None | Currency unit for cost |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Usage Criteria Structure:**
```json
{
    "AccountIds": ["string"],
    "DataSources": ["FLOW_LOGS|CLOUD_TRAIL|DNS_LOGS|S3_LOGS|KUBERNETES_AUDIT_LOGS|EC2_MALWARE_SCAN"],
    "Resources": ["string"],
    "Features": ["FLOW_LOGS|CLOUD_TRAIL|DNS_LOGS|S3_DATA_EVENTS|EKS_AUDIT_LOGS|EBS_MALWARE_PROTECTION|RDS_LOGIN_EVENTS|LAMBDA_NETWORK_LOGS|EKS_RUNTIME_MONITORING|FARGATE_RUNTIME_MONITORING|EC2_RUNTIME_MONITORING|RDS_DBI_PROTECTION_PROVISIONED|RDS_DBI_PROTECTION_SERVERLESS"]
}
```

**Output Schema:**
```json
{
    "UsageStatistics": {
        "SumByAccount": [
            {
                "AccountId": "string",
                "Total": {
                    "Amount": "string",
                    "Unit": "string"
                }
            }
        ],
        "SumByDataSource": [
            {
                "DataSource": "string",
                "Total": {
                    "Amount": "string",
                    "Unit": "string"
                }
            }
        ],
        "SumByResource": [
            {
                "Resource": "string",
                "Total": {
                    "Amount": "string",
                    "Unit": "string"
                }
            }
        ],
        "TopResources": [
            {
                "Resource": "string",
                "Total": {
                    "Amount": "string",
                    "Unit": "string"
                }
            }
        ],
        "SumByFeature": [
            {
                "Feature": "string",
                "Total": {
                    "Amount": "string",
                    "Unit": "string"
                }
            }
        ],
        "TopAccountsByFeature": [
            {
                "Feature": "string",
                "Accounts": [
                    {
                        "AccountId": "string",
                        "Total": {
                            "Amount": "string",
                            "Unit": "string"
                        }
                    }
                ]
            }
        ]
    },
    "NextToken": "string"
}
```

---

### 12.4 `tag-resource`

Adds tags to a GuardDuty resource.

**Synopsis:**
```bash
aws guardduty tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags to add (key-value pairs, max 200) |

**Output:** None (HTTP 200 on success)

---

### 12.5 `untag-resource`

Removes tags from a GuardDuty resource.

**Synopsis:**
```bash
aws guardduty untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None (HTTP 200 on success)

---

### 12.6 `list-tags-for-resource`

Lists tags for a GuardDuty resource.

**Synopsis:**
```bash
aws guardduty list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "Tags": {
        "string": "string"
    }
}
```
