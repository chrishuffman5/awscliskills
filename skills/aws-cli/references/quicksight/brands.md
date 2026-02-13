# Brands

Brands allow customizing the QuickSight experience with logos, colors, and application themes.

### 17.1 `create-brand`

Creates a brand.

**Synopsis:**
```bash
aws quicksight create-brand \
    --aws-account-id <value> \
    --brand-id <value> \
    --brand-definition <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--brand-id` | **Yes** | string | -- | Brand ID |
| `--brand-definition` | **Yes** | structure | -- | Brand definition (logo, colors, favicon) |
| `--tags` | No | list | None | Resource tags |

**Output Schema:**
```json
{
    "BrandDetail": {
        "BrandId": "string",
        "Arn": "string",
        "BrandStatus": "CREATE_IN_PROGRESS|CREATE_SUCCEEDED|CREATE_FAILED|DELETE_IN_PROGRESS|DELETE_FAILED",
        "CreatedTime": "timestamp",
        "LastUpdatedTime": "timestamp",
        "VersionId": "string",
        "VersionStatus": "string",
        "Errors": [],
        "Logo": {}
    },
    "BrandDefinition": {},
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 17.2 `describe-brand` / `update-brand` / `delete-brand`

Manage brands.

**Synopsis:**
```bash
aws quicksight describe-brand --aws-account-id <value> --brand-id <value>
aws quicksight update-brand --aws-account-id <value> --brand-id <value> --brand-definition <value>
aws quicksight delete-brand --aws-account-id <value> --brand-id <value>
```

---

### 17.3 `list-brands`

Lists brands.

**Synopsis:**
```bash
aws quicksight list-brands \
    --aws-account-id <value> \
    [--starting-token <value>] [--max-items <value>]
```

---

### 17.4 `describe-brand-assignment` / `update-brand-assignment` / `delete-brand-assignment`

Manage brand assignment (which brand is active).

**Synopsis:**
```bash
aws quicksight describe-brand-assignment --aws-account-id <value>
aws quicksight update-brand-assignment --aws-account-id <value> --brand-arn <value>
aws quicksight delete-brand-assignment --aws-account-id <value>
```

---

### 17.5 `describe-brand-published-version` / `update-brand-published-version`

Manage brand published versions.

**Synopsis:**
```bash
aws quicksight describe-brand-published-version --aws-account-id <value> --brand-id <value>
aws quicksight update-brand-published-version --aws-account-id <value> --brand-id <value> --version-id <value>
```
