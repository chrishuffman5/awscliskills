# Sampling

### 3.1 `create-sampling-rule`

Creates a sampling rule that controls how X-Ray samples requests for instrumented applications.

**Synopsis:**
```bash
aws xray create-sampling-rule \
    --sampling-rule <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sampling-rule` | **Yes** | structure | -- | Sampling rule definition (JSON or shorthand) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Sampling Rule Structure:**
```json
{
    "RuleName": "string",
    "RuleARN": "string",
    "ResourceARN": "string",
    "Priority": "integer",
    "FixedRate": "double",
    "ReservoirSize": "integer",
    "ServiceName": "string",
    "ServiceType": "string",
    "Host": "string",
    "HTTPMethod": "string",
    "URLPath": "string",
    "Version": 1,
    "Attributes": {
        "string": "string"
    }
}
```

**Output Schema:**
```json
{
    "SamplingRuleRecord": {
        "SamplingRule": {
            "RuleName": "string",
            "RuleARN": "string",
            "ResourceARN": "string",
            "Priority": "integer",
            "FixedRate": "double",
            "ReservoirSize": "integer",
            "ServiceName": "string",
            "ServiceType": "string",
            "Host": "string",
            "HTTPMethod": "string",
            "URLPath": "string",
            "Version": "integer",
            "Attributes": {}
        },
        "CreatedAt": "timestamp",
        "ModifiedAt": "timestamp"
    }
}
```

---

### 3.2 `delete-sampling-rule`

Deletes a sampling rule.

**Synopsis:**
```bash
aws xray delete-sampling-rule \
    [--rule-name <value>] \
    [--rule-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-name` | No | string | None | Name of the sampling rule to delete (specify either name or ARN) |
| `--rule-arn` | No | string | None | ARN of the sampling rule to delete |

**Output Schema:**
```json
{
    "SamplingRuleRecord": {
        "SamplingRule": {
            "RuleName": "string",
            "RuleARN": "string",
            "ResourceARN": "string",
            "Priority": "integer",
            "FixedRate": "double",
            "ReservoirSize": "integer",
            "ServiceName": "string",
            "ServiceType": "string",
            "Host": "string",
            "HTTPMethod": "string",
            "URLPath": "string",
            "Version": "integer",
            "Attributes": {}
        },
        "CreatedAt": "timestamp",
        "ModifiedAt": "timestamp"
    }
}
```

---

### 3.3 `get-sampling-rules`

Returns all sampling rules. **Paginated operation.**

**Synopsis:**
```bash
aws xray get-sampling-rules \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "SamplingRuleRecords": [
        {
            "SamplingRule": {
                "RuleName": "string",
                "RuleARN": "string",
                "ResourceARN": "string",
                "Priority": "integer",
                "FixedRate": "double",
                "ReservoirSize": "integer",
                "ServiceName": "string",
                "ServiceType": "string",
                "Host": "string",
                "HTTPMethod": "string",
                "URLPath": "string",
                "Version": "integer",
                "Attributes": {}
            },
            "CreatedAt": "timestamp",
            "ModifiedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `update-sampling-rule`

Modifies a sampling rule's configuration.

**Synopsis:**
```bash
aws xray update-sampling-rule \
    --sampling-rule-update <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sampling-rule-update` | **Yes** | structure | -- | Updated sampling rule definition |

**Sampling Rule Update Structure:**
```json
{
    "RuleName": "string",
    "RuleARN": "string",
    "ResourceARN": "string",
    "Priority": "integer",
    "FixedRate": "double",
    "ReservoirSize": "integer",
    "Host": "string",
    "ServiceName": "string",
    "ServiceType": "string",
    "HTTPMethod": "string",
    "URLPath": "string",
    "Attributes": {}
}
```

**Output Schema:**
```json
{
    "SamplingRuleRecord": {
        "SamplingRule": {
            "RuleName": "string",
            "RuleARN": "string",
            "ResourceARN": "string",
            "Priority": "integer",
            "FixedRate": "double",
            "ReservoirSize": "integer",
            "ServiceName": "string",
            "ServiceType": "string",
            "Host": "string",
            "HTTPMethod": "string",
            "URLPath": "string",
            "Version": "integer",
            "Attributes": {}
        },
        "CreatedAt": "timestamp",
        "ModifiedAt": "timestamp"
    }
}
```

---

### 3.5 `get-sampling-statistic-summaries`

Returns information about recent sampling results for all sampling rules. **Paginated operation.**

**Synopsis:**
```bash
aws xray get-sampling-statistic-summaries \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "SamplingStatisticSummaries": [
        {
            "RuleName": "string",
            "Timestamp": "timestamp",
            "RequestCount": "integer",
            "BorrowCount": "integer",
            "SampledCount": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.6 `get-sampling-targets`

Requests sampling target information for active sampling rules. Used by the X-Ray SDK to determine sampling decisions.

**Synopsis:**
```bash
aws xray get-sampling-targets \
    --sampling-statistics-documents <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sampling-statistics-documents` | **Yes** | list | -- | Sampling statistics from the SDK. JSON: `[{"RuleName":"string","ClientID":"string","Timestamp":"timestamp","RequestCount":"integer","SampledCount":"integer","BorrowCount":"integer"}]` |

**Output Schema:**
```json
{
    "SamplingTargetDocuments": [
        {
            "RuleName": "string",
            "FixedRate": "double",
            "ReservoirQuota": "integer",
            "ReservoirQuotaTTL": "timestamp",
            "Interval": "integer"
        }
    ],
    "LastRuleModification": "timestamp",
    "UnprocessedStatistics": [
        {
            "RuleName": "string",
            "ErrorCode": "string",
            "Message": "string"
        }
    ]
}
```
