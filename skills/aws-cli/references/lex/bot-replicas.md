# Bot Replicas

### 10.1 `create-bot-replica`

Creates a bot replica in a secondary AWS region for disaster recovery or latency reduction.

**Synopsis:**
```bash
aws lexv2-models create-bot-replica \
    --bot-id <value> \
    --replica-region <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--replica-region` | **Yes** | string | -- | AWS region for the replica (2-25 chars) |

**Output Schema:**
```json
{
    "botId": "string",
    "replicaRegion": "string",
    "sourceRegion": "string",
    "creationDateTime": "timestamp",
    "botReplicaStatus": "Enabling|Enabled|Deleting|Failed"
}
```

---

### 10.2 `delete-bot-replica`

Deletes a bot replica.

**Synopsis:**
```bash
aws lexv2-models delete-bot-replica \
    --bot-id <value> \
    --replica-region <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--replica-region` | **Yes** | string | -- | Region of the replica |

**Output Schema:**
```json
{
    "botId": "string",
    "replicaRegion": "string",
    "botReplicaStatus": "Enabling|Enabled|Deleting|Failed"
}
```

---

### 10.3 `describe-bot-replica`

Gets metadata for a bot replica.

**Synopsis:**
```bash
aws lexv2-models describe-bot-replica \
    --bot-id <value> \
    --replica-region <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--replica-region` | **Yes** | string | -- | Region of the replica |

**Output Schema:**
```json
{
    "botId": "string",
    "replicaRegion": "string",
    "sourceRegion": "string",
    "creationDateTime": "timestamp",
    "botReplicaStatus": "Enabling|Enabled|Deleting|Failed",
    "failureReasons": ["string"]
}
```

---

### 10.4 `list-bot-replicas`

Lists all replicas for a bot.

**Synopsis:**
```bash
aws lexv2-models list-bot-replicas \
    --bot-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |

**Output Schema:**
```json
{
    "botId": "string",
    "sourceRegion": "string",
    "botReplicaSummaries": [
        {
            "replicaRegion": "string",
            "creationDateTime": "timestamp",
            "botReplicaStatus": "Enabling|Enabled|Deleting|Failed",
            "failureReasons": ["string"]
        }
    ]
}
```

---

### 10.5 `list-bot-alias-replicas`

Lists alias replicas for a bot in a specific replica region.

**Synopsis:**
```bash
aws lexv2-models list-bot-alias-replicas \
    --bot-id <value> \
    --replica-region <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--replica-region` | **Yes** | string | -- | Region of the replica |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "sourceRegion": "string",
    "replicaRegion": "string",
    "botAliasReplicaSummaries": [
        {
            "botAliasId": "string",
            "botAliasReplicationStatus": "Creating|Updating|Available|Deleting|Failed",
            "botVersion": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "failureReasons": ["string"]
        }
    ],
    "nextToken": "string"
}
```

---

### 10.6 `list-bot-version-replicas`

Lists version replicas for a bot in a specific replica region.

**Synopsis:**
```bash
aws lexv2-models list-bot-version-replicas \
    --bot-id <value> \
    --replica-region <value> \
    [--sort-by <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--replica-region` | **Yes** | string | -- | Region of the replica |
| `--sort-by` | No | structure | None | Sort field and order |
| `--max-results` | No | integer | None | Maximum results (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "botId": "string",
    "sourceRegion": "string",
    "replicaRegion": "string",
    "botVersionReplicaSummaries": [
        {
            "botVersion": "string",
            "botVersionReplicationStatus": "Creating|Available|Deleting|Failed",
            "creationDateTime": "timestamp",
            "failureReasons": ["string"]
        }
    ],
    "nextToken": "string"
}
```
