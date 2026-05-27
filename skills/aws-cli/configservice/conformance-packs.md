# Conformance Packs

### 2.1 `put-conformance-pack`

Creates or updates a conformance pack. A conformance pack is a collection of Config rules and remediation actions.

**Synopsis:**
```bash
aws configservice put-conformance-pack \
    --conformance-pack-name <value> \
    [--template-s3-uri <value>] \
    [--template-body <value>] \
    [--delivery-s3-bucket <value>] \
    [--delivery-s3-key-prefix <value>] \
    [--conformance-pack-input-parameters <value>] \
    [--template-ssm-document-details <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--conformance-pack-name` | **Yes** | string | -- | Name of the conformance pack (1-256 chars) |
| `--template-s3-uri` | No | string | None | S3 URI of the conformance pack template |
| `--template-body` | No | string | None | Inline template body (max 51200 bytes) |
| `--delivery-s3-bucket` | No | string | None | S3 bucket for delivery of rule evaluations |
| `--delivery-s3-key-prefix` | No | string | None | S3 key prefix for delivery |
| `--conformance-pack-input-parameters` | No | list | None | Input parameters for the template. Shorthand: `ParameterName=string,ParameterValue=string ...` |
| `--template-ssm-document-details` | No | structure | None | SSM document details for the template |

**Output Schema:**
```json
{
    "ConformancePackArn": "string"
}
```

---

### 2.2 `delete-conformance-pack`

Deletes the specified conformance pack and all Config rules and remediation actions in it.

**Synopsis:**
```bash
aws configservice delete-conformance-pack \
    --conformance-pack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--conformance-pack-name` | **Yes** | string | -- | Name of the conformance pack to delete |

**Output Schema:**
```json
{}
```

---

### 2.3 `describe-conformance-packs`

Returns details about one or more conformance packs. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-conformance-packs \
    [--conformance-pack-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--conformance-pack-names` | No | list(string) | None | Specific conformance pack names |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConformancePackDetails": [
        {
            "ConformancePackName": "string",
            "ConformancePackArn": "string",
            "ConformancePackId": "string",
            "DeliveryS3Bucket": "string",
            "DeliveryS3KeyPrefix": "string",
            "ConformancePackInputParameters": [
                {
                    "ParameterName": "string",
                    "ParameterValue": "string"
                }
            ],
            "LastUpdateRequestedTime": "timestamp",
            "CreatedBy": "string",
            "TemplateSSMDocumentDetails": {
                "DocumentName": "string",
                "DocumentVersion": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `describe-conformance-pack-status`

Returns the status of one or more conformance packs. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-conformance-pack-status \
    [--conformance-pack-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--conformance-pack-names` | No | list(string) | None | Specific conformance pack names |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConformancePackStatusDetails": [
        {
            "ConformancePackName": "string",
            "ConformancePackId": "string",
            "ConformancePackArn": "string",
            "ConformancePackState": "CREATE_IN_PROGRESS|CREATE_COMPLETE|CREATE_FAILED|DELETE_IN_PROGRESS|DELETE_FAILED",
            "StackArn": "string",
            "ConformancePackStatusReason": "string",
            "LastUpdateRequestedTime": "timestamp",
            "LastUpdateCompletedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `get-conformance-pack-compliance-summary`

Returns compliance summary for one or more conformance packs. **Paginated operation.**

**Synopsis:**
```bash
aws configservice get-conformance-pack-compliance-summary \
    --conformance-pack-names <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--conformance-pack-names` | **Yes** | list(string) | -- | Conformance pack names (up to 5) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConformancePackComplianceSummaryList": [
        {
            "ConformancePackName": "string",
            "ConformancePackComplianceStatus": "COMPLIANT|NON_COMPLIANT|INSUFFICIENT_DATA"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.6 `describe-conformance-pack-compliance`

Returns compliance details for rules within a conformance pack. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-conformance-pack-compliance \
    --conformance-pack-name <value> \
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
| `--conformance-pack-name` | **Yes** | string | -- | Name of the conformance pack |
| `--filters` | No | structure | None | Filter by compliance type. Shorthand: `ConfigRuleNames=string,string,ComplianceType=COMPLIANT\|NON_COMPLIANT\|INSUFFICIENT_DATA` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConformancePackName": "string",
    "ConformancePackRuleComplianceList": [
        {
            "ConfigRuleName": "string",
            "ComplianceType": "COMPLIANT|NON_COMPLIANT|INSUFFICIENT_DATA",
            "Controls": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 2.7 `get-conformance-pack-compliance-details`

Returns resource-level compliance details for a conformance pack. **Paginated operation.**

**Synopsis:**
```bash
aws configservice get-conformance-pack-compliance-details \
    --conformance-pack-name <value> \
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
| `--conformance-pack-name` | **Yes** | string | -- | Name of the conformance pack |
| `--filters` | No | structure | None | Filter results. Shorthand: `ConfigRuleNames=string,string,ComplianceType=COMPLIANT\|NON_COMPLIANT,ResourceType=string,ResourceIds=string,string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConformancePackName": "string",
    "ConformancePackRuleEvaluationResults": [
        {
            "ComplianceType": "COMPLIANT|NON_COMPLIANT|INSUFFICIENT_DATA",
            "EvaluationResultIdentifier": {
                "EvaluationResultQualifier": {
                    "ConfigRuleName": "string",
                    "ResourceType": "string",
                    "ResourceId": "string",
                    "EvaluationMode": "DETECTIVE|PROACTIVE"
                },
                "OrderingTimestamp": "timestamp",
                "ResourceEvaluationId": "string"
            },
            "ConfigRuleInvokedTime": "timestamp",
            "ResultRecordedTime": "timestamp",
            "Annotation": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.8 `list-conformance-pack-compliance-scores`

Returns compliance scores for one or more conformance packs. A compliance score is the percentage of compliant rule-resource combinations. **Paginated operation.**

**Synopsis:**
```bash
aws configservice list-conformance-pack-compliance-scores \
    [--filters <value>] \
    [--sort-order <value>] \
    [--sort-by <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | structure | None | Filter by conformance pack names. Shorthand: `ConformancePackNames=string,string` |
| `--sort-order` | No | string | `DESCENDING` | Sort order: `ASCENDING` or `DESCENDING` |
| `--sort-by` | No | string | `SCORE` | Sort by: `SCORE` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConformancePackComplianceScores": [
        {
            "Score": "string",
            "ConformancePackName": "string",
            "LastUpdatedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
