# Serverless Indexes & Settings

### 14.1 `create-index` (serverless)

Creates an index on an OpenSearch Serverless collection.

**Synopsis:**
```bash
aws opensearchserverless create-index \
    --collection-id <value> \
    --index-name <value> \
    [--index-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | Collection ID |
| `--index-name` | **Yes** | string | -- | Index name |
| `--index-settings` | No | structure | None | Index settings (number of shards, replicas) |

**Output Schema:**
```json
{
    "IndexName": "string",
    "Status": "CREATING|ACTIVE|DELETING|FAILED"
}
```

---

### 14.2 `delete-index` (serverless)

Deletes an index from an OpenSearch Serverless collection.

**Synopsis:**
```bash
aws opensearchserverless delete-index \
    --collection-id <value> \
    --index-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | Collection ID |
| `--index-name` | **Yes** | string | -- | Index name |

**Output Schema:**
```json
{
    "IndexName": "string",
    "Status": "DELETING"
}
```

---

### 14.3 `get-index` (serverless)

Returns details about an index on a serverless collection.

**Synopsis:**
```bash
aws opensearchserverless get-index \
    --collection-id <value> \
    --index-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | Collection ID |
| `--index-name` | **Yes** | string | -- | Index name |

**Output Schema:**
```json
{
    "IndexName": "string",
    "Status": "CREATING|ACTIVE|DELETING|FAILED"
}
```

---

### 14.4 `update-index` (serverless)

Updates an index on a serverless collection.

**Synopsis:**
```bash
aws opensearchserverless update-index \
    --collection-id <value> \
    --index-name <value> \
    [--index-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-id` | **Yes** | string | -- | Collection ID |
| `--index-name` | **Yes** | string | -- | Index name |
| `--index-settings` | No | structure | None | Updated settings |

**Output Schema:**
```json
{
    "IndexName": "string",
    "Status": "string"
}
```

---

### 14.5 `get-account-settings`

Returns account-level settings for OpenSearch Serverless.

**Synopsis:**
```bash
aws opensearchserverless get-account-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "accountSettingsDetail": {
        "capacityLimits": {
            "maxIndexingCapacityInOCU": "integer",
            "maxSearchCapacityInOCU": "integer"
        }
    }
}
```

---

### 14.6 `update-account-settings`

Updates account-level settings for OpenSearch Serverless.

**Synopsis:**
```bash
aws opensearchserverless update-account-settings \
    [--capacity-limits <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--capacity-limits` | No | structure | None | Capacity limits. Shorthand: `maxIndexingCapacityInOCU=integer,maxSearchCapacityInOCU=integer` |

**Output Schema:**
```json
{
    "accountSettingsDetail": {
        "capacityLimits": {
            "maxIndexingCapacityInOCU": "integer",
            "maxSearchCapacityInOCU": "integer"
        }
    }
}
```

---

### 14.7 `get-policies-stats`

Returns statistics about security, access, and lifecycle policies.

**Synopsis:**
```bash
aws opensearchserverless get-policies-stats \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "AccessPolicyStats": {
        "DataPolicyCount": "long"
    },
    "SecurityPolicyStats": {
        "EncryptionPolicyCount": "long",
        "NetworkPolicyCount": "long"
    },
    "SecurityConfigStats": {
        "SamlConfigCount": "long"
    },
    "LifecyclePolicyStats": {
        "RetentionPolicyCount": "long"
    },
    "TotalPolicyCount": "long"
}
```

---

### 14.8 `tag-resource` (serverless)

Adds tags to an OpenSearch Serverless resource.

**Synopsis:**
```bash
aws opensearchserverless tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `key=string,value=string ...` |

**Output:** None

---

### 14.9 `untag-resource` (serverless)

Removes tags from an OpenSearch Serverless resource.

**Synopsis:**
```bash
aws opensearchserverless untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 14.10 `list-tags-for-resource` (serverless)

Lists tags for an OpenSearch Serverless resource.

**Synopsis:**
```bash
aws opensearchserverless list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "tags": [
        {
            "key": "string",
            "value": "string"
        }
    ]
}
```
