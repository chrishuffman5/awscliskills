# Workgroups

### 4.1 `create-work-group`

Creates a workgroup to organize and control query access and costs.

**Synopsis:**
```bash
aws athena create-work-group \
    --name <value> \
    [--configuration <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Workgroup name |
| `--configuration` | No | structure | -- | Workgroup configuration (see below) |
| `--description` | No | string | -- | Description |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Configuration Structure:**
```json
{
    "ResultConfiguration": {
        "OutputLocation": "s3://bucket/results/",
        "EncryptionConfiguration": {
            "EncryptionOption": "SSE_S3|SSE_KMS|CSE_KMS",
            "KmsKey": "string"
        },
        "ExpectedBucketOwner": "string",
        "AclConfiguration": {
            "S3AclOption": "BUCKET_OWNER_FULL_CONTROL"
        }
    },
    "EnforceWorkGroupConfiguration": true|false,
    "PublishCloudWatchMetricsEnabled": true|false,
    "BytesScannedCutoffPerQuery": "long",
    "RequesterPaysEnabled": true|false,
    "EngineVersion": {
        "SelectedEngineVersion": "string",
        "EffectiveEngineVersion": "string"
    },
    "AdditionalConfiguration": "string",
    "ExecutionRole": "string",
    "CustomerContentEncryptionConfiguration": {
        "KmsKey": "string"
    },
    "EnableMinimumEncryptionConfiguration": true|false,
    "IdentityCenterConfiguration": {
        "EnableIdentityCenter": true|false,
        "IdentityCenterInstanceArn": "string"
    },
    "QueryResultsS3AccessGrantsConfiguration": {
        "EnableS3AccessGrants": true|false,
        "CreateUserLevelPrefix": true|false,
        "AuthenticationType": "DIRECTORY_IDENTITY"
    }
}
```

No output on success.

---

### 4.2 `delete-work-group`

Deletes a workgroup. The `primary` workgroup cannot be deleted.

**Synopsis:**
```bash
aws athena delete-work-group \
    --work-group <value> \
    [--recursive-delete-option | --no-recursive-delete-option] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--work-group` | **Yes** | string | -- | Workgroup to delete |
| `--recursive-delete-option` | No | boolean | false | Delete even if workgroup contains named queries/prepared statements |

No output on success.

---

### 4.3 `get-work-group`

Returns information about a workgroup.

**Synopsis:**
```bash
aws athena get-work-group \
    --work-group <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--work-group` | **Yes** | string | -- | Workgroup name |

**Output Schema:**
```json
{
    "WorkGroup": {
        "Name": "string",
        "State": "ENABLED|DISABLED",
        "Configuration": {
            "ResultConfiguration": {},
            "EnforceWorkGroupConfiguration": "boolean",
            "PublishCloudWatchMetricsEnabled": "boolean",
            "BytesScannedCutoffPerQuery": "long",
            "RequesterPaysEnabled": "boolean",
            "EngineVersion": {
                "SelectedEngineVersion": "string",
                "EffectiveEngineVersion": "string"
            },
            "AdditionalConfiguration": "string",
            "ExecutionRole": "string",
            "CustomerContentEncryptionConfiguration": {},
            "EnableMinimumEncryptionConfiguration": "boolean",
            "IdentityCenterConfiguration": {},
            "QueryResultsS3AccessGrantsConfiguration": {}
        },
        "Description": "string",
        "CreationTime": "timestamp",
        "IdentityCenterApplicationArn": "string"
    }
}
```

---

### 4.4 `update-work-group`

Updates a workgroup's configuration.

**Synopsis:**
```bash
aws athena update-work-group \
    --work-group <value> \
    [--description <value>] \
    [--configuration-updates <value>] \
    [--state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--work-group` | **Yes** | string | -- | Workgroup to update |
| `--description` | No | string | -- | New description |
| `--configuration-updates` | No | structure | -- | Configuration updates (JSON) |
| `--state` | No | string | -- | `ENABLED` or `DISABLED` |

**Configuration Updates Structure:**
```json
{
    "EnforceWorkGroupConfiguration": true|false,
    "ResultConfigurationUpdates": {
        "OutputLocation": "string",
        "RemoveOutputLocation": true|false,
        "EncryptionConfiguration": {},
        "RemoveEncryptionConfiguration": true|false,
        "ExpectedBucketOwner": "string",
        "RemoveExpectedBucketOwner": true|false,
        "AclConfiguration": {},
        "RemoveAclConfiguration": true|false
    },
    "PublishCloudWatchMetricsEnabled": true|false,
    "BytesScannedCutoffPerQuery": "long",
    "RemoveBytesScannedCutoffPerQuery": true|false,
    "RequesterPaysEnabled": true|false,
    "EngineVersion": {},
    "RemoveCustomerContentEncryptionConfiguration": true|false,
    "AdditionalConfiguration": "string",
    "ExecutionRole": "string",
    "CustomerContentEncryptionConfiguration": {},
    "EnableMinimumEncryptionConfiguration": true|false,
    "QueryResultsS3AccessGrantsConfiguration": {}
}
```

No output on success.

---

### 4.5 `list-work-groups`

Lists all workgroups. **Paginated operation.**

**Synopsis:**
```bash
aws athena list-work-groups \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "WorkGroups": [
        {
            "Name": "string",
            "State": "ENABLED|DISABLED",
            "Description": "string",
            "CreationTime": "timestamp",
            "EngineVersion": {
                "SelectedEngineVersion": "string",
                "EffectiveEngineVersion": "string"
            },
            "IdentityCenterApplicationArn": "string"
        }
    ],
    "NextToken": "string"
}
```
