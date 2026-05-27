# Tags

Tags commands are available on both `aws ssm-incidents` and `aws ssm-contacts` services. Use the appropriate service prefix based on the resource being tagged.

---

### 12.1 `tag-resource` (ssm-incidents)

Adds a tag to a response plan or incident record.

**Synopsis:**
```bash
aws ssm-incidents tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | map | -- | Tags to add. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{}
```

---

### 12.2 `untag-resource` (ssm-incidents)

Removes a tag from a resource.

**Synopsis:**
```bash
aws ssm-incidents untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 12.3 `list-tags-for-resource` (ssm-incidents)

Lists the tags that are attached to the specified response plan or incident.

**Synopsis:**
```bash
aws ssm-incidents list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```

---

### 12.4 `tag-resource` (ssm-contacts)

Tags a contact or escalation plan.

**Synopsis:**
```bash
aws ssm-contacts tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Contact or escalation plan ARN |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{}
```

---

### 12.5 `untag-resource` (ssm-contacts)

Removes tags from a contact or escalation plan.

**Synopsis:**
```bash
aws ssm-contacts untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Contact or escalation plan ARN |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 12.6 `list-tags-for-resource` (ssm-contacts)

Lists the tags of a contact or escalation plan.

**Synopsis:**
```bash
aws ssm-contacts list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Contact or escalation plan ARN |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
