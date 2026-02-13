# Resource Policies

### 15.1 `put-resource-policy`

Attaches a resource-based policy to a table or stream.

**Synopsis:**
```bash
aws dynamodb put-resource-policy \
    --resource-arn <value> \
    --policy <value> \
    [--expected-revision-id <value>] \
    [--confirm-remove-self-resource-access | --no-confirm-remove-self-resource-access] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Table or stream ARN (1-1283 chars) |
| `--policy` | **Yes** | string | -- | JSON resource-based policy document (max 20 KB) |
| `--expected-revision-id` | No | string | -- | Expected current revision ID for optimistic locking |
| `--confirm-remove-self-resource-access` | No | boolean | false | Confirm removal of permissions for the caller |

**Output Schema:**
```json
{
    "RevisionId": "string"
}
```

---

### 15.2 `get-resource-policy`

Returns the resource-based policy attached to a table or stream.

**Synopsis:**
```bash
aws dynamodb get-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Table or stream ARN (1-1283 chars) |

**Output Schema:**
```json
{
    "Policy": "string",
    "RevisionId": "string"
}
```

---

### 15.3 `delete-resource-policy`

Deletes the resource-based policy from a table or stream.

**Synopsis:**
```bash
aws dynamodb delete-resource-policy \
    --resource-arn <value> \
    [--expected-revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Table or stream ARN (1-1283 chars) |
| `--expected-revision-id` | No | string | -- | Expected current revision ID for optimistic locking |

**Output Schema:**
```json
{
    "RevisionId": "string"
}
```

---
