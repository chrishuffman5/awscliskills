# Tags

### 8.1 `add-tags`

Adds the specified tags to the specified resource. Supports load balancers, target groups, listeners, rules, and trust stores.

**Synopsis:**
```bash
aws elbv2 add-tags \
    --resource-arns <value> \
    --tags <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arns` | **Yes** | list | -- | ARNs of the resources |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Output Schema:** None (no output on success).

---

### 8.2 `remove-tags`

Removes the specified tags from the specified resource.

**Synopsis:**
```bash
aws elbv2 remove-tags \
    --resource-arns <value> \
    --tag-keys <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arns` | **Yes** | list | -- | ARNs of the resources |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output Schema:** None (no output on success).

---

### 8.3 `describe-tags`

Describes the tags for the specified resources (max 20).

**Synopsis:**
```bash
aws elbv2 describe-tags \
    --resource-arns <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arns` | **Yes** | list | -- | ARNs of the resources (max 20) |

**Output Schema:**
```json
{
    "TagDescriptions": [
        {
            "ResourceArn": "string",
            "Tags": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ]
        }
    ]
}
```

---
