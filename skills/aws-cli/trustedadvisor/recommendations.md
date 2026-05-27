# Recommendations

### 1.1 `list-recommendations`

Lists Trusted Advisor recommendations. **Paginated operation.**

**Synopsis:**
```bash
aws trustedadvisor list-recommendations \
    [--after-last-updated-at <value>] \
    [--aws-service <value>] \
    [--before-last-updated-at <value>] \
    [--check-identifier <value>] \
    [--pillar <value>] \
    [--source <value>] \
    [--status <value>] \
    [--type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--after-last-updated-at` | No | timestamp | None | Filter recommendations updated after this timestamp |
| `--aws-service` | No | string | None | Filter by AWS service name (2-30 chars) |
| `--before-last-updated-at` | No | timestamp | None | Filter recommendations updated before this timestamp |
| `--check-identifier` | No | string | None | Filter by check ARN (pattern: `^arn:[\w-]+:trustedadvisor:::check/[\w-]+$`) |
| `--pillar` | No | string | None | Filter by pillar: `cost_optimizing`, `performance`, `security`, `service_limits`, `fault_tolerance`, `operational_excellence` |
| `--source` | No | string | None | Filter by source: `aws_config`, `compute_optimizer`, `cost_explorer`, `lse`, `manual`, `pse`, `rds`, `resilience`, `resilience_hub`, `security_hub`, `stir`, `ta_check`, `well_architected` |
| `--status` | No | string | None | Filter by status: `ok`, `warning`, `error` |
| `--type` | No | string | None | Filter by type: `standard`, `priority` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "nextToken": "string",
    "recommendationSummaries": [
        {
            "arn": "string",
            "awsServices": ["string"],
            "checkArn": "string",
            "createdAt": "timestamp",
            "id": "string",
            "lastUpdatedAt": "timestamp",
            "lifecycleStage": "in_progress|pending_response|dismissed|resolved",
            "name": "string",
            "pillarSpecificAggregates": {
                "costOptimizing": {
                    "estimatedMonthlySavings": "double",
                    "estimatedPercentMonthlySavings": "double"
                }
            },
            "pillars": ["cost_optimizing|performance|security|service_limits|fault_tolerance|operational_excellence"],
            "resourcesAggregates": {
                "errorCount": "long",
                "okCount": "long",
                "warningCount": "long"
            },
            "source": "string",
            "status": "ok|warning|error",
            "type": "standard|priority"
        }
    ]
}
```

---

### 1.2 `get-recommendation`

Gets a specific Trusted Advisor recommendation by its identifier.

**Synopsis:**
```bash
aws trustedadvisor get-recommendation \
    --recommendation-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recommendation-identifier` | **Yes** | string | -- | The recommendation ARN (pattern: `^arn:[\w-]+:trustedadvisor::\d{12}:recommendation/[\w-]+$`) |

**Output Schema:**
```json
{
    "recommendation": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "id": "string",
        "status": "ok|warning|error",
        "type": "standard|priority",
        "source": "string",
        "pillars": ["string"],
        "awsServices": ["string"],
        "checkArn": "string",
        "resourcesAggregates": {
            "errorCount": "long",
            "okCount": "long",
            "warningCount": "long"
        },
        "pillarSpecificAggregates": {
            "costOptimizing": {
                "estimatedMonthlySavings": "double",
                "estimatedPercentMonthlySavings": "double"
            }
        },
        "lastUpdatedAt": "timestamp",
        "createdAt": "timestamp",
        "createdBy": "string",
        "resolvedAt": "timestamp",
        "lifecycleStage": "in_progress|pending_response|dismissed|resolved",
        "updateReason": "string",
        "updateReasonCode": "non_critical_account|temporary_account|valid_business_case|other_methods_available|low_priority|not_applicable|other",
        "updatedOnBehalfOf": "string",
        "updatedOnBehalfOfJobTitle": "string"
    }
}
```

---

### 1.3 `list-recommendation-resources`

Lists resources associated with a recommendation. **Paginated operation.**

**Synopsis:**
```bash
aws trustedadvisor list-recommendation-resources \
    --recommendation-identifier <value> \
    [--exclusion-status <value>] \
    [--region-code <value>] \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recommendation-identifier` | **Yes** | string | -- | The recommendation ARN |
| `--exclusion-status` | No | string | None | Filter by exclusion status: `excluded`, `included` |
| `--region-code` | No | string | None | Filter by AWS Region code |
| `--status` | No | string | None | Filter by resource status: `ok`, `warning`, `error` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "nextToken": "string",
    "recommendationResourceSummaries": [
        {
            "arn": "string",
            "id": "string",
            "awsResourceId": "string",
            "lastUpdatedAt": "timestamp",
            "metadata": {
                "string": "string"
            },
            "recommendationArn": "string",
            "regionCode": "string",
            "status": "ok|warning|error",
            "exclusionStatus": "excluded|included"
        }
    ]
}
```

---

### 1.4 `update-recommendation-lifecycle`

Updates the lifecycle stage of a Trusted Advisor recommendation.

**Synopsis:**
```bash
aws trustedadvisor update-recommendation-lifecycle \
    --lifecycle-stage <value> \
    --recommendation-identifier <value> \
    [--update-reason <value>] \
    [--update-reason-code <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lifecycle-stage` | **Yes** | string | -- | New lifecycle stage: `pending_response`, `in_progress`, `dismissed`, `resolved` |
| `--recommendation-identifier` | **Yes** | string | -- | The recommendation ARN |
| `--update-reason` | No | string | None | Reason for the lifecycle change (10-4096 chars) |
| `--update-reason-code` | No | string | None | Reason code: `non_critical_account`, `temporary_account`, `valid_business_case`, `other_methods_available`, `low_priority`, `not_applicable`, `other` |

**Output:** None

---

### 1.5 `batch-update-recommendation-resource-exclusion`

Batch updates the exclusion status of recommendation resources.

**Synopsis:**
```bash
aws trustedadvisor batch-update-recommendation-resource-exclusion \
    --recommendation-resource-exclusions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recommendation-resource-exclusions` | **Yes** | list | -- | List of resource exclusion updates (1-100 items) |

**Exclusion Structure:**
```json
[
    {
        "arn": "string",
        "isExcluded": true|false
    }
]
```

**Output Schema:**
```json
{
    "batchUpdateRecommendationResourceExclusionErrors": [
        {
            "arn": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 1.6 `list-checks`

Lists all available Trusted Advisor checks. **Paginated operation.**

**Synopsis:**
```bash
aws trustedadvisor list-checks \
    [--aws-service <value>] \
    [--language <value>] \
    [--pillar <value>] \
    [--source <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-service` | No | string | None | Filter by AWS service name (2-30 chars) |
| `--language` | No | string | None | Language code: `en`, `ja`, `zh`, `fr`, `de`, `ko`, `zh_TW`, `it`, `es`, `pt_BR`, `id` |
| `--pillar` | No | string | None | Filter by pillar: `cost_optimizing`, `performance`, `security`, `service_limits`, `fault_tolerance`, `operational_excellence` |
| `--source` | No | string | None | Filter by source: `aws_config`, `compute_optimizer`, `cost_explorer`, `lse`, `manual`, `pse`, `rds`, `resilience`, `resilience_hub`, `security_hub`, `stir`, `ta_check`, `well_architected` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "checkSummaries": [
        {
            "arn": "string",
            "awsServices": ["string"],
            "description": "string",
            "id": "string",
            "metadata": {
                "string": "string"
            },
            "name": "string",
            "pillars": ["string"],
            "source": "string"
        }
    ],
    "nextToken": "string"
}
```
