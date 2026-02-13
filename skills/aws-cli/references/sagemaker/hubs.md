# Hubs

## 1. `create-hub`

Creates a SageMaker Hub for sharing ML resources.

**Synopsis:**
```bash
aws sagemaker create-hub \
    --hub-name <value> \
    --hub-description <value> \
    [--hub-display-name <value>] \
    [--hub-search-keywords <value>] \
    [--s3-storage-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hub-name` | **Yes** | string | -- | Hub name |
| `--hub-description` | **Yes** | string | -- | Description |
| `--hub-display-name` | No | string | -- | Display name |
| `--hub-search-keywords` | No | list | -- | Search keywords |
| `--s3-storage-config` | No | structure | -- | `S3OutputPath` |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "HubArn": "string"
}
```

---

## 2. `describe-hub` / `list-hubs` / `update-hub` / `delete-hub`

```bash
aws sagemaker describe-hub --hub-name <value>
aws sagemaker list-hubs [--name-contains <value>] [--creation-time-before <value>] [--creation-time-after <value>] [--sort-by <value>] [--sort-order <value>]
aws sagemaker update-hub --hub-name <value> [--hub-description <value>] [--hub-display-name <value>] [--hub-search-keywords <value>]
aws sagemaker delete-hub --hub-name <value>
```

**describe-hub Output:**
```json
{
    "HubName": "string",
    "HubArn": "string",
    "HubDisplayName": "string",
    "HubDescription": "string",
    "HubSearchKeywords": ["string"],
    "S3StorageConfig": {"S3OutputPath": "string"},
    "HubStatus": "Creating|Active|UpdateFailed|CreateFailed|Deleting|DeleteFailed",
    "FailureReason": "string",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp"
}
```

---

## Hub Content

### 3. `describe-hub-content`

Returns details about hub content.

```bash
aws sagemaker describe-hub-content \
    --hub-name <value> \
    --hub-content-type <value> \
    --hub-content-name <value> \
    [--hub-content-version <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hub-name` | **Yes** | string | -- | Hub name |
| `--hub-content-type` | **Yes** | string | -- | `Model`, `Notebook`, `ModelReference` |
| `--hub-content-name` | **Yes** | string | -- | Content name |
| `--hub-content-version` | No | string | -- | Content version |

---

### 4. `list-hub-contents` / `list-hub-content-versions`

```bash
aws sagemaker list-hub-contents --hub-name <value> --hub-content-type <value> [--name-contains <value>] [--sort-by <value>] [--sort-order <value>]
aws sagemaker list-hub-content-versions --hub-name <value> --hub-content-type <value> --hub-content-name <value> [--sort-by <value>] [--sort-order <value>]
```

---

### 5. `import-hub-content`

Imports content to a hub.

```bash
aws sagemaker import-hub-content \
    --hub-name <value> \
    --hub-content-name <value> \
    --hub-content-type <value> \
    --document-schema-version <value> \
    --hub-content-document <value> \
    [--hub-content-version <value>] \
    [--hub-content-display-name <value>] \
    [--hub-content-description <value>] \
    [--hub-content-markdown <value>] \
    [--hub-content-search-keywords <value>] \
    [--tags <value>]
```

**Output Schema:**
```json
{
    "HubArn": "string",
    "HubContentArn": "string"
}
```

---

### 6. `update-hub-content` / `delete-hub-content`

```bash
aws sagemaker update-hub-content --hub-name <value> --hub-content-name <value> --hub-content-type <value> [--hub-content-display-name <value>] [--hub-content-description <value>]
aws sagemaker delete-hub-content --hub-name <value> --hub-content-type <value> --hub-content-name <value>
```

---

### 7. `create-hub-content-reference` / `delete-hub-content-reference`

```bash
aws sagemaker create-hub-content-reference --hub-name <value> --sage-maker-public-hub-content-arn <value> [--hub-content-name <value>] [--min-version <value>] [--tags <value>]
aws sagemaker delete-hub-content-reference --hub-name <value> --hub-content-type <value> --hub-content-name <value>
```
