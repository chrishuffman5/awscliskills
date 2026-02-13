# Resource Policy

### 8.1 `put-resource-policy`

Creates or updates the resource-based delegation policy for the organization.

**Synopsis:**
```bash
aws organizations put-resource-policy \
    --content <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--content` | **Yes** | string | -- | JSON policy document (string or `file://` path) |
| `--tags` | No | list | None | Tags for the resource policy |

**Output Schema:**
```json
{
    "ResourcePolicy": {
        "ResourcePolicySummary": {
            "Id": "string",
            "Arn": "string"
        },
        "Content": "string"
    }
}
```

---

### 8.2 `delete-resource-policy`

Deletes the resource-based delegation policy from the organization.

**Synopsis:**
```bash
aws organizations delete-resource-policy \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| _(none)_ | -- | -- | -- | No parameters beyond global options |

**Output Schema:**
```json
{}
```

---

### 8.3 `describe-resource-policy`

Retrieves the resource-based delegation policy for the organization.

**Synopsis:**
```bash
aws organizations describe-resource-policy \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| _(none)_ | -- | -- | -- | No parameters beyond global options |

**Output Schema:**
```json
{
    "ResourcePolicy": {
        "ResourcePolicySummary": {
            "Id": "string",
            "Arn": "string"
        },
        "Content": "string"
    }
}
```
