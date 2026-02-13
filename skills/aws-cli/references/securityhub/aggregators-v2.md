# Aggregators v2

### 9.1 `create-aggregator-v2`

Creates a v2 finding aggregator for cross-Region aggregation with enhanced capabilities.

**Synopsis:**
```bash
aws securityhub create-aggregator-v2 \
    --region-linking-mode <value> \
    [--regions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--region-linking-mode` | **Yes** | string | -- | Aggregation mode: `ALL_REGIONS`, `ALL_REGIONS_EXCEPT_SPECIFIED`, `SPECIFIED_REGIONS` |
| `--regions` | No | list(string) | None | Regions to include/exclude |

**Output Schema:**
```json
{
    "AggregatorV2Arn": "string",
    "AggregationRegion": "string",
    "RegionLinkingMode": "ALL_REGIONS|ALL_REGIONS_EXCEPT_SPECIFIED|SPECIFIED_REGIONS",
    "Regions": ["string"]
}
```

---

### 9.2 `delete-aggregator-v2`

Deletes a v2 aggregator.

**Synopsis:**
```bash
aws securityhub delete-aggregator-v2 \
    --aggregator-v2-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aggregator-v2-arn` | **Yes** | string | -- | ARN of the v2 aggregator |

**Output:** None (HTTP 200 on success)

---

### 9.3 `get-aggregator-v2`

Returns details about a v2 aggregator.

**Synopsis:**
```bash
aws securityhub get-aggregator-v2 \
    --aggregator-v2-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aggregator-v2-arn` | **Yes** | string | -- | ARN of the v2 aggregator |

**Output Schema:**
```json
{
    "AggregatorV2Arn": "string",
    "AggregationRegion": "string",
    "RegionLinkingMode": "ALL_REGIONS|ALL_REGIONS_EXCEPT_SPECIFIED|SPECIFIED_REGIONS",
    "Regions": ["string"]
}
```

---

### 9.4 `list-aggregators-v2`

Lists v2 aggregators. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub list-aggregators-v2 \
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
    "AggregatorsV2": [
        {
            "AggregatorV2Arn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.5 `update-aggregator-v2`

Updates a v2 aggregator.

**Synopsis:**
```bash
aws securityhub update-aggregator-v2 \
    --aggregator-v2-arn <value> \
    --region-linking-mode <value> \
    [--regions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aggregator-v2-arn` | **Yes** | string | -- | ARN of the v2 aggregator |
| `--region-linking-mode` | **Yes** | string | -- | Aggregation mode |
| `--regions` | No | list(string) | None | Regions to include/exclude |

**Output Schema:**
```json
{
    "AggregatorV2Arn": "string",
    "AggregationRegion": "string",
    "RegionLinkingMode": "string",
    "Regions": ["string"]
}
```
