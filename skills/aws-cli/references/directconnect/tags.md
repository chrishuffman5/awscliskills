# Tags

### 8.1 `tag-resource`

Adds the specified tags to the specified Direct Connect resource. Each resource can have a maximum of 50 tags.

**Synopsis:**
```bash
aws directconnect tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the Direct Connect resource |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `key=string,value=string ...` (key: 1-128 chars, value: 0-256 chars) |

**Output Schema:**

No output on success.

---

### 8.2 `untag-resource`

Removes one or more tags from the specified Direct Connect resource.

**Synopsis:**
```bash
aws directconnect untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the Direct Connect resource |
| `--tag-keys` | **Yes** | list(string) | -- | The tag keys to remove |

**Output Schema:**

No output on success.

---

### 8.3 `describe-tags`

Describes the tags associated with the specified Direct Connect resources.

**Synopsis:**
```bash
aws directconnect describe-tags \
    --resource-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arns` | **Yes** | list(string) | -- | The ARNs of the resources to describe tags for |

**Output Schema:**
```json
{
    "resourceTags": [
        {
            "resourceArn": "string",
            "tags": [
                {
                    "key": "string",
                    "value": "string"
                }
            ]
        }
    ]
}
```
