# Metric Sets

### 2.1 `create-metric-set`

Creates a metric set (dataset) for an anomaly detector.

**Synopsis:**
```bash
aws lookoutmetrics create-metric-set \
    --anomaly-detector-arn <value> \
    --metric-set-name <value> \
    --metric-list <value> \
    --metric-source <value> \
    [--metric-set-description <value>] \
    [--metric-set-frequency <value>] \
    [--dimension-list <value>] \
    [--timestamp-column <value>] \
    [--offset <value>] \
    [--timezone <value>] \
    [--dimension-filter-list <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the anomaly detector |
| `--metric-set-name` | **Yes** | string | -- | Dataset name |
| `--metric-list` | **Yes** | list | -- | Metrics to monitor. Shorthand: `MetricName=revenue,AggregationFunction=SUM` |
| `--metric-source` | **Yes** | structure | -- | Data source configuration (JSON) |
| `--metric-set-description` | No | string | -- | Description |
| `--metric-set-frequency` | No | string | -- | Frequency: `P1D`, `PT1H`, `PT10M`, `PT5M` |
| `--dimension-list` | No | list(string) | -- | Dimension field names |
| `--timestamp-column` | No | structure | -- | Timestamp column. Shorthand: `ColumnName=string,ColumnFormat=string` |
| `--offset` | No | integer | -- | Seconds to wait after interval before ingesting |
| `--timezone` | No | string | -- | Timezone for data (e.g., `America/New_York`) |
| `--dimension-filter-list` | No | list | -- | Dimension filters (JSON) |
| `--tags` | No | map | -- | Tags as key=value pairs |

**Metric List Structure:**
```json
[
    {
        "MetricName": "string",
        "AggregationFunction": "AVG|SUM",
        "Namespace": "string"
    }
]
```

**Metric Source Structure:**
```json
{
    "S3SourceConfig": {
        "RoleArn": "string",
        "TemplatedPathList": ["string"],
        "HistoricalDataPathList": ["string"],
        "FileFormatDescriptor": {
            "CsvFormatDescriptor": {
                "FileCompression": "NONE|GZIP",
                "Charset": "string",
                "ContainsHeader": true,
                "Delimiter": "string",
                "HeaderList": ["string"],
                "QuoteSymbol": "string"
            },
            "JsonFormatDescriptor": {
                "FileCompression": "NONE|GZIP",
                "Charset": "string"
            }
        }
    },
    "AppFlowConfig": {
        "RoleArn": "string",
        "FlowName": "string"
    },
    "CloudWatchConfig": {
        "RoleArn": "string",
        "BackTestConfiguration": {
            "RunBackTestMode": true
        }
    },
    "RDSSourceConfig": {
        "DBInstanceIdentifier": "string",
        "DatabaseHost": "string",
        "DatabasePort": "integer",
        "SecretManagerArn": "string",
        "DatabaseName": "string",
        "TableName": "string",
        "RoleArn": "string",
        "VpcConfiguration": {
            "SubnetIdList": ["string"],
            "SecurityGroupIdList": ["string"]
        }
    },
    "RedshiftSourceConfig": {
        "ClusterIdentifier": "string",
        "DatabaseHost": "string",
        "DatabasePort": "integer",
        "SecretManagerArn": "string",
        "DatabaseName": "string",
        "TableName": "string",
        "RoleArn": "string",
        "VpcConfiguration": {
            "SubnetIdList": ["string"],
            "SecurityGroupIdList": ["string"]
        }
    },
    "AthenaSourceConfig": {
        "RoleArn": "string",
        "DatabaseName": "string",
        "DataCatalog": "string",
        "TableName": "string",
        "WorkGroupName": "string",
        "S3ResultsPath": "string",
        "BackTestConfiguration": {
            "RunBackTestMode": true
        }
    }
}
```

**Timestamp Column Structure:**
```json
{
    "ColumnName": "string",
    "ColumnFormat": "string"
}
```

**Output Schema:**
```json
{
    "MetricSetArn": "string"
}
```

---

### 2.2 `describe-metric-set`

Describes a metric set.

**Synopsis:**
```bash
aws lookoutmetrics describe-metric-set \
    --metric-set-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-set-arn` | **Yes** | string | -- | ARN of the metric set |

**Output Schema:**
```json
{
    "MetricSetArn": "string",
    "AnomalyDetectorArn": "string",
    "MetricSetName": "string",
    "MetricSetDescription": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "Offset": "integer",
    "MetricList": [
        {
            "MetricName": "string",
            "AggregationFunction": "AVG|SUM",
            "Namespace": "string"
        }
    ],
    "TimestampColumn": {
        "ColumnName": "string",
        "ColumnFormat": "string"
    },
    "DimensionList": ["string"],
    "MetricSetFrequency": "P1D|PT1H|PT10M|PT5M",
    "Timezone": "string",
    "MetricSource": {},
    "DimensionFilterList": []
}
```

---

### 2.3 `list-metric-sets`

Lists metric sets in the current region. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutmetrics list-metric-sets \
    [--anomaly-detector-arn <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | No | string | -- | Filter by detector ARN |
| `--max-results` | No | integer | -- | Max items to return |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "MetricSetSummaryList": [
        {
            "MetricSetArn": "string",
            "AnomalyDetectorArn": "string",
            "MetricSetName": "string",
            "MetricSetDescription": "string",
            "CreationTime": "timestamp",
            "LastModificationTime": "timestamp",
            "Tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `update-metric-set`

Updates a metric set.

**Synopsis:**
```bash
aws lookoutmetrics update-metric-set \
    --metric-set-arn <value> \
    [--metric-set-description <value>] \
    [--metric-list <value>] \
    [--offset <value>] \
    [--timestamp-column <value>] \
    [--dimension-list <value>] \
    [--metric-set-frequency <value>] \
    [--metric-source <value>] \
    [--timezone <value>] \
    [--dimension-filter-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-set-arn` | **Yes** | string | -- | ARN of the metric set to update |
| `--metric-set-description` | No | string | -- | Updated description |
| `--metric-list` | No | list | -- | Updated metric list |
| `--offset` | No | integer | -- | Updated offset in seconds |
| `--timestamp-column` | No | structure | -- | Updated timestamp column |
| `--dimension-list` | No | list(string) | -- | Updated dimension list |
| `--metric-set-frequency` | No | string | -- | Updated frequency |
| `--metric-source` | No | structure | -- | Updated data source |
| `--timezone` | No | string | -- | Updated timezone |
| `--dimension-filter-list` | No | list | -- | Updated dimension filters |

**Output Schema:**
```json
{
    "MetricSetArn": "string"
}
```

---

### 2.5 `detect-metric-set-config`

Auto-detects an S3 dataset's file format, interval, and offset.

**Synopsis:**
```bash
aws lookoutmetrics detect-metric-set-config \
    --anomaly-detector-arn <value> \
    --auto-detection-metric-source <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector |
| `--auto-detection-metric-source` | **Yes** | structure | -- | S3 source config for auto-detection (JSON) |

**Auto Detection Metric Source Structure:**
```json
{
    "S3SourceConfig": {
        "TemplatedPathList": ["string"],
        "HistoricalDataPathList": ["string"]
    }
}
```

**Output Schema:**
```json
{
    "DetectedMetricSetConfig": {
        "Offset": {
            "Value": {
                "S": "string",
                "N": "string"
            },
            "Confidence": "HIGH|LOW|NONE"
        },
        "MetricSetFrequency": {
            "Value": {
                "S": "string"
            },
            "Confidence": "HIGH|LOW|NONE"
        },
        "MetricSource": {
            "S3SourceConfig": {
                "FileFormatDescriptor": {}
            }
        }
    }
}
```

---

### 2.6 `get-sample-data`

Returns sample records from an S3 data source.

**Synopsis:**
```bash
aws lookoutmetrics get-sample-data \
    [--s3-source-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-source-config` | No | structure | -- | S3 source configuration (JSON) |

**S3 Source Config Structure:**
```json
{
    "RoleArn": "string",
    "TemplatedPathList": ["string"],
    "HistoricalDataPathList": ["string"],
    "FileFormatDescriptor": {}
}
```

**Output Schema:**
```json
{
    "HeaderValues": ["string"],
    "SampleRows": [["string"]]
}
```

---

### 2.7 `get-data-quality-metrics`

Returns data quality metrics for a detector.

**Synopsis:**
```bash
aws lookoutmetrics get-data-quality-metrics \
    --anomaly-detector-arn <value> \
    [--metric-set-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-detector-arn` | **Yes** | string | -- | ARN of the detector |
| `--metric-set-arn` | No | string | -- | Filter by metric set ARN |

**Output Schema:**
```json
{
    "AnomalyDetectorDataQualityMetricList": [
        {
            "StartTimestamp": "timestamp",
            "MetricSetDataQualityMetricList": [
                {
                    "MetricSetArn": "string",
                    "DataQualityMetricList": [
                        {
                            "MetricType": "string",
                            "MetricDescription": "string",
                            "RelatedColumnName": "string",
                            "MetricValue": "double"
                        }
                    ]
                }
            ]
        }
    ]
}
```
