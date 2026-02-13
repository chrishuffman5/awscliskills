# Automated Reasoning

### `create-automated-reasoning-policy`

Creates an Automated Reasoning policy for Amazon Bedrock Guardrails. Automated reasoning uses mathematical techniques to detect hallucinations, suggest corrections, and highlight unstated assumptions.

**Synopsis:**
```bash
aws bedrock create-automated-reasoning-policy \
    --name <value> \
    [--description <value>] \
    [--client-request-token <value>] \
    [--policy-definition <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Policy name (1-256 chars). Pattern: `[0-9a-zA-Z-_ ]+` |
| `--description` | No | string | None | Policy description (0-1024 chars) |
| `--client-request-token` | No | string | None | Idempotency token (1-256 chars) |
| `--policy-definition` | No | structure | None | Policy definition with rules, variables, and types |
| `--kms-key-id` | No | string | None | KMS key for encryption (1-2048 chars) |
| `--tags` | No | list | None | Tags (max 200) |

**Policy Definition Structure:**
```json
{
    "version": "string",
    "types": [
        {
            "name": "string",
            "description": "string",
            "values": [
                {
                    "value": "string",
                    "description": "string"
                }
            ]
        }
    ],
    "rules": [
        {
            "id": "string",
            "expression": "string",
            "alternateExpression": "string"
        }
    ],
    "variables": [
        {
            "name": "string",
            "type": "string",
            "description": "string"
        }
    ]
}
```

**Output Schema:**
```json
{
    "policyArn": "string",
    "version": "string",
    "name": "string",
    "description": "string",
    "definitionHash": "string",
    "createdAt": "timestamp",
    "updatedAt": "timestamp"
}
```

---

### `get-automated-reasoning-policy`

Gets details of an automated reasoning policy.

**Synopsis:**
```bash
aws bedrock get-automated-reasoning-policy \
    --policy-identifier <value> \
    [--policy-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-identifier` | **Yes** | string | -- | Policy ARN or ID |
| `--policy-version` | No | string | None | Version number or `DRAFT` |

**Output Schema:**
```json
{
    "policyArn": "string",
    "name": "string",
    "description": "string",
    "version": "string",
    "status": "CREATING|ACTIVE|FAILED|DELETING",
    "policyDefinition": {
        "version": "string",
        "types": [...],
        "rules": [...],
        "variables": [...]
    },
    "definitionHash": "string",
    "kmsKeyArn": "string",
    "createdAt": "timestamp",
    "updatedAt": "timestamp"
}
```

---

### `list-automated-reasoning-policies`

Lists automated reasoning policies. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-automated-reasoning-policies \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "automatedReasoningPolicySummaries": [
        {
            "policyArn": "string",
            "name": "string",
            "description": "string",
            "version": "string",
            "status": "CREATING|ACTIVE|FAILED|DELETING",
            "createdAt": "timestamp",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `delete-automated-reasoning-policy`

Deletes an automated reasoning policy.

**Synopsis:**
```bash
aws bedrock delete-automated-reasoning-policy \
    --policy-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-identifier` | **Yes** | string | -- | Policy ARN or ID |

**Output:** None (HTTP 200 on success)

---

### `create-automated-reasoning-policy-version`

Creates a versioned snapshot of an automated reasoning policy.

**Synopsis:**
```bash
aws bedrock create-automated-reasoning-policy-version \
    --policy-identifier <value> \
    [--definition-hash <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-identifier` | **Yes** | string | -- | Policy ARN or ID |
| `--definition-hash` | No | string | None | Expected hash for optimistic locking |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "policyArn": "string",
    "version": "string"
}
```

---

### `create-automated-reasoning-policy-test-case`

Creates a test case for an automated reasoning policy.

**Synopsis:**
```bash
aws bedrock create-automated-reasoning-policy-test-case \
    --policy-identifier <value> \
    --test-case <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-identifier` | **Yes** | string | -- | Policy ARN or ID |
| `--test-case` | **Yes** | structure | -- | Test case definition |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "testCaseId": "string",
    "results": [...]
}
```

---

### `start-automated-reasoning-policy-build-workflow`

Starts a build workflow for an automated reasoning policy. This compiles the policy rules.

**Synopsis:**
```bash
aws bedrock start-automated-reasoning-policy-build-workflow \
    --policy-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-identifier` | **Yes** | string | -- | Policy ARN or ID |

**Output Schema:**
```json
{
    "policyArn": "string",
    "workflowId": "string"
}
```

---

### `cancel-automated-reasoning-policy-build-workflow`

Cancels a running automated reasoning policy build workflow.

**Synopsis:**
```bash
aws bedrock cancel-automated-reasoning-policy-build-workflow \
    --policy-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-identifier` | **Yes** | string | -- | Policy ARN or ID |

**Output:** None (HTTP 200 on success)

---

### `get-automated-reasoning-policy-build-workflow-status`

Gets the status of an automated reasoning policy build workflow.

**Synopsis:**
```bash
aws bedrock get-automated-reasoning-policy-build-workflow-status \
    --policy-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-identifier` | **Yes** | string | -- | Policy ARN or ID |

**Output Schema:**
```json
{
    "policyArn": "string",
    "workflowId": "string",
    "status": "IN_PROGRESS|COMPLETED|FAILED|CANCELLED",
    "message": "string"
}
```
