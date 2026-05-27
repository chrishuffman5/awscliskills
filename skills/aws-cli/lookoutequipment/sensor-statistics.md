# Sensor Statistics

### 6.1 `list-sensor-statistics`

Lists data quality statistics for sensors in a dataset, including missing values, invalid values, duplicate timestamps, and data quality indicators. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutequipment list-sensor-statistics \
    --dataset-name <value> \
    [--ingestion-job-id <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-name` | **Yes** | string | -- | Name of the dataset |
| `--ingestion-job-id` | No | string | None | Filter by specific ingestion job ID |
| `--max-results` | No | integer | None | Max results per page (1-500) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "SensorStatisticsSummaries": [
        {
            "ComponentName": "string",
            "SensorName": "string",
            "DataExists": "boolean",
            "MissingValues": {
                "Count": "integer",
                "Percentage": "float"
            },
            "InvalidValues": {
                "Count": "integer",
                "Percentage": "float"
            },
            "InvalidDateEntries": {
                "Count": "integer",
                "Percentage": "float"
            },
            "DuplicateTimestamps": {
                "Count": "integer",
                "Percentage": "float"
            },
            "CategoricalValues": {
                "Status": "POTENTIAL_ISSUE_DETECTED|NO_ISSUE_DETECTED",
                "NumberOfCategory": "integer"
            },
            "MultipleOperatingModes": {
                "Status": "POTENTIAL_ISSUE_DETECTED|NO_ISSUE_DETECTED"
            },
            "LargeTimestampGaps": {
                "Status": "POTENTIAL_ISSUE_DETECTED|NO_ISSUE_DETECTED",
                "NumberOfLargeTimestampGaps": "integer",
                "MaxTimestampGapInDays": "integer"
            },
            "MonotonicValues": {
                "Status": "POTENTIAL_ISSUE_DETECTED|NO_ISSUE_DETECTED",
                "Monotonicity": "DECREASING|INCREASING|STATIC"
            },
            "DataStartTime": "timestamp",
            "DataEndTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
