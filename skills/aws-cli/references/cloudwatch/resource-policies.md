# Resource Policies

### 16.1 `put-resource-policy`

Creates or updates a resource policy allowing other AWS services to put log events to this account.

**Synopsis:**
```bash
aws logs put-resource-policy \
    [--policy-name <value>] \
    [--policy-document <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | No | string | -- | Policy name |
| `--policy-document` | No | string | -- | IAM policy document in JSON (max 5120 chars) |

**Output Schema:**
```json
{
    "resourcePolicy": {
        "policyName": "string",
        "policyDocument": "string",
        "lastUpdatedTime": long
    }
}
```

---

### 16.2 `describe-resource-policies`

Lists resource policies. **Paginated.**

**Synopsis:**
```bash
aws logs describe-resource-policies \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "resourcePolicies": [
        {
            "policyName": "string",
            "policyDocument": "string",
            "lastUpdatedTime": long
        }
    ],
    "nextToken": "string"
}
```

---

### 16.3 `delete-resource-policy`

Deletes a resource policy.

**Synopsis:**
```bash
aws logs delete-resource-policy \
    [--policy-name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | No | string | -- | Policy name to delete |

**Output:** None on success.

---
