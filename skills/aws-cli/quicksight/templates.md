# Templates

### 5.1 `create-template`

Creates a template from an analysis or definition. Templates are reusable blueprints for dashboards and analyses.

**Synopsis:**
```bash
aws quicksight create-template \
    --aws-account-id <value> \
    --template-id <value> \
    --name <value> \
    [--source-entity <value>] \
    [--definition <value>] \
    [--permissions <value>] \
    [--tags <value>] \
    [--version-description <value>] \
    [--validation-strategy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--template-id` | **Yes** | string | -- | Template ID (1-512 chars) |
| `--name` | **Yes** | string | -- | Display name (1-2048 chars) |
| `--source-entity` | No* | structure | None | Source analysis or template ARN |
| `--definition` | No* | structure | None | Full template definition |
| `--permissions` | No | list | None | Resource permissions |
| `--tags` | No | list | None | Resource tags |
| `--version-description` | No | string | None | Version description |
| `--validation-strategy` | No | structure | None | `{"Mode":"STRICT|LENIENT"}` |

**Output Schema:**
```json
{
    "Arn": "string",
    "VersionArn": "string",
    "TemplateId": "string",
    "CreationStatus": "string",
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 5.2 `describe-template` / `describe-template-definition`

Describes a template or its full definition.

**Synopsis:**
```bash
aws quicksight describe-template \
    --aws-account-id <value> \
    --template-id <value> \
    [--version-number <value>] \
    [--alias-name <value>]

aws quicksight describe-template-definition \
    --aws-account-id <value> \
    --template-id <value> \
    [--version-number <value>] \
    [--alias-name <value>]
```

---

### 5.3 `update-template`

Updates a template (creates a new version).

**Synopsis:**
```bash
aws quicksight update-template \
    --aws-account-id <value> \
    --template-id <value> \
    --name <value> \
    [--source-entity <value>] \
    [--definition <value>] \
    [--version-description <value>] \
    [--validation-strategy <value>]
```

---

### 5.4 `delete-template`

Deletes a template (all versions or a specific version).

**Synopsis:**
```bash
aws quicksight delete-template \
    --aws-account-id <value> \
    --template-id <value> \
    [--version-number <value>]
```

---

### 5.5 `list-templates`

Lists all templates. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-templates \
    --aws-account-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "TemplateSummaryList": [
        {
            "Arn": "string",
            "TemplateId": "string",
            "Name": "string",
            "LatestVersionNumber": "long",
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

### 5.6 `list-template-versions`

Lists versions of a template. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-template-versions \
    --aws-account-id <value> \
    --template-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 5.7 `describe-template-permissions` / `update-template-permissions`

Manage template permissions.

**Synopsis:**
```bash
aws quicksight describe-template-permissions \
    --aws-account-id <value> \
    --template-id <value>

aws quicksight update-template-permissions \
    --aws-account-id <value> \
    --template-id <value> \
    [--grant-permissions <value>] \
    [--revoke-permissions <value>]
```

---

### 5.8 `create-template-alias`

Creates a template alias pointing to a specific version.

**Synopsis:**
```bash
aws quicksight create-template-alias \
    --aws-account-id <value> \
    --template-id <value> \
    --alias-name <value> \
    --template-version-number <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--template-id` | **Yes** | string | -- | Template ID |
| `--alias-name` | **Yes** | string | -- | Alias name (e.g., `$LATEST`, `prod`) |
| `--template-version-number` | **Yes** | long | -- | Version number to alias |

**Output Schema:**
```json
{
    "TemplateAlias": {
        "AliasName": "string",
        "Arn": "string",
        "TemplateVersionNumber": "long"
    },
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 5.9 `describe-template-alias` / `update-template-alias` / `delete-template-alias`

Manage template aliases.

**Synopsis:**
```bash
aws quicksight describe-template-alias \
    --aws-account-id <value> --template-id <value> --alias-name <value>

aws quicksight update-template-alias \
    --aws-account-id <value> --template-id <value> --alias-name <value> \
    --template-version-number <value>

aws quicksight delete-template-alias \
    --aws-account-id <value> --template-id <value> --alias-name <value>
```

---

### 5.10 `list-template-aliases`

Lists template aliases. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-template-aliases \
    --aws-account-id <value> \
    --template-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```
