# Tags

## 18.1 `tag-resource`

Adds tags to an IoT resource.

**Synopsis:**
```bash
aws iot tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | list | -- | Tags: `[{Key: "string", Value: "string"}]` |

**Output:** None

---

## 18.2 `untag-resource`

Removes tags from an IoT resource.

**Synopsis:**
```bash
aws iot untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None

---

## 18.3 `list-tags-for-resource`

Lists tags for an IoT resource.

**Synopsis:**
```bash
aws iot list-tags-for-resource \
    --resource-arn <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "nextToken": "string"
}
```
