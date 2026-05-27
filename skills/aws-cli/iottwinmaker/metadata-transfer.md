# Metadata Transfer

### 7.1 `create-metadata-transfer-job`

Creates a metadata transfer job between IoT TwinMaker, SiteWise, and S3.

**Synopsis:**
```bash
aws iottwinmaker create-metadata-transfer-job \
    --sources <value> \
    --destination <value> \
    [--metadata-transfer-job-id <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sources` | **Yes** | list | -- | Transfer sources (max 1) |
| `--destination` | **Yes** | structure | -- | Transfer destination |
| `--metadata-transfer-job-id` | No | string | Auto | Job ID (1-128 chars) |
| `--description` | No | string | None | Description (0-2048 chars) |

**Source/Destination Structure:**
```json
{
    "type": "s3|iotsitewise|iottwinmaker",
    "s3Configuration": {
        "location": "string"
    },
    "iotSiteWiseConfiguration": {
        "filters": [
            {"filterByAssetModel": {"assetModelId": "string"}},
            {"filterByAsset": {"assetId": "string"}}
        ]
    },
    "iotTwinMakerConfiguration": {
        "workspace": "string",
        "filters": [
            {"filterByComponentType": {"componentTypeId": "string"}},
            {"filterByEntity": {"entityId": "string"}}
        ]
    }
}
```

**Output Schema:**
```json
{
    "metadataTransferJobId": "string",
    "arn": "string",
    "creationDateTime": "timestamp",
    "status": {
        "state": "VALIDATING|PENDING|RUNNING|CANCELLING|ERROR|COMPLETED|CANCELLED",
        "error": {"code": "string", "message": "string"},
        "queuedPosition": "integer"
    }
}
```

---

### 7.2 `get-metadata-transfer-job`

Gets details of a metadata transfer job.

**Synopsis:**
```bash
aws iottwinmaker get-metadata-transfer-job \
    --metadata-transfer-job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metadata-transfer-job-id` | **Yes** | string | -- | Job ID |

**Output Schema:**
```json
{
    "metadataTransferJobId": "string",
    "arn": "string",
    "description": "string",
    "sources": [],
    "destination": {},
    "metadataTransferJobRole": "string",
    "reportUrl": "string",
    "creationDateTime": "timestamp",
    "updateDateTime": "timestamp",
    "status": {
        "state": "VALIDATING|PENDING|RUNNING|CANCELLING|ERROR|COMPLETED|CANCELLED",
        "error": {},
        "queuedPosition": "integer"
    },
    "progress": {
        "totalCount": "integer",
        "succeededCount": "integer",
        "skippedCount": "integer",
        "failedCount": "integer"
    }
}
```

---

### 7.3 `list-metadata-transfer-jobs`

Lists metadata transfer jobs. **Paginated operation.**

**Synopsis:**
```bash
aws iottwinmaker list-metadata-transfer-jobs \
    --destination-type <value> \
    --source-type <value> \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-type` | **Yes** | string | -- | `s3`, `iotsitewise`, or `iottwinmaker` |
| `--source-type` | **Yes** | string | -- | `s3`, `iotsitewise`, or `iottwinmaker` |
| `--filters` | No | list | None | Filters (by `workspaceId`, `state`) |
| `--max-results` | No | integer | 25 | Max results per page (1-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "metadataTransferJobSummaries": [
        {
            "metadataTransferJobId": "string",
            "arn": "string",
            "creationDateTime": "timestamp",
            "updateDateTime": "timestamp",
            "status": {"state": "string", "error": {}},
            "progress": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 7.4 `cancel-metadata-transfer-job`

Cancels a metadata transfer job.

**Synopsis:**
```bash
aws iottwinmaker cancel-metadata-transfer-job \
    --metadata-transfer-job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metadata-transfer-job-id` | **Yes** | string | -- | Job ID |

**Output Schema:**
```json
{
    "metadataTransferJobId": "string",
    "arn": "string",
    "updateDateTime": "timestamp",
    "status": {
        "state": "CANCELLING",
        "error": {}
    },
    "progress": {}
}
```
