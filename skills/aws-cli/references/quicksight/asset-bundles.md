# Asset Bundles

Asset bundles allow exporting and importing QuickSight resources (dashboards, analyses, data sets, data sources, themes) between accounts.

### 16.1 `start-asset-bundle-export-job`

Starts an asynchronous export job.

**Synopsis:**
```bash
aws quicksight start-asset-bundle-export-job \
    --aws-account-id <value> \
    --asset-bundle-export-job-id <value> \
    --resource-arns <value> \
    --export-format <value> \
    [--include-all-dependencies | --no-include-all-dependencies] \
    [--cloud-formation-override-property-configuration <value>] \
    [--include-permissions | --no-include-permissions] \
    [--include-tags | --no-include-tags] \
    [--validation-strategy <value>] \
    [--include-folder-memberships | --no-include-folder-memberships] \
    [--include-folder-members <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--asset-bundle-export-job-id` | **Yes** | string | -- | Export job ID |
| `--resource-arns` | **Yes** | list(string) | -- | ARNs of resources to export |
| `--export-format` | **Yes** | string | -- | `CLOUDFORMATION_JSON`, `QUICKSIGHT_JSON` |
| `--include-all-dependencies` | No | boolean | false | Include dependent resources |
| `--include-permissions` | No | boolean | false | Include permissions |
| `--include-tags` | No | boolean | false | Include tags |

**Output Schema:**
```json
{
    "Arn": "string",
    "AssetBundleExportJobId": "string",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 16.2 `describe-asset-bundle-export-job`

Describes an export job.

**Synopsis:**
```bash
aws quicksight describe-asset-bundle-export-job \
    --aws-account-id <value> \
    --asset-bundle-export-job-id <value>
```

**Output Schema:**
```json
{
    "JobStatus": "QUEUED_FOR_IMMEDIATE_EXECUTION|IN_PROGRESS|SUCCESSFUL|FAILED",
    "DownloadUrl": "string",
    "Errors": [],
    "Arn": "string",
    "CreatedTime": "timestamp",
    "AssetBundleExportJobId": "string",
    "AwsAccountId": "string",
    "ResourceArns": ["string"],
    "IncludeAllDependencies": "boolean",
    "ExportFormat": "string",
    "IncludePermissions": "boolean",
    "IncludeTags": "boolean",
    "ValidationStrategy": {},
    "Warnings": [],
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 16.3 `list-asset-bundle-export-jobs`

Lists export jobs. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-asset-bundle-export-jobs \
    --aws-account-id <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

---

### 16.4 `start-asset-bundle-import-job`

Starts an asynchronous import job from a bundle.

**Synopsis:**
```bash
aws quicksight start-asset-bundle-import-job \
    --aws-account-id <value> \
    --asset-bundle-import-job-id <value> \
    --asset-bundle-import-source <value> \
    [--override-parameters <value>] \
    [--failure-action <value>] \
    [--override-permissions <value>] \
    [--override-tags <value>] \
    [--override-validation-strategy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--asset-bundle-import-job-id` | **Yes** | string | -- | Import job ID |
| `--asset-bundle-import-source` | **Yes** | structure | -- | Bundle source (S3 URI or body) |
| `--override-parameters` | No | structure | None | Override resource parameters |
| `--failure-action` | No | string | `DO_NOTHING` | `DO_NOTHING` or `ROLLBACK` |
| `--override-permissions` | No | structure | None | Override permissions |
| `--override-tags` | No | structure | None | Override tags |

**Import Source:**
```json
{
    "Body": "blob",
    "S3Uri": "string"
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "AssetBundleImportJobId": "string",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 16.5 `describe-asset-bundle-import-job`

Describes an import job.

**Synopsis:**
```bash
aws quicksight describe-asset-bundle-import-job \
    --aws-account-id <value> \
    --asset-bundle-import-job-id <value>
```

---

### 16.6 `list-asset-bundle-import-jobs`

Lists import jobs. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-asset-bundle-import-jobs \
    --aws-account-id <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```
