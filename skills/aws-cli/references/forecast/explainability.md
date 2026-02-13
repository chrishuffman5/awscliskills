# Explainability

### 4.1 `create-explainability`

Creates an Explainability resource for a predictor or forecast. Only available for AutoPredictors.

**Synopsis:**
```bash
aws forecast create-explainability \
    --explainability-name <value> \
    --resource-arn <value> \
    --explainability-config <value> \
    [--data-source <value>] \
    [--schema <value>] \
    [--enable-visualization | --no-enable-visualization] \
    [--start-date-time <value>] \
    [--end-date-time <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--explainability-name` | **Yes** | string | -- | Name (1-63 chars) |
| `--resource-arn` | **Yes** | string | -- | Predictor or Forecast ARN |
| `--explainability-config` | **Yes** | structure | -- | Granularity config (see below) |
| `--data-source` | No | structure | None | S3 data source (required if TimeSeriesGranularity is SPECIFIC) |
| `--schema` | No | structure | None | Schema (required if TimeSeriesGranularity is SPECIFIC) |
| `--enable-visualization` | No | boolean | false | Create visualization in console |
| `--start-date-time` | No | string | None | Start time (`yyyy-MM-ddTHH:mm:ss`). Required if TimePointGranularity is SPECIFIC |
| `--end-date-time` | No | string | None | End time. Required if TimePointGranularity is SPECIFIC |
| `--tags` | No | list | None | Tags |

**Explainability Config Structure:**
```json
{
    "TimeSeriesGranularity": "ALL|SPECIFIC",
    "TimePointGranularity": "ALL|SPECIFIC"
}
```

**Notes:**
- One Explainability per predictor
- With Forecast ARN + SPECIFIC granularity: max 50 time series and 500 time points
- Predictor must include related time series, item metadata, or additional datasets

**Output Schema:**
```json
{
    "ExplainabilityArn": "string"
}
```

---

### 4.2 `describe-explainability`

Gets properties of an Explainability resource.

**Synopsis:**
```bash
aws forecast describe-explainability \
    --explainability-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--explainability-arn` | **Yes** | string | -- | Explainability ARN |

**Output Schema:**
```json
{
    "ExplainabilityArn": "string",
    "ExplainabilityName": "string",
    "ResourceArn": "string",
    "ExplainabilityConfig": {},
    "EnableVisualization": "boolean",
    "DataSource": {},
    "Schema": {},
    "StartDateTime": "string",
    "EndDateTime": "string",
    "EstimatedTimeRemainingInMinutes": "long",
    "Status": "string",
    "Message": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp"
}
```

---

### 4.3 `list-explainabilities`

Lists Explainability resources. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-explainabilities \
    [--next-token <value>] \
    [--max-results <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "Explainabilities": [
        {
            "ExplainabilityArn": "string",
            "ExplainabilityName": "string",
            "ResourceArn": "string",
            "ExplainabilityConfig": {},
            "Status": "string",
            "Message": "string",
            "CreationTime": "timestamp",
            "LastModificationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `delete-explainability`

Deletes an Explainability resource.

**Synopsis:**
```bash
aws forecast delete-explainability \
    --explainability-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--explainability-arn` | **Yes** | string | -- | Explainability ARN |

**Output:** None

---

## Explainability Exports

### 4.5 `create-explainability-export`

Exports Explainability data to S3.

**Synopsis:**
```bash
aws forecast create-explainability-export \
    --explainability-export-name <value> \
    --explainability-arn <value> \
    --destination <value> \
    [--tags <value>] \
    [--format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--explainability-export-name` | **Yes** | string | -- | Export name (1-63 chars) |
| `--explainability-arn` | **Yes** | string | -- | Explainability ARN |
| `--destination` | **Yes** | structure | -- | S3 config: `S3Config={Path=string,RoleArn=string,KMSKeyArn=string}` |
| `--tags` | No | list | None | Tags |
| `--format` | No | string | `CSV` | Format: `CSV` or `PARQUET` |

**Output Schema:**
```json
{
    "ExplainabilityExportArn": "string"
}
```

---

### 4.6 `describe-explainability-export`

Gets properties of an Explainability export.

**Synopsis:**
```bash
aws forecast describe-explainability-export \
    --explainability-export-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--explainability-export-arn` | **Yes** | string | -- | Export ARN |

**Output Schema:**
```json
{
    "ExplainabilityExportArn": "string",
    "ExplainabilityExportName": "string",
    "ExplainabilityArn": "string",
    "Destination": {"S3Config": {}},
    "Status": "string",
    "Message": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "Format": "string"
}
```

---

### 4.7 `list-explainability-exports`

Lists Explainability exports. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-explainability-exports \
    [--next-token <value>] \
    [--max-results <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "ExplainabilityExports": [
        {
            "ExplainabilityExportArn": "string",
            "ExplainabilityExportName": "string",
            "ExplainabilityArn": "string",
            "Destination": {},
            "Status": "string",
            "Message": "string",
            "CreationTime": "timestamp",
            "LastModificationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.8 `delete-explainability-export`

Deletes an Explainability export.

**Synopsis:**
```bash
aws forecast delete-explainability-export \
    --explainability-export-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--explainability-export-arn` | **Yes** | string | -- | Export ARN |

**Output:** None
