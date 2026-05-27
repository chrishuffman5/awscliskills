# Tags

CodePipeline supports the standard AWS resource tagging pattern for pipelines, webhooks, and custom action types.

---

### 6.1 `tag-resource`

Adds tags to a CodePipeline resource (pipeline, webhook, or custom action type).

**Synopsis:**
```bash
aws codepipeline tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `key=string,value=string ...` |

**Output Schema:**
```json
{}
```

---

### 6.2 `untag-resource`

Removes tags from a CodePipeline resource.

**Synopsis:**
```bash
aws codepipeline untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 6.3 `list-tags-for-resource`

Gets the set of tags for a specified resource.

**Synopsis:**
```bash
aws codepipeline list-tags-for-resource \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

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
