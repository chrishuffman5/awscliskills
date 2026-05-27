# Projects

## 1. `create-project`

Creates a SageMaker project from a Service Catalog template.

**Synopsis:**
```bash
aws sagemaker create-project \
    --project-name <value> \
    --service-catalog-provisioning-details <value> \
    [--project-description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project name (1-32 chars) |
| `--service-catalog-provisioning-details` | **Yes** | structure | -- | `ProductId`, `ProvisioningArtifactId`, `PathId`, `ProvisioningParameters` |
| `--project-description` | No | string | -- | Description (max 1024 chars) |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "ProjectArn": "string",
    "ProjectId": "string"
}
```

---

## 2. `describe-project`

Returns details about a project.

```bash
aws sagemaker describe-project --project-name <value>
```

**Output Schema:**
```json
{
    "ProjectArn": "string",
    "ProjectName": "string",
    "ProjectId": "string",
    "ProjectDescription": "string",
    "ServiceCatalogProvisioningDetails": {
        "ProductId": "string",
        "ProvisioningArtifactId": "string",
        "PathId": "string",
        "ProvisioningParameters": [{"Key": "string", "Value": "string"}]
    },
    "ServiceCatalogProvisionedProductDetails": {
        "ProvisionedProductId": "string",
        "ProvisionedProductStatusMessage": "string"
    },
    "ProjectStatus": "Pending|CreateInProgress|CreateCompleted|CreateFailed|DeleteInProgress|DeleteFailed|DeleteCompleted|UpdateInProgress|UpdateCompleted|UpdateFailed",
    "CreatedBy": {...},
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "LastModifiedBy": {...}
}
```

---

## 3. `list-projects`

Lists projects. **Paginated operation.**

```bash
aws sagemaker list-projects \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--name-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

## 4. `update-project`

Updates a project.

```bash
aws sagemaker update-project \
    --project-name <value> \
    [--project-description <value>] \
    [--service-catalog-provisioning-update-details <value>] \
    [--tags <value>]
```

**Output Schema:**
```json
{
    "ProjectArn": "string"
}
```

---

## 5. `delete-project`

Deletes a project.

```bash
aws sagemaker delete-project --project-name <value>
```

**Output:** None

---

## Service Catalog Integration

### 6. `enable-sagemaker-servicecatalog-portfolio`

Enables the SageMaker Service Catalog portfolio for the account.

```bash
aws sagemaker enable-sagemaker-servicecatalog-portfolio
```

**Output:** None

---

### 7. `disable-sagemaker-servicecatalog-portfolio`

Disables the SageMaker Service Catalog portfolio.

```bash
aws sagemaker disable-sagemaker-servicecatalog-portfolio
```

**Output:** None

---

### 8. `get-sagemaker-servicecatalog-portfolio-status`

Gets the Service Catalog portfolio status.

```bash
aws sagemaker get-sagemaker-servicecatalog-portfolio-status
```

**Output Schema:**
```json
{
    "Status": "Enabled|Disabled"
}
```

---

### 9. `list-resource-catalogs`

Lists resource catalogs. **Paginated operation.**

```bash
aws sagemaker list-resource-catalogs \
    [--name-contains <value>] \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```
