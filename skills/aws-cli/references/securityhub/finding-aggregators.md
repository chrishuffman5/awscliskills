# Finding Aggregators

### 8.1 `create-finding-aggregator`

Creates a finding aggregator for cross-Region aggregation.

**Synopsis:**
```bash
aws securityhub create-finding-aggregator \
    --region-linking-mode <value> \
    [--regions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--region-linking-mode` | **Yes** | string | -- | Aggregation mode: `ALL_REGIONS`, `ALL_REGIONS_EXCEPT_SPECIFIED`, `SPECIFIED_REGIONS` |
| `--regions` | No | list(string) | None | Regions to include/exclude based on linking mode |

**Output Schema:**
```json
{
    "FindingAggregatorArn": "string",
    "FindingAggregationRegion": "string",
    "RegionLinkingMode": "ALL_REGIONS|ALL_REGIONS_EXCEPT_SPECIFIED|SPECIFIED_REGIONS",
    "Regions": ["string"]
}
```

---

### 8.2 `delete-finding-aggregator`

Deletes a finding aggregator.

**Synopsis:**
```bash
aws securityhub delete-finding-aggregator \
    --finding-aggregator-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-aggregator-arn` | **Yes** | string | -- | ARN of the finding aggregator |

**Output:** None (HTTP 200 on success)

---

### 8.3 `get-finding-aggregator`

Returns details about a finding aggregator.

**Synopsis:**
```bash
aws securityhub get-finding-aggregator \
    --finding-aggregator-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-aggregator-arn` | **Yes** | string | -- | ARN of the finding aggregator |

**Output Schema:**
```json
{
    "FindingAggregatorArn": "string",
    "FindingAggregationRegion": "string",
    "RegionLinkingMode": "ALL_REGIONS|ALL_REGIONS_EXCEPT_SPECIFIED|SPECIFIED_REGIONS",
    "Regions": ["string"]
}
```

---

### 8.4 `list-finding-aggregators`

Lists all finding aggregators. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub list-finding-aggregators \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "FindingAggregators": [
        {
            "FindingAggregatorArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `update-finding-aggregator`

Updates the finding aggregator configuration.

**Synopsis:**
```bash
aws securityhub update-finding-aggregator \
    --finding-aggregator-arn <value> \
    --region-linking-mode <value> \
    [--regions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-aggregator-arn` | **Yes** | string | -- | ARN of the finding aggregator |
| `--region-linking-mode` | **Yes** | string | -- | Aggregation mode |
| `--regions` | No | list(string) | None | Regions to include/exclude |

**Output Schema:**
```json
{
    "FindingAggregatorArn": "string",
    "FindingAggregationRegion": "string",
    "RegionLinkingMode": "string",
    "Regions": ["string"]
}
```
