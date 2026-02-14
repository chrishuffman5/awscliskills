# Configuration & Tags

### 4.1 `get-configuration`

Retrieves the tag query configuration for the account.

**Synopsis:**
```bash
aws servicecatalog-appregistry get-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No command-specific parameters.

**Output Schema:**
```json
{
    "configuration": {
        "tagQueryConfiguration": {
            "tagKey": "string"
        }
    }
}
```

---

### 4.2 `put-configuration`

Associates a tag key configuration to the account. Sets the tag key used to associate resources with applications.

**Synopsis:**
```bash
aws servicecatalog-appregistry put-configuration \
    --configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration` | **Yes** | structure | -- | Configuration with tag query. Shorthand: `tagQueryConfiguration={tagKey=string}` |

**Configuration Structure:**
```json
{
    "tagQueryConfiguration": {
        "tagKey": "string"
    }
}
```

- `tagKey`: The tag key used to associate resources with applications (0-128 chars)

**Output:** None

---

### 4.3 `tag-resource`

Assigns tags to a Service Catalog AppRegistry resource.

**Synopsis:**
```bash
aws servicecatalog-appregistry tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag (1-1600 chars) |
| `--tags` | **Yes** | map | -- | Key-value pairs (max 50 tags). Shorthand: `Key1=Value1,Key2=Value2` |

**Output:** None

---

### 4.4 `untag-resource`

Removes tags from a Service Catalog AppRegistry resource.

**Synopsis:**
```bash
aws servicecatalog-appregistry untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (1-1600 chars) |
| `--tag-keys` | **Yes** | list | -- | List of tag keys to remove (max 50). Space-separated |

**Output:** None

---

### 4.5 `list-tags-for-resource`

Lists tags for a Service Catalog AppRegistry resource.

**Synopsis:**
```bash
aws servicecatalog-appregistry list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (1-1600 chars) |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```
