# Quotas

### 1.1 `get-service-quota`

Retrieves the applied value for the specified quota. The applied value is the quota value that is actually in effect for your account.

**Synopsis:**
```bash
aws service-quotas get-service-quota \
    --service-code <value> \
    --quota-code <value> \
    [--context-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | **Yes** | string | -- | Service code (e.g., `ec2`, `lambda`) |
| `--quota-code` | **Yes** | string | -- | Quota code (e.g., `L-1216C47A`) |
| `--context-id` | No | string | -- | Context ID for resource-level quotas |

**Output Schema:**
```json
{
    "Quota": {
        "ServiceCode": "string",
        "ServiceName": "string",
        "QuotaArn": "string",
        "QuotaCode": "string",
        "QuotaName": "string",
        "Value": "double",
        "Unit": "string",
        "Adjustable": "boolean",
        "GlobalQuota": "boolean",
        "UsageMetric": {
            "MetricNamespace": "string",
            "MetricName": "string",
            "MetricDimensions": {
                "string": "string"
            },
            "MetricStatisticRecommendation": "string"
        },
        "Period": {
            "PeriodValue": "integer",
            "PeriodUnit": "MICROSECOND|MILLISECOND|SECOND|MINUTE|HOUR|DAY|WEEK"
        },
        "ErrorReason": {
            "ErrorCode": "DEPENDENCY_ACCESS_DENIED_ERROR|DEPENDENCY_THROTTLING_ERROR|DEPENDENCY_SERVICE_ERROR|SERVICE_QUOTA_NOT_AVAILABLE_ERROR",
            "ErrorMessage": "string"
        },
        "QuotaAppliedAtLevel": "ACCOUNT|RESOURCE|ALL",
        "QuotaContext": {
            "ContextScope": "RESOURCE|ACCOUNT",
            "ContextScopeType": "string",
            "ContextId": "string"
        }
    }
}
```

---

### 1.2 `get-aws-default-service-quota`

Retrieves the default value for the specified quota. The default value does not reflect any quota increases.

**Synopsis:**
```bash
aws service-quotas get-aws-default-service-quota \
    --service-code <value> \
    --quota-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | **Yes** | string | -- | Service code |
| `--quota-code` | **Yes** | string | -- | Quota code |

**Output Schema:**
```json
{
    "Quota": {
        "ServiceCode": "string",
        "ServiceName": "string",
        "QuotaArn": "string",
        "QuotaCode": "string",
        "QuotaName": "string",
        "Value": "double",
        "Unit": "string",
        "Adjustable": "boolean",
        "GlobalQuota": "boolean",
        "UsageMetric": {},
        "Period": {},
        "ErrorReason": {},
        "QuotaAppliedAtLevel": "ACCOUNT|RESOURCE|ALL",
        "QuotaContext": {}
    }
}
```

---

### 1.3 `list-services`

Lists the names and codes of available AWS services with Service Quotas. **Paginated operation.**

**Synopsis:**
```bash
aws service-quotas list-services \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Services": [
        {
            "ServiceCode": "string",
            "ServiceName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `list-service-quotas`

Lists the applied quotas for the specified AWS service. **Paginated operation.**

**Synopsis:**
```bash
aws service-quotas list-service-quotas \
    --service-code <value> \
    [--quota-code <value>] \
    [--quota-applied-at-level <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | **Yes** | string | -- | Service code |
| `--quota-code` | No | string | -- | Filter by specific quota code |
| `--quota-applied-at-level` | No | string | -- | Filter by level: `ACCOUNT`, `RESOURCE`, `ALL` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Quotas": [
        {
            "ServiceCode": "string",
            "ServiceName": "string",
            "QuotaArn": "string",
            "QuotaCode": "string",
            "QuotaName": "string",
            "Value": "double",
            "Unit": "string",
            "Adjustable": "boolean",
            "GlobalQuota": "boolean",
            "UsageMetric": {},
            "Period": {},
            "ErrorReason": {},
            "QuotaAppliedAtLevel": "ACCOUNT|RESOURCE|ALL",
            "QuotaContext": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `list-aws-default-service-quotas`

Lists the default values for the quotas for the specified AWS service. **Paginated operation.**

**Synopsis:**
```bash
aws service-quotas list-aws-default-service-quotas \
    --service-code <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | **Yes** | string | -- | Service code |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Quotas": [
        {
            "ServiceCode": "string",
            "ServiceName": "string",
            "QuotaArn": "string",
            "QuotaCode": "string",
            "QuotaName": "string",
            "Value": "double",
            "Unit": "string",
            "Adjustable": "boolean",
            "GlobalQuota": "boolean",
            "UsageMetric": {},
            "Period": {}
        }
    ],
    "NextToken": "string"
}
```
