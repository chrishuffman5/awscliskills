# Tags

### 3.1 `tag-resource`

Adds tags to an AWS Cloud9 development environment.

**Synopsis:**
```bash
aws cloud9 tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource (environment ARN) |
| `--tags` | **Yes** | list | -- | Tags to add (max 200). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{}
```

---

### 3.2 `untag-resource`

Removes tags from an AWS Cloud9 development environment.

**Synopsis:**
```bash
aws cloud9 untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove (max 200) |

**Output Schema:**
```json
{}
```

---

### 3.3 `list-tags-for-resource`

Gets a list of the tags associated with an AWS Cloud9 development environment.

**Synopsis:**
```bash
aws cloud9 list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource |

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
