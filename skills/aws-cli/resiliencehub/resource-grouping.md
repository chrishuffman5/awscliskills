# Resource Grouping

### 7.1 `start-resource-grouping-recommendation-task`

Starts a resource grouping recommendation task for an application.

**Synopsis:**
```bash
aws resiliencehub start-resource-grouping-recommendation-task \
    --app-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |

**Output Schema:**
```json
{
    "appArn": "string",
    "errorMessage": "string",
    "groupingId": "string",
    "status": "Pending|InProgress|Failed|Success"
}
```

---

### 7.2 `describe-resource-grouping-recommendation-task`

Describes a resource grouping recommendation task.

**Synopsis:**
```bash
aws resiliencehub describe-resource-grouping-recommendation-task \
    --app-arn <value> \
    [--grouping-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--grouping-id` | No | string | None | Grouping recommendation task ID (1-255 chars) |

**Output Schema:**
```json
{
    "errorMessage": "string",
    "groupingId": "string",
    "status": "Pending|InProgress|Failed|Success"
}
```

---

### 7.3 `list-resource-grouping-recommendations`

Lists resource grouping recommendations. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-resource-grouping-recommendations \
    [--app-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | No | string | None | Application ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "groupingRecommendations": [
        {
            "confidenceLevel": "High|Medium",
            "creationTime": "timestamp",
            "groupingAppComponent": {
                "appComponentId": "string",
                "appComponentName": "string",
                "appComponentType": "string"
            },
            "groupingRecommendationId": "string",
            "recommendationReasons": ["string"],
            "rejectionReason": "DistinctBusinessPurpose|SeparateDataConcern|DistinctUserGroupHandling|Other",
            "resources": [
                {
                    "logicalResourceId": {
                        "eksSourceName": "string",
                        "identifier": "string",
                        "logicalStackName": "string",
                        "resourceGroupName": "string",
                        "terraformSourceName": "string"
                    },
                    "physicalResourceId": {
                        "awsAccountId": "string",
                        "awsRegion": "string",
                        "identifier": "string",
                        "type": "Arn|Native"
                    },
                    "resourceName": "string",
                    "resourceType": "string",
                    "sourceAppComponentIds": ["string"]
                }
            ],
            "score": "double",
            "status": "Accepted|Rejected|PendingDecision"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.4 `accept-resource-grouping-recommendations`

Accepts resource grouping recommendations to include them in the application.

**Synopsis:**
```bash
aws resiliencehub accept-resource-grouping-recommendations \
    --app-arn <value> \
    --entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--entries` | **Yes** | list | -- | Recommendations to accept (1-30). Each: `groupingRecommendationId=string` |

**Output Schema:**
```json
{
    "appArn": "string",
    "failedEntries": [
        {
            "groupingRecommendationId": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 7.5 `reject-resource-grouping-recommendations`

Rejects resource grouping recommendations to exclude them from the application.

**Synopsis:**
```bash
aws resiliencehub reject-resource-grouping-recommendations \
    --app-arn <value> \
    --entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--entries` | **Yes** | list | -- | Recommendations to reject (1-30). Each: `groupingRecommendationId=string,rejectionReason=string` |

**Rejection Reasons:** `DistinctBusinessPurpose`, `SeparateDataConcern`, `DistinctUserGroupHandling`, `Other`

**Output Schema:**
```json
{
    "appArn": "string",
    "failedEntries": [
        {
            "groupingRecommendationId": "string",
            "errorMessage": "string"
        }
    ]
}
```
