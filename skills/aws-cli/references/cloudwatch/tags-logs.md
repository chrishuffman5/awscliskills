# Tags (logs)

### 20.1 `tag-resource`

Adds tags to a CloudWatch Logs resource (log group, destination, query definition, anomaly detector).

**Synopsis:**
```bash
aws logs tag-resource \
    --resource-arn <value> \
    --tags <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | map | -- | Key-value tags |

**Output:** None on success.

---

### 20.2 `untag-resource`

Removes tags from a CloudWatch Logs resource.

**Synopsis:**
```bash
aws logs untag-resource \
    --resource-arn <value> \
    --tag-keys <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None on success.

---

### 20.3 `list-tags-for-resource`

Lists tags for a CloudWatch Logs resource.

**Synopsis:**
```bash
aws logs list-tags-for-resource \
    --resource-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```

---
