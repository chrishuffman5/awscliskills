# Observability

### 4.1 `create-observability-configuration`

Creates an observability configuration for App Runner (X-Ray tracing).

**Synopsis:**
```bash
aws apprunner create-observability-configuration \
    --observability-configuration-name <value> \
    --trace-configuration <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--observability-configuration-name` | **Yes** | string | -- | Name for the config |
| `--trace-configuration` | **Yes** | structure | -- | Trace config. Shorthand: `Vendor=AWSXRAY` |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "ObservabilityConfiguration": {
        "ObservabilityConfigurationArn": "string",
        "ObservabilityConfigurationName": "string",
        "ObservabilityConfigurationRevision": "integer",
        "Latest": true|false,
        "Status": "ACTIVE|INACTIVE",
        "TraceConfiguration": {
            "Vendor": "AWSXRAY"
        },
        "CreatedAt": "timestamp",
        "DeletedAt": "timestamp"
    }
}
```

---

### 4.2 `delete-observability-configuration`

Deletes an observability configuration.

**Synopsis:**
```bash
aws apprunner delete-observability-configuration \
    --observability-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--observability-configuration-arn` | **Yes** | string | -- | ARN of the config to delete |

**Output Schema:**
```json
{
    "ObservabilityConfiguration": {
        "ObservabilityConfigurationArn": "string",
        "ObservabilityConfigurationName": "string",
        "Status": "INACTIVE"
    }
}
```

---

### 4.3 `describe-observability-configuration`

Returns a description of an observability configuration.

**Synopsis:**
```bash
aws apprunner describe-observability-configuration \
    --observability-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--observability-configuration-arn` | **Yes** | string | -- | ARN of the config |

**Output Schema:**
```json
{
    "ObservabilityConfiguration": {
        "ObservabilityConfigurationArn": "string",
        "ObservabilityConfigurationName": "string",
        "ObservabilityConfigurationRevision": "integer",
        "Latest": true|false,
        "Status": "ACTIVE|INACTIVE",
        "TraceConfiguration": {
            "Vendor": "AWSXRAY"
        },
        "CreatedAt": "timestamp",
        "DeletedAt": "timestamp"
    }
}
```

---

### 4.4 `list-observability-configurations`

Lists observability configurations. **Paginated operation.**

**Synopsis:**
```bash
aws apprunner list-observability-configurations \
    [--observability-configuration-name <value>] \
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
| `--observability-configuration-name` | No | string | None | Filter by name |
| `--latest-only` | No | boolean | true | Only return latest revisions |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ObservabilityConfigurationSummaryList": [
        {
            "ObservabilityConfigurationArn": "string",
            "ObservabilityConfigurationName": "string",
            "ObservabilityConfigurationRevision": "integer",
            "Status": "ACTIVE|INACTIVE",
            "CreatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
