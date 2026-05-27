# Organization & Tags

### 4.1 `tag-resource`

Adds tags to an Amazon Security Lake resource.

**Synopsis:**
```bash
aws securitylake tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Security Lake resource to tag |
| `--tags` | **Yes** | list(structure) | -- | Tags to add (max 50). Structure: `key=string,value=string` |

**Tag Structure:**
```json
{
    "key": "string",
    "value": "string"
}
```

**Output Schema:**

No output on success (HTTP 200).

---

### 4.2 `untag-resource`

Removes tags from an Amazon Security Lake resource.

**Synopsis:**
```bash
aws securitylake untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Security Lake resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**

No output on success (HTTP 200).

---

### 4.3 `list-tags-for-resource`

Lists the tags associated with an Amazon Security Lake resource.

**Synopsis:**
```bash
aws securitylake list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Security Lake resource |

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
