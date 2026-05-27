# Resource Policies

### 6.1 `get-resource-policy`

Retrieves the JSON resource-based policy attached to a secret.

**Synopsis:**
```bash
aws secretsmanager get-resource-policy \
    --secret-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string",
    "ResourcePolicy": "string"
}
```

---

### 6.2 `put-resource-policy`

Attaches a resource-based policy to a secret for cross-account access or fine-grained permissions.

**Synopsis:**
```bash
aws secretsmanager put-resource-policy \
    --secret-id <value> \
    --resource-policy <value> \
    [--block-public-policy | --no-block-public-policy] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |
| `--resource-policy` | **Yes** | string | -- | JSON policy document (1-20480 chars). Use `file://policy.json` for file input |
| `--block-public-policy` | No | boolean | false | Block policies that allow broad access (wildcard principals) |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string"
}
```

---

### 6.3 `delete-resource-policy`

Removes the resource-based policy attached to a secret.

**Synopsis:**
```bash
aws secretsmanager delete-resource-policy \
    --secret-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string"
}
```

---

### 6.4 `validate-resource-policy`

Validates a resource-based policy before attaching it. Uses Zelkova automated reasoning, syntax checking, and caller lockout verification.

**Synopsis:**
```bash
aws secretsmanager validate-resource-policy \
    [--secret-id <value>] \
    --resource-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | No | string | None | ARN or name of the secret to validate against (1-2048 chars) |
| `--resource-policy` | **Yes** | string | -- | JSON policy document to validate (1-20480 chars) |

**Output Schema:**
```json
{
    "PolicyValidationPassed": true|false,
    "ValidationErrors": [
        {
            "CheckName": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---
