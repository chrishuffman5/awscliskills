# Feature Store

## 1. `create-feature-group`

Creates a feature group for storing and retrieving ML features.

**Synopsis:**
```bash
aws sagemaker create-feature-group \
    --feature-group-name <value> \
    --record-identifier-feature-name <value> \
    --event-time-feature-name <value> \
    --feature-definitions <value> \
    [--online-store-config <value>] \
    [--offline-store-config <value>] \
    [--throughput-config <value>] \
    [--role-arn <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--feature-group-name` | **Yes** | string | -- | Unique name (1-64 chars, `[a-zA-Z0-9](-*[a-zA-Z0-9]){0,63}`) |
| `--record-identifier-feature-name` | **Yes** | string | -- | Name of the record identifier feature |
| `--event-time-feature-name` | **Yes** | string | -- | Name of the event time feature |
| `--feature-definitions` | **Yes** | list | -- | Feature name/type definitions |
| `--online-store-config` | No | structure | -- | Online store settings (`EnableOnlineStore`, `SecurityConfig`, `StorageType`, `TtlDuration`) |
| `--offline-store-config` | No | structure | -- | Offline store S3 config, data catalog config, format (`Glue`/`Iceberg`) |
| `--throughput-config` | No | structure | -- | `ThroughputMode` (`OnDemand`/`Provisioned`), `ProvisionedReadCapacityUnits`, `ProvisionedWriteCapacityUnits` |
| `--role-arn` | No | string | -- | IAM role ARN |
| `--description` | No | string | -- | Description (max 128 chars) |
| `--tags` | No | list | -- | Key-value tags |

**Feature Definitions:**
```json
[
    {"FeatureName": "string", "FeatureType": "Integral|Fractional|String"},
    {"FeatureName": "customer_id", "FeatureType": "String"},
    {"FeatureName": "age", "FeatureType": "Integral"},
    {"FeatureName": "score", "FeatureType": "Fractional"}
]
```

**Online Store Config:**
```json
{
    "SecurityConfig": {"KmsKeyId": "string"},
    "EnableOnlineStore": true,
    "StorageType": "Standard|InMemory",
    "TtlDuration": {"Unit": "Seconds|Minutes|Hours|Days|Weeks", "Value": "integer"}
}
```

**Offline Store Config:**
```json
{
    "S3StorageConfig": {
        "S3Uri": "string",
        "KmsKeyId": "string",
        "ResolvedOutputS3Uri": "string"
    },
    "DisableGlueTableCreation": false,
    "DataCatalogConfig": {
        "TableName": "string",
        "Catalog": "string",
        "Database": "string"
    },
    "TableFormat": "Glue|Iceberg"
}
```

**Output Schema:**
```json
{
    "FeatureGroupArn": "string"
}
```

---

## 2. `describe-feature-group`

Returns details about a feature group.

**Synopsis:**
```bash
aws sagemaker describe-feature-group \
    --feature-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--feature-group-name` | **Yes** | string | -- | Feature group name or ARN |

**Output Schema:**
```json
{
    "FeatureGroupArn": "string",
    "FeatureGroupName": "string",
    "RecordIdentifierFeatureName": "string",
    "EventTimeFeatureName": "string",
    "FeatureDefinitions": [{"FeatureName": "string", "FeatureType": "Integral|Fractional|String", "CollectionType": "List|Set|Vector", "CollectionConfig": {...}}],
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "OnlineStoreConfig": {...},
    "OfflineStoreConfig": {...},
    "ThroughputConfig": {"ThroughputMode": "OnDemand|Provisioned", "ProvisionedReadCapacityUnits": "integer", "ProvisionedWriteCapacityUnits": "integer"},
    "RoleArn": "string",
    "FeatureGroupStatus": "Creating|Created|CreateFailed|Deleting|DeleteFailed",
    "OfflineStoreStatus": {"Status": "Active|Blocked|Disabled", "BlockedReason": "string"},
    "LastUpdateStatus": {"Status": "Successful|Failed|InProgress", "FailureReason": "string"},
    "FailureReason": "string",
    "Description": "string",
    "OnlineStoreTotalSizeBytes": "long"
}
```

---

## 3. `list-feature-groups`

Lists feature groups. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-feature-groups \
    [--name-contains <value>] \
    [--feature-group-status-equals <value>] \
    [--offline-store-status-equals <value>] \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-contains` | No | string | -- | Filter by name substring |
| `--feature-group-status-equals` | No | string | -- | `Creating`, `Created`, `CreateFailed`, `Deleting`, `DeleteFailed` |
| `--offline-store-status-equals` | No | string | -- | `Active`, `Blocked`, `Disabled` |
| `--sort-by` | No | string | `CreationTime` | `Name`, `FeatureGroupStatus`, `OfflineStoreStatus`, `CreationTime` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "FeatureGroupSummaries": [
        {
            "FeatureGroupName": "string",
            "FeatureGroupArn": "string",
            "CreationTime": "timestamp",
            "FeatureGroupStatus": "string",
            "OfflineStoreStatus": {"Status": "string"}
        }
    ],
    "NextToken": "string"
}
```

---

## 4. `update-feature-group`

Updates a feature group (add features, change throughput, update online store config).

**Synopsis:**
```bash
aws sagemaker update-feature-group \
    --feature-group-name <value> \
    [--feature-additions <value>] \
    [--online-store-config <value>] \
    [--throughput-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--feature-group-name` | **Yes** | string | -- | Feature group name |
| `--feature-additions` | No | list | -- | New feature definitions to add |
| `--online-store-config` | No | structure | -- | Updated TTL duration |
| `--throughput-config` | No | structure | -- | Updated throughput settings |

**Output Schema:**
```json
{
    "FeatureGroupArn": "string"
}
```

---

## 5. `delete-feature-group`

Deletes a feature group.

**Synopsis:**
```bash
aws sagemaker delete-feature-group \
    --feature-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--feature-group-name` | **Yes** | string | -- | Feature group name |

**Output:** None

---

## 6. `describe-feature-metadata`

Returns metadata for a specific feature within a feature group.

**Synopsis:**
```bash
aws sagemaker describe-feature-metadata \
    --feature-group-name <value> \
    --feature-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--feature-group-name` | **Yes** | string | -- | Feature group name |
| `--feature-name` | **Yes** | string | -- | Feature name |

**Output Schema:**
```json
{
    "FeatureGroupArn": "string",
    "FeatureGroupName": "string",
    "FeatureName": "string",
    "FeatureType": "Integral|Fractional|String",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "Description": "string",
    "Parameters": [{"Key": "string", "Value": "string"}]
}
```

---

## 7. `update-feature-metadata`

Updates metadata for a feature.

**Synopsis:**
```bash
aws sagemaker update-feature-metadata \
    --feature-group-name <value> \
    --feature-name <value> \
    [--description <value>] \
    [--parameter-additions <value>] \
    [--parameter-removals <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--feature-group-name` | **Yes** | string | -- | Feature group name |
| `--feature-name` | **Yes** | string | -- | Feature name |
| `--description` | No | string | -- | Updated description |
| `--parameter-additions` | No | list | -- | `[{Key, Value}]` parameters to add |
| `--parameter-removals` | No | list | -- | Parameter keys to remove |

**Output:** None
