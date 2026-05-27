# Web Tags

> Commands use `aws workspaces-web` CLI prefix.

### 14.1 `tag-resource`

Adds or overwrites one or more tags for the specified WorkSpaces Web resource.

**Synopsis:**
```bash
aws workspaces-web tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{}
```

---

### 14.2 `untag-resource`

Removes one or more tags from the specified WorkSpaces Web resource.

**Synopsis:**
```bash
aws workspaces-web untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 14.3 `list-tags-for-resource`

Lists tags for the specified WorkSpaces Web resource.

**Synopsis:**
```bash
aws workspaces-web list-tags-for-resource \
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
    "tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
