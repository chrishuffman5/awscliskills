# Lifecycle

### 9.1 `create-lifecycle-policy`

Creates a lifecycle policy to automate image management (deprecation, deletion, disabling).

**Synopsis:**
```bash
aws imagebuilder create-lifecycle-policy \
    --name <value> \
    --execution-role <value> \
    --resource-type <value> \
    --policy-details <value> \
    --resource-selection <value> \
    [--description <value>] \
    [--status <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the lifecycle policy |
| `--execution-role` | **Yes** | string | -- | IAM role ARN for executing the policy |
| `--resource-type` | **Yes** | string | -- | Resource type: `AMI_IMAGE` or `DOCKER_IMAGE` |
| `--policy-details` | **Yes** | list | -- | Policy details with actions, filters, and exclusion rules |
| `--resource-selection` | **Yes** | structure | -- | Resource selection criteria |
| `--description` | No | string | -- | Description |
| `--status` | No | string | `ENABLED` | Policy status: `ENABLED` or `DISABLED` |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Policy Details Structure:**
```json
[
    {
        "action": {
            "type": "DELETE|DEPRECATE|DISABLE",
            "includeResources": {
                "amis": "boolean",
                "snapshots": "boolean",
                "containers": "boolean"
            }
        },
        "filter": {
            "type": "AGE|COUNT",
            "value": "integer",
            "unit": "DAYS|WEEKS|MONTHS|YEARS",
            "retainAtLeast": "integer"
        },
        "exclusionRules": {
            "tagMap": {
                "string": "string"
            },
            "amis": {
                "isPublic": "boolean",
                "regions": ["string"],
                "sharedAccounts": ["string"],
                "lastLaunched": {
                    "value": "integer",
                    "unit": "DAYS|WEEKS|MONTHS|YEARS"
                },
                "tagMap": {}
            }
        }
    }
]
```

**Resource Selection Structure:**
```json
{
    "tagMap": {
        "string": "string"
    },
    "recipes": [
        {
            "name": "string",
            "semanticVersion": "string"
        }
    ]
}
```

**Output Schema:**
```json
{
    "clientToken": "string",
    "lifecyclePolicyArn": "string"
}
```

---

### 9.2 `get-lifecycle-policy`

Gets a lifecycle policy.

**Synopsis:**
```bash
aws imagebuilder get-lifecycle-policy \
    --lifecycle-policy-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lifecycle-policy-arn` | **Yes** | string | -- | ARN of the lifecycle policy |

**Output Schema:**
```json
{
    "lifecyclePolicy": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "status": "DISABLED|ENABLED",
        "executionRole": "string",
        "resourceType": "AMI_IMAGE|DOCKER_IMAGE",
        "policyDetails": [],
        "resourceSelection": {},
        "dateCreated": "timestamp",
        "dateUpdated": "timestamp",
        "dateLastRun": "timestamp",
        "tags": {}
    }
}
```

---

### 9.3 `list-lifecycle-policies`

Lists lifecycle policies. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-lifecycle-policies \
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
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "lifecyclePolicySummaryList": [
        {
            "arn": "string",
            "name": "string",
            "description": "string",
            "status": "DISABLED|ENABLED",
            "executionRole": "string",
            "resourceType": "AMI_IMAGE|DOCKER_IMAGE",
            "dateCreated": "timestamp",
            "dateUpdated": "timestamp",
            "dateLastRun": "timestamp",
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 9.4 `update-lifecycle-policy`

Updates a lifecycle policy.

**Synopsis:**
```bash
aws imagebuilder update-lifecycle-policy \
    --lifecycle-policy-arn <value> \
    --execution-role <value> \
    --resource-type <value> \
    --policy-details <value> \
    --resource-selection <value> \
    [--description <value>] \
    [--status <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lifecycle-policy-arn` | **Yes** | string | -- | ARN of the policy to update |
| `--execution-role` | **Yes** | string | -- | Execution role ARN |
| `--resource-type` | **Yes** | string | -- | Resource type: `AMI_IMAGE` or `DOCKER_IMAGE` |
| `--policy-details` | **Yes** | list | -- | Updated policy details |
| `--resource-selection` | **Yes** | structure | -- | Updated resource selection |
| `--description` | No | string | -- | Updated description |
| `--status` | No | string | -- | Policy status |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "lifecyclePolicyArn": "string"
}
```

---

### 9.5 `delete-lifecycle-policy`

Deletes a lifecycle policy.

**Synopsis:**
```bash
aws imagebuilder delete-lifecycle-policy \
    --lifecycle-policy-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lifecycle-policy-arn` | **Yes** | string | -- | ARN of the policy to delete |

**Output Schema:**
```json
{
    "lifecyclePolicyArn": "string"
}
```

---

### 9.6 `list-lifecycle-executions`

Lists lifecycle executions for a specific resource. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-lifecycle-executions \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "lifecycleExecutions": [
        {
            "lifecycleExecutionId": "string",
            "lifecyclePolicyArn": "string",
            "resourcesImpactedSummary": {
                "hasImpactedResources": "boolean"
            },
            "state": {
                "status": "IN_PROGRESS|CANCELLED|CANCELLING|FAILED|SUCCESS",
                "reason": "string"
            },
            "startTime": "timestamp",
            "endTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.7 `list-lifecycle-execution-resources`

Lists resources affected by a lifecycle execution. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-lifecycle-execution-resources \
    --lifecycle-execution-id <value> \
    [--parent-resource-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lifecycle-execution-id` | **Yes** | string | -- | ID of the lifecycle execution |
| `--parent-resource-id` | No | string | -- | ID of the parent resource |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "lifecycleExecutionId": "string",
    "lifecycleExecutionState": {
        "status": "IN_PROGRESS|CANCELLED|CANCELLING|FAILED|SUCCESS",
        "reason": "string"
    },
    "resources": [
        {
            "accountId": "string",
            "resourceId": "string",
            "state": {
                "status": "FAILED|IN_PROGRESS|SKIPPED|SUCCESS",
                "reason": "string"
            },
            "action": {
                "name": "AVAILABLE|DELETE|DEPRECATE|DISABLE",
                "reason": "string"
            },
            "region": "string",
            "snapshots": [],
            "imageUris": ["string"],
            "startTime": "timestamp",
            "endTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
