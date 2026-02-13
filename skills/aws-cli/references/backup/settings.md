# Settings

### 12.1 `describe-global-settings`

Returns the current global settings for the account, including cross-account backup and multi-party approval status.

**Synopsis:**
```bash
aws backup describe-global-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None (command-specific)

**Output Schema:**
```json
{
    "GlobalSettings": {
        "isCrossAccountBackupEnabled": "string",
        "isMpaEnabled": "string",
        "isDelegatedAdministratorEnabled": "string"
    },
    "LastUpdateTime": "timestamp"
}
```

---

### 12.2 `update-global-settings`

Updates global settings for the account. Requires Organizations management account.

**Synopsis:**
```bash
aws backup update-global-settings \
    [--global-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-settings` | No | map | None | Key-value settings: `isCrossAccountBackupEnabled`, `isMpaEnabled`, `isDelegatedAdministratorEnabled` |

**Example:**
```bash
# Enable cross-account backup
aws backup update-global-settings \
    --global-settings isCrossAccountBackupEnabled=true

# Enable multi-party approval
aws backup update-global-settings \
    --global-settings isMpaEnabled=true
```

**Output:** None

---

### 12.3 `describe-region-settings`

Returns the current service opt-in settings for the Region.

**Synopsis:**
```bash
aws backup describe-region-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None (command-specific)

**Output Schema:**
```json
{
    "ResourceTypeOptInPreference": {
        "string": "boolean"
    },
    "ResourceTypeManagementPreference": {
        "string": "boolean"
    }
}
```

| Field | Type | Description |
|-------|------|-------------|
| `ResourceTypeOptInPreference` | map | Service opt-in preferences per resource type |
| `ResourceTypeManagementPreference` | map | Whether Backup fully manages backups per resource type |

---

### 12.4 `update-region-settings`

Updates the current service opt-in settings for the Region.

**Synopsis:**
```bash
aws backup update-region-settings \
    [--resource-type-opt-in-preference <value>] \
    [--resource-type-management-preference <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type-opt-in-preference` | No | map | None | Service opt-in preferences (`KeyName=boolean,...`) |
| `--resource-type-management-preference` | No | map | None | Full management preferences (`KeyName=boolean,...`) |

**Example:**
```bash
# Opt in EBS and RDS
aws backup update-region-settings \
    --resource-type-opt-in-preference EBS=true,RDS=true

# Enable full management for DynamoDB
aws backup update-region-settings \
    --resource-type-management-preference DynamoDB=true
```

**Output:** None

---

### 12.5 `list-backup-job-summaries`

Returns aggregated backup job counts for the last 30 days. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-backup-job-summaries \
    [--account-id <value>] \
    [--state <value>] \
    [--resource-type <value>] \
    [--message-category <value>] \
    [--aggregation-period <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | No | string | None | 12-digit account ID, `ANY`, or `AGGREGATE_ALL` |
| `--state` | No | string | None | Job state filter (CREATED\|PENDING\|RUNNING\|ABORTING\|ABORTED\|COMPLETED\|FAILED\|EXPIRED\|PARTIAL\|AGGREGATE_ALL\|ANY) |
| `--resource-type` | No | string | None | Resource type filter |
| `--message-category` | No | string | None | Message category filter |
| `--aggregation-period` | No | string | None | ONE_DAY\|SEVEN_DAYS\|FOURTEEN_DAYS |
| `--max-results` | No | integer | None | Max items (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "BackupJobSummaries": [
        {
            "Region": "string",
            "AccountId": "string",
            "State": "string",
            "ResourceType": "string",
            "MessageCategory": "string",
            "Count": "integer",
            "StartTime": "timestamp",
            "EndTime": "timestamp"
        }
    ],
    "AggregationPeriod": "string",
    "NextToken": "string"
}
```

---

### 12.6 `list-copy-job-summaries`

Returns aggregated copy job counts for the last 30 days. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-copy-job-summaries \
    [--account-id <value>] \
    [--state <value>] \
    [--resource-type <value>] \
    [--message-category <value>] \
    [--aggregation-period <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | No | string | None | 12-digit account ID, `ANY`, or `AGGREGATE_ALL` |
| `--state` | No | string | None | Job state filter |
| `--resource-type` | No | string | None | Resource type filter |
| `--message-category` | No | string | None | Message category filter |
| `--aggregation-period` | No | string | None | ONE_DAY\|SEVEN_DAYS\|FOURTEEN_DAYS |
| `--max-results` | No | integer | None | Max items (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "CopyJobSummaries": [
        {
            "Region": "string",
            "AccountId": "string",
            "State": "string",
            "ResourceType": "string",
            "MessageCategory": "string",
            "Count": "integer",
            "StartTime": "timestamp",
            "EndTime": "timestamp"
        }
    ],
    "AggregationPeriod": "string",
    "NextToken": "string"
}
```

---

### 12.7 `list-restore-job-summaries`

Returns aggregated restore job counts for the last 30 days. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-restore-job-summaries \
    [--account-id <value>] \
    [--state <value>] \
    [--resource-type <value>] \
    [--aggregation-period <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | No | string | None | 12-digit account ID, `ANY`, or `AGGREGATE_ALL` |
| `--state` | No | string | None | Job state filter |
| `--resource-type` | No | string | None | Resource type filter |
| `--aggregation-period` | No | string | None | ONE_DAY\|SEVEN_DAYS\|FOURTEEN_DAYS |
| `--max-results` | No | integer | None | Max items (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "RestoreJobSummaries": [
        {
            "Region": "string",
            "AccountId": "string",
            "State": "string",
            "ResourceType": "string",
            "Count": "integer",
            "StartTime": "timestamp",
            "EndTime": "timestamp"
        }
    ],
    "AggregationPeriod": "string",
    "NextToken": "string"
}
```
