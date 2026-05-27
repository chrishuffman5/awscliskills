# Projects

### 1.1 `create-project`

Creates a new Amazon Lookout for Vision project. A project is a grouping of datasets and model versions for a specific anomaly detection use case.

**Synopsis:**
```bash
aws lookoutvision create-project \
    --project-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Name for the project |
| `--client-token` | No | string | Auto | Idempotency token (active for 8 hours) |

**Output Schema:**
```json
{
    "ProjectMetadata": {
        "ProjectArn": "string",
        "ProjectName": "string",
        "CreationTimestamp": "timestamp"
    }
}
```

---

### 1.2 `delete-project`

Deletes an Amazon Lookout for Vision project. All model versions and datasets must be removed before deleting the project.

**Synopsis:**
```bash
aws lookoutvision delete-project \
    --project-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Name of the project to delete |
| `--client-token` | No | string | Auto | Idempotency token (active for 8 hours) |

**Output Schema:**
```json
{
    "ProjectArn": "string"
}
```

---

### 1.3 `describe-project`

Describes an Amazon Lookout for Vision project, including its datasets.

**Synopsis:**
```bash
aws lookoutvision describe-project \
    --project-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Name of the project to describe |

**Output Schema:**
```json
{
    "ProjectDescription": {
        "ProjectArn": "string",
        "ProjectName": "string",
        "CreationTimestamp": "timestamp",
        "Datasets": [
            {
                "DatasetType": "string",
                "CreationTimestamp": "timestamp",
                "Status": "string",
                "StatusMessage": "string"
            }
        ]
    }
}
```

---

### 1.4 `list-projects`

Lists Amazon Lookout for Vision projects in the current AWS account and region. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutvision list-projects \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Maximum total items to return |

**Output Schema:**
```json
{
    "Projects": [
        {
            "ProjectArn": "string",
            "ProjectName": "string",
            "CreationTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
