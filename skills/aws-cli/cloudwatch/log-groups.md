# Log Groups

### 8.1 `create-log-group`

Creates a log group with the specified name.

**Synopsis:**
```bash
aws logs create-log-group \
    --log-group-name <value> \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--log-group-class <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars). Pattern: `[\.\-_/#A-Za-z0-9]+` |
| `--kms-key-id` | No | string | -- | KMS key ARN for encryption (max 256 chars) |
| `--tags` | No | map | -- | Key-value tags (1-50 tags) |
| `--log-group-class` | No | string | `STANDARD` | `STANDARD`, `INFREQUENT_ACCESS`, or `DELIVERY` |

**Output:** None on success.

---

### 8.2 `delete-log-group`

Deletes a log group and all associated archived log events.

**Synopsis:**
```bash
aws logs delete-log-group \
    --log-group-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars) |

**Output:** None on success.

---

### 8.3 `describe-log-groups`

Lists log groups. **Paginated.**

**Synopsis:**
```bash
aws logs describe-log-groups \
    [--log-group-name-prefix <value>] \
    [--log-group-name-pattern <value>] \
    [--account-identifiers <value>] \
    [--include-linked-accounts | --no-include-linked-accounts] \
    [--log-group-class <value>] \
    [--log-group-identifiers <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name-prefix` | No | string | -- | Prefix to match (mutually exclusive with `--log-group-name-pattern`) |
| `--log-group-name-pattern` | No | string | -- | Case-sensitive substring match (mutually exclusive with prefix) |
| `--account-identifiers` | No | list | -- | Account IDs to search (max 20, requires `--include-linked-accounts`) |
| `--include-linked-accounts` | No | boolean | false | Include linked source accounts |
| `--log-group-class` | No | string | -- | `STANDARD`, `INFREQUENT_ACCESS`, `DELIVERY` |
| `--log-group-identifiers` | No | list | -- | Specific log group ARNs or names (1-50) |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "logGroups": [
        {
            "logGroupName": "string",
            "creationTime": long,
            "retentionInDays": integer,
            "metricFilterCount": integer,
            "arn": "string",
            "storedBytes": long,
            "kmsKeyId": "string",
            "dataProtectionStatus": "ACTIVATED|DELETED|ARCHIVED|DISABLED",
            "inheritedProperties": ["ACCOUNT_DATA_PROTECTION"],
            "logGroupClass": "STANDARD|INFREQUENT_ACCESS|DELIVERY",
            "logGroupArn": "string",
            "deletionProtectionEnabled": true|false
        }
    ],
    "nextToken": "string"
}
```

---

### 8.4 `put-retention-policy`

Sets the retention policy for a log group. Log events older than the retention period are deleted.

**Synopsis:**
```bash
aws logs put-retention-policy \
    --log-group-name <value> \
    --retention-in-days <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars) |
| `--retention-in-days` | **Yes** | integer | -- | Valid values: 1, 3, 5, 7, 14, 30, 60, 90, 120, 150, 180, 365, 400, 545, 731, 1096, 1827, 2192, 2557, 2922, 3288, 3653 |

**Output:** None on success.

---

### 8.5 `delete-retention-policy`

Removes the retention policy from a log group. Events will be retained indefinitely.

**Synopsis:**
```bash
aws logs delete-retention-policy \
    --log-group-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | **Yes** | string | -- | Log group name (1-512 chars) |

**Output:** None on success.

---

### 8.6 `associate-kms-key`

Associates a KMS key with a log group for encryption.

**Synopsis:**
```bash
aws logs associate-kms-key \
    [--log-group-name <value>] \
    --kms-key-id <value> \
    [--resource-identifier <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | No | string | -- | Log group name (1-512 chars) |
| `--kms-key-id` | **Yes** | string | -- | KMS key ARN (max 256 chars) |
| `--resource-identifier` | No | string | -- | Log group ARN (for specific resource) |

**Output:** None on success.

---

### 8.7 `disassociate-kms-key`

Removes KMS key association from a log group.

**Synopsis:**
```bash
aws logs disassociate-kms-key \
    [--log-group-name <value>] \
    [--resource-identifier <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | No | string | -- | Log group name (1-512 chars) |
| `--resource-identifier` | No | string | -- | Log group ARN |

**Output:** None on success.

---
