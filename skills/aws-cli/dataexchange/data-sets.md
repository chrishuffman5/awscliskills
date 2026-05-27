# Data Sets

## 1.1 `create-data-set`

Creates a new data set.

**Synopsis:**
```bash
aws dataexchange create-data-set \
    --asset-type <value> \
    --description <value> \
    --name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-type` | **Yes** | string | -- | Asset type: `S3_SNAPSHOT`, `REDSHIFT_DATA_SHARE`, `API_GATEWAY_API`, `S3_DATA_ACCESS`, `LAKE_FORMATION_DATA_PERMISSION` |
| `--description` | **Yes** | string | -- | Description (max 16,348 chars) |
| `--name` | **Yes** | string | -- | Name of the data set |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "Arn": "string",
    "AssetType": "S3_SNAPSHOT|REDSHIFT_DATA_SHARE|API_GATEWAY_API|S3_DATA_ACCESS|LAKE_FORMATION_DATA_PERMISSION",
    "CreatedAt": "timestamp",
    "Description": "string",
    "Id": "string",
    "Name": "string",
    "Origin": "OWNED|ENTITLED",
    "OriginDetails": {
        "ProductId": "string",
        "DataGrantId": "string"
    },
    "SourceId": "string",
    "Tags": { "string": "string" },
    "UpdatedAt": "timestamp"
}
```

---

## 1.2 `get-data-set`

Returns details for a data set.

**Synopsis:**
```bash
aws dataexchange get-data-set \
    --data-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |

**Output Schema:**
```json
{
    "Arn": "string",
    "AssetType": "string",
    "CreatedAt": "timestamp",
    "Description": "string",
    "Id": "string",
    "Name": "string",
    "Origin": "OWNED|ENTITLED",
    "OriginDetails": {
        "ProductId": "string",
        "DataGrantId": "string"
    },
    "SourceId": "string",
    "Tags": { "string": "string" },
    "UpdatedAt": "timestamp"
}
```

---

## 1.3 `list-data-sets`

Lists data sets owned by or entitled to the account. **Paginated operation.**

**Synopsis:**
```bash
aws dataexchange list-data-sets \
    [--origin <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--origin` | No | string | None | Filter by origin: `OWNED` or `ENTITLED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DataSets": [
        {
            "Arn": "string",
            "AssetType": "string",
            "CreatedAt": "timestamp",
            "Description": "string",
            "Id": "string",
            "Name": "string",
            "Origin": "OWNED|ENTITLED",
            "OriginDetails": {},
            "SourceId": "string",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 1.4 `update-data-set`

Updates a data set's name or description.

**Synopsis:**
```bash
aws dataexchange update-data-set \
    --data-set-id <value> \
    [--description <value>] \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--description` | No | string | None | Updated description |
| `--name` | No | string | None | Updated name |

**Output Schema:**
```json
{
    "Arn": "string",
    "AssetType": "string",
    "CreatedAt": "timestamp",
    "Description": "string",
    "Id": "string",
    "Name": "string",
    "Origin": "string",
    "OriginDetails": {},
    "SourceId": "string",
    "UpdatedAt": "timestamp"
}
```

---

## 1.5 `delete-data-set`

Deletes a data set. All revisions must be deleted first.

**Synopsis:**
```bash
aws dataexchange delete-data-set \
    --data-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID to delete |

**Output Schema:**

None (HTTP 204 on success).

---

## 1.6 `send-data-set-notification`

Sends a notification to subscribers of a data set.

**Synopsis:**
```bash
aws dataexchange send-data-set-notification \
    --data-set-id <value> \
    --type <value> \
    [--scope <value>] \
    [--client-token <value>] \
    [--comment <value>] \
    [--details <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--type` | **Yes** | string | -- | Notification type: `DATA_DELAY`, `DATA_UPDATE`, `DEPRECATION`, `SCHEMA_CHANGE` |
| `--scope` | No | structure | None | Scope of affected resources (LakeFormationTagPolicies, RedshiftDataShares, S3DataAccesses) |
| `--client-token` | No | string | None | Idempotency token |
| `--comment` | No | string | None | Free-form comment (max 4096 chars) |
| `--details` | No | structure | None | Notification-type-specific details |

**Output Schema:**

None (HTTP 202 on success).
