# Views

### 2.1 `create-view`

Creates a view that defines which resources are visible in search results. Views can include filters and additional properties.

**Synopsis:**
```bash
aws resource-explorer-2 create-view \
    --view-name <value> \
    [--client-token <value>] \
    [--included-properties <value>] \
    [--scope <value>] \
    [--filters <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--view-name` | **Yes** | string | -- | View name (1-64 chars, alphanumeric + dash) |
| `--client-token` | No | string | None | Idempotency token (1-2048 chars) |
| `--included-properties` | No | list | None | Properties to include (currently only `tags`). Shorthand: `Name=tags` |
| `--scope` | No | string | None | Root ARN of account, OU, or organization |
| `--filters` | No | structure | None | Filter criteria. Shorthand: `FilterString="service:ec2"` |
| `--tags` | No | map | None | Tags for the view |

**Output Schema:**
```json
{
    "View": {
        "ViewArn": "string",
        "ViewName": "string",
        "Owner": "string",
        "LastUpdatedAt": "timestamp",
        "Scope": "string",
        "IncludedProperties": [{ "Name": "string" }],
        "Filters": { "FilterString": "string" }
    }
}
```

---

### 2.2 `delete-view`

Deletes a view.

**Synopsis:**
```bash
aws resource-explorer-2 delete-view \
    --view-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--view-arn` | **Yes** | string | -- | ARN of the view to delete (1-1011 chars) |

**Output Schema:**
```json
{
    "ViewArn": "string"
}
```

---

### 2.3 `get-view`

Retrieves details of a specific view.

**Synopsis:**
```bash
aws resource-explorer-2 get-view \
    --view-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--view-arn` | **Yes** | string | -- | ARN of the view (1-1011 chars) |

**Output Schema:**
```json
{
    "View": {
        "ViewArn": "string",
        "ViewName": "string",
        "Owner": "string",
        "LastUpdatedAt": "timestamp",
        "Scope": "string",
        "IncludedProperties": [{ "Name": "string" }],
        "Filters": { "FilterString": "string" }
    },
    "Tags": { "string": "string" }
}
```

---

### 2.4 `list-views`

Lists view ARNs in the current Region. **Paginated.**

**Synopsis:**
```bash
aws resource-explorer-2 list-views \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:** Pagination only.

**Output Schema:**
```json
{
    "Views": ["string"],
    "NextToken": "string"
}
```

---

### 2.5 `update-view`

Updates the filters or included properties of an existing view.

**Synopsis:**
```bash
aws resource-explorer-2 update-view \
    --view-arn <value> \
    [--included-properties <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--view-arn` | **Yes** | string | -- | ARN of the view to update (1-1011 chars) |
| `--included-properties` | No | list | None | Properties to include. Shorthand: `Name=tags` |
| `--filters` | No | structure | None | Updated filter. Shorthand: `FilterString="service:ec2"` |

**Output Schema:**
```json
{
    "View": {
        "ViewArn": "string",
        "ViewName": "string",
        "Owner": "string",
        "LastUpdatedAt": "timestamp",
        "Scope": "string",
        "IncludedProperties": [{ "Name": "string" }],
        "Filters": { "FilterString": "string" }
    }
}
```

---

### 2.6 `batch-get-view`

Retrieves details for multiple views at once.

**Synopsis:**
```bash
aws resource-explorer-2 batch-get-view \
    [--view-arns <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--view-arns` | No | list(string) | None | View ARNs to retrieve (1-20) |

**Output Schema:**
```json
{
    "Views": [
        {
            "ViewArn": "string",
            "ViewName": "string",
            "Owner": "string",
            "LastUpdatedAt": "timestamp",
            "Scope": "string",
            "IncludedProperties": [{ "Name": "string" }],
            "Filters": { "FilterString": "string" }
        }
    ],
    "Errors": [
        {
            "ViewArn": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 2.7 `get-managed-view`

Retrieves details of an AWS-managed view.

**Synopsis:**
```bash
aws resource-explorer-2 get-managed-view \
    --managed-view-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--managed-view-arn` | **Yes** | string | -- | ARN of the managed view (1-1011 chars) |

**Output Schema:**
```json
{
    "ManagedView": {
        "ManagedViewArn": "string",
        "ManagedViewName": "string",
        "TrustedService": "string",
        "LastUpdatedAt": "timestamp",
        "Owner": "string",
        "Scope": "string",
        "IncludedProperties": [{ "Name": "string" }],
        "Filters": { "FilterString": "string" },
        "ResourcePolicy": "string",
        "Version": "string"
    }
}
```

---

### 2.8 `list-managed-views`

Lists AWS-managed view ARNs. **Paginated.**

**Synopsis:**
```bash
aws resource-explorer-2 list-managed-views \
    [--service-principal <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-principal` | No | string | None | Filter by managing service principal (1-1024 chars) |

**Output Schema:**
```json
{
    "ManagedViews": ["string"],
    "NextToken": "string"
}
```

---

### 2.9 `get-service-view`

Retrieves details of a service-managed view.

**Synopsis:**
```bash
aws resource-explorer-2 get-service-view \
    --service-view-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-view-arn` | **Yes** | string | -- | ARN of the service view (1-1011 chars) |

**Output Schema:**
```json
{
    "View": {
        "ServiceViewArn": "string",
        "ServiceViewName": "string",
        "Filters": { "FilterString": "string" },
        "IncludedProperties": [{ "Name": "string" }],
        "StreamingAccessForService": "string",
        "ScopeType": "string"
    }
}
```

---

### 2.10 `list-service-views`

Lists service-managed view ARNs. **Paginated.**

**Synopsis:**
```bash
aws resource-explorer-2 list-service-views \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:** Pagination only.

**Output Schema:**
```json
{
    "ServiceViews": ["string"],
    "NextToken": "string"
}
```

---

### 2.11 `associate-default-view`

Sets a view as the default for the current Region. Search operations that do not specify a view use this default.

**Synopsis:**
```bash
aws resource-explorer-2 associate-default-view \
    --view-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--view-arn` | **Yes** | string | -- | ARN of the view to set as default (1-1011 chars) |

**Output Schema:**
```json
{
    "ViewArn": "string"
}
```

---

### 2.12 `disassociate-default-view`

Removes the default view for the current Region. After this, search operations must explicitly specify a view.

**Synopsis:**
```bash
aws resource-explorer-2 disassociate-default-view \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None.

**Output Schema:**

None (empty response on success).

---

### 2.13 `get-default-view`

Retrieves the ARN of the default view for the current Region.

**Synopsis:**
```bash
aws resource-explorer-2 get-default-view \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None.

**Output Schema:**
```json
{
    "ViewArn": "string"
}
```
