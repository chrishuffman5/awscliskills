# Subscription Filters

### 12.1 `put-subscription-filter`

Creates or updates a subscription filter to stream log events to a destination (Lambda, Kinesis, Firehose).

**Synopsis:**
```bash
aws logs put-subscription-filter \
    --log-group-name <value> \
    --filter-name <value> \
    --filter-pattern <value> \
    --destination-arn <value> \
    [--role-arn <value>] \
    [--distribution <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars) |
| `--filter-name` | **Yes** | string | -- | Subscription filter name (1-512 chars). Pattern: `[^:*]*` |
| `--filter-pattern` | **Yes** | string | -- | Filter pattern (0-1024 chars) |
| `--destination-arn` | **Yes** | string | -- | ARN of destination (Lambda, Kinesis Data Stream, Firehose) |
| `--role-arn` | No | string | -- | IAM role ARN granting CloudWatch Logs permissions to the destination |
| `--distribution` | No | string | -- | `Random` or `ByLogStream` (Kinesis streams only) |

**Output:** None on success.

---

### 12.2 `describe-subscription-filters`

Lists subscription filters for a log group. **Paginated.**

**Synopsis:**
```bash
aws logs describe-subscription-filters \
    --log-group-name <value> \
    [--filter-name-prefix <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars) |
| `--filter-name-prefix` | No | string | -- | Filter name prefix (1-512 chars) |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "subscriptionFilters": [
        {
            "filterName": "string",
            "logGroupName": "string",
            "filterPattern": "string",
            "destinationArn": "string",
            "roleArn": "string",
            "distribution": "Random|ByLogStream",
            "creationTime": long
        }
    ],
    "nextToken": "string"
}
```

---

### 12.3 `delete-subscription-filter`

Deletes a subscription filter.

**Synopsis:**
```bash
aws logs delete-subscription-filter \
    --log-group-name <value> \
    --filter-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars) |
| `--filter-name` | **Yes** | string | -- | Subscription filter name (1-512 chars) |

**Output:** None on success.

---
