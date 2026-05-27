# Indexing

### 6.1 `get-indexing-rules`

Returns the indexing rules configuration for the account.

**Synopsis:**
```bash
aws xray get-indexing-rules \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No required parameters.

**Output Schema:**
```json
{
    "IndexingRules": [
        {
            "Name": "string",
            "ModifiedAt": "timestamp",
            "Rule": {
                "Probabilistic": {
                    "DesiredSamplingPercentage": "double",
                    "ActualSamplingPercentage": "double"
                }
            }
        }
    ]
}
```

---

### 6.2 `update-indexing-rule`

Updates an indexing rule configuration.

**Synopsis:**
```bash
aws xray update-indexing-rule \
    --name <value> \
    --rule <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the indexing rule to update |
| `--rule` | **Yes** | structure | -- | Updated rule configuration. JSON: `{"Probabilistic":{"DesiredSamplingPercentage":double}}` |

**Output Schema:**
```json
{
    "IndexingRule": {
        "Name": "string",
        "ModifiedAt": "timestamp",
        "Rule": {
            "Probabilistic": {
                "DesiredSamplingPercentage": "double",
                "ActualSamplingPercentage": "double"
            }
        }
    }
}
```
