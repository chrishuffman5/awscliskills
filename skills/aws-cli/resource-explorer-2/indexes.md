# Indexes

### 1.1 `create-index`

Creates a Resource Explorer index in the current AWS Region. This turns on Resource Explorer for that Region and begins discovering resources.

**Synopsis:**
```bash
aws resource-explorer-2 create-index \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-token` | No | string | None | Idempotency token (UUID) |
| `--tags` | No | map | None | Tags for the index. Shorthand: `key1=value1,key2=value2` |

**Output Schema:**
```json
{
    "Arn": "string",
    "CreatedAt": "timestamp",
    "State": "CREATING|ACTIVE|DELETING|DELETED|UPDATING"
}
```

---

### 1.2 `delete-index`

Deletes the Resource Explorer index in the specified Region. Turns off Resource Explorer and deletes all views in that Region.

**Synopsis:**
```bash
aws resource-explorer-2 delete-index \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the index to delete |

**Output Schema:**
```json
{
    "Arn": "string",
    "State": "CREATING|ACTIVE|DELETING|DELETED|UPDATING",
    "LastUpdatedAt": "timestamp"
}
```

> After deleting an aggregator index, wait 24 hours before promoting another local index to aggregator.

---

### 1.3 `get-index`

Retrieves details about the Resource Explorer index in the current Region.

**Synopsis:**
```bash
aws resource-explorer-2 get-index \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None (uses current Region).

**Output Schema:**
```json
{
    "Arn": "string",
    "Type": "LOCAL|AGGREGATOR",
    "State": "CREATING|ACTIVE|DELETING|DELETED|UPDATING",
    "ReplicatingFrom": ["string"],
    "ReplicatingTo": ["string"],
    "CreatedAt": "timestamp",
    "LastUpdatedAt": "timestamp",
    "Tags": { "string": "string" }
}
```

> `ReplicatingFrom` is present only for AGGREGATOR indexes. `ReplicatingTo` is present only for LOCAL indexes.

---

### 1.4 `list-indexes`

Lists Resource Explorer indexes across Regions. **Paginated.**

**Synopsis:**
```bash
aws resource-explorer-2 list-indexes \
    [--type <value>] \
    [--regions <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | No | string | None | Filter by `LOCAL` or `AGGREGATOR` |
| `--regions` | No | list(string) | None | Filter by Regions (0-20) |

**Output Schema:**
```json
{
    "Indexes": [
        {
            "Region": "string",
            "Arn": "string",
            "Type": "LOCAL|AGGREGATOR"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-index-type`

Promotes a local index to aggregator or demotes an aggregator to local. Asynchronous.

**Synopsis:**
```bash
aws resource-explorer-2 update-index-type \
    --arn <value> \
    --type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the index to update |
| `--type` | **Yes** | string | -- | New type: `LOCAL` or `AGGREGATOR` |

**Output Schema:**
```json
{
    "Arn": "string",
    "Type": "LOCAL|AGGREGATOR",
    "State": "CREATING|ACTIVE|DELETING|DELETED|UPDATING",
    "LastUpdatedAt": "timestamp"
}
```

---

### 1.6 `list-indexes-for-members`

Lists indexes for specified Organization member accounts. **Paginated.**

**Synopsis:**
```bash
aws resource-explorer-2 list-indexes-for-members \
    --account-id-list <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id-list` | **Yes** | list(string) | -- | Account IDs to query (1-10) |

**Output Schema:**
```json
{
    "Indexes": [
        {
            "AccountId": "string",
            "Region": "string",
            "Arn": "string",
            "Type": "LOCAL|AGGREGATOR"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.7 `get-service-index`

Retrieves the service-managed index in the current Region.

**Synopsis:**
```bash
aws resource-explorer-2 get-service-index \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None.

**Output Schema:**
```json
{
    "Arn": "string",
    "Type": "LOCAL|AGGREGATOR"
}
```

---

### 1.8 `list-service-indexes`

Lists service-managed indexes across Regions. **Paginated.**

**Synopsis:**
```bash
aws resource-explorer-2 list-service-indexes \
    [--regions <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--regions` | No | list(string) | None | Filter by Regions (0-20) |

**Output Schema:**
```json
{
    "Indexes": [
        {
            "Region": "string",
            "Arn": "string",
            "Type": "LOCAL|AGGREGATOR"
        }
    ],
    "NextToken": "string"
}
```
