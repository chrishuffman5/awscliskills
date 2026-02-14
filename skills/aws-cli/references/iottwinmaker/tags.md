# Tags

### 10.1 `tag-resource`

Adds tags to an IoT TwinMaker resource.

**Synopsis:**
```bash
aws iottwinmaker tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | map | -- | Key-value tag pairs (max 50) |

**Output:** None

---

### 10.2 `untag-resource`

Removes tags from an IoT TwinMaker resource.

**Synopsis:**
```bash
aws iottwinmaker untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove |

**Output:** None

---

### 10.3 `list-tags-for-resource`

Lists tags for an IoT TwinMaker resource.

**Synopsis:**
```bash
aws iottwinmaker list-tags-for-resource \
    --resource-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    },
    "nextToken": "string"
}
```
