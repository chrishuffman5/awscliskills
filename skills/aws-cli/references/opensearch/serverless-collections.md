# Serverless Collections

### 10.1 `create-collection`

Creates an OpenSearch Serverless collection.

**Synopsis:**
```bash
aws opensearchserverless create-collection \
    --name <value> \
    [--type <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--standby-replicas <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Collection name (3-32 chars, pattern: `[a-z][a-z0-9-]+`) |
| `--type` | No | string | `TIMESERIES` | `SEARCH`, `TIMESERIES`, or `VECTORSEARCH` |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |
| `--standby-replicas` | No | string | `ENABLED` | `ENABLED` or `DISABLED` |
| `--client-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "createCollectionDetail": {
        "id": "string",
        "name": "string",
        "status": "CREATING|DELETING|ACTIVE|FAILED",
        "type": "SEARCH|TIMESERIES|VECTORSEARCH",
        "description": "string",
        "arn": "string",
        "kmsKeyArn": "string",
        "standbyReplicas": "ENABLED|DISABLED",
        "createdDate": "long",
        "lastModifiedDate": "long"
    }
}
```

---

### 10.2 `delete-collection`

Deletes an OpenSearch Serverless collection.

**Synopsis:**
```bash
aws opensearchserverless delete-collection \
    --id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Collection ID (3-40 chars) |
| `--client-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "deleteCollectionDetail": {
        "id": "string",
        "name": "string",
        "status": "DELETING"
    }
}
```

---

### 10.3 `batch-get-collection`

Returns details about one or more collections.

**Synopsis:**
```bash
aws opensearchserverless batch-get-collection \
    [--ids <value>] \
    [--names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ids` | No* | list(string) | None | Collection IDs (max 20) |
| `--names` | No* | list(string) | None | Collection names (max 20) |

*Provide either `--ids` or `--names`.

**Output Schema:**
```json
{
    "collectionDetails": [
        {
            "id": "string",
            "name": "string",
            "status": "CREATING|DELETING|ACTIVE|FAILED",
            "type": "SEARCH|TIMESERIES|VECTORSEARCH",
            "description": "string",
            "arn": "string",
            "collectionEndpoint": "string",
            "dashboardEndpoint": "string",
            "kmsKeyArn": "string",
            "standbyReplicas": "string",
            "createdDate": "long",
            "lastModifiedDate": "long"
        }
    ],
    "collectionErrorDetails": [
        {
            "id": "string",
            "name": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 10.4 `list-collections`

Lists OpenSearch Serverless collections. **Paginated operation.**

**Synopsis:**
```bash
aws opensearchserverless list-collections \
    [--collection-filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collection-filters` | No | structure | None | Filters. Shorthand: `name=string,status=string` |

**Output Schema:**
```json
{
    "collectionSummaries": [
        {
            "id": "string",
            "name": "string",
            "status": "string",
            "arn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 10.5 `update-collection`

Updates a collection description.

**Synopsis:**
```bash
aws opensearchserverless update-collection \
    --id <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Collection ID |
| `--description` | No | string | None | Updated description |
| `--client-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "updateCollectionDetail": {
        "id": "string",
        "name": "string",
        "status": "string",
        "description": "string",
        "lastModifiedDate": "long"
    }
}
```

---

### 10.6 `create-collection-group`

Creates an OpenSearch Serverless collection group.

**Synopsis:**
```bash
aws opensearchserverless create-collection-group \
    --name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Group name (3-32 chars) |
| `--description` | No | string | None | Description |
| `--tags` | No | list | None | Tags |
| `--client-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "createCollectionGroupDetail": {
        "id": "string",
        "name": "string",
        "status": "string",
        "createdDate": "long",
        "lastModifiedDate": "long"
    }
}
```

---

### 10.7 `delete-collection-group`

Deletes a collection group.

**Synopsis:**
```bash
aws opensearchserverless delete-collection-group \
    --id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Collection group ID |

**Output Schema:**
```json
{
    "deleteCollectionGroupDetail": {
        "id": "string",
        "name": "string",
        "status": "DELETING"
    }
}
```

---

### 10.8 `batch-get-collection-group`

Returns details about multiple collection groups.

**Synopsis:**
```bash
aws opensearchserverless batch-get-collection-group \
    --ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ids` | **Yes** | list(string) | -- | Collection group IDs |

**Output Schema:**
```json
{
    "collectionGroupDetails": [],
    "collectionGroupErrorDetails": []
}
```

---

### 10.9 `list-collection-groups`

Lists collection groups. **Paginated operation.**

**Synopsis:**
```bash
aws opensearchserverless list-collection-groups \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "collectionGroupSummaries": [],
    "nextToken": "string"
}
```

---

### 10.10 `update-collection-group`

Updates a collection group.

**Synopsis:**
```bash
aws opensearchserverless update-collection-group \
    --id <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Collection group ID |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "updateCollectionGroupDetail": {
        "id": "string",
        "name": "string",
        "status": "string",
        "lastModifiedDate": "long"
    }
}
```
