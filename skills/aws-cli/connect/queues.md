# Queues

### 6.1 `create-queue`

Creates a queue for the specified instance.

**Synopsis:**
```bash
aws connect create-queue \
    --instance-id <value> \
    --name <value> \
    --hours-of-operation-id <value> \
    [--description <value>] \
    [--outbound-caller-config <value>] \
    [--outbound-email-config <value>] \
    [--max-contacts <value>] \
    [--quick-connect-ids <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Queue name (1-127 chars) |
| `--hours-of-operation-id` | **Yes** | string | -- | Hours of operation ID |
| `--description` | No | string | None | Description (1-250 chars) |
| `--outbound-caller-config` | No | structure | None | `OutboundCallerIdName`, `OutboundCallerIdNumberId`, `OutboundFlowId` |
| `--outbound-email-config` | No | structure | None | `OutboundEmailAddressId` |
| `--max-contacts` | No | integer | None | Max contacts before full (min 0) |
| `--quick-connect-ids` | No | list | None | Quick connect IDs (1-50) |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "QueueArn": "string",
    "QueueId": "string"
}
```

---

### 6.2 `describe-queue`

Describes a queue.

**Synopsis:**
```bash
aws connect describe-queue \
    --instance-id <value> \
    --queue-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--queue-id` | **Yes** | string | -- | Queue ID |

**Output Schema:**
```json
{
    "Queue": {
        "Name": "string",
        "QueueArn": "string",
        "QueueId": "string",
        "Description": "string",
        "OutboundCallerConfig": { "OutboundCallerIdName": "string", "OutboundCallerIdNumberId": "string", "OutboundFlowId": "string" },
        "OutboundEmailConfig": { "OutboundEmailAddressId": "string" },
        "HoursOfOperationId": "string",
        "MaxContacts": "integer",
        "Status": "ENABLED|DISABLED",
        "Tags": { "key": "value" },
        "LastModifiedTime": "timestamp",
        "LastModifiedRegion": "string"
    }
}
```

---

### 6.3 `list-queues`

Lists queues. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-queues \
    --instance-id <value> \
    [--queue-types <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--queue-types` | No | list | None | `STANDARD` or `AGENT` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

**Output Schema:**
```json
{
    "QueueSummaryList": [ { "Id": "string", "Arn": "string", "Name": "string", "QueueType": "STANDARD|AGENT", "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" } ],
    "NextToken": "string"
}
```

---

### 6.4-6.9 Queue Update Commands

`update-queue-hours-of-operation`, `update-queue-max-contacts`, `update-queue-name`, `update-queue-outbound-caller-config`, `update-queue-outbound-email-config`, `update-queue-status` all require `--instance-id` and `--queue-id`, plus the specific field being updated.

**Synopsis (update-queue-status example):**
```bash
aws connect update-queue-status \
    --instance-id <value> \
    --queue-id <value> \
    --status <value>
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--queue-id` | **Yes** | string | -- | Queue ID |
| `--status` | **Yes** | string | -- | `ENABLED` or `DISABLED` |

**Output:** None (for all update commands)

---

### 6.10 `delete-queue`

Deletes a queue.

**Synopsis:**
```bash
aws connect delete-queue \
    --instance-id <value> \
    --queue-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--queue-id` | **Yes** | string | -- | Queue ID |

**Output:** None

---

### 6.11 `search-queues`

Searches queues. **Paginated operation.**

**Synopsis:**
```bash
aws connect search-queues \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--search-filter <value>] \
    [--search-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-filter` | No | structure | None | Tag filter |
| `--search-criteria` | No | structure | None | Search criteria |

**Output Schema:**
```json
{
    "Queues": [ { "Name": "string", "QueueArn": "string", "QueueId": "string", "Description": "string", "HoursOfOperationId": "string", "MaxContacts": "integer", "Status": "string", "Tags": {} } ],
    "NextToken": "string",
    "ApproximateTotalCount": "long"
}
```

---

### 6.12 `associate-queue-quick-connects`

Associates quick connects with a queue.

**Synopsis:**
```bash
aws connect associate-queue-quick-connects \
    --instance-id <value> \
    --queue-id <value> \
    --quick-connect-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--queue-id` | **Yes** | string | -- | Queue ID |
| `--quick-connect-ids` | **Yes** | list | -- | Quick connect IDs (1-50) |

**Output:** None

---

### 6.13 `list-queue-quick-connects`

Lists quick connects associated with a queue. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-queue-quick-connects \
    --instance-id <value> \
    --queue-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--queue-id` | **Yes** | string | -- | Queue ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

**Output Schema:**
```json
{
    "QuickConnectSummaryList": [ { "Id": "string", "Arn": "string", "Name": "string", "QuickConnectType": "USER|QUEUE|PHONE_NUMBER|FLOW", "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" } ],
    "NextToken": "string",
    "LastModifiedTime": "timestamp",
    "LastModifiedRegion": "string"
}
```

---

### 6.14 `disassociate-queue-quick-connects`

Removes quick connects from a queue.

**Synopsis:**
```bash
aws connect disassociate-queue-quick-connects \
    --instance-id <value> \
    --queue-id <value> \
    --quick-connect-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--queue-id` | **Yes** | string | -- | Queue ID |
| `--quick-connect-ids` | **Yes** | list | -- | Quick connect IDs to remove |

**Output:** None
