# Recommendations

### 5.1 `list-alarm-recommendations`

Lists alarm recommendations from an assessment. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-alarm-recommendations \
    --assessment-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-arn` | **Yes** | string | -- | Assessment ARN |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "alarmRecommendations": [
        {
            "appComponentName": "string",
            "appComponentNames": ["string"],
            "description": "string",
            "items": [
                {
                    "alreadyImplemented": "boolean",
                    "discoveredAlarm": {
                        "alarmArn": "string",
                        "source": "string"
                    },
                    "excludeReason": "AlreadyImplemented|NotRelevant|ComplexityOfImplementation",
                    "excluded": "boolean",
                    "resourceId": "string",
                    "targetAccountId": "string",
                    "targetRegion": "string"
                }
            ],
            "name": "string",
            "prerequisite": "string",
            "recommendationId": "string",
            "recommendationStatus": "Implemented|Inactive|NotImplemented|Excluded",
            "referenceId": "string",
            "type": "Metric|Composite|Canary|Logs|Event"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.2 `list-sop-recommendations`

Lists SOP (Standard Operating Procedure) recommendations from an assessment. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-sop-recommendations \
    --assessment-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-arn` | **Yes** | string | -- | Assessment ARN |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "sopRecommendations": [
        {
            "appComponentName": "string",
            "description": "string",
            "items": [
                {
                    "alreadyImplemented": "boolean",
                    "excludeReason": "AlreadyImplemented|NotRelevant|ComplexityOfImplementation",
                    "excluded": "boolean",
                    "resourceId": "string",
                    "targetAccountId": "string",
                    "targetRegion": "string"
                }
            ],
            "name": "string",
            "prerequisite": "string",
            "recommendationId": "string",
            "recommendationStatus": "Implemented|Inactive|NotImplemented|Excluded",
            "referenceId": "string",
            "serviceType": "SSM"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.3 `list-test-recommendations`

Lists test recommendations from an assessment. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-test-recommendations \
    --assessment-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-arn` | **Yes** | string | -- | Assessment ARN |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "testRecommendations": [
        {
            "appComponentId": "string",
            "appComponentName": "string",
            "dependsOnAlarms": ["string"],
            "description": "string",
            "intent": "string",
            "items": [
                {
                    "alreadyImplemented": "boolean",
                    "excludeReason": "AlreadyImplemented|NotRelevant|ComplexityOfImplementation",
                    "excluded": "boolean",
                    "resourceId": "string",
                    "targetAccountId": "string",
                    "targetRegion": "string"
                }
            ],
            "name": "string",
            "prerequisite": "string",
            "recommendationId": "string",
            "recommendationStatus": "Implemented|Inactive|NotImplemented|Excluded",
            "referenceId": "string",
            "risk": "Small|Medium|High",
            "type": "Software|Hardware|AZ|Region"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.4 `list-app-component-compliances`

Lists compliance status of AppComponents against resiliency policies. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-app-component-compliances \
    --assessment-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-arn` | **Yes** | string | -- | Assessment ARN |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "componentCompliances": [
        {
            "appComponentName": "string",
            "compliance": {
                "Software|Hardware|AZ|Region": {
                    "achievableRpoInSecs": "integer",
                    "achievableRtoInSecs": "integer",
                    "complianceStatus": "PolicyBreached|PolicyMet|NotApplicable|MissingPolicy",
                    "currentRpoInSecs": "integer",
                    "currentRtoInSecs": "integer",
                    "message": "string",
                    "rpoDescription": "string",
                    "rtoDescription": "string"
                }
            },
            "cost": {
                "amount": "double",
                "currency": "string",
                "frequency": "Hourly|Daily|Monthly|Yearly"
            },
            "message": "string",
            "resiliencyScore": {
                "componentScore": {
                    "Compliance|Test|Alarm|Sop": {
                        "excludedCount": "long",
                        "outstandingCount": "long",
                        "possibleScore": "double",
                        "score": "double"
                    }
                },
                "disruptionScore": {
                    "Software|Hardware|AZ|Region": "double"
                },
                "score": "double"
            },
            "status": "PolicyBreached|PolicyMet|NotApplicable|MissingPolicy"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.5 `list-app-component-recommendations`

Lists configuration recommendations for AppComponents. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-app-component-recommendations \
    --assessment-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-arn` | **Yes** | string | -- | Assessment ARN |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "componentRecommendations": [
        {
            "appComponentName": "string",
            "configRecommendations": [
                {
                    "appComponentName": "string",
                    "compliance": {
                        "Software|Hardware|AZ|Region": {
                            "achievableRpoInSecs": "integer",
                            "achievableRtoInSecs": "integer",
                            "complianceStatus": "PolicyBreached|PolicyMet|NotApplicable|MissingPolicy",
                            "currentRpoInSecs": "integer",
                            "currentRtoInSecs": "integer"
                        }
                    },
                    "cost": {
                        "amount": "double",
                        "currency": "string",
                        "frequency": "Hourly|Daily|Monthly|Yearly"
                    },
                    "description": "string",
                    "haArchitecture": "MultiSite|WarmStandby|PilotLight|BackupAndRestore|NoRecoveryPlan",
                    "name": "string",
                    "optimizationType": "LeastCost|LeastChange|BestAZRecovery|LeastErrors|BestAttainable|BestRegionRecovery",
                    "recommendationCompliance": {
                        "Software|Hardware|AZ|Region": {
                            "expectedComplianceStatus": "PolicyBreached|PolicyMet|NotApplicable|MissingPolicy",
                            "expectedRpoInSecs": "integer",
                            "expectedRtoInSecs": "integer"
                        }
                    },
                    "referenceId": "string",
                    "suggestedChanges": ["string"]
                }
            ],
            "recommendationStatus": "BreachedUnattainable|BreachedCanMeet|MetCanImprove|MissingPolicy"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.6 `batch-update-recommendation-status`

Includes or excludes operational recommendations for an application.

**Synopsis:**
```bash
aws resiliencehub batch-update-recommendation-status \
    --app-arn <value> \
    --request-entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--request-entries` | **Yes** | list | -- | Entries to update (1-50). Each requires `entryId`, `referenceId`, `excluded` |

**Request Entry Structure:**
```json
[
    {
        "entryId": "string",
        "referenceId": "string",
        "excluded": true,
        "excludeReason": "AlreadyImplemented|NotRelevant|ComplexityOfImplementation",
        "item": {
            "resourceId": "string",
            "targetAccountId": "string",
            "targetRegion": "string"
        }
    }
]
```

**Output Schema:**
```json
{
    "appArn": "string",
    "successfulEntries": [
        {
            "entryId": "string",
            "referenceId": "string",
            "excluded": "boolean",
            "excludeReason": "AlreadyImplemented|NotRelevant|ComplexityOfImplementation",
            "item": {
                "resourceId": "string",
                "targetAccountId": "string",
                "targetRegion": "string"
            }
        }
    ],
    "failedEntries": [
        {
            "entryId": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 5.7 `create-recommendation-template`

Creates a CloudFormation template from assessment recommendations.

**Synopsis:**
```bash
aws resiliencehub create-recommendation-template \
    --assessment-arn <value> \
    --name <value> \
    [--bucket-name <value>] \
    [--client-token <value>] \
    [--format <value>] \
    [--recommendation-ids <value>] \
    [--recommendation-types <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-arn` | **Yes** | string | -- | Assessment ARN |
| `--name` | **Yes** | string | -- | Template name (2-60 chars) |
| `--bucket-name` | No | string | None | S3 bucket for the template |
| `--client-token` | No | string | Auto | Idempotency token (1-63 chars) |
| `--format` | No | string | None | Template format: `CfnJson`, `CfnYaml` |
| `--recommendation-ids` | No | list | None | UUIDs of recommendations to include (1-200) |
| `--recommendation-types` | No | list | None | Types: `Alarm`, `Sop`, `Test` |
| `--tags` | No | map | None | Resource tags (1-50 tags) |

**Output Schema:**
```json
{
    "recommendationTemplate": {
        "appArn": "string",
        "assessmentArn": "string",
        "endTime": "timestamp",
        "format": "CfnYaml|CfnJson",
        "message": "string",
        "name": "string",
        "needsReplacements": "boolean",
        "recommendationIds": ["string"],
        "recommendationTemplateArn": "string",
        "recommendationTypes": ["Alarm|Sop|Test"],
        "startTime": "timestamp",
        "status": "Pending|InProgress|Failed|Success",
        "tags": {"string": "string"},
        "templatesLocation": {
            "bucket": "string",
            "prefix": "string"
        }
    }
}
```

---

### 5.8 `delete-recommendation-template`

Deletes a recommendation template.

**Synopsis:**
```bash
aws resiliencehub delete-recommendation-template \
    --recommendation-template-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recommendation-template-arn` | **Yes** | string | -- | Recommendation template ARN |
| `--client-token` | No | string | Auto | Idempotency token (1-63 chars) |

**Output Schema:**
```json
{
    "recommendationTemplateArn": "string",
    "status": "Pending|InProgress|Failed|Success"
}
```

---

### 5.9 `list-recommendation-templates`

Lists recommendation templates. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-recommendation-templates \
    [--assessment-arn <value>] \
    [--max-results <value>] \
    [--name <value>] \
    [--next-token <value>] \
    [--recommendation-template-arn <value>] \
    [--reverse-order | --no-reverse-order] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-arn` | No | string | None | Filter by assessment ARN |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--name` | No | string | None | Filter by template name |
| `--next-token` | No | string | None | Pagination token |
| `--recommendation-template-arn` | No | string | None | Filter by template ARN |
| `--reverse-order` | No | boolean | false | Sort descending by start time |
| `--status` | No | list | None | Filter: `Pending`, `InProgress`, `Failed`, `Success` |

**Output Schema:**
```json
{
    "recommendationTemplates": [
        {
            "appArn": "string",
            "assessmentArn": "string",
            "endTime": "timestamp",
            "format": "CfnYaml|CfnJson",
            "message": "string",
            "name": "string",
            "needsReplacements": "boolean",
            "recommendationIds": ["string"],
            "recommendationTemplateArn": "string",
            "recommendationTypes": ["Alarm|Sop|Test"],
            "startTime": "timestamp",
            "status": "Pending|InProgress|Failed|Success",
            "tags": {"string": "string"},
            "templatesLocation": {
                "bucket": "string",
                "prefix": "string"
            }
        }
    ],
    "nextToken": "string"
}
```
