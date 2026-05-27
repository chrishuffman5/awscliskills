# Predefined Attributes

### 16.1 `create-predefined-attribute`

Creates a predefined attribute for the specified instance.

**Synopsis:**
```bash
aws connect create-predefined-attribute \
    --instance-id <value> \
    --name <value> \
    [--values <value>] \
    [--purposes <value>] \
    [--attribute-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Attribute name (1-100 chars) |
| `--values` | No | tagged union | None | `StringList`: list of values (max 500, each 1-100 chars) |
| `--purposes` | No | list | None | Categorization purposes (max 10) |
| `--attribute-configuration` | No | structure | None | `EnableValueValidationOnAssociation`: boolean |

**Output:** None

---

### 16.2 `describe-predefined-attribute`

Describes a predefined attribute.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Attribute name |

**Output Schema:**
```json
{
    "PredefinedAttribute": {
        "Name": "string",
        "Values": { "StringList": ["string"] },
        "LastModifiedTime": "timestamp",
        "LastModifiedRegion": "string"
    }
}
```

---

### 16.3 `list-predefined-attributes`

Lists predefined attributes. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

**Output Schema:**
```json
{
    "PredefinedAttributeSummaryList": [ { "Name": "string", "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" } ],
    "NextToken": "string"
}
```

---

### 16.4 `update-predefined-attribute`

Updates a predefined attribute.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Attribute name |
| `--values` | No | tagged union | None | Updated values |

**Output:** None

---

### 16.5 `delete-predefined-attribute`

Deletes a predefined attribute.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Attribute name |

**Output:** None

---

### 16.6 `search-predefined-attributes`

Searches predefined attributes. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-criteria` | No | structure | None | Search criteria |

**Output Schema:**
```json
{
    "PredefinedAttributes": [ { "Name": "string", "Values": { "StringList": [] }, "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" } ],
    "NextToken": "string",
    "ApproximateTotalCount": "long"
}
```
