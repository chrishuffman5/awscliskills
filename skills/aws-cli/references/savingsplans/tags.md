# Tags

### 3.1 `tag-resource`

Adds tags to a Savings Plans resource.

**Synopsis:**
```bash
aws savingsplans tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Savings Plan resource |
| `--tags` | **Yes** | map | -- | Key-value tags. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{}
```

---

### 3.2 `untag-resource`

Removes tags from a Savings Plans resource.

**Synopsis:**
```bash
aws savingsplans untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Savings Plan resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 3.3 `list-tags-for-resource`

Lists tags associated with a Savings Plans resource.

**Synopsis:**
```bash
aws savingsplans list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Savings Plan resource |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```
