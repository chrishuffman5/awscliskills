# Tags

### 14.1 `add-tags-to-resource`

Adds metadata tags to a DMS resource, including replication instances, endpoints, subnet groups, and tasks.

**Synopsis:**
```bash
aws dms add-tags-to-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the DMS resource to tag |
| `--tags` | **Yes** | list | -- | Tags: `key=string,value=string ...` |

**Output Schema:** None (HTTP 200 on success).

---

### 14.2 `remove-tags-from-resource`

Removes metadata tags from a DMS resource.

**Synopsis:**
```bash
aws dms remove-tags-from-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the DMS resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:** None (HTTP 200 on success).

---

### 14.3 `list-tags-for-resource`

Lists all metadata tags attached to a DMS resource.

**Synopsis:**
```bash
aws dms list-tags-for-resource \
    [--resource-arn <value>] \
    [--resource-arn-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | No | string | -- | ARN of a single resource |
| `--resource-arn-list` | No | list(string) | -- | ARNs of multiple resources |

**Output Schema:**
```json
{
    "TagList": [
        {
            "Key": "string",
            "Value": "string",
            "ResourceArn": "string"
        }
    ]
}
```
