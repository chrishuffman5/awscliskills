# Resource Policies

### 12.1 `create-resource-policy`

Creates a resource-based policy for a bot or bot alias to grant cross-account access.

**Synopsis:**
```bash
aws lexv2-models create-resource-policy \
    --resource-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the bot or bot alias (1-1011 chars) |
| `--policy` | **Yes** | string | -- | Resource policy JSON document (2+ chars) |

**Output Schema:**
```json
{
    "resourceArn": "string",
    "revisionId": "string"
}
```

---

### 12.2 `delete-resource-policy`

Deletes a resource policy from a bot or bot alias.

**Synopsis:**
```bash
aws lexv2-models delete-resource-policy \
    --resource-arn <value> \
    [--expected-revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the bot or bot alias |
| `--expected-revision-id` | No | string | None | Expected revision ID for optimistic locking |

**Output Schema:**
```json
{
    "resourceArn": "string",
    "revisionId": "string"
}
```

---

### 12.3 `describe-resource-policy`

Gets the resource policy for a bot or bot alias.

**Synopsis:**
```bash
aws lexv2-models describe-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the bot or bot alias |

**Output Schema:**
```json
{
    "resourceArn": "string",
    "policy": "string",
    "revisionId": "string"
}
```

---

### 12.4 `update-resource-policy`

Replaces the resource policy on a bot or bot alias.

**Synopsis:**
```bash
aws lexv2-models update-resource-policy \
    --resource-arn <value> \
    --policy <value> \
    [--expected-revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the bot or bot alias |
| `--policy` | **Yes** | string | -- | Updated resource policy JSON document |
| `--expected-revision-id` | No | string | None | Expected revision ID for optimistic locking |

**Output Schema:**
```json
{
    "resourceArn": "string",
    "revisionId": "string"
}
```

---

### 12.5 `create-resource-policy-statement`

Adds a statement to a resource policy. If the policy does not exist, a new one is created.

**Synopsis:**
```bash
aws lexv2-models create-resource-policy-statement \
    --resource-arn <value> \
    --statement-id <value> \
    --effect <value> \
    --principal <value> \
    --action <value> \
    [--condition <value>] \
    [--expected-revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the bot or bot alias |
| `--statement-id` | **Yes** | string | -- | Statement ID (1-100 chars, pattern: `^([0-9a-zA-Z][_-]?){1,100}$`) |
| `--effect` | **Yes** | string | -- | `Allow` or `Deny` |
| `--principal` | **Yes** | list | -- | AWS principals to grant/deny access |
| `--action` | **Yes** | list(string) | -- | Actions to allow/deny (e.g., `lex:RecognizeText`) |
| `--condition` | No | map | None | Conditions for the statement |
| `--expected-revision-id` | No | string | None | Expected revision ID for optimistic locking |

**Output Schema:**
```json
{
    "resourceArn": "string",
    "revisionId": "string"
}
```

---

### 12.6 `delete-resource-policy-statement`

Removes a statement from a resource policy.

**Synopsis:**
```bash
aws lexv2-models delete-resource-policy-statement \
    --resource-arn <value> \
    --statement-id <value> \
    [--expected-revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the bot or bot alias |
| `--statement-id` | **Yes** | string | -- | Statement ID to remove |
| `--expected-revision-id` | No | string | None | Expected revision ID for optimistic locking |

**Output Schema:**
```json
{
    "resourceArn": "string",
    "revisionId": "string"
}
```
