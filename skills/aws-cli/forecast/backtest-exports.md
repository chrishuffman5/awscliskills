# Backtest Exports

### 7.1 `create-predictor-backtest-export-job`

Exports predictor backtest results to S3. Includes forecasted values and actual values for backtesting windows.

**Synopsis:**
```bash
aws forecast create-predictor-backtest-export-job \
    --predictor-backtest-export-job-name <value> \
    --predictor-arn <value> \
    --destination <value> \
    [--tags <value>] \
    [--format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--predictor-backtest-export-job-name` | **Yes** | string | -- | Export job name (1-63 chars) |
| `--predictor-arn` | **Yes** | string | -- | Predictor ARN |
| `--destination` | **Yes** | structure | -- | S3 config: `S3Config={Path=string,RoleArn=string,KMSKeyArn=string}` |
| `--tags` | No | list | None | Tags |
| `--format` | No | string | `CSV` | Format: `CSV` or `PARQUET` |

**Output Schema:**
```json
{
    "PredictorBacktestExportJobArn": "string"
}
```

---

### 7.2 `describe-predictor-backtest-export-job`

Gets properties of a backtest export job.

**Synopsis:**
```bash
aws forecast describe-predictor-backtest-export-job \
    --predictor-backtest-export-job-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--predictor-backtest-export-job-arn` | **Yes** | string | -- | Export job ARN |

**Output Schema:**
```json
{
    "PredictorBacktestExportJobArn": "string",
    "PredictorBacktestExportJobName": "string",
    "PredictorArn": "string",
    "Destination": {"S3Config": {}},
    "Status": "string",
    "Message": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "Format": "string"
}
```

---

### 7.3 `list-predictor-backtest-export-jobs`

Lists backtest export jobs. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-predictor-backtest-export-jobs \
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
    "PredictorBacktestExportJobs": [
        {
            "PredictorBacktestExportJobArn": "string",
            "PredictorBacktestExportJobName": "string",
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

### 7.4 `delete-predictor-backtest-export-job`

Deletes a backtest export job.

**Synopsis:**
```bash
aws forecast delete-predictor-backtest-export-job \
    --predictor-backtest-export-job-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--predictor-backtest-export-job-arn` | **Yes** | string | -- | Export job ARN |

**Output:** None
