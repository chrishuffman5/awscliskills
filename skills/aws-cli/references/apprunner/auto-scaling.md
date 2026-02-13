# Auto Scaling

### 3.1 `create-auto-scaling-configuration`

Creates an auto scaling configuration for App Runner.

**Synopsis:**
```bash
aws apprunner create-auto-scaling-configuration \
    --auto-scaling-configuration-name <value> \
    [--max-concurrency <value>] \
    [--min-size <value>] \
    [--max-size <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-configuration-name` | **Yes** | string | -- | Name for the config |
| `--max-concurrency` | No | integer | 100 | Max concurrent requests per instance |
| `--min-size` | No | integer | 1 | Min number of instances |
| `--max-size` | No | integer | 25 | Max number of instances |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "AutoScalingConfiguration": {
        "AutoScalingConfigurationArn": "string",
        "AutoScalingConfigurationName": "string",
        "AutoScalingConfigurationRevision": "integer",
        "Latest": true|false,
        "Status": "ACTIVE|INACTIVE",
        "MaxConcurrency": "integer",
        "MinSize": "integer",
        "MaxSize": "integer",
        "CreatedAt": "timestamp",
        "DeletedAt": "timestamp",
        "HasAssociatedService": true|false,
        "IsDefault": true|false
    }
}
```

---

### 3.2 `delete-auto-scaling-configuration`

Deletes an auto scaling configuration.

**Synopsis:**
```bash
aws apprunner delete-auto-scaling-configuration \
    --auto-scaling-configuration-arn <value> \
    [--delete-all-revisions | --no-delete-all-revisions] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-configuration-arn` | **Yes** | string | -- | ARN of the config (specific revision or latest) |
| `--delete-all-revisions` | No | boolean | false | Delete all revisions |

**Output Schema:**
```json
{
    "AutoScalingConfiguration": {
        "AutoScalingConfigurationArn": "string",
        "AutoScalingConfigurationName": "string",
        "AutoScalingConfigurationRevision": "integer",
        "Status": "INACTIVE"
    }
}
```

---

### 3.3 `describe-auto-scaling-configuration`

Returns a description of an auto scaling configuration.

**Synopsis:**
```bash
aws apprunner describe-auto-scaling-configuration \
    --auto-scaling-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-configuration-arn` | **Yes** | string | -- | ARN of the config |

**Output Schema:**
```json
{
    "AutoScalingConfiguration": {
        "AutoScalingConfigurationArn": "string",
        "AutoScalingConfigurationName": "string",
        "AutoScalingConfigurationRevision": "integer",
        "Latest": true|false,
        "Status": "ACTIVE|INACTIVE",
        "MaxConcurrency": "integer",
        "MinSize": "integer",
        "MaxSize": "integer",
        "CreatedAt": "timestamp",
        "DeletedAt": "timestamp",
        "HasAssociatedService": true|false,
        "IsDefault": true|false
    }
}
```

---

### 3.4 `list-auto-scaling-configurations`

Lists auto scaling configurations. **Paginated operation.**

**Synopsis:**
```bash
aws apprunner list-auto-scaling-configurations \
    [--auto-scaling-configuration-name <value>] \
    [--latest-only | --no-latest-only] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-configuration-name` | No | string | None | Filter by name |
| `--latest-only` | No | boolean | true | Only return latest revisions |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AutoScalingConfigurationSummaryList": [
        {
            "AutoScalingConfigurationArn": "string",
            "AutoScalingConfigurationName": "string",
            "AutoScalingConfigurationRevision": "integer",
            "Status": "ACTIVE|INACTIVE",
            "CreatedAt": "timestamp",
            "HasAssociatedService": true|false,
            "IsDefault": true|false
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `list-services-for-auto-scaling-configuration`

Lists services associated with an auto scaling configuration. **Paginated operation.**

**Synopsis:**
```bash
aws apprunner list-services-for-auto-scaling-configuration \
    --auto-scaling-configuration-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-configuration-arn` | **Yes** | string | -- | ARN of the auto scaling configuration |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ServiceArnList": ["string"],
    "NextToken": "string"
}
```

---

### 3.6 `update-default-auto-scaling-configuration`

Updates the default auto scaling configuration for the account.

**Synopsis:**
```bash
aws apprunner update-default-auto-scaling-configuration \
    --auto-scaling-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-configuration-arn` | **Yes** | string | -- | ARN of the config to set as default |

**Output Schema:**
```json
{
    "AutoScalingConfiguration": {
        "AutoScalingConfigurationArn": "string",
        "AutoScalingConfigurationName": "string",
        "AutoScalingConfigurationRevision": "integer",
        "Latest": true|false,
        "Status": "ACTIVE",
        "MaxConcurrency": "integer",
        "MinSize": "integer",
        "MaxSize": "integer",
        "IsDefault": true
    }
}
```
