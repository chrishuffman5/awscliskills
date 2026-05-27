# Tags

### 10.1 `add-tags-to-resource`

Adds tags to an RDS resource (DB instance, cluster, snapshot, subnet group, etc.).

```bash
aws rds add-tags-to-resource \
    --resource-name <value> \
    --tags <value>
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--resource-name` | **Yes** | string | Resource ARN |
| `--tags` | **Yes** | list | `Key=string,Value=string ...` |

**Output:** None on success.

---

### 10.2 `remove-tags-from-resource`

Removes tags from an RDS resource.

```bash
aws rds remove-tags-from-resource \
    --resource-name <value> \
    --tag-keys <value>
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--resource-name` | **Yes** | string | Resource ARN |
| `--tag-keys` | **Yes** | list | Tag keys to remove |

**Output:** None on success.

---

### 10.3 `list-tags-for-resource`

Lists tags for an RDS resource.

```bash
aws rds list-tags-for-resource \
    --resource-name <value> \
    [--filters <value>]
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--resource-name` | **Yes** | string | Resource ARN |
| `--filters` | No | list | Filters |

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
