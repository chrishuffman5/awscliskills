# Tags

### 11.1 `tag-resource`

Adds tags to a Well-Architected resource.

**Synopsis:**
```bash
aws wellarchitected tag-resource \
    --workload-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | map | -- | Tags to add. Shorthand: `KeyName1=string,KeyName2=string` (1-50 tags) |

**Output Schema:**
```json
None
```

---

### 11.2 `untag-resource`

Removes tags from a Well-Architected resource.

**Synopsis:**
```bash
aws wellarchitected untag-resource \
    --workload-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove (1-50) |

**Output Schema:**
```json
None
```

---

### 11.3 `list-tags-for-resource`

Lists tags for a Well-Architected resource.

**Synopsis:**
```bash
aws wellarchitected list-tags-for-resource \
    --workload-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "Tags": {
        "string": "string"
    }
}
```
