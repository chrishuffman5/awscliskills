# Resource Policies

### 6.1 `describe-resource-policy`

Describes the resource policy for a workspace.

**Synopsis:**
```bash
aws amp describe-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the workspace |

**Output Schema:**
```json
{
    "policy": "string",
    "revisionId": "string"
}
```

---

### 6.2 `put-resource-policy`

Creates or updates the resource policy for a workspace. Used for cross-account access.

**Synopsis:**
```bash
aws amp put-resource-policy \
    --resource-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the workspace |
| `--policy` | **Yes** | string | -- | JSON resource policy document |

**Output Schema:**
```json
{
    "policy": "string",
    "revisionId": "string"
}
```

---

### 6.3 `delete-resource-policy`

Deletes the resource policy from a workspace.

**Synopsis:**
```bash
aws amp delete-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the workspace |

**Output Schema:**
```json
{}
```
