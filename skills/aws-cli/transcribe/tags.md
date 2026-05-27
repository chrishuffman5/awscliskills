# Tags

### 6.1 `tag-resource`

Adds tags to a Transcribe resource.

**Synopsis:**
```bash
aws transcribe tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string ...` (1-200 tags) |

**Valid Resource Types:**
- `transcription-job`
- `medical-transcription-job`
- `vocabulary`
- `medical-vocabulary`
- `vocabulary-filter`
- `language-model`

**ARN Format:** `arn:aws:transcribe:<region>:<account-id>:<resource-type>/<resource-name>`

**Output:** None (HTTP 200 on success)

---

### 6.2 `untag-resource`

Removes tags from a Transcribe resource.

**Synopsis:**
```bash
aws transcribe untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove (1-200 keys, each 1-128 chars) |

**Output:** None (HTTP 200 on success)

---

### 6.3 `list-tags-for-resource`

Lists all tags for a Transcribe resource.

**Synopsis:**
```bash
aws transcribe list-tags-for-resource \
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
    "ResourceArn": "string",
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
