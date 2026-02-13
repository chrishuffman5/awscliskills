# CIS Scans

### 6.1 `create-cis-scan-configuration`

Creates a CIS (Center for Internet Security) scan configuration.

**Synopsis:**
```bash
aws inspector2 create-cis-scan-configuration \
    --scan-name <value> \
    --security-level <value> \
    --schedule <value> \
    --targets <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-name` | **Yes** | string | -- | Scan name (1-128 chars) |
| `--security-level` | **Yes** | string | -- | CIS security level: `LEVEL_1`, `LEVEL_2` |
| `--schedule` | **Yes** | tagged union | -- | Schedule configuration (see below) |
| `--targets` | **Yes** | structure | -- | Target accounts and resource tags (see below) |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |

**Schedule Structure (one of):**
```json
{
    "oneTime": {},
    "daily": {
        "startTime": {"timeOfDay": "HH:MM", "timezone": "string"}
    },
    "weekly": {
        "startTime": {"timeOfDay": "HH:MM", "timezone": "string"},
        "days": ["SUN|MON|TUE|WED|THU|FRI|SAT"]
    },
    "monthly": {
        "startTime": {"timeOfDay": "HH:MM", "timezone": "string"},
        "day": "SUN|MON|TUE|WED|THU|FRI|SAT"
    }
}
```

**Targets Structure:**
```json
{
    "accountIds": ["string"],
    "targetResourceTags": {
        "string": ["string"]
    }
}
```
- `accountIds`: Account IDs or `ALL_ACCOUNTS` or `SELF` (max 10000)
- `targetResourceTags`: Resource tags to filter targets (max 5 keys)

**Output Schema:**
```json
{
    "scanConfigurationArn": "string"
}
```

---

### 6.2 `delete-cis-scan-configuration`

Deletes a CIS scan configuration.

**Synopsis:**
```bash
aws inspector2 delete-cis-scan-configuration \
    --scan-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-configuration-arn` | **Yes** | string | -- | ARN of the CIS scan configuration to delete |

**Output Schema:**
```json
{
    "scanConfigurationArn": "string"
}
```

---

### 6.3 `update-cis-scan-configuration`

Updates a CIS scan configuration.

**Synopsis:**
```bash
aws inspector2 update-cis-scan-configuration \
    --scan-configuration-arn <value> \
    [--scan-name <value>] \
    [--security-level <value>] \
    [--schedule <value>] \
    [--targets <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-configuration-arn` | **Yes** | string | -- | ARN of the configuration to update |
| `--scan-name` | No | string | None | Updated scan name |
| `--security-level` | No | string | None | Updated level: `LEVEL_1`, `LEVEL_2` |
| `--schedule` | No | tagged union | None | Updated schedule |
| `--targets` | No | structure | None | Updated targets |

**Output Schema:**
```json
{
    "scanConfigurationArn": "string"
}
```

---

### 6.4 `list-cis-scan-configurations`

Lists CIS scan configurations. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-cis-scan-configurations \
    [--filter-criteria <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-criteria` | No | structure | None | Filter by scan configuration ARN, scan name, target resource tags |
| `--sort-by` | No | string | None | Sort field: `SCAN_NAME`, `SCAN_CONFIGURATION_ARN` |
| `--sort-order` | No | string | None | Sort order: `ASC`, `DESC` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "scanConfigurations": [
        {
            "scanConfigurationArn": "string",
            "ownerId": "string",
            "scanName": "string",
            "securityLevel": "LEVEL_1|LEVEL_2",
            "schedule": {},
            "targets": {
                "accountIds": ["string"],
                "targetResourceTags": {}
            },
            "tags": {"key": "value"}
        }
    ],
    "nextToken": "string"
}
```

---

### 6.5 `list-cis-scans`

Lists completed CIS scans. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-cis-scans \
    [--filter-criteria <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--detail-level <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-criteria` | No | structure | None | Filter by scan name, status, dates, etc. |
| `--sort-by` | No | string | None | Sort field: `STATUS`, `SCHEDULED_BY`, `SCAN_START_DATE`, `FAILED_CHECKS` |
| `--sort-order` | No | string | None | Sort order: `ASC`, `DESC` |
| `--detail-level` | No | string | None | Detail level: `ORGANIZATION`, `MEMBER` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "scans": [
        {
            "scanArn": "string",
            "scanConfigurationArn": "string",
            "scanName": "string",
            "scanDate": "timestamp",
            "scheduledBy": "string",
            "securityLevel": "LEVEL_1|LEVEL_2",
            "status": "COMPLETED|CANCELLED|FAILED|IN_PROGRESS",
            "totalChecks": "integer",
            "failedChecks": "integer",
            "targets": {
                "accountIds": ["string"],
                "targetResourceTags": {}
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 6.6 `get-cis-scan-report`

Gets a downloadable CIS scan report.

**Synopsis:**
```bash
aws inspector2 get-cis-scan-report \
    --scan-arn <value> \
    [--report-format <value>] \
    [--target-accounts <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-arn` | **Yes** | string | -- | ARN of the CIS scan |
| `--report-format` | No | string | None | Format: `PDF`, `CSV` |
| `--target-accounts` | No | list(string) | None | Target accounts to filter the report |

**Output Schema:**
```json
{
    "url": "string",
    "status": "SUCCEEDED|FAILED|IN_PROGRESS"
}
```

---

### 6.7 `get-cis-scan-result-details`

Gets CIS scan result details for a specific check. **Paginated.**

**Synopsis:**
```bash
aws inspector2 get-cis-scan-result-details \
    --scan-arn <value> \
    --account-id <value> \
    --target-resource-id <value> \
    [--filter-criteria <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-arn` | **Yes** | string | -- | ARN of the CIS scan |
| `--account-id` | **Yes** | string | -- | Account ID (12 digits) |
| `--target-resource-id` | **Yes** | string | -- | Target resource ID |
| `--filter-criteria` | No | structure | None | Filter by check ID, finding status |
| `--sort-by` | No | string | None | Sort field: `CHECK_ID`, `STATUS` |
| `--sort-order` | No | string | None | Sort order: `ASC`, `DESC` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "scanResultDetails": [
        {
            "scanArn": "string",
            "accountId": "string",
            "targetResourceId": "string",
            "checkId": "string",
            "checkDescription": "string",
            "status": "PASSED|FAILED|ERROR|NOT_APPLICABLE|INFORMATIONAL|UNKNOWN",
            "statusReason": "string",
            "platform": "string",
            "securityLevel": "LEVEL_1|LEVEL_2",
            "title": "string",
            "findingArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.8 `list-cis-scan-results-aggregated-by-checks`

Lists CIS scan results aggregated by checks. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-cis-scan-results-aggregated-by-checks \
    --scan-arn <value> \
    [--filter-criteria <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-arn` | **Yes** | string | -- | ARN of the CIS scan |
| `--filter-criteria` | No | structure | None | Filter by check ID, title, security level |
| `--sort-by` | No | string | None | Sort field: `CHECK_ID`, `TITLE`, `PLATFORM`, `FAILED_COUNTS`, `SECURITY_LEVEL` |
| `--sort-order` | No | string | None | Sort order: `ASC`, `DESC` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "checkAggregations": [
        {
            "scanArn": "string",
            "checkId": "string",
            "checkDescription": "string",
            "title": "string",
            "platform": "string",
            "securityLevel": "LEVEL_1|LEVEL_2",
            "accountId": "string",
            "statusCounts": {
                "passed": "integer",
                "failed": "integer",
                "skipped": "integer"
            },
            "totalResourceCount": "integer"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.9 `list-cis-scan-results-aggregated-by-target-resource`

Lists CIS scan results aggregated by target resource. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-cis-scan-results-aggregated-by-target-resource \
    --scan-arn <value> \
    [--filter-criteria <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-arn` | **Yes** | string | -- | ARN of the CIS scan |
| `--filter-criteria` | No | structure | None | Filter by target resource ID, status, platform |
| `--sort-by` | No | string | None | Sort field: `RESOURCE_ID`, `FAILED_COUNTS`, `ACCOUNT_ID`, `PLATFORM`, `TARGET_STATUS`, `TARGET_STATUS_REASON` |
| `--sort-order` | No | string | None | Sort order: `ASC`, `DESC` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "targetResourceAggregations": [
        {
            "scanArn": "string",
            "targetResourceId": "string",
            "accountId": "string",
            "platform": "string",
            "targetStatus": "TIMED_OUT|CANCELLED|COMPLETED",
            "targetStatusReason": "SCAN_IN_PROGRESS|UNSUPPORTED_OS|SSM_UNMANAGED",
            "statusCounts": {
                "passed": "integer",
                "failed": "integer",
                "skipped": "integer"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 6.10 `start-cis-session`

Starts a CIS scan session. Used internally by the CIS scanning agent.

**Synopsis:**
```bash
aws inspector2 start-cis-session \
    --scan-arn <value> \
    --message <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-arn` | **Yes** | string | -- | ARN of the CIS scan |
| `--message` | **Yes** | structure | -- | Session start message with session token |

**Output Schema:** Empty on success.

---

### 6.11 `stop-cis-session`

Stops a CIS scan session.

**Synopsis:**
```bash
aws inspector2 stop-cis-session \
    --scan-arn <value> \
    --message <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-arn` | **Yes** | string | -- | ARN of the CIS scan |
| `--message` | **Yes** | structure | -- | Session stop message with status and reason |

**Output Schema:** Empty on success.

---

### 6.12 `send-cis-session-health`

Sends CIS session health data during a scan.

**Synopsis:**
```bash
aws inspector2 send-cis-session-health \
    --scan-arn <value> \
    --session-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-arn` | **Yes** | string | -- | ARN of the CIS scan |
| `--session-token` | **Yes** | string | -- | Session token from start-cis-session |

**Output Schema:** Empty on success.

---

### 6.13 `send-cis-session-telemetry`

Sends CIS session telemetry data with check results.

**Synopsis:**
```bash
aws inspector2 send-cis-session-telemetry \
    --scan-arn <value> \
    --session-token <value> \
    --messages <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-arn` | **Yes** | string | -- | ARN of the CIS scan |
| `--session-token` | **Yes** | string | -- | Session token |
| `--messages` | **Yes** | list | -- | Telemetry messages containing check results |

**Output Schema:** Empty on success.
