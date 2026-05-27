# Query Logging

### 6.1 `create-query-logging-config`

Creates a configuration to log DNS queries for a public hosted zone to CloudWatch Logs.

**Synopsis:**
```bash
aws route53 create-query-logging-config \
    --hosted-zone-id <value> \
    --cloud-watch-logs-log-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | **Yes** | string | -- | Public hosted zone ID (max 32 chars) |
| `--cloud-watch-logs-log-group-arn` | **Yes** | string | -- | CloudWatch Logs log group ARN. Must be in `us-east-1` |

**Output Schema:**
```json
{
    "QueryLoggingConfig": {
        "Id": "string",
        "HostedZoneId": "string",
        "CloudWatchLogsLogGroupArn": "string"
    },
    "Location": "string"
}
```

> **Note:** The CloudWatch Logs log group must be in `us-east-1` and have a resource policy allowing Route 53 to create log streams and write log events.

---

### 6.2 `delete-query-logging-config`

Deletes a query logging configuration. Does not delete the CloudWatch Logs log group or existing log data.

**Synopsis:**
```bash
aws route53 delete-query-logging-config \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Query logging config ID (1-36 chars) |

**Output:** None on success.

---

### 6.3 `get-query-logging-config`

Gets information about a specified query logging configuration.

**Synopsis:**
```bash
aws route53 get-query-logging-config \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Query logging config ID (1-36 chars) |

**Output Schema:**
```json
{
    "QueryLoggingConfig": {
        "Id": "string",
        "HostedZoneId": "string",
        "CloudWatchLogsLogGroupArn": "string"
    }
}
```

---

### 6.4 `list-query-logging-configs`

Lists query logging configurations, optionally filtered by hosted zone. **Paginated operation.**

**Synopsis:**
```bash
aws route53 list-query-logging-configs \
    [--hosted-zone-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hosted-zone-id` | No | string | None | Filter by hosted zone (max 32 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | string | None | Items per API call |
| `--max-items` | No | string | None | Total items to return |

**Output Schema:**
```json
{
    "QueryLoggingConfigs": [
        {
            "Id": "string",
            "HostedZoneId": "string",
            "CloudWatchLogsLogGroupArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---
