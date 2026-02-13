# Tags

### 10.1 `tag-resource`

Associates the specified tags with an ECS resource (cluster, service, task, task definition, container instance, or capacity provider).

**Synopsis:**
```bash
aws ecs tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Full ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags to add (max 50 per resource). Shorthand: `key=string,value=string ...` |

**Output:** None on success.

---

### 10.2 `untag-resource`

Deletes specified tags from an ECS resource.

**Synopsis:**
```bash
aws ecs untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Full ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None on success.

---

### 10.3 `list-tags-for-resource`

Lists the tags for the specified ECS resource.

**Synopsis:**
```bash
aws ecs list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Full ARN of the resource |

**Output Schema:**
```json
{
    "tags": [
        {
            "key": "string",
            "value": "string"
        }
    ]
}
```
