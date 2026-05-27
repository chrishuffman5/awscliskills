# Associations

### 3.1 `associate-attribute-group`

Associates an attribute group with an application to add the attribute group's metadata to the application.

**Synopsis:**
```bash
aws servicecatalog-appregistry associate-attribute-group \
    --application <value> \
    --attribute-group <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application` | **Yes** | string | -- | The name, ID, or ARN of the application (1-256 chars) |
| `--attribute-group` | **Yes** | string | -- | The name, ID, or ARN of the attribute group (1-512 chars) |

**Output Schema:**
```json
{
    "applicationArn": "string",
    "attributeGroupArn": "string"
}
```

---

### 3.2 `disassociate-attribute-group`

Disassociates an attribute group from an application, removing the extra attributes from the application's metadata.

**Synopsis:**
```bash
aws servicecatalog-appregistry disassociate-attribute-group \
    --application <value> \
    --attribute-group <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application` | **Yes** | string | -- | The name, ID, or ARN of the application (1-256 chars) |
| `--attribute-group` | **Yes** | string | -- | The name, ID, or ARN of the attribute group (1-512 chars) |

**Output Schema:**
```json
{
    "applicationArn": "string",
    "attributeGroupArn": "string"
}
```

---

### 3.3 `associate-resource`

Associates a resource (e.g., CloudFormation stack) with an application.

**Synopsis:**
```bash
aws servicecatalog-appregistry associate-resource \
    --application <value> \
    --resource-type <value> \
    --resource <value> \
    [--options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application` | **Yes** | string | -- | The name, ID, or ARN of the application (1-256 chars) |
| `--resource-type` | **Yes** | string | -- | Resource type: `CFN_STACK` or `RESOURCE_TAG_VALUE` |
| `--resource` | **Yes** | string | -- | The name or ID of the resource (1-256 chars) |
| `--options` | No | list | None | Tag options: `APPLY_APPLICATION_TAG`, `SKIP_APPLICATION_TAG` |

**Output Schema:**
```json
{
    "applicationArn": "string",
    "resourceArn": "string",
    "options": ["APPLY_APPLICATION_TAG|SKIP_APPLICATION_TAG"]
}
```

---

### 3.4 `disassociate-resource`

Disassociates a resource from an application.

**Synopsis:**
```bash
aws servicecatalog-appregistry disassociate-resource \
    --application <value> \
    --resource-type <value> \
    --resource <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application` | **Yes** | string | -- | The name, ID, or ARN of the application (1-256 chars) |
| `--resource-type` | **Yes** | string | -- | Resource type: `CFN_STACK` or `RESOURCE_TAG_VALUE` |
| `--resource` | **Yes** | string | -- | The name or ID of the resource (1-256 chars) |

**Output Schema:**
```json
{
    "applicationArn": "string",
    "resourceArn": "string"
}
```

---

### 3.5 `get-associated-resource`

Gets detailed information about a resource associated with an application.

**Synopsis:**
```bash
aws servicecatalog-appregistry get-associated-resource \
    --application <value> \
    --resource-type <value> \
    --resource <value> \
    [--next-token <value>] \
    [--resource-tag-status <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application` | **Yes** | string | -- | The name, ID, or ARN of the application (1-256 chars) |
| `--resource-type` | **Yes** | string | -- | Resource type: `CFN_STACK` or `RESOURCE_TAG_VALUE` |
| `--resource` | **Yes** | string | -- | The name or ID of the resource (1-256 chars) |
| `--next-token` | No | string | None | Pagination token (1-2024 chars) |
| `--resource-tag-status` | No | list | None | Filter by tag status: `SUCCESS`, `FAILED`, `IN_PROGRESS`, `SKIPPED` |
| `--max-results` | No | integer | 25 | Max results per page (1-100) |

**Output Schema:**
```json
{
    "resource": {
        "name": "string",
        "arn": "string",
        "associationTime": "timestamp",
        "integrations": {
            "resourceGroup": {
                "state": "CREATING|CREATE_COMPLETE|CREATE_FAILED|UPDATING|UPDATE_COMPLETE|UPDATE_FAILED",
                "arn": "string",
                "errorMessage": "string"
            }
        },
        "options": ["APPLY_APPLICATION_TAG|SKIP_APPLICATION_TAG"],
        "applicationTagResult": {
            "applicationTagStatus": "IN_PROGRESS|SUCCESS|FAILURE",
            "errorMessage": "string",
            "resources": [
                {
                    "resourceArn": "string",
                    "errorMessage": "string",
                    "status": "string",
                    "resourceType": "string"
                }
            ],
            "nextToken": "string"
        }
    }
}
```

---

### 3.6 `list-associated-attribute-groups`

Lists the attribute group IDs associated with an application. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog-appregistry list-associated-attribute-groups \
    --application <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application` | **Yes** | string | -- | The name, ID, or ARN of the application (1-256 chars) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Number of items per page |
| `--max-items` | No | integer | None | Total number of items to return |

**Output Schema:**
```json
{
    "attributeGroups": ["string"],
    "nextToken": "string"
}
```

---

### 3.7 `list-associated-resources`

Lists resources associated with an application. **Paginated operation.**

**Synopsis:**
```bash
aws servicecatalog-appregistry list-associated-resources \
    --application <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application` | **Yes** | string | -- | The name, ID, or ARN of the application (1-256 chars) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Number of items per page |
| `--max-items` | No | integer | None | Total number of items to return |

**Output Schema:**
```json
{
    "resources": [
        {
            "name": "string",
            "arn": "string",
            "resourceType": "CFN_STACK|RESOURCE_TAG_VALUE",
            "resourceDetails": {
                "tagValue": "string"
            },
            "options": ["APPLY_APPLICATION_TAG|SKIP_APPLICATION_TAG"]
        }
    ],
    "nextToken": "string"
}
```

---

### 3.8 `sync-resource`

Syncs a resource with its application. If the resource was associated with the application via a CloudFormation stack, this re-syncs the resource metadata.

**Synopsis:**
```bash
aws servicecatalog-appregistry sync-resource \
    --resource-type <value> \
    --resource <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | Resource type: `CFN_STACK` or `RESOURCE_TAG_VALUE` |
| `--resource` | **Yes** | string | -- | The name or ID of the resource (1-256 chars) |

**Output Schema:**
```json
{
    "applicationArn": "string",
    "resourceArn": "string",
    "actionTaken": "START_SYNC|NO_ACTION"
}
```
