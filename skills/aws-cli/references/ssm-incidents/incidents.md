# Incidents

### 2.1 `start-incident`

Used to start an incident from CloudWatch alarms, EventBridge events, or manually.

**Synopsis:**
```bash
aws ssm-incidents start-incident \
    --response-plan-arn <value> \
    [--title <value>] \
    [--impact <value>] \
    [--trigger-details <value>] \
    [--related-items <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--response-plan-arn` | **Yes** | string | -- | Response plan ARN |
| `--title` | No | string | None | Override the incident template title |
| `--impact` | No | integer | None | Override the incident template impact (1-5) |
| `--trigger-details` | No | structure | None | Details about what triggered the incident |
| `--related-items` | No | list | None | Related items to associate |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "incidentRecordArn": "string"
}
```

---

### 2.2 `get-incident-record`

Returns the details of the specified incident record.

**Synopsis:**
```bash
aws ssm-incidents get-incident-record \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Incident record ARN |

**Output Schema:**
```json
{
    "incidentRecord": {
        "arn": "string",
        "title": "string",
        "summary": "string",
        "status": "OPEN|RESOLVED",
        "impact": "integer",
        "creationTime": "timestamp",
        "resolvedTime": "timestamp",
        "lastModifiedTime": "timestamp",
        "lastModifiedBy": "string",
        "automationExecutions": [
            {
                "ssmExecutionArn": "string"
            }
        ],
        "incidentRecordSource": {
            "createdBy": "string",
            "invokedBy": "string",
            "resourceArn": "string",
            "source": "string"
        },
        "dedupeString": "string",
        "chatChannel": {
            "chatbotSns": ["string"],
            "empty": {}
        },
        "notificationTargets": [
            {
                "snsTopicArn": "string"
            }
        ]
    }
}
```

---

### 2.3 `delete-incident-record`

Delete an incident record from Incident Manager.

**Synopsis:**
```bash
aws ssm-incidents delete-incident-record \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Incident record ARN |

**Output Schema:**
```json
{}
```

---

### 2.4 `update-incident-record`

Update the details of an incident record.

**Synopsis:**
```bash
aws ssm-incidents update-incident-record \
    --arn <value> \
    [--title <value>] \
    [--summary <value>] \
    [--impact <value>] \
    [--status <value>] \
    [--chat-channel <value>] \
    [--notification-targets <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Incident record ARN |
| `--title` | No | string | None | Updated title |
| `--summary` | No | string | None | Updated summary |
| `--impact` | No | integer | None | Updated impact (1-5) |
| `--status` | No | string | None | `OPEN` or `RESOLVED` |
| `--chat-channel` | No | structure | None | Updated chat channel |
| `--notification-targets` | No | list | None | Updated notification targets |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{}
```

---

### 2.5 `list-incident-records`

Lists all incident records in your account. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-incidents list-incident-records \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Each: `key=string,condition={...}` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "incidentRecordSummaries": [
        {
            "arn": "string",
            "title": "string",
            "status": "OPEN|RESOLVED",
            "impact": "integer",
            "creationTime": "timestamp",
            "resolvedTime": "timestamp",
            "incidentRecordSource": {
                "createdBy": "string",
                "invokedBy": "string",
                "resourceArn": "string",
                "source": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 2.6 `update-deletion-protection`

Update deletion protection to either allow or deny deletion of the final Region in a replication set.

**Synopsis:**
```bash
aws ssm-incidents update-deletion-protection \
    --arn <value> \
    --deletion-protected | --no-deletion-protected \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Replication set ARN |
| `--deletion-protected` | **Yes** | boolean | -- | Enable or disable deletion protection |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{}
```
