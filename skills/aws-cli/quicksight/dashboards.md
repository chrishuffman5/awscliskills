# Dashboards

### 2.1 `create-dashboard`

Creates a dashboard from a template or definition.

**Synopsis:**
```bash
aws quicksight create-dashboard \
    --aws-account-id <value> \
    --dashboard-id <value> \
    --name <value> \
    [--source-entity <value>] \
    [--definition <value>] \
    [--parameters <value>] \
    [--permissions <value>] \
    [--tags <value>] \
    [--theme-arn <value>] \
    [--dashboard-publish-options <value>] \
    [--version-description <value>] \
    [--validation-strategy <value>] \
    [--folder-arns <value>] \
    [--link-sharing-configuration <value>] \
    [--link-entities <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID (1-512 chars, pattern: `[\w\-]+`) |
| `--name` | **Yes** | string | -- | Display name (1-2048 chars) |
| `--source-entity` | No* | structure | None | Source template with data set references |
| `--definition` | No* | structure | None | Full dashboard definition (JSON) |
| `--parameters` | No | structure | None | Default parameter values |
| `--permissions` | No | list | None | Resource permissions |
| `--tags` | No | list | None | Resource tags |
| `--theme-arn` | No | string | None | Theme ARN to apply |
| `--dashboard-publish-options` | No | structure | None | Publish options |
| `--version-description` | No | string | None | Version description (1-512 chars) |
| `--validation-strategy` | No | structure | None | `{"Mode":"STRICT|LENIENT"}` |
| `--folder-arns` | No | list(string) | None | Folders to add the dashboard to |

*Either `--source-entity` or `--definition` is required (not both).

**Source Entity Structure:**
```json
{
    "SourceTemplate": {
        "DataSetReferences": [
            {
                "DataSetPlaceholder": "string",
                "DataSetArn": "string"
            }
        ],
        "Arn": "string"
    }
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "VersionArn": "string",
    "DashboardId": "string",
    "CreationStatus": "CREATION_IN_PROGRESS|CREATION_SUCCESSFUL|CREATION_FAILED|UPDATE_IN_PROGRESS|UPDATE_SUCCESSFUL|UPDATE_FAILED|DELETED",
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 2.2 `describe-dashboard`

Describes a dashboard.

**Synopsis:**
```bash
aws quicksight describe-dashboard \
    --aws-account-id <value> \
    --dashboard-id <value> \
    [--version-number <value>] \
    [--alias-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID |
| `--version-number` | No | long | latest | Version number |
| `--alias-name` | No | string | None | Alias name |

**Output Schema:**
```json
{
    "Dashboard": {
        "DashboardId": "string",
        "Arn": "string",
        "Name": "string",
        "Version": {
            "CreatedTime": "timestamp",
            "Errors": [],
            "VersionNumber": "long",
            "Status": "string",
            "Arn": "string",
            "SourceEntityArn": "string",
            "DataSetArns": ["string"],
            "Description": "string",
            "ThemeArn": "string",
            "Sheets": [
                {
                    "SheetId": "string",
                    "Name": "string"
                }
            ]
        },
        "CreatedTime": "timestamp",
        "LastPublishedTime": "timestamp",
        "LastUpdatedTime": "timestamp",
        "LinkEntities": ["string"]
    },
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 2.3 `describe-dashboard-definition`

Returns the full definition of a dashboard (visual layout, parameters, filters, etc.). Use `--cli-input-json file://` for complex definitions.

**Synopsis:**
```bash
aws quicksight describe-dashboard-definition \
    --aws-account-id <value> \
    --dashboard-id <value> \
    [--version-number <value>] \
    [--alias-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `describe-dashboard`.

**Output Schema:**
```json
{
    "DashboardId": "string",
    "Name": "string",
    "ResourceStatus": "string",
    "Definition": {},
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 2.4 `update-dashboard`

Updates a dashboard. Creates a new version.

**Synopsis:**
```bash
aws quicksight update-dashboard \
    --aws-account-id <value> \
    --dashboard-id <value> \
    --name <value> \
    [--source-entity <value>] \
    [--definition <value>] \
    [--parameters <value>] \
    [--theme-arn <value>] \
    [--dashboard-publish-options <value>] \
    [--version-description <value>] \
    [--validation-strategy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `create-dashboard` (minus `--permissions`, `--tags`, `--folder-arns`).

**Output Schema:** Same as `create-dashboard`.

---

### 2.5 `delete-dashboard`

Deletes a dashboard (all versions or a specific version).

**Synopsis:**
```bash
aws quicksight delete-dashboard \
    --aws-account-id <value> \
    --dashboard-id <value> \
    [--version-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID |
| `--version-number` | No | long | all versions | Specific version to delete |

**Output Schema:**
```json
{
    "DashboardId": "string",
    "Arn": "string",
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 2.6 `list-dashboards`

Lists dashboards in an account. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-dashboards \
    --aws-account-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Output Schema:**
```json
{
    "DashboardSummaryList": [
        {
            "Arn": "string",
            "DashboardId": "string",
            "Name": "string",
            "CreatedTime": "timestamp",
            "LastUpdatedTime": "timestamp",
            "PublishedVersionNumber": "long",
            "LastPublishedTime": "timestamp"
        }
    ],
    "NextToken": "string",
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 2.7 `list-dashboard-versions`

Lists all versions of a dashboard. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-dashboard-versions \
    --aws-account-id <value> \
    --dashboard-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID |

**Output Schema:**
```json
{
    "DashboardVersionSummaryList": [
        {
            "Arn": "string",
            "CreatedTime": "timestamp",
            "VersionNumber": "long",
            "Status": "string",
            "SourceEntityArn": "string",
            "Description": "string"
        }
    ],
    "NextToken": "string",
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 2.8 `search-dashboards`

Searches dashboards using filters. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight search-dashboards \
    --aws-account-id <value> \
    --filters <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--filters` | **Yes** | list | -- | Search filters. Operator: `StringEquals`, `StringLike` |

**Filter Structure:**
```json
[
    {
        "Operator": "StringEquals",
        "Name": "QUICKSIGHT_USER|QUICKSIGHT_VIEWER_OR_OWNER|DIRECT_QUICKSIGHT_VIEWER_OR_OWNER|DASHBOARD_NAME",
        "Value": "string"
    }
]
```

**Output Schema:** Same as `list-dashboards`.

---

### 2.9 `update-dashboard-published-version`

Updates which version is the published version of a dashboard.

**Synopsis:**
```bash
aws quicksight update-dashboard-published-version \
    --aws-account-id <value> \
    --dashboard-id <value> \
    --version-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID |
| `--version-number` | **Yes** | long | -- | Version number to publish |

**Output Schema:**
```json
{
    "DashboardId": "string",
    "DashboardArn": "string",
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 2.10 `update-dashboard-links`

Updates linked dashboards (analyses) for a dashboard.

**Synopsis:**
```bash
aws quicksight update-dashboard-links \
    --aws-account-id <value> \
    --dashboard-id <value> \
    --link-entities <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID |
| `--link-entities` | **Yes** | list(string) | -- | ARNs of linked entities |

**Output Schema:**
```json
{
    "DashboardArn": "string",
    "LinkEntities": ["string"],
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 2.11 `describe-dashboard-permissions`

Describes permissions for a dashboard.

**Synopsis:**
```bash
aws quicksight describe-dashboard-permissions \
    --aws-account-id <value> \
    --dashboard-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID |

**Output Schema:**
```json
{
    "DashboardId": "string",
    "DashboardArn": "string",
    "Permissions": [
        {
            "Principal": "string",
            "Actions": ["string"]
        }
    ],
    "Status": "integer",
    "RequestId": "string",
    "LinkSharingConfiguration": {
        "Permissions": []
    }
}
```

---

### 2.12 `update-dashboard-permissions`

Updates dashboard permissions.

**Synopsis:**
```bash
aws quicksight update-dashboard-permissions \
    --aws-account-id <value> \
    --dashboard-id <value> \
    [--grant-permissions <value>] \
    [--revoke-permissions <value>] \
    [--grant-link-permissions <value>] \
    [--revoke-link-permissions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--dashboard-id` | **Yes** | string | -- | Dashboard ID |
| `--grant-permissions` | No | list | None | Permissions to grant |
| `--revoke-permissions` | No | list | None | Permissions to revoke |
| `--grant-link-permissions` | No | list | None | Link sharing permissions to grant |
| `--revoke-link-permissions` | No | list | None | Link sharing permissions to revoke |

**Output Schema:** Same as `describe-dashboard-permissions`.
