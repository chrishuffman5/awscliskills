# What-If Analysis

## What-If Analyses

### 6.1 `create-what-if-analysis`

Creates a what-if scenario analysis for exploring how modifications affect forecasts.

**Synopsis:**
```bash
aws forecast create-what-if-analysis \
    --what-if-analysis-name <value> \
    --forecast-arn <value> \
    [--time-series-selector <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--what-if-analysis-name` | **Yes** | string | -- | Analysis name (1-63 chars) |
| `--forecast-arn` | **Yes** | string | -- | Baseline forecast ARN |
| `--time-series-selector` | No | structure | None | Subset of time series |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "WhatIfAnalysisArn": "string"
}
```

---

### 6.2 `describe-what-if-analysis`

Gets properties of a what-if analysis.

**Synopsis:**
```bash
aws forecast describe-what-if-analysis \
    --what-if-analysis-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--what-if-analysis-arn` | **Yes** | string | -- | What-if analysis ARN |

**Output Schema:**
```json
{
    "WhatIfAnalysisName": "string",
    "WhatIfAnalysisArn": "string",
    "ForecastArn": "string",
    "EstimatedTimeRemainingInMinutes": "long",
    "Status": "string",
    "Message": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "TimeSeriesSelector": {}
}
```

---

### 6.3 `list-what-if-analyses`

Lists what-if analyses. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-what-if-analyses \
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
    "WhatIfAnalyses": [
        {
            "WhatIfAnalysisArn": "string",
            "WhatIfAnalysisName": "string",
            "ForecastArn": "string",
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

### 6.4 `delete-what-if-analysis`

Deletes a what-if analysis. Also deletes child what-if forecasts and exports.

**Synopsis:**
```bash
aws forecast delete-what-if-analysis \
    --what-if-analysis-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--what-if-analysis-arn` | **Yes** | string | -- | What-if analysis ARN |

**Output:** None

---

## What-If Forecasts

### 6.5 `create-what-if-forecast`

Creates a what-if forecast with time-series transformations or replacement data.

**Synopsis:**
```bash
aws forecast create-what-if-forecast \
    --what-if-forecast-name <value> \
    --what-if-analysis-arn <value> \
    [--time-series-transformations <value>] \
    [--time-series-replacements-data-source <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--what-if-forecast-name` | **Yes** | string | -- | Forecast name (1-63 chars) |
| `--what-if-analysis-arn` | **Yes** | string | -- | Parent what-if analysis ARN |
| `--time-series-transformations` | No | list | None | Transformations (max 30, see below) |
| `--time-series-replacements-data-source` | No | structure | None | Replacement data from S3 |
| `--tags` | No | list | None | Tags |

**Transformations Structure:**
```json
[
    {
        "Action": {
            "AttributeName": "string",
            "Operation": "ADD|SUBTRACT|MULTIPLY|DIVIDE",
            "Value": 1.10
        },
        "TimeSeriesConditions": [
            {
                "AttributeName": "string",
                "AttributeValue": "string",
                "Condition": "EQUALS|NOT_EQUALS|LESS_THAN|GREATER_THAN"
            }
        ]
    }
]
```

**Replacements Data Source Structure:**
```json
{
    "S3Config": {"Path": "string", "RoleArn": "string", "KMSKeyArn": "string"},
    "Schema": {"Attributes": [{"AttributeName": "string", "AttributeType": "string"}]},
    "Format": "CSV|PARQUET",
    "TimestampFormat": "string"
}
```

**Output Schema:**
```json
{
    "WhatIfForecastArn": "string"
}
```

---

### 6.6 `describe-what-if-forecast`

Gets properties of a what-if forecast.

**Synopsis:**
```bash
aws forecast describe-what-if-forecast \
    --what-if-forecast-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--what-if-forecast-arn` | **Yes** | string | -- | What-if forecast ARN |

**Output Schema:**
```json
{
    "WhatIfForecastName": "string",
    "WhatIfForecastArn": "string",
    "WhatIfAnalysisArn": "string",
    "EstimatedTimeRemainingInMinutes": "long",
    "Status": "string",
    "Message": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "TimeSeriesTransformations": [],
    "TimeSeriesReplacementsDataSource": {},
    "ForecastTypes": ["string"]
}
```

---

### 6.7 `list-what-if-forecasts`

Lists what-if forecasts. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-what-if-forecasts \
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
    "WhatIfForecasts": [
        {
            "WhatIfForecastArn": "string",
            "WhatIfForecastName": "string",
            "WhatIfAnalysisArn": "string",
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

### 6.8 `delete-what-if-forecast`

Deletes a what-if forecast.

**Synopsis:**
```bash
aws forecast delete-what-if-forecast \
    --what-if-forecast-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--what-if-forecast-arn` | **Yes** | string | -- | What-if forecast ARN |

**Output:** None

---

## What-If Forecast Exports

### 6.9 `create-what-if-forecast-export`

Exports one or more what-if forecasts to S3.

**Synopsis:**
```bash
aws forecast create-what-if-forecast-export \
    --what-if-forecast-export-name <value> \
    --what-if-forecast-arns <value> \
    --destination <value> \
    [--tags <value>] \
    [--format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--what-if-forecast-export-name` | **Yes** | string | -- | Export name (1-63 chars) |
| `--what-if-forecast-arns` | **Yes** | list | -- | What-if forecast ARNs (1-50) |
| `--destination` | **Yes** | structure | -- | S3 config: `S3Config={Path=string,RoleArn=string,KMSKeyArn=string}` |
| `--tags` | No | list | None | Tags |
| `--format` | No | string | `CSV` | Format: `CSV` or `PARQUET` |

**Output Schema:**
```json
{
    "WhatIfForecastExportArn": "string"
}
```

---

### 6.10 `describe-what-if-forecast-export`

Gets properties of a what-if forecast export.

**Synopsis:**
```bash
aws forecast describe-what-if-forecast-export \
    --what-if-forecast-export-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--what-if-forecast-export-arn` | **Yes** | string | -- | Export ARN |

**Output Schema:**
```json
{
    "WhatIfForecastExportArn": "string",
    "WhatIfForecastExportName": "string",
    "WhatIfForecastArns": ["string"],
    "Destination": {"S3Config": {}},
    "Status": "string",
    "Message": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "EstimatedTimeRemainingInMinutes": "long",
    "Format": "string"
}
```

---

### 6.11 `list-what-if-forecast-exports`

Lists what-if forecast exports. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-what-if-forecast-exports \
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
    "WhatIfForecastExports": [
        {
            "WhatIfForecastExportArn": "string",
            "WhatIfForecastExportName": "string",
            "WhatIfForecastArns": ["string"],
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

### 6.12 `delete-what-if-forecast-export`

Deletes a what-if forecast export.

**Synopsis:**
```bash
aws forecast delete-what-if-forecast-export \
    --what-if-forecast-export-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--what-if-forecast-export-arn` | **Yes** | string | -- | Export ARN |

**Output:** None
