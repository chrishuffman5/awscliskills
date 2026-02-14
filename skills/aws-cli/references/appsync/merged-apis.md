# Merged APIs

### 9.1 `associate-merged-graphql-api`

Associates a source API with a merged API (called from the source API owner account).

**Synopsis:**
```bash
aws appsync associate-merged-graphql-api \
    --source-api-identifier <value> \
    --merged-api-identifier <value> \
    [--description <value>] \
    [--source-api-association-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-api-identifier` | **Yes** | string | -- | Source API ID or ARN |
| `--merged-api-identifier` | **Yes** | string | -- | Merged API ID or ARN |
| `--description` | No | string | None | Association description |
| `--source-api-association-config` | No | structure | None | Association configuration |

**SourceApiAssociationConfig:**
```json
{
    "mergeType": "MANUAL_MERGE|AUTO_MERGE"
}
```

**Output Schema:**
```json
{
    "sourceApiAssociation": {
        "associationId": "string",
        "associationArn": "string",
        "sourceApiId": "string",
        "sourceApiArn": "string",
        "mergedApiArn": "string",
        "mergedApiId": "string",
        "description": "string",
        "sourceApiAssociationConfig": {
            "mergeType": "MANUAL_MERGE|AUTO_MERGE"
        },
        "sourceApiAssociationStatus": "MERGE_SCHEDULED|MERGE_FAILED|MERGE_SUCCESS|MERGE_IN_PROGRESS|AUTO_MERGE_SCHEDULE_FAILED|DELETION_SCHEDULED|DELETION_IN_PROGRESS|DELETION_FAILED",
        "sourceApiAssociationStatusDetail": "string",
        "lastSuccessfulMergeDate": "timestamp"
    }
}
```

---

### 9.2 `disassociate-merged-graphql-api`

Disassociates a source API from a merged API (called from the source API owner account).

**Synopsis:**
```bash
aws appsync disassociate-merged-graphql-api \
    --source-api-identifier <value> \
    --association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-api-identifier` | **Yes** | string | -- | Source API ID or ARN |
| `--association-id` | **Yes** | string | -- | The association ID |

**Output Schema:**
```json
{
    "sourceApiAssociationStatus": "MERGE_SCHEDULED|MERGE_FAILED|MERGE_SUCCESS|MERGE_IN_PROGRESS|AUTO_MERGE_SCHEDULE_FAILED|DELETION_SCHEDULED|DELETION_IN_PROGRESS|DELETION_FAILED"
}
```

---

### 9.3 `associate-source-graphql-api`

Associates a source API with a merged API (called from the merged API owner account).

**Synopsis:**
```bash
aws appsync associate-source-graphql-api \
    --merged-api-identifier <value> \
    --source-api-identifier <value> \
    [--description <value>] \
    [--source-api-association-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--merged-api-identifier` | **Yes** | string | -- | Merged API ID or ARN |
| `--source-api-identifier` | **Yes** | string | -- | Source API ID or ARN |
| `--description` | No | string | None | Association description |
| `--source-api-association-config` | No | structure | None | Association configuration |

**Output Schema:** Same as `associate-merged-graphql-api`.

---

### 9.4 `disassociate-source-graphql-api`

Disassociates a source API from a merged API (called from the merged API owner account).

**Synopsis:**
```bash
aws appsync disassociate-source-graphql-api \
    --merged-api-identifier <value> \
    --association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--merged-api-identifier` | **Yes** | string | -- | Merged API ID or ARN |
| `--association-id` | **Yes** | string | -- | The association ID |

**Output Schema:**
```json
{
    "sourceApiAssociationStatus": "MERGE_SCHEDULED|MERGE_FAILED|MERGE_SUCCESS|MERGE_IN_PROGRESS|AUTO_MERGE_SCHEDULE_FAILED|DELETION_SCHEDULED|DELETION_IN_PROGRESS|DELETION_FAILED"
}
```

---

### 9.5 `get-source-api-association`

Retrieves a source API association for a merged API.

**Synopsis:**
```bash
aws appsync get-source-api-association \
    --merged-api-identifier <value> \
    --association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--merged-api-identifier` | **Yes** | string | -- | Merged API ID or ARN |
| `--association-id` | **Yes** | string | -- | The association ID |

**Output Schema:**
```json
{
    "sourceApiAssociation": {
        "associationId": "string",
        "associationArn": "string",
        "sourceApiId": "string",
        "sourceApiArn": "string",
        "mergedApiArn": "string",
        "mergedApiId": "string",
        "description": "string",
        "sourceApiAssociationConfig": {
            "mergeType": "MANUAL_MERGE|AUTO_MERGE"
        },
        "sourceApiAssociationStatus": "string",
        "sourceApiAssociationStatusDetail": "string",
        "lastSuccessfulMergeDate": "timestamp"
    }
}
```

---

### 9.6 `list-source-api-associations`

Lists source API associations for a merged API. **Paginated operation.**

**Synopsis:**
```bash
aws appsync list-source-api-associations \
    --api-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--api-id` | **Yes** | string | -- | The merged API ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Results per page |
| `--max-items` | No | integer | None | Max total results |

**Output Schema:**
```json
{
    "sourceApiAssociationSummaries": [
        {
            "associationId": "string",
            "associationArn": "string",
            "sourceApiId": "string",
            "sourceApiArn": "string",
            "mergedApiId": "string",
            "mergedApiArn": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.7 `update-source-api-association`

Updates a source API association configuration (e.g., merge type).

**Synopsis:**
```bash
aws appsync update-source-api-association \
    --association-id <value> \
    --merged-api-identifier <value> \
    [--description <value>] \
    [--source-api-association-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-id` | **Yes** | string | -- | The association ID |
| `--merged-api-identifier` | **Yes** | string | -- | Merged API ID or ARN |
| `--description` | No | string | None | Updated description |
| `--source-api-association-config` | No | structure | None | Updated configuration |

**Output Schema:**
```json
{
    "sourceApiAssociation": {
        "associationId": "string",
        "associationArn": "string",
        "sourceApiId": "string",
        "sourceApiArn": "string",
        "mergedApiArn": "string",
        "mergedApiId": "string",
        "description": "string",
        "sourceApiAssociationConfig": {
            "mergeType": "MANUAL_MERGE|AUTO_MERGE"
        },
        "sourceApiAssociationStatus": "string",
        "sourceApiAssociationStatusDetail": "string",
        "lastSuccessfulMergeDate": "timestamp"
    }
}
```

---

### 9.8 `start-schema-merge`

Triggers a schema merge for a merged API from a source API association. Asynchronous operation.

**Synopsis:**
```bash
aws appsync start-schema-merge \
    --association-id <value> \
    --merged-api-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-id` | **Yes** | string | -- | The association ID |
| `--merged-api-identifier` | **Yes** | string | -- | Merged API ID or ARN |

**Output Schema:**
```json
{
    "sourceApiAssociationStatus": "MERGE_SCHEDULED|MERGE_FAILED|MERGE_SUCCESS|MERGE_IN_PROGRESS|AUTO_MERGE_SCHEDULE_FAILED|DELETION_SCHEDULED|DELETION_IN_PROGRESS|DELETION_FAILED"
}
```
