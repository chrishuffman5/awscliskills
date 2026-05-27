# Analyses

### 4.1 `create-analysis`

Creates an analysis from a template or definition.

**Synopsis:**
```bash
aws quicksight create-analysis \
    --aws-account-id <value> \
    --analysis-id <value> \
    --name <value> \
    [--source-entity <value>] \
    [--definition <value>] \
    [--parameters <value>] \
    [--permissions <value>] \
    [--tags <value>] \
    [--theme-arn <value>] \
    [--validation-strategy <value>] \
    [--folder-arns <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--analysis-id` | **Yes** | string | -- | Analysis ID (1-512 chars) |
| `--name` | **Yes** | string | -- | Display name (1-2048 chars) |
| `--source-entity` | No* | structure | None | Source template with data set references |
| `--definition` | No* | structure | None | Full analysis definition |
| `--parameters` | No | structure | None | Default parameter values |
| `--permissions` | No | list | None | Resource permissions |
| `--tags` | No | list | None | Resource tags |
| `--theme-arn` | No | string | None | Theme ARN |
| `--validation-strategy` | No | structure | None | `{"Mode":"STRICT|LENIENT"}` |
| `--folder-arns` | No | list(string) | None | Folders to add to |

*Either `--source-entity` or `--definition` is required.

**Output Schema:**
```json
{
    "Arn": "string",
    "AnalysisId": "string",
    "CreationStatus": "CREATION_IN_PROGRESS|CREATION_SUCCESSFUL|CREATION_FAILED|UPDATE_IN_PROGRESS|UPDATE_SUCCESSFUL|UPDATE_FAILED|DELETED",
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 4.2 `describe-analysis`

Describes an analysis.

**Synopsis:**
```bash
aws quicksight describe-analysis \
    --aws-account-id <value> \
    --analysis-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--analysis-id` | **Yes** | string | -- | Analysis ID |

**Output Schema:**
```json
{
    "Analysis": {
        "AnalysisId": "string",
        "Arn": "string",
        "Name": "string",
        "Status": "string",
        "DataSetArns": ["string"],
        "ThemeArn": "string",
        "CreatedTime": "timestamp",
        "LastUpdatedTime": "timestamp",
        "Sheets": [
            {
                "SheetId": "string",
                "Name": "string"
            }
        ]
    },
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 4.3 `describe-analysis-definition`

Returns the full definition of an analysis.

**Synopsis:**
```bash
aws quicksight describe-analysis-definition \
    --aws-account-id <value> \
    --analysis-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `describe-analysis`.

**Output Schema:**
```json
{
    "AnalysisId": "string",
    "Name": "string",
    "ResourceStatus": "string",
    "Definition": {},
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 4.4 `update-analysis`

Updates an analysis.

**Synopsis:**
```bash
aws quicksight update-analysis \
    --aws-account-id <value> \
    --analysis-id <value> \
    --name <value> \
    [--source-entity <value>] \
    [--definition <value>] \
    [--parameters <value>] \
    [--theme-arn <value>] \
    [--validation-strategy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `create-analysis` (minus `--permissions`, `--tags`, `--folder-arns`).

**Output Schema:** Same as `create-analysis`.

---

### 4.5 `delete-analysis`

Deletes an analysis (recoverable for 30 days unless force-deleted).

**Synopsis:**
```bash
aws quicksight delete-analysis \
    --aws-account-id <value> \
    --analysis-id <value> \
    [--recovery-window-in-days <value>] \
    [--force-delete-without-recovery | --no-force-delete-without-recovery] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--analysis-id` | **Yes** | string | -- | Analysis ID |
| `--recovery-window-in-days` | No | long | 30 | Recovery window (0-30 days) |
| `--force-delete-without-recovery` | No | boolean | false | Permanently delete immediately |

**Output Schema:**
```json
{
    "Status": "integer",
    "Arn": "string",
    "AnalysisId": "string",
    "DeletionTime": "timestamp",
    "RequestId": "string"
}
```

---

### 4.6 `list-analyses`

Lists analyses in an account. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-analyses \
    --aws-account-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "AnalysisSummaryList": [
        {
            "Arn": "string",
            "AnalysisId": "string",
            "Name": "string",
            "Status": "string",
            "CreatedTime": "timestamp",
            "LastUpdatedTime": "timestamp"
        }
    ],
    "NextToken": "string",
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 4.7 `search-analyses`

Searches analyses using filters. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight search-analyses \
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
| `--filters` | **Yes** | list | -- | Search filters with `Operator`, `Name`, `Value` |

**Output Schema:** Same as `list-analyses`.

---

### 4.8 `restore-analysis`

Restores a deleted analysis (within the recovery window).

**Synopsis:**
```bash
aws quicksight restore-analysis \
    --aws-account-id <value> \
    --analysis-id <value> \
    [--restore-to-folder-arns <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--analysis-id` | **Yes** | string | -- | Analysis ID to restore |

**Output Schema:**
```json
{
    "Status": "integer",
    "Arn": "string",
    "AnalysisId": "string",
    "RequestId": "string"
}
```

---

### 4.9 `describe-analysis-permissions`

Describes permissions for an analysis.

**Synopsis:**
```bash
aws quicksight describe-analysis-permissions \
    --aws-account-id <value> \
    --analysis-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "AnalysisId": "string",
    "AnalysisArn": "string",
    "Permissions": [
        {
            "Principal": "string",
            "Actions": ["string"]
        }
    ],
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 4.10 `update-analysis-permissions`

Updates analysis permissions.

**Synopsis:**
```bash
aws quicksight update-analysis-permissions \
    --aws-account-id <value> \
    --analysis-id <value> \
    [--grant-permissions <value>] \
    [--revoke-permissions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--analysis-id` | **Yes** | string | -- | Analysis ID |
| `--grant-permissions` | No | list | None | Permissions to grant |
| `--revoke-permissions` | No | list | None | Permissions to revoke |

**Output Schema:** Same as `describe-analysis-permissions`.
