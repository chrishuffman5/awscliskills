# Resource Policies

### 11.1 `put-resource-policy`

Attaches a resource-based policy to a custom model (document classifier or entity recognizer) to enable cross-account access.

**Synopsis:**
```bash
aws comprehend put-resource-policy \
    --resource-arn <value> \
    --resource-policy <value> \
    [--policy-revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the custom model to attach the policy to |
| `--resource-policy` | **Yes** | string | -- | JSON resource-based policy (max 20000 chars) |
| `--policy-revision-id` | No | string | -- | Revision ID of the policy being updated. Omit when creating a new policy |

**Output Schema:**
```json
{
    "PolicyRevisionId": "string"
}
```

---

### 11.2 `delete-resource-policy`

Deletes a resource-based policy attached to a custom model.

**Synopsis:**
```bash
aws comprehend delete-resource-policy \
    --resource-arn <value> \
    [--policy-revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the custom model with the policy to delete |
| `--policy-revision-id` | No | string | -- | Revision ID of the policy to delete |

**Output:** None (HTTP 200 on success)

---

### 11.3 `describe-resource-policy`

Gets the resource-based policy attached to a custom model.

**Synopsis:**
```bash
aws comprehend describe-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the custom model |

**Output Schema:**
```json
{
    "ResourcePolicy": "string",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "PolicyRevisionId": "string"
}
```

---

### 11.4 `import-model`

Imports a custom model (document classifier or entity recognizer) from another AWS account using a resource-based policy.

**Synopsis:**
```bash
aws comprehend import-model \
    --source-model-arn <value> \
    [--model-name <value>] \
    [--version-name <value>] \
    [--model-kms-key-id <value>] \
    [--data-access-role-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-model-arn` | **Yes** | string | -- | ARN of the custom model to import |
| `--model-name` | No | string | -- | Name for the imported model (max 63 chars) |
| `--version-name` | No | string | -- | Version name for the imported model (max 63 chars) |
| `--model-kms-key-id` | No | string | -- | KMS key for encrypting the imported model |
| `--data-access-role-arn` | No | string | -- | IAM role ARN for KMS access |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "ModelArn": "string"
}
```
