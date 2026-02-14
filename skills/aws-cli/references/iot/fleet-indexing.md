# Fleet Indexing

## 11.1 `get-indexing-configuration`

Gets the fleet indexing configuration.

**Synopsis:**
```bash
aws iot get-indexing-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "thingIndexingConfiguration": {
        "thingIndexingMode": "OFF|REGISTRY|REGISTRY_AND_SHADOW",
        "thingConnectivityIndexingMode": "OFF|STATUS",
        "deviceDefenderIndexingMode": "OFF|VIOLATIONS",
        "namedShadowIndexingMode": "OFF|ON",
        "managedFields": [{"name": "string", "type": "Number|String|Boolean"}],
        "customFields": [{"name": "string", "type": "Number|String|Boolean"}],
        "filter": {"namedShadowNames": ["string"], "geoLocations": []}
    },
    "thingGroupIndexingConfiguration": {
        "thingGroupIndexingMode": "OFF|ON",
        "managedFields": [],
        "customFields": []
    }
}
```

---

## 11.2 `update-indexing-configuration`

Updates the fleet indexing configuration.

**Synopsis:**
```bash
aws iot update-indexing-configuration \
    [--thing-indexing-configuration <value>] \
    [--thing-group-indexing-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-indexing-configuration` | No | structure | None | Thing indexing config (thingIndexingMode, thingConnectivityIndexingMode, customFields, etc.) |
| `--thing-group-indexing-configuration` | No | structure | None | Thing group indexing config |

**Output:** None

---

## 11.3 `describe-index`

Describes an index.

**Synopsis:**
```bash
aws iot describe-index \
    --index-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-name` | **Yes** | string | -- | Index name (default: `AWS_Things`) |

**Output Schema:**
```json
{
    "indexName": "string",
    "indexStatus": "ACTIVE|BUILDING|REBUILDING",
    "schema": "string"
}
```

---

## 11.4 `list-indices`

Lists fleet indices. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-indices \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "indexNames": ["string"],
    "nextToken": "string"
}
```

---

## 11.5 `search-index`

Searches the fleet index using a query string.

**Synopsis:**
```bash
aws iot search-index \
    --query-string <value> \
    [--index-name <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--query-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-string` | **Yes** | string | -- | Query string (see IoT query syntax) |
| `--index-name` | No | string | AWS_Things | Index to search |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--query-version` | No | string | None | Query version |

**Output Schema:**
```json
{
    "nextToken": "string",
    "things": [
        {
            "thingName": "string",
            "thingId": "string",
            "thingTypeName": "string",
            "thingGroupNames": ["string"],
            "attributes": {"string": "string"},
            "shadow": "string",
            "deviceDefender": "string",
            "connectivity": {
                "connected": "boolean",
                "timestamp": "long",
                "disconnectReason": "string"
            }
        }
    ],
    "thingGroups": [
        {
            "thingGroupName": "string",
            "thingGroupId": "string",
            "thingGroupDescription": "string",
            "attributes": {},
            "parentGroupNames": ["string"]
        }
    ]
}
```

---

## 11.6 `get-statistics`

Gets aggregate statistics from the fleet index.

**Synopsis:**
```bash
aws iot get-statistics \
    --query-string <value> \
    [--index-name <value>] \
    [--aggregation-field <value>] \
    [--query-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-string` | **Yes** | string | -- | Query string |
| `--index-name` | No | string | AWS_Things | Index name |
| `--aggregation-field` | No | string | None | Field to aggregate |
| `--query-version` | No | string | None | Query version |

**Output Schema:**
```json
{
    "statistics": {
        "count": "integer",
        "average": "double",
        "sum": "double",
        "minimum": "double",
        "maximum": "double",
        "sumOfSquares": "double",
        "variance": "double",
        "stdDeviation": "double"
    }
}
```

---

## 11.7 `get-cardinality`

Gets the count of unique values for a field.

**Synopsis:**
```bash
aws iot get-cardinality \
    --query-string <value> \
    [--index-name <value>] \
    [--aggregation-field <value>] \
    [--query-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-string` | **Yes** | string | -- | Query string |
| `--index-name` | No | string | AWS_Things | Index name |
| `--aggregation-field` | No | string | None | Field to count |
| `--query-version` | No | string | None | Query version |

**Output Schema:**
```json
{
    "cardinality": "integer"
}
```

---

## 11.8 `get-percentiles`

Gets percentile values from the fleet index.

**Synopsis:**
```bash
aws iot get-percentiles \
    --query-string <value> \
    [--index-name <value>] \
    [--aggregation-field <value>] \
    [--query-version <value>] \
    [--percents <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-string` | **Yes** | string | -- | Query string |
| `--index-name` | No | string | AWS_Things | Index name |
| `--aggregation-field` | No | string | None | Field to compute percentiles |
| `--query-version` | No | string | None | Query version |
| `--percents` | No | list | None | Percentile values (e.g., 25, 50, 75, 99) |

**Output Schema:**
```json
{
    "percentiles": [
        {"percent": "double", "value": "double"}
    ]
}
```

---

## 11.9 `get-buckets-aggregation`

Gets bucketed aggregation results from the fleet index.

**Synopsis:**
```bash
aws iot get-buckets-aggregation \
    --query-string <value> \
    --aggregation-field <value> \
    --buckets-aggregation-type <value> \
    [--index-name <value>] \
    [--query-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-string` | **Yes** | string | -- | Query string |
| `--aggregation-field` | **Yes** | string | -- | Field to aggregate |
| `--buckets-aggregation-type` | **Yes** | structure | -- | Aggregation type (termsAggregation with maxBuckets) |
| `--index-name` | No | string | AWS_Things | Index name |
| `--query-version` | No | string | None | Query version |

**Output Schema:**
```json
{
    "totalCount": "integer",
    "buckets": [
        {"keyValue": "string", "count": "integer"}
    ]
}
```

---

## 11.10 `create-fleet-metric`

Creates a fleet metric for aggregated monitoring.

**Synopsis:**
```bash
aws iot create-fleet-metric \
    --metric-name <value> \
    --query-string <value> \
    --aggregation-type <value> \
    --period <value> \
    --aggregation-field <value> \
    [--description <value>] \
    [--query-version <value>] \
    [--index-name <value>] \
    [--unit <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-name` | **Yes** | string | -- | Metric name (1-128 chars) |
| `--query-string` | **Yes** | string | -- | Query string |
| `--aggregation-type` | **Yes** | structure | -- | `{name: "Statistics"|"Percentiles"|"Cardinality", values: []}` |
| `--period` | **Yes** | integer | -- | Emission period in seconds (60-86400, multiple of 60) |
| `--aggregation-field` | **Yes** | string | -- | Field to aggregate |
| `--description` | No | string | None | Description |
| `--query-version` | No | string | None | Query version |
| `--index-name` | No | string | None | Index name |
| `--unit` | No | string | None | CloudWatch unit |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "metricName": "string",
    "metricArn": "string"
}
```

---

## 11.11 `describe-fleet-metric`

Describes a fleet metric.

**Synopsis:**
```bash
aws iot describe-fleet-metric \
    --metric-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-name` | **Yes** | string | -- | Metric name |

**Output Schema:**
```json
{
    "metricName": "string",
    "queryString": "string",
    "aggregationType": {},
    "period": "integer",
    "aggregationField": "string",
    "description": "string",
    "queryVersion": "string",
    "indexName": "string",
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp",
    "unit": "string",
    "version": "long",
    "metricArn": "string"
}
```

---

## 11.12 `list-fleet-metrics`

Lists fleet metrics. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-fleet-metrics \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "fleetMetrics": [
        {"metricName": "string", "metricArn": "string"}
    ],
    "nextToken": "string"
}
```

---

## 11.13 `update-fleet-metric`

Updates a fleet metric.

**Synopsis:**
```bash
aws iot update-fleet-metric \
    --metric-name <value> \
    --index-name <value> \
    [--query-string <value>] \
    [--aggregation-type <value>] \
    [--period <value>] \
    [--aggregation-field <value>] \
    [--description <value>] \
    [--query-version <value>] \
    [--unit <value>] \
    [--expected-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-name` | **Yes** | string | -- | Metric name |
| `--index-name` | **Yes** | string | -- | Index name |
| `--query-string` | No | string | None | Updated query |
| `--aggregation-type` | No | structure | None | Updated aggregation |
| `--period` | No | integer | None | Updated period |
| `--aggregation-field` | No | string | None | Updated field |
| `--description` | No | string | None | Updated description |
| `--query-version` | No | string | None | Query version |
| `--unit` | No | string | None | Updated unit |
| `--expected-version` | No | long | None | Expected version |

**Output:** None

---

## 11.14 `delete-fleet-metric`

Deletes a fleet metric.

**Synopsis:**
```bash
aws iot delete-fleet-metric \
    --metric-name <value> \
    [--expected-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-name` | **Yes** | string | -- | Metric name |
| `--expected-version` | No | long | None | Expected version |

**Output:** None
