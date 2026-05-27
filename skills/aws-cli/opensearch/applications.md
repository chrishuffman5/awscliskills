# Applications

### 6.1 `create-application`

Creates an OpenSearch application.

**Synopsis:**
```bash
aws opensearch create-application \
    --name <value> \
    [--data-sources <value>] \
    [--iam-identity-center-options <value>] \
    [--app-configs <value>] \
    [--tag-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Application name (3-28 chars) |
| `--data-sources` | No | list | None | Data sources for the application |
| `--iam-identity-center-options` | No | structure | None | IAM Identity Center config |
| `--app-configs` | No | list | None | Application configuration |
| `--tag-list` | No | list | None | Tags |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "Arn": "string",
    "DataSources": [],
    "IamIdentityCenterOptions": {},
    "AppConfigs": [],
    "CreatedAt": "timestamp"
}
```

---

### 6.2 `delete-application`

Deletes an OpenSearch application.

**Synopsis:**
```bash
aws opensearch delete-application \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Application ID |

**Output:** None

---

### 6.3 `update-application`

Updates an OpenSearch application.

**Synopsis:**
```bash
aws opensearch update-application \
    --id <value> \
    [--data-sources <value>] \
    [--app-configs <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Application ID |
| `--data-sources` | No | list | None | Updated data sources |
| `--app-configs` | No | list | None | Updated configuration |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "Arn": "string",
    "DataSources": [],
    "AppConfigs": [],
    "LastUpdatedAt": "timestamp"
}
```

---

### 6.4 `get-application`

Returns details about an OpenSearch application.

**Synopsis:**
```bash
aws opensearch get-application \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Application ID |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "Arn": "string",
    "DataSources": [],
    "IamIdentityCenterOptions": {},
    "AppConfigs": [],
    "CreatedAt": "timestamp",
    "LastUpdatedAt": "timestamp"
}
```

---

### 6.5 `list-applications`

Lists OpenSearch applications. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch list-applications \
    [--statuses <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--statuses` | No | list(string) | None | Filter by status |

**Output Schema:**
```json
{
    "ApplicationSummaries": [
        {
            "Id": "string",
            "Name": "string",
            "Arn": "string",
            "Status": "string",
            "CreatedAt": "timestamp",
            "LastUpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
