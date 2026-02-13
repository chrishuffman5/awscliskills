# Locations (Common)

### 6.1 `create-location-object-storage`

Creates a transfer location for a self-managed object storage system (S3-compatible).

**Synopsis:**
```bash
aws datasync create-location-object-storage \
    --server-hostname <value> \
    --bucket-name <value> \
    [--server-port <value>] \
    [--server-protocol <value>] \
    [--subdirectory <value>] \
    [--access-key <value>] \
    [--secret-key <value>] \
    [--agent-arns <value>] \
    [--tags <value>] \
    [--server-certificate <value>] \
    [--cmk-secret-config <value>] \
    [--custom-secret-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-hostname` | **Yes** | string | -- | Object storage server hostname or IP (max 255 chars) |
| `--bucket-name` | **Yes** | string | -- | Bucket name (3-63 chars) |
| `--server-port` | No | integer | None | Server port (1-65536) |
| `--server-protocol` | No | string | `HTTPS` | `HTTPS` or `HTTP` |
| `--subdirectory` | No | string | None | Object prefix (max 4096 chars) |
| `--access-key` | No | string | None | Access key for authentication (max 200 chars) |
| `--secret-key` | No | string | None | Secret key for authentication (max 200 chars) |
| `--agent-arns` | No | list(string) | None | Agent ARNs (max 8) |
| `--tags` | No | list | None | Tags (max 50) |
| `--server-certificate` | No | blob | None | PEM certificate chain (max 32768 bytes) |
| `--cmk-secret-config` | No | structure | None | DataSync-managed secret with customer-managed KMS key |
| `--custom-secret-config` | No | structure | None | Customer-managed Secrets Manager secret |

**Output Schema:**
```json
{
    "LocationArn": "string"
}
```

---

### 6.2 `create-location-azure-blob`

Creates a transfer location for a Microsoft Azure Blob Storage container.

**Synopsis:**
```bash
aws datasync create-location-azure-blob \
    --container-url <value> \
    --authentication-type <value> \
    [--sas-configuration <value>] \
    [--blob-type <value>] \
    [--access-tier <value>] \
    [--subdirectory <value>] \
    [--agent-arns <value>] \
    [--tags <value>] \
    [--cmk-secret-config <value>] \
    [--custom-secret-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-url` | **Yes** | string | -- | Azure Blob Storage container URL (max 325 chars) |
| `--authentication-type` | **Yes** | string | -- | `SAS` or `NONE` |
| `--sas-configuration` | No | structure | None | SAS token configuration |
| `--blob-type` | No | string | None | `BLOCK` (currently only option) |
| `--access-tier` | No | string | None | `HOT`, `COOL`, or `ARCHIVE` |
| `--subdirectory` | No | string | None | Virtual directory path (max 1024 chars) |
| `--agent-arns` | No | list(string) | None | Agent ARNs (max 8) |
| `--tags` | No | list | None | Tags (max 50) |
| `--cmk-secret-config` | No | structure | None | DataSync-managed secret with customer-managed KMS key |
| `--custom-secret-config` | No | structure | None | Customer-managed Secrets Manager secret |

**SAS Configuration Structure (shorthand):**
```
Token=string
```

**Output Schema:**
```json
{
    "LocationArn": "string"
}
```

---

### 6.3 `describe-location-object-storage`

Gets details about an object storage location.

**Synopsis:**
```bash
aws datasync describe-location-object-storage \
    --location-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the object storage location |

**Output Schema:**
```json
{
    "LocationArn": "string",
    "LocationUri": "string",
    "AccessKey": "string",
    "ServerPort": "integer",
    "ServerProtocol": "HTTPS|HTTP",
    "AgentArns": ["string"],
    "CreationTime": "timestamp",
    "ServerCertificate": "blob"
}
```

---

### 6.4 `describe-location-azure-blob`

Gets details about an Azure Blob Storage location.

**Synopsis:**
```bash
aws datasync describe-location-azure-blob \
    --location-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the Azure Blob location |

**Output Schema:**
```json
{
    "LocationArn": "string",
    "LocationUri": "string",
    "AuthenticationType": "SAS|NONE",
    "BlobType": "BLOCK",
    "AccessTier": "HOT|COOL|ARCHIVE",
    "AgentArns": ["string"],
    "CreationTime": "timestamp"
}
```

---

### 6.5 `update-location-object-storage`

Updates an object storage location configuration.

**Synopsis:**
```bash
aws datasync update-location-object-storage \
    --location-arn <value> \
    [--server-port <value>] \
    [--server-protocol <value>] \
    [--subdirectory <value>] \
    [--access-key <value>] \
    [--secret-key <value>] \
    [--agent-arns <value>] \
    [--server-certificate <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the object storage location |
| `--server-port` | No | integer | None | New server port |
| `--server-protocol` | No | string | None | `HTTPS` or `HTTP` |
| `--subdirectory` | No | string | None | New object prefix |
| `--access-key` | No | string | None | New access key |
| `--secret-key` | No | string | None | New secret key |
| `--agent-arns` | No | list(string) | None | New agent ARNs |
| `--server-certificate` | No | blob | None | New PEM certificate |

**Output:** None on success.

---

### 6.6 `update-location-azure-blob`

Updates an Azure Blob Storage location configuration.

**Synopsis:**
```bash
aws datasync update-location-azure-blob \
    --location-arn <value> \
    [--subdirectory <value>] \
    [--authentication-type <value>] \
    [--sas-configuration <value>] \
    [--blob-type <value>] \
    [--access-tier <value>] \
    [--agent-arns <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the Azure Blob location |
| `--subdirectory` | No | string | None | New virtual directory path |
| `--authentication-type` | No | string | None | `SAS` or `NONE` |
| `--sas-configuration` | No | structure | None | New SAS token config |
| `--blob-type` | No | string | None | `BLOCK` |
| `--access-tier` | No | string | None | `HOT`, `COOL`, or `ARCHIVE` |
| `--agent-arns` | No | list(string) | None | New agent ARNs |

**Output:** None on success.

---

### 6.7 `delete-location`

Deletes any transfer location.

**Synopsis:**
```bash
aws datasync delete-location \
    --location-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--location-arn` | **Yes** | string | -- | ARN of the location to delete |

**Output:** None on success.

---

### 6.8 `list-locations`

Lists all transfer locations. **Paginated operation.**

**Synopsis:**
```bash
aws datasync list-locations \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |
| `--filters` | No | list | None | Filter by LocationUri, LocationType, or CreationTime |

**Filter Structure (JSON):**
```json
[
    {
        "Name": "LocationUri|LocationType|CreationTime",
        "Values": ["string"],
        "Operator": "Equals|NotEquals|In|LessThan|GreaterThan|Contains|BeginsWith"
    }
]
```

**Output Schema:**
```json
{
    "Locations": [
        {
            "LocationArn": "string",
            "LocationUri": "string"
        }
    ],
    "NextToken": "string"
}
```
