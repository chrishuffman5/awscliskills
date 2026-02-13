# Preferences

### 4.1 `get-effective-recommendation-preferences`

Returns the effective recommendation preferences for a specific resource (combines account, organization, and resource-level settings).

**Synopsis:**
```bash
aws compute-optimizer get-effective-recommendation-preferences \
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
    "enhancedInfrastructureMetrics": "Active|Inactive",
    "externalMetricsPreference": {
        "source": "Datadog|Dynatrace|NewRelic|Instana"
    },
    "lookBackPeriod": "DAYS_14|DAYS_32|DAYS_93",
    "utilizationPreferences": [
        {
            "metricName": "CpuOverprovisioned|MemoryOverprovisioned",
            "metricParameters": {
                "threshold": "P90|P95|P99_5",
                "headroom": "PERCENT_30|PERCENT_20|PERCENT_10|PERCENT_0"
            }
        }
    ],
    "preferredResources": [
        {
            "name": "Ec2InstanceTypes",
            "includeList": ["string"],
            "excludeList": ["string"]
        }
    ]
}
```

---

### 4.2 `get-recommendation-preferences`

Returns recommendation preferences. **Paginated operation.**

**Synopsis:**
```bash
aws compute-optimizer get-recommendation-preferences \
    --resource-type <value> \
    [--scope <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | Resource type: `Ec2Instance`, `AutoScalingGroup`, `EbsVolume`, `LambdaFunction`, `EcsService`, `RdsDBInstance` |
| `--scope` | No | structure | None | Scope filter. Shorthand: `name=Organization\|AccountId\|ResourceArn,value=string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "recommendationPreferencesDetails": [
        {
            "scope": {
                "name": "Organization|AccountId|ResourceArn",
                "value": "string"
            },
            "resourceType": "string",
            "enhancedInfrastructureMetrics": "Active|Inactive",
            "inferredWorkloadTypes": "Active|Inactive",
            "externalMetricsPreference": {
                "source": "Datadog|Dynatrace|NewRelic|Instana"
            },
            "lookBackPeriod": "DAYS_14|DAYS_32|DAYS_93",
            "utilizationPreferences": [],
            "preferredResources": []
        }
    ],
    "nextToken": "string"
}
```

---

### 4.3 `put-recommendation-preferences`

Creates or updates recommendation preferences for a resource type at the specified scope.

**Synopsis:**
```bash
aws compute-optimizer put-recommendation-preferences \
    --resource-type <value> \
    [--scope <value>] \
    [--enhanced-infrastructure-metrics <value>] \
    [--inferred-workload-types <value>] \
    [--external-metrics-preference <value>] \
    [--look-back-period <value>] \
    [--utilization-preferences <value>] \
    [--preferred-resources <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | Resource type: `Ec2Instance`, `AutoScalingGroup`, `EbsVolume`, `LambdaFunction`, `EcsService`, `RdsDBInstance` |
| `--scope` | No | structure | None | Scope. Shorthand: `name=Organization\|AccountId\|ResourceArn,value=string` |
| `--enhanced-infrastructure-metrics` | No | string | None | Enable extended metrics: `Active` or `Inactive` |
| `--inferred-workload-types` | No | string | None | Inferred workload type recommendations: `Active` or `Inactive` |
| `--external-metrics-preference` | No | structure | None | External monitoring tool. Shorthand: `source=Datadog\|Dynatrace\|NewRelic\|Instana` |
| `--look-back-period` | No | string | None | Look-back period: `DAYS_14`, `DAYS_32`, `DAYS_93` |
| `--utilization-preferences` | No | list | None | Utilization threshold preferences |
| `--preferred-resources` | No | list | None | Preferred or excluded instance types |

**Output Schema:**
```json
{}
```

---

### 4.4 `delete-recommendation-preferences`

Deletes recommendation preferences for a resource type at the specified scope.

**Synopsis:**
```bash
aws compute-optimizer delete-recommendation-preferences \
    --resource-type <value> \
    --recommendation-preference-names <value> \
    [--scope <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | Resource type |
| `--recommendation-preference-names` | **Yes** | list(string) | -- | Preference names to delete: `EnhancedInfrastructureMetrics`, `InferredWorkloadTypes`, `ExternalMetricsPreference`, `LookBackPeriodPreference`, `PreferredResources`, `UtilizationPreferences` |
| `--scope` | No | structure | None | Scope. Shorthand: `name=Organization\|AccountId\|ResourceArn,value=string` |

**Output Schema:**
```json
{}
```
