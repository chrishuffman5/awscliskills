# Action Types

### 4.1 `get-action-type`

Returns information about an action type.

**Synopsis:**
```bash
aws codepipeline get-action-type \
    --category <value> \
    --owner <value> \
    --provider <value> \
    --version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--category` | **Yes** | string | -- | Action category: `Source`, `Build`, `Deploy`, `Test`, `Invoke`, `Approval` |
| `--owner` | **Yes** | string | -- | Action owner: `AWS`, `ThirdParty`, `Custom` |
| `--provider` | **Yes** | string | -- | Action provider name |
| `--version` | **Yes** | string | -- | Action type version |

**Output Schema:**
```json
{
    "actionType": {
        "description": "string",
        "executor": {
            "configuration": {
                "lambdaExecutorConfiguration": {
                    "lambdaFunctionArn": "string"
                },
                "jobWorkerExecutorConfiguration": {
                    "pollingAccounts": ["string"],
                    "pollingServicePrincipals": ["string"]
                }
            },
            "type": "JobWorker|Lambda",
            "policyStatementsTemplate": "string",
            "jobTimeout": "integer"
        },
        "id": {
            "category": "Source|Build|Deploy|Test|Invoke|Approval",
            "owner": "string",
            "provider": "string",
            "version": "string"
        },
        "inputArtifactDetails": {
            "minimumCount": "integer",
            "maximumCount": "integer"
        },
        "outputArtifactDetails": {
            "minimumCount": "integer",
            "maximumCount": "integer"
        },
        "permissions": {
            "allowedAccounts": ["string"]
        },
        "properties": [
            {
                "name": "string",
                "optional": true|false,
                "key": true|false,
                "noEcho": true|false,
                "queryable": true|false,
                "description": "string"
            }
        ],
        "urls": {
            "configurationUrl": "string",
            "entityUrlTemplate": "string",
            "executionUrlTemplate": "string",
            "revisionUrlTemplate": "string"
        }
    }
}
```

---

### 4.2 `list-action-types`

Gets a summary of all action types available for pipelines in your account. **Paginated operation.**

**Synopsis:**
```bash
aws codepipeline list-action-types \
    [--action-owner-filter <value>] \
    [--region-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-owner-filter` | No | string | None | Filter by owner: `AWS`, `ThirdParty`, `Custom` |
| `--region-filter` | No | string | None | Filter by region |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "actionTypes": [
        {
            "id": {
                "category": "Source|Build|Deploy|Test|Invoke|Approval",
                "owner": "AWS|ThirdParty|Custom",
                "provider": "string",
                "version": "string"
            },
            "settings": {
                "thirdPartyConfigurationUrl": "string",
                "entityUrlTemplate": "string",
                "executionUrlTemplate": "string",
                "revisionUrlTemplate": "string"
            },
            "actionConfigurationProperties": [
                {
                    "name": "string",
                    "required": true|false,
                    "key": true|false,
                    "secret": true|false,
                    "queryable": true|false,
                    "description": "string",
                    "type": "String|Number|Boolean"
                }
            ],
            "inputArtifactDetails": {
                "minimumCount": "integer",
                "maximumCount": "integer"
            },
            "outputArtifactDetails": {
                "minimumCount": "integer",
                "maximumCount": "integer"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 4.3 `update-action-type`

Updates an action type that was created with any supported integration model.

**Synopsis:**
```bash
aws codepipeline update-action-type \
    --action-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-type` | **Yes** | structure | -- | Action type structure (same as `get-action-type` output `actionType` format) |

**Output Schema:**
```json
{}
```
