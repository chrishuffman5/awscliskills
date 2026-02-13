# Log Data Protection

### 17.1 `put-data-protection-policy`

Creates or updates a data protection policy to audit and mask sensitive data in log events.

**Synopsis:**
```bash
aws logs put-data-protection-policy \
    --log-group-identifier <value> \
    --policy-document <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-identifier` | **Yes** | string | -- | Log group name or ARN |
| `--policy-document` | **Yes** | string | -- | Data protection policy document in JSON |

**Output Schema:**
```json
{
    "logGroupIdentifier": "string",
    "policyDocument": "string",
    "lastUpdatedTime": long
}
```

---

### 17.2 `get-data-protection-policy`

Retrieves the data protection policy for a log group.

**Synopsis:**
```bash
aws logs get-data-protection-policy \
    --log-group-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-identifier` | **Yes** | string | -- | Log group name or ARN |

**Output Schema:**
```json
{
    "logGroupIdentifier": "string",
    "policyDocument": "string",
    "lastUpdatedTime": long
}
```

---

### 17.3 `delete-data-protection-policy`

Deletes the data protection policy from a log group.

**Synopsis:**
```bash
aws logs delete-data-protection-policy \
    --log-group-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-identifier` | **Yes** | string | -- | Log group name or ARN |

**Output:** None on success.

---
