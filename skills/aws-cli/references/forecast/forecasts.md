# Forecasts

### 3.1 `create-forecast`

Generates a forecast from a trained predictor.

**Synopsis:**
```bash
aws forecast create-forecast \
    --forecast-name <value> \
    --predictor-arn <value> \
    [--forecast-types <value>] \
    [--tags <value>] \
    [--time-series-selector <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--forecast-name` | **Yes** | string | -- | Forecast name (1-63 chars) |
| `--predictor-arn` | **Yes** | string | -- | Predictor ARN |
| `--forecast-types` | No | list | `["0.1","0.5","0.9"]` | Quantiles (up to 5): `0.01`-`0.99` or `mean` |
| `--tags` | No | list | None | Tags |
| `--time-series-selector` | No | structure | None | Subset of time series to forecast |

**Time Series Selector Structure:**
```json
{
    "TimeSeriesIdentifiers": {
        "DataSource": {"S3Config": {"Path": "string", "RoleArn": "string"}},
        "Schema": {"Attributes": [{"AttributeName": "string", "AttributeType": "string"}]},
        "Format": "CSV|PARQUET"
    }
}
```

**Output Schema:**
```json
{
    "ForecastArn": "string"
}
```

---

### 3.2 `describe-forecast`

Gets properties of a forecast.

**Synopsis:**
```bash
aws forecast describe-forecast \
    --forecast-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--forecast-arn` | **Yes** | string | -- | Forecast ARN |

**Output Schema:**
```json
{
    "ForecastArn": "string",
    "ForecastName": "string",
    "ForecastTypes": ["string"],
    "PredictorArn": "string",
    "DatasetGroupArn": "string",
    "EstimatedTimeRemainingInMinutes": "long",
    "Status": "string",
    "Message": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "TimeSeriesSelector": {}
}
```

---

### 3.3 `list-forecasts`

Lists forecasts. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-forecasts \
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
| `--filters` | No | list | None | Filters: `Key=string,Value=string,Condition=string` |

**Output Schema:**
```json
{
    "Forecasts": [
        {
            "ForecastArn": "string",
            "ForecastName": "string",
            "PredictorArn": "string",
            "DatasetGroupArn": "string",
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

### 3.4 `delete-forecast`

Deletes a forecast.

**Synopsis:**
```bash
aws forecast delete-forecast \
    --forecast-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--forecast-arn` | **Yes** | string | -- | Forecast ARN |

**Output:** None

---

## Forecast Export Jobs

### 3.5 `create-forecast-export-job`

Exports a forecast to S3.

**Synopsis:**
```bash
aws forecast create-forecast-export-job \
    --forecast-export-job-name <value> \
    --forecast-arn <value> \
    --destination <value> \
    [--tags <value>] \
    [--format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--forecast-export-job-name` | **Yes** | string | -- | Export job name (1-63 chars) |
| `--forecast-arn` | **Yes** | string | -- | Forecast ARN |
| `--destination` | **Yes** | structure | -- | S3 config: `S3Config={Path=string,RoleArn=string,KMSKeyArn=string}` |
| `--tags` | No | list | None | Tags |
| `--format` | No | string | `CSV` | Export format: `CSV` or `PARQUET` |

**Output Schema:**
```json
{
    "ForecastExportJobArn": "string"
}
```

---

### 3.6 `describe-forecast-export-job`

Gets properties of a forecast export job.

**Synopsis:**
```bash
aws forecast describe-forecast-export-job \
    --forecast-export-job-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--forecast-export-job-arn` | **Yes** | string | -- | Export job ARN |

**Output Schema:**
```json
{
    "ForecastExportJobArn": "string",
    "ForecastExportJobName": "string",
    "ForecastArn": "string",
    "Destination": {"S3Config": {}},
    "Status": "string",
    "Message": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "Format": "string"
}
```

---

### 3.7 `list-forecast-export-jobs`

Lists forecast export jobs. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-forecast-export-jobs \
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
    "ForecastExportJobs": [
        {
            "ForecastExportJobArn": "string",
            "ForecastExportJobName": "string",
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

### 3.8 `delete-forecast-export-job`

Deletes a forecast export job.

**Synopsis:**
```bash
aws forecast delete-forecast-export-job \
    --forecast-export-job-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--forecast-export-job-arn` | **Yes** | string | -- | Export job ARN |

**Output:** None
