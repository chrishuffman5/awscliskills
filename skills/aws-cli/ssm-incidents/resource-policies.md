# Resource Policies

### 7.1 `get-resource-policies`

Retrieves the resource policies attached to the specified response plan. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-incidents get-resource-policies \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN (response plan ARN) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "resourcePolicies": [
        {
            "policyId": "string",
            "policyDocument": "string",
            "ramResourceShareRegion": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.2 `put-resource-policy`

Adds a resource policy to the specified response plan.

**Synopsis:**
```bash
aws ssm-incidents put-resource-policy \
    --resource-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--policy` | **Yes** | string | -- | JSON resource policy document |

**Output Schema:**
```json
{
    "policyId": "string"
}
```

---

### 7.3 `delete-resource-policy`

Deletes the specified resource policy.

**Synopsis:**
```bash
aws ssm-incidents delete-resource-policy \
    --resource-arn <value> \
    --policy-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--policy-id` | **Yes** | string | -- | Policy ID to delete |

**Output Schema:**
```json
{}
```
