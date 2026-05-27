# Resource Evaluation

### 8.1 `put-evaluations`

Used by custom Config rule Lambda functions to submit evaluation results. Called from within the Lambda function.

**Synopsis:**
```bash
aws configservice put-evaluations \
    --result-token <value> \
    [--evaluations <value>] \
    [--test-mode | --no-test-mode] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--result-token` | **Yes** | string | -- | Token from the Config event passed to the Lambda function |
| `--evaluations` | No | list | None | Evaluation results. Shorthand: `ComplianceResourceType=string,ComplianceResourceId=string,ComplianceType=string,Annotation=string,OrderingTimestamp=timestamp ...` |
| `--test-mode` | No | boolean | false | Test mode; evaluations are not stored |

**Output Schema:**
```json
{
    "FailedEvaluations": [
        {
            "ComplianceResourceType": "string",
            "ComplianceResourceId": "string",
            "ComplianceType": "COMPLIANT|NON_COMPLIANT|NOT_APPLICABLE|INSUFFICIENT_DATA",
            "Annotation": "string",
            "OrderingTimestamp": "timestamp"
        }
    ]
}
```

---

### 8.2 `start-resource-evaluation`

Starts evaluating a resource against a proactive Config rule.

**Synopsis:**
```bash
aws configservice start-resource-evaluation \
    --resource-details <value> \
    --evaluation-mode <value> \
    [--evaluation-context <value>] \
    [--evaluation-timeout <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-details` | **Yes** | structure | -- | Resource to evaluate |
| `--evaluation-mode` | **Yes** | string | -- | Evaluation mode: `DETECTIVE` or `PROACTIVE` |
| `--evaluation-context` | No | structure | None | Evaluation context identifier |
| `--evaluation-timeout` | No | integer | None | Timeout in seconds |

**Resource Details Structure:**
```json
{
    "ResourceId": "string",
    "ResourceType": "string",
    "ResourceConfiguration": "string",
    "ResourceConfigurationSchemaType": "CFN_RESOURCE_SCHEMA"
}
```

**Output Schema:**
```json
{
    "ResourceEvaluationId": "string"
}
```

---

### 8.3 `get-resource-evaluation-summary`

Returns a summary of a resource evaluation.

**Synopsis:**
```bash
aws configservice get-resource-evaluation-summary \
    --resource-evaluation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-evaluation-id` | **Yes** | string | -- | Resource evaluation ID |

**Output Schema:**
```json
{
    "ResourceEvaluationId": "string",
    "EvaluationMode": "DETECTIVE|PROACTIVE",
    "EvaluationStatus": {
        "Status": "IN_PROGRESS|FAILED|SUCCEEDED",
        "FailureReason": "string"
    },
    "EvaluationStartTimestamp": "timestamp",
    "Compliance": "COMPLIANT|NON_COMPLIANT|NOT_APPLICABLE|INSUFFICIENT_DATA",
    "EvaluationContext": {
        "EvaluationContextIdentifier": "string"
    },
    "ResourceDetails": {
        "ResourceId": "string",
        "ResourceType": "string",
        "ResourceConfiguration": "string",
        "ResourceConfigurationSchemaType": "string"
    }
}
```

---

### 8.4 `list-resource-evaluations`

Lists resource evaluations. **Paginated operation.**

**Synopsis:**
```bash
aws configservice list-resource-evaluations \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | structure | None | Filter by evaluation mode or time range |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filters Structure:**
```json
{
    "EvaluationMode": "DETECTIVE|PROACTIVE",
    "TimeWindow": {
        "StartTime": "timestamp",
        "EndTime": "timestamp"
    },
    "EvaluationContextIdentifier": "string"
}
```

**Output Schema:**
```json
{
    "ResourceEvaluations": [
        {
            "ResourceEvaluationId": "string",
            "EvaluationMode": "DETECTIVE|PROACTIVE",
            "EvaluationStartTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `put-external-evaluation`

Publishes evaluation results from an external process. Used by third-party integrations to report compliance data to Config.

**Synopsis:**
```bash
aws configservice put-external-evaluation \
    --config-rule-name <value> \
    --external-evaluation <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--config-rule-name` | **Yes** | string | -- | Name of the Config rule |
| `--external-evaluation` | **Yes** | structure | -- | External evaluation result |

**External Evaluation Structure:**
```json
{
    "ComplianceResourceType": "string",
    "ComplianceResourceId": "string",
    "ComplianceType": "COMPLIANT|NON_COMPLIANT|NOT_APPLICABLE|INSUFFICIENT_DATA",
    "Annotation": "string",
    "OrderingTimestamp": "timestamp"
}
```

**Output Schema:**
```json
{}
```
