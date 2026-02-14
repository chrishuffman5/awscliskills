# Tags

### 4.1 `tag-resource`

Adds tags to an Application Auto Scaling scalable target.

**Synopsis:**
```bash
aws application-autoscaling tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Scalable target ARN |
| `--tags` | **Yes** | map | -- | Key-value tag pairs |

**Tags example:**
```bash
aws application-autoscaling tag-resource \
    --resource-arn arn:aws:application-autoscaling:us-east-1:123456789012:scalable-target/1234abcd \
    --tags environment=production,team=backend
```

**Output:** None

---

### 4.2 `untag-resource`

Removes tags from an Application Auto Scaling scalable target.

**Synopsis:**
```bash
aws application-autoscaling untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Scalable target ARN |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove |

**Output:** None

---

### 4.3 `list-tags-for-resource`

Lists tags for an Application Auto Scaling scalable target.

**Synopsis:**
```bash
aws application-autoscaling list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Scalable target ARN |

**Output Schema:**
```json
{
    "Tags": {
        "string": "string"
    }
}
```
