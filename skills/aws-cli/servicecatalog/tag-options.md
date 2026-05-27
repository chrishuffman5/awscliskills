# Tag Options

### 9.1 `create-tag-option`

Creates a TagOption.

**Synopsis:**
```bash
aws servicecatalog create-tag-option \
    --key <value> \
    --value <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key` | **Yes** | string | -- | TagOption key (1-128 chars) |
| `--value` | **Yes** | string | -- | TagOption value (1-256 chars) |

**Output Schema:**
```json
{
    "TagOptionDetail": {
        "Key": "string",
        "Value": "string",
        "Active": "boolean",
        "Id": "string",
        "Owner": "string"
    }
}
```

---

### 9.2 `delete-tag-option`

Deletes the specified TagOption. Cannot delete a TagOption that is associated with a resource.

**Synopsis:**
```bash
aws servicecatalog delete-tag-option \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | TagOption identifier |

**Output Schema:**
```json
{}
```

---

### 9.3 `describe-tag-option`

Gets information about the specified TagOption.

**Synopsis:**
```bash
aws servicecatalog describe-tag-option \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | TagOption identifier |

**Output Schema:**
```json
{
    "TagOptionDetail": {
        "Key": "string",
        "Value": "string",
        "Active": "boolean",
        "Id": "string",
        "Owner": "string"
    }
}
```

---

### 9.4 `update-tag-option`

Updates the specified TagOption.

**Synopsis:**
```bash
aws servicecatalog update-tag-option \
    --id <value> \
    [--value <value>] \
    [--active | --no-active] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | TagOption identifier |
| `--value` | No | string | None | Updated value |
| `--active` | No | boolean | None | Whether the TagOption is active |

**Output Schema:**
```json
{
    "TagOptionDetail": {
        "Key": "string",
        "Value": "string",
        "Active": "boolean",
        "Id": "string",
        "Owner": "string"
    }
}
```

---

### 9.5 `list-tag-options`

Lists the specified TagOptions or all TagOptions. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-tag-options \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | structure | None | Filters. Shorthand: `Key=string,Value=string,Active=boolean` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "TagOptionDetails": [
        {
            "Key": "string",
            "Value": "string",
            "Active": "boolean",
            "Id": "string",
            "Owner": "string"
        }
    ],
    "PageToken": "string"
}
```

---

### 9.6 `associate-tag-option-with-resource`

Associates the specified TagOption with the specified resource.

**Synopsis:**
```bash
aws servicecatalog associate-tag-option-with-resource \
    --resource-id <value> \
    --tag-option-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Resource identifier (portfolio or product ID) |
| `--tag-option-id` | **Yes** | string | -- | TagOption identifier |

**Output Schema:**
```json
{}
```

---

### 9.7 `disassociate-tag-option-from-resource`

Disassociates the specified TagOption from the specified resource.

**Synopsis:**
```bash
aws servicecatalog disassociate-tag-option-from-resource \
    --resource-id <value> \
    --tag-option-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Resource identifier |
| `--tag-option-id` | **Yes** | string | -- | TagOption identifier |

**Output Schema:**
```json
{}
```

---

### 9.8 `list-resources-for-tag-option`

Lists the resources associated with the specified TagOption. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog list-resources-for-tag-option \
    --tag-option-id <value> \
    [--resource-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tag-option-id` | **Yes** | string | -- | TagOption identifier |
| `--resource-type` | No | string | None | Filter by resource type: `Portfolio`, `Product` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "ResourceDetails": [
        {
            "Id": "string",
            "ARN": "string",
            "Name": "string",
            "Description": "string",
            "CreatedTime": "timestamp"
        }
    ],
    "PageToken": "string"
}
```
