# Tags

### 10.1 `add-tags-to-resource`

Adds or overwrites tags on the specified resource. Tags are metadata key-value pairs.

**Synopsis:**
```bash
aws ssm add-tags-to-resource \
    --resource-type <value> \
    --resource-id <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | Resource type: `Document`, `ManagedInstance`, `MaintenanceWindow`, `Parameter`, `PatchBaseline`, `OpsItem`, `OpsMetadata`, `Automation`, `Association` |
| `--resource-id` | **Yes** | string | -- | Resource ID (name for documents, instance ID for managed instances, etc.) |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{}
```

---

### 10.2 `remove-tags-from-resource`

Removes tags from the specified resource.

**Synopsis:**
```bash
aws ssm remove-tags-from-resource \
    --resource-type <value> \
    --resource-id <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | Resource type (same values as add-tags-to-resource) |
| `--resource-id` | **Yes** | string | -- | Resource ID |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 10.3 `list-tags-for-resource`

Returns the tags for a specified resource.

**Synopsis:**
```bash
aws ssm list-tags-for-resource \
    --resource-type <value> \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | Resource type (same values as add-tags-to-resource) |
| `--resource-id` | **Yes** | string | -- | Resource ID |

**Output Schema:**
```json
{
    "TagList": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
