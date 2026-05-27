# Insights

### 3.1 `create-insight`

Creates a custom insight in Security Hub. An insight groups related findings using a group-by attribute.

**Synopsis:**
```bash
aws securityhub create-insight \
    --name <value> \
    --filters <value> \
    --group-by-attribute <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the custom insight |
| `--filters` | **Yes** | structure | -- | Filters for findings included in the insight |
| `--group-by-attribute` | **Yes** | string | -- | Attribute to group findings by |

**Output Schema:**
```json
{
    "InsightArn": "string"
}
```

---

### 3.2 `delete-insight`

Deletes the insight specified by the insight ARN.

**Synopsis:**
```bash
aws securityhub delete-insight \
    --insight-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--insight-arn` | **Yes** | string | -- | ARN of the insight to delete |

**Output Schema:**
```json
{
    "InsightArn": "string"
}
```

---

### 3.3 `get-insights`

Lists and describes insights for the specified insight ARNs. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub get-insights \
    [--insight-arns <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--insight-arns` | No | list(string) | None | ARNs of insights to describe (omit for all) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Insights": [
        {
            "InsightArn": "string",
            "Name": "string",
            "Filters": {},
            "GroupByAttribute": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `get-insight-results`

Lists the results of the Security Hub insight specified by the insight ARN.

**Synopsis:**
```bash
aws securityhub get-insight-results \
    --insight-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--insight-arn` | **Yes** | string | -- | ARN of the insight to get results for |

**Output Schema:**
```json
{
    "InsightResults": {
        "InsightArn": "string",
        "GroupByAttribute": "string",
        "ResultValues": [
            {
                "GroupByAttributeValue": "string",
                "Count": "integer"
            }
        ]
    }
}
```

---

### 3.5 `update-insight`

Updates the Security Hub insight specified by the insight ARN.

**Synopsis:**
```bash
aws securityhub update-insight \
    --insight-arn <value> \
    [--name <value>] \
    [--filters <value>] \
    [--group-by-attribute <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--insight-arn` | **Yes** | string | -- | ARN of the insight to update |
| `--name` | No | string | None | New insight name |
| `--filters` | No | structure | None | Updated filters |
| `--group-by-attribute` | No | string | None | New group-by attribute |

**Output:** None (HTTP 200 on success)
