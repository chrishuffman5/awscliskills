# Retention & Queries

### 10.1 `put-retention-configuration`

Creates or updates the retention period for AWS Config configuration history and configuration snapshots.

**Synopsis:**
```bash
aws configservice put-retention-configuration \
    --retention-period-in-days <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--retention-period-in-days` | **Yes** | integer | -- | Number of days to retain (30-2557, i.e. ~7 years) |

**Output Schema:**
```json
{
    "RetentionConfiguration": {
        "Name": "string",
        "RetentionPeriodInDays": "integer"
    }
}
```

---

### 10.2 `delete-retention-configuration`

Deletes the retention configuration.

**Synopsis:**
```bash
aws configservice delete-retention-configuration \
    --retention-configuration-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--retention-configuration-name` | **Yes** | string | -- | Name of the retention configuration (e.g., `default`) |

**Output Schema:**
```json
{}
```

---

### 10.3 `describe-retention-configurations`

Returns the details of the retention configuration. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-retention-configurations \
    [--retention-configuration-names <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--retention-configuration-names` | No | list(string) | None | Specific retention config names |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RetentionConfigurations": [
        {
            "Name": "string",
            "RetentionPeriodInDays": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.4 `put-stored-query`

Creates or updates a stored query for use with `select-resource-config` or `select-aggregate-resource-config`.

**Synopsis:**
```bash
aws configservice put-stored-query \
    --stored-query <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stored-query` | **Yes** | structure | -- | Stored query definition |
| `--tags` | No | list | None | Tags to apply |

**Stored Query Structure:**
```json
{
    "QueryId": "string",
    "QueryArn": "string",
    "QueryName": "string",
    "Description": "string",
    "Expression": "string"
}
```

**Output Schema:**
```json
{
    "QueryArn": "string"
}
```

---

### 10.5 `delete-stored-query`

Deletes a stored query.

**Synopsis:**
```bash
aws configservice delete-stored-query \
    --query-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-name` | **Yes** | string | -- | Name of the stored query to delete |

**Output Schema:**
```json
{}
```

---

### 10.6 `get-stored-query`

Returns the details of a stored query.

**Synopsis:**
```bash
aws configservice get-stored-query \
    --query-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-name` | **Yes** | string | -- | Name of the stored query |

**Output Schema:**
```json
{
    "StoredQuery": {
        "QueryId": "string",
        "QueryArn": "string",
        "QueryName": "string",
        "Description": "string",
        "Expression": "string"
    }
}
```

---

### 10.7 `list-stored-queries`

Lists all stored queries. **Paginated operation.**

**Synopsis:**
```bash
aws configservice list-stored-queries \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "StoredQueryMetadata": [
        {
            "QueryId": "string",
            "QueryArn": "string",
            "QueryName": "string",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```
