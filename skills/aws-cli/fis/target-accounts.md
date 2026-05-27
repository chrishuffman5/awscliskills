# Target Accounts

### 4.1 `create-target-account-configuration`

Creates a target account configuration for multi-account experiments.

**Synopsis:**
```bash
aws fis create-target-account-configuration \
    --experiment-template-id <value> \
    --account-id <value> \
    --role-arn <value> \
    [--client-token <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-template-id` | **Yes** | string | -- | ID of the experiment template |
| `--account-id` | **Yes** | string | -- | Target AWS account ID (12 digits) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN in the target account |
| `--client-token` | No | string | Auto-generated | Idempotency token |
| `--description` | No | string | None | Description of the configuration |

**Output Schema:**
```json
{
    "targetAccountConfiguration": {
        "roleArn": "string",
        "accountId": "string",
        "description": "string"
    }
}
```

---

### 4.2 `delete-target-account-configuration`

Deletes a target account configuration.

**Synopsis:**
```bash
aws fis delete-target-account-configuration \
    --experiment-template-id <value> \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-template-id` | **Yes** | string | -- | ID of the experiment template |
| `--account-id` | **Yes** | string | -- | Target AWS account ID |

**Output Schema:**
```json
{
    "targetAccountConfiguration": {
        "roleArn": "string",
        "accountId": "string",
        "description": "string"
    }
}
```

---

### 4.3 `get-target-account-configuration`

Returns a target account configuration for an experiment template.

**Synopsis:**
```bash
aws fis get-target-account-configuration \
    --experiment-template-id <value> \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-template-id` | **Yes** | string | -- | ID of the experiment template |
| `--account-id` | **Yes** | string | -- | Target AWS account ID |

**Output Schema:**
```json
{
    "targetAccountConfiguration": {
        "roleArn": "string",
        "accountId": "string",
        "description": "string"
    }
}
```

---

### 4.4 `list-target-account-configurations`

Lists target account configurations for an experiment template. **Paginated operation.**

**Synopsis:**
```bash
aws fis list-target-account-configurations \
    --experiment-template-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-template-id` | **Yes** | string | -- | ID of the experiment template |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "targetAccountConfigurations": [
        {
            "roleArn": "string",
            "accountId": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.5 `update-target-account-configuration`

Updates a target account configuration.

**Synopsis:**
```bash
aws fis update-target-account-configuration \
    --experiment-template-id <value> \
    --account-id <value> \
    [--role-arn <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-template-id` | **Yes** | string | -- | ID of the experiment template |
| `--account-id` | **Yes** | string | -- | Target AWS account ID |
| `--role-arn` | No | string | None | Updated IAM role ARN |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "targetAccountConfiguration": {
        "roleArn": "string",
        "accountId": "string",
        "description": "string"
    }
}
```

---

### 4.6 `get-experiment-target-account-configuration`

Returns the target account configuration for a running or completed experiment.

**Synopsis:**
```bash
aws fis get-experiment-target-account-configuration \
    --experiment-id <value> \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-id` | **Yes** | string | -- | ID of the experiment |
| `--account-id` | **Yes** | string | -- | Target AWS account ID |

**Output Schema:**
```json
{
    "targetAccountConfiguration": {
        "roleArn": "string",
        "accountId": "string",
        "description": "string"
    }
}
```

---

### 4.7 `list-experiment-target-account-configurations`

Lists target account configurations for a running or completed experiment. **Paginated operation.**

**Synopsis:**
```bash
aws fis list-experiment-target-account-configurations \
    --experiment-id <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-id` | **Yes** | string | -- | ID of the experiment |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "targetAccountConfigurations": [
        {
            "roleArn": "string",
            "accountId": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```
