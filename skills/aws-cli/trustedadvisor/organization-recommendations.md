# Organization Recommendations

### 2.1 `list-organization-recommendations`

Lists organization-level Trusted Advisor recommendations. Must be called from the management account or a delegated administrator. **Paginated operation.**

**Synopsis:**
```bash
aws trustedadvisor list-organization-recommendations \
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
| `--check-identifier` | No | string | None | Filter by check ARN |
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
    "organizationRecommendationSummaries": [
        {
            "arn": "string",
            "name": "string",
            "awsServices": ["string"],
            "checkArn": "string",
            "createdAt": "timestamp",
            "id": "string",
            "lastUpdatedAt": "timestamp",
            "lifecycleStage": "in_progress|pending_response|dismissed|resolved",
            "pillars": ["cost_optimizing|performance|security|service_limits|fault_tolerance|operational_excellence"],
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
            "source": "string",
            "status": "ok|warning|error",
            "type": "standard|priority"
        }
    ]
}
```

---

### 2.2 `get-organization-recommendation`

Gets a specific organization-level Trusted Advisor recommendation.

**Synopsis:**
```bash
aws trustedadvisor get-organization-recommendation \
    --organization-recommendation-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-recommendation-identifier` | **Yes** | string | -- | The organization recommendation ARN (pattern: `^arn:[\w-]+:trustedadvisor:::organization-recommendation/[\w-]+$`) |

**Output Schema:**
```json
{
    "organizationRecommendation": {
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

### 2.3 `list-organization-recommendation-accounts`

Lists accounts associated with an organization recommendation. **Paginated operation.**

**Synopsis:**
```bash
aws trustedadvisor list-organization-recommendation-accounts \
    --organization-recommendation-identifier <value> \
    [--affected-account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-recommendation-identifier` | **Yes** | string | -- | The organization recommendation ARN |
| `--affected-account-id` | No | string | None | Filter by specific account ID (12 digits) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "accountRecommendationLifecycleSummaries": [
        {
            "accountId": "string",
            "accountRecommendationArn": "string",
            "lifecycleStage": "in_progress|pending_response|dismissed|resolved",
            "updateReason": "string",
            "updateReasonCode": "non_critical_account|temporary_account|valid_business_case|other_methods_available|low_priority|not_applicable|other",
            "lastUpdatedAt": "timestamp",
            "updatedOnBehalfOf": "string",
            "updatedOnBehalfOfJobTitle": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.4 `list-organization-recommendation-resources`

Lists resources associated with an organization recommendation. **Paginated operation.**

**Synopsis:**
```bash
aws trustedadvisor list-organization-recommendation-resources \
    --organization-recommendation-identifier <value> \
    [--affected-account-id <value>] \
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
| `--organization-recommendation-identifier` | **Yes** | string | -- | The organization recommendation ARN |
| `--affected-account-id` | No | string | None | Filter by specific account ID (12 digits) |
| `--exclusion-status` | No | string | None | Filter by exclusion status: `excluded`, `included` |
| `--region-code` | No | string | None | Filter by AWS Region code |
| `--status` | No | string | None | Filter by resource status: `ok`, `warning`, `error` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "organizationRecommendationResourceSummaries": [
        {
            "arn": "string",
            "awsResourceId": "string",
            "id": "string",
            "lastUpdatedAt": "timestamp",
            "metadata": {
                "string": "string"
            },
            "recommendationArn": "string",
            "regionCode": "string",
            "status": "ok|warning|error",
            "accountId": "string",
            "exclusionStatus": "excluded|included"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.5 `update-organization-recommendation-lifecycle`

Updates the lifecycle stage of an organization-level Trusted Advisor recommendation.

**Synopsis:**
```bash
aws trustedadvisor update-organization-recommendation-lifecycle \
    --lifecycle-stage <value> \
    --organization-recommendation-identifier <value> \
    [--update-reason <value>] \
    [--update-reason-code <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lifecycle-stage` | **Yes** | string | -- | New lifecycle stage: `pending_response`, `in_progress`, `dismissed`, `resolved` |
| `--organization-recommendation-identifier` | **Yes** | string | -- | The organization recommendation ARN |
| `--update-reason` | No | string | None | Reason for the lifecycle change (10-4096 chars) |
| `--update-reason-code` | No | string | None | Reason code: `non_critical_account`, `temporary_account`, `valid_business_case`, `other_methods_available`, `low_priority`, `not_applicable`, `other` |

**Output:** None
