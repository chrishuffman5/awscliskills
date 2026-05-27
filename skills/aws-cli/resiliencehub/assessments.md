# Assessments

### 4.1 `start-app-assessment`

Creates a new assessment for a Resilience Hub application.

**Synopsis:**
```bash
aws resiliencehub start-app-assessment \
    --app-arn <value> \
    --app-version <value> \
    --assessment-name <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-version` | **Yes** | string | -- | Application version to assess |
| `--assessment-name` | **Yes** | string | -- | Assessment name (2-60 chars, alphanumeric/hyphens/underscores) |
| `--client-token` | No | string | Auto | Idempotency token (1-63 chars) |
| `--tags` | No | map | None | Resource tags (1-50 tags) |

**Output Schema:**
```json
{
    "assessment": {
        "appArn": "string",
        "appVersion": "string",
        "assessmentArn": "string",
        "assessmentName": "string",
        "assessmentStatus": "Pending|InProgress|Failed|Success",
        "compliance": {
            "Software|Hardware|AZ|Region": {
                "achievableRpoInSecs": "integer",
                "achievableRtoInSecs": "integer",
                "complianceStatus": "PolicyBreached|PolicyMet|NotApplicable|MissingPolicy",
                "currentRpoInSecs": "integer",
                "currentRtoInSecs": "integer",
                "message": "string",
                "rpoDescription": "string",
                "rpoReferenceId": "string",
                "rtoDescription": "string",
                "rtoReferenceId": "string"
            }
        },
        "complianceStatus": "PolicyBreached|PolicyMet|NotApplicable|MissingPolicy",
        "cost": {
            "amount": "double",
            "currency": "string",
            "frequency": "Hourly|Daily|Monthly|Yearly"
        },
        "driftStatus": "NotChecked|NotDetected|Detected",
        "endTime": "timestamp",
        "invoker": "User|System",
        "message": "string",
        "policy": {
            "creationTime": "timestamp",
            "dataLocationConstraint": "AnyLocation|SameContinent|SameCountry",
            "estimatedCostTier": "L1|L2|L3|L4",
            "policy": {
                "Software|Hardware|AZ|Region": {
                    "rpoInSecs": "integer",
                    "rtoInSecs": "integer"
                }
            },
            "policyArn": "string",
            "policyDescription": "string",
            "policyName": "string",
            "tags": {"string": "string"},
            "tier": "MissionCritical|Critical|Important|CoreServices|NonCritical|NotApplicable"
        },
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
        "resourceErrorsDetails": {
            "hasMoreErrors": "boolean",
            "resourceErrors": [
                {
                    "logicalResourceId": "string",
                    "physicalResourceId": "string",
                    "reason": "string"
                }
            ]
        },
        "startTime": "timestamp",
        "tags": {"string": "string"},
        "versionName": "string"
    }
}
```

---

### 4.2 `delete-app-assessment`

Deletes an application assessment.

**Synopsis:**
```bash
aws resiliencehub delete-app-assessment \
    --assessment-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-arn` | **Yes** | string | -- | Assessment ARN |
| `--client-token` | No | string | Auto | Idempotency token (1-63 chars) |

**Output Schema:**
```json
{
    "assessmentArn": "string",
    "assessmentStatus": "Pending|InProgress|Failed|Success"
}
```

---

### 4.3 `describe-app-assessment`

Describes an application assessment.

**Synopsis:**
```bash
aws resiliencehub describe-app-assessment \
    --assessment-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-arn` | **Yes** | string | -- | Assessment ARN |

**Output Schema:**
```json
{
    "assessment": {
        "appArn": "string",
        "appVersion": "string",
        "assessmentArn": "string",
        "assessmentName": "string",
        "assessmentStatus": "Pending|InProgress|Failed|Success",
        "compliance": {
            "Software|Hardware|AZ|Region": {
                "achievableRpoInSecs": "integer",
                "achievableRtoInSecs": "integer",
                "complianceStatus": "PolicyBreached|PolicyMet|NotApplicable|MissingPolicy",
                "currentRpoInSecs": "integer",
                "currentRtoInSecs": "integer",
                "message": "string",
                "rpoDescription": "string",
                "rpoReferenceId": "string",
                "rtoDescription": "string",
                "rtoReferenceId": "string"
            }
        },
        "complianceStatus": "PolicyBreached|PolicyMet|NotApplicable|MissingPolicy",
        "cost": {
            "amount": "double",
            "currency": "string",
            "frequency": "Hourly|Daily|Monthly|Yearly"
        },
        "driftStatus": "NotChecked|NotDetected|Detected",
        "endTime": "timestamp",
        "invoker": "User|System",
        "message": "string",
        "policy": {
            "creationTime": "timestamp",
            "dataLocationConstraint": "AnyLocation|SameContinent|SameCountry",
            "estimatedCostTier": "L1|L2|L3|L4",
            "policy": {
                "Software|Hardware|AZ|Region": {
                    "rpoInSecs": "integer",
                    "rtoInSecs": "integer"
                }
            },
            "policyArn": "string",
            "policyDescription": "string",
            "policyName": "string",
            "tags": {"string": "string"},
            "tier": "MissionCritical|Critical|Important|CoreServices|NonCritical|NotApplicable"
        },
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
        "resourceErrorsDetails": {
            "hasMoreErrors": "boolean",
            "resourceErrors": [
                {
                    "logicalResourceId": "string",
                    "physicalResourceId": "string",
                    "reason": "string"
                }
            ]
        },
        "startTime": "timestamp",
        "tags": {"string": "string"},
        "versionName": "string"
    }
}
```

---

### 4.4 `list-app-assessments`

Lists assessments for Resilience Hub applications. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-app-assessments \
    [--app-arn <value>] \
    [--assessment-name <value>] \
    [--assessment-status <value>] \
    [--compliance-status <value>] \
    [--invoker <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--reverse-order | --no-reverse-order] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | No | string | None | Filter by application ARN |
| `--assessment-name` | No | string | None | Filter by assessment name |
| `--assessment-status` | No | list | None | Filter by status: `Pending`, `InProgress`, `Failed`, `Success` |
| `--compliance-status` | No | string | None | Filter: `PolicyBreached`, `PolicyMet`, `NotApplicable`, `MissingPolicy` |
| `--invoker` | No | string | None | Filter by invoker: `User`, `System` |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |
| `--reverse-order` | No | boolean | false | Sort descending by start time |

**Output Schema:**
```json
{
    "assessmentSummaries": [
        {
            "appArn": "string",
            "appVersion": "string",
            "assessmentArn": "string",
            "assessmentName": "string",
            "assessmentStatus": "Pending|InProgress|Failed|Success",
            "complianceStatus": "PolicyBreached|PolicyMet|NotApplicable|MissingPolicy",
            "cost": {
                "amount": "double",
                "currency": "string",
                "frequency": "Hourly|Daily|Monthly|Yearly"
            },
            "driftStatus": "NotChecked|NotDetected|Detected",
            "endTime": "timestamp",
            "invoker": "User|System",
            "message": "string",
            "resiliencyScore": "double",
            "startTime": "timestamp",
            "versionName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.5 `list-app-assessment-compliance-drifts`

Lists compliance drifts for an assessment. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-app-assessment-compliance-drifts \
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
    "complianceDrifts": [
        {
            "actualReferenceId": "string",
            "actualValue": {
                "Software|Hardware|AZ|Region": {
                    "achievableRpoInSecs": "integer",
                    "achievableRtoInSecs": "integer",
                    "complianceStatus": "PolicyBreached|PolicyMet|NotApplicable|MissingPolicy",
                    "currentRpoInSecs": "integer",
                    "currentRtoInSecs": "integer",
                    "message": "string"
                }
            },
            "appId": "string",
            "appVersion": "string",
            "diffType": "NotEqual|Added|Removed",
            "driftType": "ApplicationCompliance|AppComponentResiliencyComplianceStatus",
            "entityId": "string",
            "entityType": "string",
            "expectedReferenceId": "string",
            "expectedValue": {
                "Software|Hardware|AZ|Region": {
                    "achievableRpoInSecs": "integer",
                    "achievableRtoInSecs": "integer",
                    "complianceStatus": "PolicyBreached|PolicyMet|NotApplicable|MissingPolicy",
                    "currentRpoInSecs": "integer",
                    "currentRtoInSecs": "integer",
                    "message": "string"
                }
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 4.6 `list-app-assessment-resource-drifts`

Lists resource drifts for an assessment. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-app-assessment-resource-drifts \
    --assessment-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assessment-arn` | **Yes** | string | -- | Assessment ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "resourceDrifts": [
        {
            "appArn": "string",
            "appVersion": "string",
            "diffType": "NotEqual|Added|Removed",
            "referenceId": "string",
            "resourceIdentifier": {
                "logicalResourceId": {
                    "eksSourceName": "string",
                    "identifier": "string",
                    "logicalStackName": "string",
                    "resourceGroupName": "string",
                    "terraformSourceName": "string"
                },
                "resourceType": "string"
            }
        }
    ],
    "nextToken": "string"
}
```
