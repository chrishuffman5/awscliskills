# Quota Requests

### 2.1 `request-service-quota-increase`

Submits a quota increase request for a specific quota.

**Synopsis:**
```bash
aws service-quotas request-service-quota-increase \
    --service-code <value> \
    --quota-code <value> \
    --desired-value <value> \
    [--context-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | **Yes** | string | -- | Service code (e.g., `ec2`) |
| `--quota-code` | **Yes** | string | -- | Quota code (e.g., `L-1216C47A`) |
| `--desired-value` | **Yes** | double | -- | Desired new quota value |
| `--context-id` | No | string | -- | Context ID for resource-level quotas |

**Output Schema:**
```json
{
    "RequestedQuota": {
        "Id": "string",
        "CaseId": "string",
        "ServiceCode": "string",
        "ServiceName": "string",
        "QuotaCode": "string",
        "QuotaName": "string",
        "DesiredValue": "double",
        "Status": "PENDING|CASE_OPENED|APPROVED|DENIED|CASE_CLOSED|NOT_APPROVED|INVALID_REQUEST",
        "Created": "timestamp",
        "LastUpdated": "timestamp",
        "Requester": "string",
        "QuotaArn": "string",
        "GlobalQuota": "boolean",
        "Unit": "string",
        "QuotaRequestedAtLevel": "ACCOUNT|RESOURCE|ALL",
        "QuotaContext": {
            "ContextScope": "RESOURCE|ACCOUNT",
            "ContextScopeType": "string",
            "ContextId": "string"
        }
    }
}
```

---

### 2.2 `get-requested-service-quota-change`

Retrieves information about a quota increase request.

**Synopsis:**
```bash
aws service-quotas get-requested-service-quota-change \
    --request-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--request-id` | **Yes** | string | -- | ID of the quota increase request |

**Output Schema:**
```json
{
    "RequestedQuota": {
        "Id": "string",
        "CaseId": "string",
        "ServiceCode": "string",
        "ServiceName": "string",
        "QuotaCode": "string",
        "QuotaName": "string",
        "DesiredValue": "double",
        "Status": "PENDING|CASE_OPENED|APPROVED|DENIED|CASE_CLOSED|NOT_APPROVED|INVALID_REQUEST",
        "Created": "timestamp",
        "LastUpdated": "timestamp",
        "Requester": "string",
        "QuotaArn": "string",
        "GlobalQuota": "boolean",
        "Unit": "string",
        "QuotaRequestedAtLevel": "ACCOUNT|RESOURCE|ALL",
        "QuotaContext": {}
    }
}
```

---

### 2.3 `list-requested-service-quota-change-history`

Retrieves the quota increase requests in the specified account. **Paginated operation.**

**Synopsis:**
```bash
aws service-quotas list-requested-service-quota-change-history \
    [--service-code <value>] \
    [--status <value>] \
    [--quota-requested-at-level <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code` | No | string | -- | Filter by service code |
| `--status` | No | string | -- | Filter by status: `PENDING`, `CASE_OPENED`, `APPROVED`, `DENIED`, `CASE_CLOSED`, `NOT_APPROVED`, `INVALID_REQUEST` |
| `--quota-requested-at-level` | No | string | -- | Filter by level: `ACCOUNT`, `RESOURCE`, `ALL` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RequestedQuotas": [
        {
            "Id": "string",
            "CaseId": "string",
            "ServiceCode": "string",
            "ServiceName": "string",
            "QuotaCode": "string",
            "QuotaName": "string",
            "DesiredValue": "double",
            "Status": "string",
            "Created": "timestamp",
            "LastUpdated": "timestamp",
            "Requester": "string",
            "QuotaArn": "string",
            "GlobalQuota": "boolean",
            "Unit": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `list-requested-service-quota-change-history-by-quota`

Retrieves the quota increase requests for the specified quota. **Paginated operation.**

**Synopsis:**
```bash
aws service-quotas list-requested-service-quota-change-history-by-quota \
    --service-code <value> \
    --quota-code <value> \
    [--status <value>] \
    [--quota-requested-at-level <value>] \
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
| `--quota-code` | **Yes** | string | -- | Quota code |
| `--status` | No | string | -- | Filter by status |
| `--quota-requested-at-level` | No | string | -- | Filter by level |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RequestedQuotas": [
        {
            "Id": "string",
            "CaseId": "string",
            "ServiceCode": "string",
            "ServiceName": "string",
            "QuotaCode": "string",
            "QuotaName": "string",
            "DesiredValue": "double",
            "Status": "string",
            "Created": "timestamp",
            "LastUpdated": "timestamp",
            "Requester": "string",
            "QuotaArn": "string",
            "GlobalQuota": "boolean",
            "Unit": "string"
        }
    ],
    "NextToken": "string"
}
```
