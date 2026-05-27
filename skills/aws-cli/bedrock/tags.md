# Tags

Tags are shared across all four Bedrock services. Each service has its own `tag-resource`, `untag-resource`, and `list-tags-for-resource` commands.

---

## `aws bedrock` Tag Commands

### `tag-resource`

Adds tags to an Amazon Bedrock resource.

**Synopsis:**
```bash
aws bedrock tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags to add (max 200). Shorthand: `key=string,value=string` |

**Output:** None (HTTP 200 on success)

---

### `untag-resource`

Removes tags from an Amazon Bedrock resource.

**Synopsis:**
```bash
aws bedrock untag-resource \
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

**Output:** None (HTTP 200 on success)

---

### `list-tags-for-resource`

Lists tags for an Amazon Bedrock resource.

**Synopsis:**
```bash
aws bedrock list-tags-for-resource \
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
    "tags": [
        {
            "key": "string",
            "value": "string"
        }
    ]
}
```

---

## `aws bedrock-agent` Tag Commands

### `tag-resource`

```bash
aws bedrock-agent tag-resource \
    --resource-arn <value> \
    --tags <value>
```

Same parameters and behavior as `aws bedrock tag-resource`.

### `untag-resource`

```bash
aws bedrock-agent untag-resource \
    --resource-arn <value> \
    --tag-keys <value>
```

### `list-tags-for-resource`

```bash
aws bedrock-agent list-tags-for-resource \
    --resource-arn <value>
```

---

## `aws bedrock-agent-runtime` Tag Commands

### `tag-resource`

```bash
aws bedrock-agent-runtime tag-resource \
    --resource-arn <value> \
    --tags <value>
```

### `untag-resource`

```bash
aws bedrock-agent-runtime untag-resource \
    --resource-arn <value> \
    --tag-keys <value>
```

### `list-tags-for-resource`

```bash
aws bedrock-agent-runtime list-tags-for-resource \
    --resource-arn <value>
```

---

## Tag Constraints

| Constraint | Value |
|-----------|-------|
| Maximum tags per resource | 200 |
| Tag key length | 1-128 characters |
| Tag value length | 0-256 characters |
| Tag key pattern | `[a-zA-Z0-9\s._:/=+@-]*` |
| Tag value pattern | `[a-zA-Z0-9\s._:/=+@-]*` |
| Case sensitive | Yes |
