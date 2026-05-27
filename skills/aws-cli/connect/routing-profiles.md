# Routing Profiles

### 7.1 `create-routing-profile`

Creates a routing profile.

**Synopsis:**
```bash
aws connect create-routing-profile \
    --instance-id <value> \
    --name <value> \
    --description <value> \
    --default-outbound-queue-id <value> \
    --media-concurrencies <value> \
    [--queue-configs <value>] \
    [--tags <value>] \
    [--agent-availability-timer <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Profile name (1-127 chars) |
| `--description` | **Yes** | string | -- | Description (1-250 chars) |
| `--default-outbound-queue-id` | **Yes** | string | -- | Default outbound queue ID |
| `--media-concurrencies` | **Yes** | list | -- | Channel concurrency settings |
| `--queue-configs` | No | list | None | Queue configurations (1-10) |
| `--tags` | No | map | None | Tags (max 50) |
| `--agent-availability-timer` | No | string | None | `TIME_SINCE_LAST_ACTIVITY` or `TIME_SINCE_LAST_INBOUND` |

**MediaConcurrencies:**
```json
[
    {
        "Channel": "VOICE|CHAT|TASK|EMAIL",
        "Concurrency": "integer",
        "CrossChannelBehavior": { "BehaviorType": "ROUTE_CURRENT_CHANNEL_ONLY|ROUTE_ANY_CHANNEL" }
    }
]
```

**QueueConfigs:**
```json
[
    {
        "QueueReference": { "QueueId": "string", "Channel": "VOICE|CHAT|TASK|EMAIL" },
        "Priority": "integer",
        "Delay": "integer"
    }
]
```

**Output Schema:**
```json
{
    "RoutingProfileArn": "string",
    "RoutingProfileId": "string"
}
```

---

### 7.2 `describe-routing-profile`

Describes a routing profile.

**Synopsis:**
```bash
aws connect describe-routing-profile \
    --instance-id <value> \
    --routing-profile-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--routing-profile-id` | **Yes** | string | -- | Routing profile ID |

**Output Schema:**
```json
{
    "RoutingProfile": {
        "InstanceId": "string",
        "Name": "string",
        "RoutingProfileArn": "string",
        "RoutingProfileId": "string",
        "Description": "string",
        "MediaConcurrencies": [],
        "DefaultOutboundQueueId": "string",
        "Tags": { "key": "value" },
        "NumberOfAssociatedQueues": "long",
        "NumberOfAssociatedUsers": "long",
        "AgentAvailabilityTimer": "string",
        "LastModifiedTime": "timestamp",
        "LastModifiedRegion": "string",
        "IsDefault": "boolean"
    }
}
```

---

### 7.3 `list-routing-profiles`

Lists routing profiles. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-routing-profiles \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

**Output Schema:**
```json
{
    "RoutingProfileSummaryList": [ { "Id": "string", "Arn": "string", "Name": "string", "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" } ],
    "NextToken": "string"
}
```

---

### 7.4-7.7 Update Commands

`update-routing-profile-name`, `update-routing-profile-default-outbound-queue`, `update-routing-profile-concurrency`, `update-routing-profile-queues`, `update-routing-profile-agent-availability-timer` all require `--instance-id` and `--routing-profile-id` plus the specific field being updated.

**Output:** None (for all update commands)

---

### 7.8 `delete-routing-profile`

Deletes a routing profile.

**Synopsis:**
```bash
aws connect delete-routing-profile \
    --instance-id <value> \
    --routing-profile-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--routing-profile-id` | **Yes** | string | -- | Routing profile ID |

**Output:** None

---

### 7.9 `associate-routing-profile-queues`

Associates queues with a routing profile.

**Synopsis:**
```bash
aws connect associate-routing-profile-queues \
    --instance-id <value> \
    --routing-profile-id <value> \
    --queue-configs <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--routing-profile-id` | **Yes** | string | -- | Routing profile ID |
| `--queue-configs` | **Yes** | list | -- | Queue config objects with priority and delay |

**Output:** None

---

### 7.10 `list-routing-profile-queues`

Lists queues associated with a routing profile. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-routing-profile-queues \
    --instance-id <value> \
    --routing-profile-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--routing-profile-id` | **Yes** | string | -- | Routing profile ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

**Output Schema:**
```json
{
    "RoutingProfileQueueConfigSummaryList": [
        { "QueueId": "string", "QueueArn": "string", "QueueName": "string", "Priority": "integer", "Delay": "integer", "Channel": "VOICE|CHAT|TASK|EMAIL" }
    ],
    "NextToken": "string",
    "LastModifiedTime": "timestamp",
    "LastModifiedRegion": "string"
}
```

---

### 7.11 `disassociate-routing-profile-queues`

Removes queues from a routing profile.

**Synopsis:**
```bash
aws connect disassociate-routing-profile-queues \
    --instance-id <value> \
    --routing-profile-id <value> \
    --queue-references <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--routing-profile-id` | **Yes** | string | -- | Routing profile ID |
| `--queue-references` | **Yes** | list | -- | Queue references with QueueId and Channel |

**Output:** None

---

### 7.12 `search-routing-profiles`

Searches routing profiles. **Paginated operation.**

**Synopsis:**
```bash
aws connect search-routing-profiles \
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
    "RoutingProfiles": [ { "InstanceId": "string", "Name": "string", "RoutingProfileArn": "string", "RoutingProfileId": "string", "Description": "string", "MediaConcurrencies": [], "DefaultOutboundQueueId": "string", "Tags": {} } ],
    "NextToken": "string",
    "ApproximateTotalCount": "long"
}
```
