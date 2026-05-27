# Tags

Tags are available in both `aws timestream-write` and `aws timestream-query` namespaces. Use the write namespace for database/table resources and the query namespace for scheduled query resources.

### 5.1 `tag-resource`

Adds tags to a Timestream resource.

**Synopsis:**
```bash
aws timestream-write tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]

aws timestream-query tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags to add (max 200). Shorthand: `Key=string,Value=string ...` |

**Tag Structure:**
```json
[
    {
        "Key": "string",
        "Value": "string"
    }
]
```
- Key: 1-128 chars, case-sensitive
- Value: 0-256 chars, case-sensitive

**Output:** None

---

### 5.2 `untag-resource`

Removes tags from a Timestream resource.

**Synopsis:**
```bash
aws timestream-write untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]

aws timestream-query untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 5.3 `list-tags-for-resource`

Lists all tags for a Timestream resource.

**Synopsis:**
```bash
aws timestream-write list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]

aws timestream-query list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

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
