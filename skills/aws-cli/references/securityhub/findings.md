# Findings

### 2.1 `get-findings`

Returns a list of findings that match the specified criteria. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub get-findings \
    [--filters <value>] \
    [--sort-criteria <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | structure | None | Finding attribute filters (up to 10 attributes, 20 values each) |
| `--sort-criteria` | No | structure | None | Sort criteria for results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Sort Criteria Structure:**
```json
{
    "Field": "string",
    "SortOrder": "asc|desc"
}
```

**Filter Structure (common filters):**
```json
{
    "SeverityLabel": [{"Value": "CRITICAL", "Comparison": "EQUALS"}],
    "WorkflowStatus": [{"Value": "NEW", "Comparison": "EQUALS"}],
    "RecordState": [{"Value": "ACTIVE", "Comparison": "EQUALS"}],
    "ProductArn": [{"Value": "string", "Comparison": "EQUALS"}],
    "AwsAccountId": [{"Value": "string", "Comparison": "EQUALS"}],
    "ResourceType": [{"Value": "string", "Comparison": "EQUALS"}],
    "Type": [{"Value": "string", "Comparison": "PREFIX"}],
    "CreatedAt": [{"DateRange": {"Value": 7, "Unit": "DAYS"}}],
    "ComplianceStatus": [{"Value": "FAILED", "Comparison": "EQUALS"}]
}
```

**Output Schema:**
```json
{
    "Findings": [
        {
            "SchemaVersion": "string",
            "Id": "string",
            "ProductArn": "string",
            "ProductName": "string",
            "CompanyName": "string",
            "GeneratorId": "string",
            "AwsAccountId": "string",
            "Types": ["string"],
            "FirstObservedAt": "string",
            "LastObservedAt": "string",
            "CreatedAt": "string",
            "UpdatedAt": "string",
            "Severity": {
                "Label": "INFORMATIONAL|LOW|MEDIUM|HIGH|CRITICAL",
                "Normalized": "integer",
                "Original": "string"
            },
            "Title": "string",
            "Description": "string",
            "Remediation": {
                "Recommendation": {
                    "Text": "string",
                    "Url": "string"
                }
            },
            "Resources": [
                {
                    "Type": "string",
                    "Id": "string",
                    "Partition": "string",
                    "Region": "string",
                    "Tags": {"string": "string"},
                    "Details": {}
                }
            ],
            "Compliance": {
                "Status": "PASSED|WARNING|FAILED|NOT_AVAILABLE",
                "SecurityControlId": "string",
                "AssociatedStandards": [
                    {
                        "StandardsId": "string"
                    }
                ]
            },
            "VerificationState": "UNKNOWN|TRUE_POSITIVE|FALSE_POSITIVE|BENIGN_POSITIVE",
            "WorkflowState": "NEW|ASSIGNED|IN_PROGRESS|DEFERRED|RESOLVED",
            "Workflow": {
                "Status": "NEW|NOTIFIED|RESOLVED|SUPPRESSED"
            },
            "RecordState": "ACTIVE|ARCHIVED",
            "Note": {
                "Text": "string",
                "UpdatedBy": "string",
                "UpdatedAt": "string"
            },
            "Confidence": "integer",
            "Criticality": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.2 `batch-import-findings`

Imports findings into Security Hub from an integrated product. Findings from the ASFF format.

**Synopsis:**
```bash
aws securityhub batch-import-findings \
    --findings <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--findings` | **Yes** | list | -- | Findings to import in ASFF format (max 100) |

**Output Schema:**
```json
{
    "FailedCount": "integer",
    "SuccessCount": "integer",
    "FailedFindings": [
        {
            "Id": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 2.3 `batch-update-findings`

Updates one or more findings. Can update workflow status, note, severity, verification state, confidence, criticality, and user-defined fields.

**Synopsis:**
```bash
aws securityhub batch-update-findings \
    --finding-identifiers <value> \
    [--note <value>] \
    [--severity <value>] \
    [--verification-state <value>] \
    [--confidence <value>] \
    [--criticality <value>] \
    [--types <value>] \
    [--user-defined-fields <value>] \
    [--workflow <value>] \
    [--related-findings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-identifiers` | **Yes** | list | -- | Finding identifiers to update (max 100) |
| `--note` | No | structure | None | Note to add to the findings |
| `--severity` | No | structure | None | Updated severity |
| `--verification-state` | No | string | None | Verification state |
| `--confidence` | No | integer | None | Confidence score (0-100) |
| `--criticality` | No | integer | None | Criticality score (0-100) |
| `--types` | No | list(string) | None | Updated finding types |
| `--user-defined-fields` | No | map | None | Custom fields |
| `--workflow` | No | structure | None | Workflow status update |
| `--related-findings` | No | list | None | Related finding identifiers |

**Finding Identifier Structure:**
```json
[
    {
        "Id": "string",
        "ProductArn": "string"
    }
]
```

**Output Schema:**
```json
{
    "ProcessedFindings": [
        {
            "Id": "string",
            "ProductArn": "string"
        }
    ],
    "UnprocessedFindings": [
        {
            "FindingIdentifier": {
                "Id": "string",
                "ProductArn": "string"
            },
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 2.4 `update-findings`

Updates the Note and RecordState of findings specified by filter. Deprecated in favor of `batch-update-findings`.

**Synopsis:**
```bash
aws securityhub update-findings \
    --filters <value> \
    [--note <value>] \
    [--record-state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | **Yes** | structure | -- | Filters to select findings to update |
| `--note` | No | structure | None | Note to add |
| `--record-state` | No | string | None | Record state: `ACTIVE` or `ARCHIVED` |

**Output:** None (HTTP 200 on success)

---

### 2.5 `get-finding-history`

Returns history for a specified finding. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub get-finding-history \
    --finding-identifier <value> \
    [--start-time <value>] \
    [--end-time <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-identifier` | **Yes** | structure | -- | Finding identifier (Id + ProductArn) |
| `--start-time` | No | timestamp | None | Start time for history |
| `--end-time` | No | timestamp | None | End time for history |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Records": [
        {
            "FindingIdentifier": {
                "Id": "string",
                "ProductArn": "string"
            },
            "UpdateTime": "timestamp",
            "FindingCreated": "boolean",
            "UpdateSource": {
                "Type": "BATCH_UPDATE_FINDINGS|BATCH_IMPORT_FINDINGS",
                "Identity": "string"
            },
            "Updates": [
                {
                    "UpdatedField": "string",
                    "OldValue": "string",
                    "NewValue": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```
