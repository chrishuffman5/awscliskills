# Tags

### 10.1 `add-tags-to-resource`

Adds tags to an ElastiCache resource (cluster, replication group, parameter group, subnet group, snapshot, user, user group, or serverless cache).

**Synopsis:**
```bash
aws elasticache add-tags-to-resource \
    --resource-name <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags to add (max 50). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "TagList": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 10.2 `remove-tags-from-resource`

Removes tags from an ElastiCache resource.

**Synopsis:**
```bash
aws elasticache remove-tags-from-resource \
    --resource-name <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{
    "TagList": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 10.3 `list-tags-for-resource`

Lists all tags currently associated with an ElastiCache resource.

**Synopsis:**
```bash
aws elasticache list-tags-for-resource \
    --resource-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "TagList": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
