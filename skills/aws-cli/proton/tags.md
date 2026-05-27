# Tags

### 9.1 `tag-resource`

Adds tags to a Proton resource.

**Synopsis:**
```bash
aws proton tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Proton resource |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `key=string,value=string ...` |

**Output Schema:**
```json
{}
```

---

### 9.2 `untag-resource`

Removes tags from a Proton resource.

**Synopsis:**
```bash
aws proton untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Proton resource |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 9.3 `list-tags-for-resource`

Lists tags for a Proton resource.

**Synopsis:**
```bash
aws proton list-tags-for-resource \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Proton resource |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "tags": [
        {
            "key": "string",
            "value": "string"
        }
    ],
    "nextToken": "string"
}
```
