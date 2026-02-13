# Analyzers

### 1.1 `create-analyzer`

Creates an analyzer to analyze resources and generate findings.

**Synopsis:**
```bash
aws accessanalyzer create-analyzer \
    --analyzer-name <value> \
    --type <value> \
    [--archive-rules <value>] \
    [--tags <value>] \
    [--configuration <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-name` | **Yes** | string | -- | Analyzer name (1-255 chars, pattern: `[A-Za-z][A-Za-z0-9_.-]*`) |
| `--type` | **Yes** | string | -- | Analyzer type: `ACCOUNT`, `ORGANIZATION`, `ACCOUNT_UNUSED_ACCESS`, `ORGANIZATION_UNUSED_ACCESS`, `ACCOUNT_INTERNAL_ACCESS`, `ORGANIZATION_INTERNAL_ACCESS` |
| `--archive-rules` | No | list | None | Archive rules to automatically archive matching findings |
| `--tags` | No | map | None | Key-value pairs for tagging (key: 1-128 chars, value: 0-256 chars) |
| `--configuration` | No | structure | None | Analyzer configuration (unusedAccess or internalAccess) |
| `--client-token` | No | string | None | Client token for idempotency |

**Archive Rule Structure:**
```json
[
    {
        "ruleName": "string",
        "filter": {
            "string": {
                "eq": ["string"],
                "neq": ["string"],
                "contains": ["string"],
                "exists": true|false
            }
        }
    }
]
```

**Configuration Structure:**
```json
{
    "unusedAccess": {
        "unusedAccessAge": "integer",
        "analysisRule": {
            "exclusions": [
                {
                    "accountIds": ["string"],
                    "resourceTags": {"string": "string"}
                }
            ]
        }
    }
}
```

**Output Schema:**
```json
{
    "arn": "string"
}
```

---

### 1.2 `get-analyzer`

Retrieves information about an analyzer.

**Synopsis:**
```bash
aws accessanalyzer get-analyzer \
    --analyzer-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-name` | **Yes** | string | -- | The name of the analyzer |

**Output Schema:**
```json
{
    "analyzer": {
        "arn": "string",
        "name": "string",
        "type": "ACCOUNT|ORGANIZATION|ACCOUNT_UNUSED_ACCESS|ORGANIZATION_UNUSED_ACCESS|ACCOUNT_INTERNAL_ACCESS|ORGANIZATION_INTERNAL_ACCESS",
        "createdAt": "timestamp",
        "status": "ACTIVE|CREATING|DISABLED|FAILED",
        "lastResourceAnalyzed": "string",
        "lastResourceAnalyzedAt": "timestamp",
        "tags": {
            "string": "string"
        },
        "statusReason": {
            "code": "string"
        },
        "configuration": {
            "unusedAccess": {
                "unusedAccessAge": "integer",
                "analysisRule": {}
            }
        }
    }
}
```

---

### 1.3 `list-analyzers`

Lists all analyzers. **Paginated operation.**

**Synopsis:**
```bash
aws accessanalyzer list-analyzers \
    [--type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | No | string | None | Filter by analyzer type |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "analyzers": [
        {
            "arn": "string",
            "name": "string",
            "type": "string",
            "createdAt": "timestamp",
            "status": "ACTIVE|CREATING|DISABLED|FAILED",
            "lastResourceAnalyzed": "string",
            "lastResourceAnalyzedAt": "timestamp",
            "tags": {"string": "string"},
            "statusReason": {"code": "string"},
            "configuration": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `update-analyzer`

Updates an existing analyzer.

**Synopsis:**
```bash
aws accessanalyzer update-analyzer \
    --analyzer-name <value> \
    [--configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-name` | **Yes** | string | -- | The name of the analyzer to update |
| `--configuration` | No | structure | None | Updated analyzer configuration |

**Output Schema:**
```json
{
    "configuration": {
        "unusedAccess": {
            "unusedAccessAge": "integer",
            "analysisRule": {}
        }
    }
}
```

---

### 1.5 `delete-analyzer`

Deletes an analyzer. When you delete an analyzer, existing findings are not affected.

**Synopsis:**
```bash
aws accessanalyzer delete-analyzer \
    --analyzer-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-name` | **Yes** | string | -- | The name of the analyzer to delete |
| `--client-token` | No | string | None | Client token for idempotency |

**Output:** None

---

### 1.6 `get-analyzed-resource`

Retrieves information about a resource that was analyzed.

**Synopsis:**
```bash
aws accessanalyzer get-analyzed-resource \
    --analyzer-arn <value> \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-arn` | **Yes** | string | -- | The ARN of the analyzer |
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource to get information about |

**Output Schema:**
```json
{
    "resource": {
        "resourceArn": "string",
        "resourceType": "string",
        "createdAt": "timestamp",
        "analyzedAt": "timestamp",
        "updatedAt": "timestamp",
        "isPublic": "boolean",
        "actions": ["string"],
        "sharedVia": ["string"],
        "status": "ACTIVE|ARCHIVED|RESOLVED",
        "resourceOwnerAccount": "string",
        "error": "string"
    }
}
```

---

### 1.7 `list-analyzed-resources`

Lists all analyzed resources for the specified analyzer. **Paginated operation.**

**Synopsis:**
```bash
aws accessanalyzer list-analyzed-resources \
    --analyzer-arn <value> \
    [--resource-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-arn` | **Yes** | string | -- | The ARN of the analyzer |
| `--resource-type` | No | string | None | Filter by resource type (e.g., `AWS::S3::Bucket`) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "analyzedResources": [
        {
            "resourceArn": "string",
            "resourceOwnerAccount": "string",
            "resourceType": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.8 `start-resource-scan`

Immediately starts a scan of the policies applied to the specified resource.

**Synopsis:**
```bash
aws accessanalyzer start-resource-scan \
    --analyzer-arn <value> \
    --resource-arn <value> \
    [--resource-owner-account <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-arn` | **Yes** | string | -- | The ARN of the analyzer |
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource to scan |
| `--resource-owner-account` | No | string | None | The account that owns the resource |

**Output:** None
