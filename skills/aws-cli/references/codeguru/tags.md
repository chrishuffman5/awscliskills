# Tags

### 7.1 `tag-resource`

Adds tags to a CodeGuru resource. Available in both `aws codeguru-reviewer` and `aws codeguru-security`.

**Synopsis (codeguru-reviewer):**
```bash
aws codeguru-reviewer tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Synopsis (codeguru-security):**
```bash
aws codeguru-security tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Tags to add. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{}
```

---

### 7.2 `untag-resource`

Removes tags from a CodeGuru resource. Available in both `aws codeguru-reviewer` and `aws codeguru-security`.

**Synopsis (codeguru-reviewer):**
```bash
aws codeguru-reviewer untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Synopsis (codeguru-security):**
```bash
aws codeguru-security untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to remove tags from |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 7.3 `list-tags-for-resource`

Returns a list of tags associated with a CodeGuru resource. Available in both `aws codeguru-reviewer` and `aws codeguru-security`.

**Synopsis (codeguru-reviewer):**
```bash
aws codeguru-reviewer list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Synopsis (codeguru-security):**
```bash
aws codeguru-security list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to list tags for |

**Output Schema:**
```json
{
    "Tags": {
        "string": "string"
    }
}
```
