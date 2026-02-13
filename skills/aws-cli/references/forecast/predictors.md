# Predictors

### 2.1 `create-auto-predictor`

Creates an AutoPredictor with automatic algorithm selection and hyperparameter optimization.

**Synopsis:**
```bash
aws forecast create-auto-predictor \
    --predictor-name <value> \
    [--forecast-horizon <value>] \
    [--forecast-types <value>] \
    [--forecast-dimensions <value>] \
    [--forecast-frequency <value>] \
    [--data-config <value>] \
    [--encryption-config <value>] \
    [--reference-predictor-arn <value>] \
    [--optimization-metric <value>] \
    [--explain-predictor | --no-explain-predictor] \
    [--tags <value>] \
    [--monitor-config <value>] \
    [--time-alignment-boundary <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--predictor-name` | **Yes** | string | -- | Predictor name (1-63 chars) |
| `--forecast-horizon` | No | integer | None | Steps to forecast (max 500) |
| `--forecast-types` | No | list | None | Quantiles to train (up to 5): `0.01`-`0.99` or `mean` |
| `--forecast-dimensions` | No | list | None | Dimension names for grouping (1-10) |
| `--forecast-frequency` | No | string | None | Frequency (e.g., `1D`, `1H`, `15min`) |
| `--data-config` | No | structure | None | Dataset group and attribute configs (see below) |
| `--encryption-config` | No | structure | None | KMS config: `RoleArn=string,KMSKeyArn=string` |
| `--reference-predictor-arn` | No | string | None | ARN of predictor to retrain/upgrade |
| `--optimization-metric` | No | string | None | Metric: `WAPE`, `RMSE`, `AverageWeightedQuantileLoss`, `MASE`, `MAPE` |
| `--explain-predictor` | No | boolean | false | Create Explainability resource |
| `--tags` | No | list | None | Tags |
| `--monitor-config` | No | structure | None | Monitor: `MonitorName=string` |
| `--time-alignment-boundary` | No | structure | None | Aggregation boundary |

**Data Config Structure:**
```json
{
    "DatasetGroupArn": "string",
    "AttributeConfigs": [
        {
            "AttributeName": "string",
            "Transformations": {
                "aggregation": "sum|avg|first|min|max",
                "frontfill": "none",
                "middlefill": "zero|nan|value|median|mean|min|max",
                "backfill": "zero|nan|value|median|mean|min|max",
                "futurefill": "zero|value|median|mean|min|max"
            }
        }
    ],
    "AdditionalDatasets": [
        {
            "Name": "holiday|weather",
            "Configuration": {"CountryCode": ["US", "CA"]}
        }
    ]
}
```

**Notes:**
- For new predictors: specify `PredictorName`, `DatasetGroupArn`, `ForecastFrequency`, `ForecastHorizon`
- For retraining/upgrading: specify `PredictorName` and `ReferencePredictorArn` only

**Output Schema:**
```json
{
    "PredictorArn": "string"
}
```

---

### 2.2 `create-predictor`

Creates a predictor (legacy). Use `create-auto-predictor` instead.

**Synopsis:**
```bash
aws forecast create-predictor \
    --predictor-name <value> \
    --forecast-horizon <value> \
    --input-data-config <value> \
    --featurization-config <value> \
    [--algorithm-arn <value>] \
    [--forecast-types <value>] \
    [--perform-auto-ml | --no-perform-auto-ml] \
    [--auto-ml-override-strategy <value>] \
    [--perform-hpo | --no-perform-hpo] \
    [--training-parameters <value>] \
    [--evaluation-parameters <value>] \
    [--hpo-config <value>] \
    [--encryption-config <value>] \
    [--tags <value>] \
    [--optimization-metric <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--predictor-name` | **Yes** | string | -- | Predictor name (1-63 chars) |
| `--forecast-horizon` | **Yes** | integer | -- | Steps to forecast |
| `--input-data-config` | **Yes** | structure | -- | Dataset group ARN and supplementary features |
| `--featurization-config` | **Yes** | structure | -- | Forecast frequency and featurizations |
| `--algorithm-arn` | No | string | None | Algorithm ARN (or use AutoML) |
| `--forecast-types` | No | list | None | Quantiles |
| `--perform-auto-ml` | No | boolean | false | Enable AutoML |
| `--optimization-metric` | No | string | None | Metric to optimize |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "PredictorArn": "string"
}
```

---

### 2.3 `describe-auto-predictor`

Gets properties of an AutoPredictor.

**Synopsis:**
```bash
aws forecast describe-auto-predictor \
    --predictor-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--predictor-arn` | **Yes** | string | -- | Predictor ARN |

**Output Schema:**
```json
{
    "PredictorArn": "string",
    "PredictorName": "string",
    "ForecastHorizon": "integer",
    "ForecastTypes": ["string"],
    "ForecastFrequency": "string",
    "ForecastDimensions": ["string"],
    "DatasetImportJobArns": ["string"],
    "DataConfig": {},
    "EncryptionConfig": {},
    "ReferencePredictorSummary": {
        "Arn": "string",
        "State": "Active|Deleted"
    },
    "EstimatedTimeRemainingInMinutes": "long",
    "Status": "string",
    "Message": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "OptimizationMetric": "string",
    "ExplainabilityInfo": {
        "ExplainabilityArn": "string",
        "Status": "string"
    },
    "MonitorInfo": {
        "MonitorArn": "string",
        "Status": "string"
    },
    "TimeAlignmentBoundary": {}
}
```

---

### 2.4 `describe-predictor`

Gets properties of a predictor (legacy).

**Synopsis:**
```bash
aws forecast describe-predictor \
    --predictor-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--predictor-arn` | **Yes** | string | -- | Predictor ARN |

**Output Schema:**
```json
{
    "PredictorArn": "string",
    "PredictorName": "string",
    "AlgorithmArn": "string",
    "AutoMLAlgorithmArns": ["string"],
    "ForecastHorizon": "integer",
    "ForecastTypes": ["string"],
    "PerformAutoML": "boolean",
    "AutoMLOverrideStrategy": "string",
    "PerformHPO": "boolean",
    "TrainingParameters": {},
    "EvaluationParameters": {},
    "HPOConfig": {},
    "InputDataConfig": {},
    "FeaturizationConfig": {},
    "EncryptionConfig": {},
    "EstimatedTimeRemainingInMinutes": "long",
    "IsAutoPredictor": "boolean",
    "DatasetImportJobArns": ["string"],
    "Status": "string",
    "Message": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "OptimizationMetric": "string"
}
```

---

### 2.5 `list-predictors`

Lists predictors. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-predictors \
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
    "Predictors": [
        {
            "PredictorArn": "string",
            "PredictorName": "string",
            "DatasetGroupArn": "string",
            "IsAutoPredictor": "boolean",
            "ReferencePredictorSummary": {},
            "Status": "string",
            "Message": "string",
            "CreationTime": "timestamp",
            "LastModificationTime": "timestamp",
            "OptimizationMetric": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.6 `delete-predictor`

Deletes a predictor.

**Synopsis:**
```bash
aws forecast delete-predictor \
    --predictor-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--predictor-arn` | **Yes** | string | -- | Predictor ARN |

**Output:** None

---

### 2.7 `get-accuracy-metrics`

Gets predictor accuracy metrics from backtesting.

**Synopsis:**
```bash
aws forecast get-accuracy-metrics \
    --predictor-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--predictor-arn` | **Yes** | string | -- | Predictor ARN (must be ACTIVE) |

**Output Schema:**
```json
{
    "PredictorEvaluationResults": [
        {
            "AlgorithmArn": "string",
            "TestWindows": [
                {
                    "TestWindowStart": "timestamp",
                    "TestWindowEnd": "timestamp",
                    "ItemCount": "integer",
                    "EvaluationType": "SUMMARY|COMPUTED",
                    "Metrics": {
                        "RMSE": "double",
                        "WeightedQuantileLosses": [
                            {"Quantile": "double", "LossValue": "double"}
                        ],
                        "ErrorMetrics": [
                            {
                                "ForecastType": "string",
                                "WAPE": "double",
                                "RMSE": "double",
                                "MASE": "double",
                                "MAPE": "double"
                            }
                        ],
                        "AverageWeightedQuantileLoss": "double"
                    }
                }
            ]
        }
    ],
    "IsAutoPredictor": "boolean",
    "AutoMLOverrideStrategy": "string",
    "OptimizationMetric": "string"
}
```
