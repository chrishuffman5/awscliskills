# TTL (Time to Live)

### 11.1 `describe-time-to-live`

Describes the TTL settings for a table.

**Synopsis:**
```bash
aws dynamodb describe-time-to-live \
    --table-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |

**Output Schema:**
```json
{
    "TimeToLiveDescription": {
        "TimeToLiveStatus": "ENABLING|DISABLING|ENABLED|DISABLED",
        "AttributeName": "string"
    }
}
```

---

### 11.2 `update-time-to-live`

Enables or disables TTL on a table. When enabled, DynamoDB automatically deletes expired items.

**Synopsis:**
```bash
aws dynamodb update-time-to-live \
    --table-name <value> \
    --time-to-live-specification <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-name` | **Yes** | string | -- | Table name or ARN (1-1024 chars) |
| `--time-to-live-specification` | **Yes** | structure | -- | Shorthand: `Enabled=true\|false,AttributeName=string` |

**Output Schema:**
```json
{
    "TimeToLiveSpecification": {
        "Enabled": "boolean",
        "AttributeName": "string"
    }
}
```

---
