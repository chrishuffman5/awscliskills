# File System Associations

### 8.1 `associate-file-system`

Associates an Amazon FSx for Windows File Server file system with an FSx File Gateway. Provides SMB access to FSx file systems through the gateway.

**Synopsis:**
```bash
aws storagegateway associate-file-system \
    --user-name <value> \
    --password <value> \
    --client-token <value> \
    --gateway-arn <value> \
    --location-arn <value> \
    [--tags <value>] \
    [--audit-destination-arn <value>] \
    [--cache-attributes <value>] \
    [--endpoint-network-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | AD user with FSx root share access (1-1024 chars) |
| `--password` | **Yes** | string | -- | AD user password (1-1024 chars) |
| `--client-token` | **Yes** | string | -- | Idempotency token (5-100 chars) |
| `--gateway-arn` | **Yes** | string | -- | FSx File Gateway ARN (50-500 chars) |
| `--location-arn` | **Yes** | string | -- | FSx file system ARN (8-512 chars) |
| `--tags` | No | list | None | Up to 50 key-value tags |
| `--audit-destination-arn` | No | string | None | Audit log destination ARN |
| `--cache-attributes` | No | structure | None | Cache stale timeout in seconds (0, 300-2592000) |
| `--endpoint-network-configuration` | No | structure | None | IP address for multiple file system associations |

**Output Schema:**
```json
{
    "FileSystemAssociationARN": "string"
}
```

---

### 8.2 `disassociate-file-system`

Disassociates an Amazon FSx file system from an FSx File Gateway.

**Synopsis:**
```bash
aws storagegateway disassociate-file-system \
    --file-system-association-arn <value> \
    [--force-delete | --no-force-delete] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-association-arn` | **Yes** | string | -- | File system association ARN (50-500 chars) |
| `--force-delete` | No | boolean | false | Force disassociation |

**Output Schema:**
```json
{
    "FileSystemAssociationARN": "string"
}
```

---

### 8.3 `describe-file-system-associations`

Returns information about file system associations for an FSx File Gateway.

**Synopsis:**
```bash
aws storagegateway describe-file-system-associations \
    --file-system-association-arn-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-association-arn-list` | **Yes** | list(string) | -- | List of file system association ARNs (1-10 items) |

**Output Schema:**
```json
{
    "FileSystemAssociationInfoList": [
        {
            "FileSystemAssociationARN": "string",
            "LocationARN": "string",
            "FileSystemAssociationStatus": "AVAILABLE|CREATING|DELETING|FORCE_DELETING|UPDATING|ERROR",
            "AuditDestinationARN": "string",
            "GatewayARN": "string",
            "Tags": [{"Key": "string", "Value": "string"}],
            "CacheAttributes": {
                "CacheStaleTimeoutInSeconds": "integer"
            },
            "EndpointNetworkConfiguration": {
                "IpAddresses": ["string"]
            },
            "FileSystemAssociationStatusDetails": [
                {
                    "ErrorCode": "string"
                }
            ]
        }
    ]
}
```

---

### 8.4 `list-file-system-associations`

Lists file system associations on a gateway. **Paginated operation.**

**Synopsis:**
```bash
aws storagegateway list-file-system-associations \
    [--gateway-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | No | string | None | Gateway ARN to filter results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "NextMarker": "string",
    "FileSystemAssociationSummaryList": [
        {
            "FileSystemAssociationId": "string",
            "FileSystemAssociationARN": "string",
            "FileSystemAssociationStatus": "string",
            "GatewayARN": "string"
        }
    ]
}
```

---

### 8.5 `update-file-system-association`

Updates a file system association, including cache attributes and audit log configuration.

**Synopsis:**
```bash
aws storagegateway update-file-system-association \
    --file-system-association-arn <value> \
    [--user-name <value>] \
    [--password <value>] \
    [--audit-destination-arn <value>] \
    [--cache-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-system-association-arn` | **Yes** | string | -- | File system association ARN |
| `--user-name` | No | string | None | Updated AD user name |
| `--password` | No | string | None | Updated AD password |
| `--audit-destination-arn` | No | string | None | Audit log destination ARN |
| `--cache-attributes` | No | structure | None | Cache stale timeout |

**Output Schema:**
```json
{
    "FileSystemAssociationARN": "string"
}
```
