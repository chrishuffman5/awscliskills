# Tags (cloudwatch)

### 7.1 `tag-resource`

Adds tags to a CloudWatch resource (alarm, Contributor Insights rule, or metric stream).

**Synopsis:**
```bash
aws cloudwatch tag-resource \
    --resource-arn <value> \
    --tags <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (1-1024 chars) |
| `--tags` | **Yes** | list | -- | Key-value tags. Shorthand: `Key=string,Value=string` |

**Output:** None on success.

---

### 7.2 `untag-resource`

Removes tags from a CloudWatch resource.

**Synopsis:**
```bash
aws cloudwatch untag-resource \
    --resource-arn <value> \
    --tag-keys <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (1-1024 chars) |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None on success.

---

### 7.3 `list-tags-for-resource`

Lists tags for a CloudWatch resource.

**Synopsis:**
```bash
aws cloudwatch list-tags-for-resource \
    --resource-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (1-1024 chars) |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

# Part B — `aws logs`

---
