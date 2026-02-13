# Volumes

### 7.1 `create-kx-volume`

Creates a new volume with a specific amount of throughput and storage capacity. A volume is a fixed-capacity storage resource used by KX dataviews and clusters.

**Synopsis:**
```bash
aws finspace create-kx-volume \
    --environment-id <value> \
    --volume-type <value> \
    --volume-name <value> \
    --az-mode <value> \
    --availability-zone-ids <value> \
    [--description <value>] \
    [--nas1-configuration <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--volume-type` | **Yes** | string | -- | Volume type: `NAS_1` |
| `--volume-name` | **Yes** | string | -- | Volume name (3-63 chars) |
| `--az-mode` | **Yes** | string | -- | AZ mode: `SINGLE` or `MULTI` |
| `--availability-zone-ids` | **Yes** | list(string) | -- | List of AZ IDs |
| `--description` | No | string | None | Description |
| `--nas1-configuration` | No | structure | -- | NAS1 volume configuration |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | Auto | Idempotency token |

**NAS1 Configuration:**
```json
{
    "type": "SSD_1000|SSD_250|HDD_12",
    "size": "integer"
}
```

| Type | Description | Min Size | Max Size |
|------|-------------|----------|----------|
| `SSD_1000` | SSD with 1000 MB/s throughput | 1200 GB | 33600 GB |
| `SSD_250` | SSD with 250 MB/s throughput | 1200 GB | 33600 GB |
| `HDD_12` | HDD with 12 MB/s throughput | 6000 GB | 33600 GB |

**Output Schema:**
```json
{
    "environmentId": "string",
    "volumeName": "string",
    "volumeType": "NAS_1",
    "volumeArn": "string",
    "nas1Configuration": {
        "type": "SSD_1000|SSD_250|HDD_12",
        "size": "integer"
    },
    "status": "CREATING|CREATE_FAILED|ACTIVE|UPDATING|UPDATED|UPDATE_FAILED|DELETING|DELETED|DELETE_FAILED",
    "statusReason": "string",
    "azMode": "SINGLE|MULTI",
    "description": "string",
    "availabilityZoneIds": ["string"],
    "createdTimestamp": "timestamp"
}
```

---

### 7.2 `delete-kx-volume`

Deletes a KX volume. The volume must not be attached to any dataviews or clusters.

**Synopsis:**
```bash
aws finspace delete-kx-volume \
    --environment-id <value> \
    --volume-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--volume-name` | **Yes** | string | -- | Volume name to delete |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None (HTTP 200 on success)

---

### 7.3 `get-kx-volume`

Returns details of a specific KX volume.

**Synopsis:**
```bash
aws finspace get-kx-volume \
    --environment-id <value> \
    --volume-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--volume-name` | **Yes** | string | -- | Volume name |

**Output Schema:**
```json
{
    "environmentId": "string",
    "volumeName": "string",
    "volumeType": "NAS_1",
    "volumeArn": "string",
    "nas1Configuration": {
        "type": "SSD_1000|SSD_250|HDD_12",
        "size": "integer"
    },
    "status": "CREATING|CREATE_FAILED|ACTIVE|UPDATING|UPDATED|UPDATE_FAILED|DELETING|DELETED|DELETE_FAILED",
    "statusReason": "string",
    "azMode": "SINGLE|MULTI",
    "description": "string",
    "availabilityZoneIds": ["string"],
    "createdTimestamp": "timestamp",
    "lastModifiedTimestamp": "timestamp",
    "attachedClusters": [
        {
            "clusterName": "string",
            "clusterType": "HDB|RDB|GATEWAY|GP|TICKERPLANT",
            "clusterStatus": "string"
        }
    ]
}
```

---

### 7.4 `list-kx-volumes`

Returns a list of all KX volumes in the specified environment. **Paginated operation.**

**Synopsis:**
```bash
aws finspace list-kx-volumes \
    --environment-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--volume-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--max-results` | No | integer | None | Maximum results per page |
| `--next-token` | No | string | None | Pagination token |
| `--volume-type` | No | string | All | Filter by volume type |

**Output Schema:**
```json
{
    "kxVolumeSummaries": [
        {
            "volumeName": "string",
            "volumeType": "NAS_1",
            "status": "string",
            "statusReason": "string",
            "azMode": "SINGLE|MULTI",
            "description": "string",
            "availabilityZoneIds": ["string"],
            "createdTimestamp": "timestamp",
            "lastModifiedTimestamp": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.5 `update-kx-volume`

Updates the configuration of a KX volume. Can modify the NAS1 storage type or description.

**Synopsis:**
```bash
aws finspace update-kx-volume \
    --environment-id <value> \
    --volume-name <value> \
    [--description <value>] \
    [--nas1-configuration <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--volume-name` | **Yes** | string | -- | Volume name |
| `--description` | No | string | -- | New description |
| `--nas1-configuration` | No | structure | -- | Updated NAS1 configuration |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:** Same as `get-kx-volume` output.
