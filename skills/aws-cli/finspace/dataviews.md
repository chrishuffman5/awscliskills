# Dataviews

### 4.1 `create-kx-dataview`

Creates a snapshot of kdb+ database data that is available on a cluster for querying. A dataview provides an optimized read path for a specific set of database paths and a specific changeset.

**Synopsis:**
```bash
aws finspace create-kx-dataview \
    --environment-id <value> \
    --database-name <value> \
    --dataview-name <value> \
    --az-mode <value> \
    [--availability-zone-id <value>] \
    [--changeset-id <value>] \
    [--segment-configurations <value>] \
    [--auto-update | --no-auto-update] \
    [--read-write | --no-read-write] \
    [--description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--database-name` | **Yes** | string | -- | Database name |
| `--dataview-name` | **Yes** | string | -- | Dataview name (3-63 chars) |
| `--az-mode` | **Yes** | string | -- | AZ mode: `SINGLE` or `MULTI` |
| `--availability-zone-id` | No | string | -- | AZ ID (required for SINGLE mode) |
| `--changeset-id` | No | string | None | Specific changeset to use |
| `--segment-configurations` | No | list | None | Segment configurations for data placement |
| `--auto-update` | No | boolean | false | Auto-update dataview when new changesets arrive |
| `--read-write` | No | boolean | false | Enable read-write access |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | Auto | Idempotency token |

**Segment Configuration:**
```json
[
    {
        "dbPaths": ["string"],
        "volumeName": "string",
        "onDemand": true|false
    }
]
```

**Output Schema:**
```json
{
    "dataviewName": "string",
    "databaseName": "string",
    "environmentId": "string",
    "azMode": "SINGLE|MULTI",
    "availabilityZoneId": "string",
    "changesetId": "string",
    "segmentConfigurations": [
        {
            "dbPaths": ["string"],
            "volumeName": "string",
            "onDemand": true|false
        }
    ],
    "description": "string",
    "autoUpdate": true|false,
    "readWrite": true|false,
    "createdTimestamp": "timestamp",
    "lastModifiedTimestamp": "timestamp",
    "status": "CREATING|ACTIVE|UPDATING|FAILED|DELETING"
}
```

---

### 4.2 `delete-kx-dataview`

Deletes a KX dataview.

**Synopsis:**
```bash
aws finspace delete-kx-dataview \
    --environment-id <value> \
    --database-name <value> \
    --dataview-name <value> \
    --client-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--database-name` | **Yes** | string | -- | Database name |
| `--dataview-name` | **Yes** | string | -- | Dataview name to delete |
| `--client-token` | **Yes** | string | -- | Idempotency token |

**Output:** None (HTTP 200 on success)

---

### 4.3 `get-kx-dataview`

Returns details of a specific KX dataview.

**Synopsis:**
```bash
aws finspace get-kx-dataview \
    --environment-id <value> \
    --database-name <value> \
    --dataview-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--database-name` | **Yes** | string | -- | Database name |
| `--dataview-name` | **Yes** | string | -- | Dataview name |

**Output Schema:**
```json
{
    "databaseName": "string",
    "dataviewName": "string",
    "azMode": "SINGLE|MULTI",
    "availabilityZoneId": "string",
    "changesetId": "string",
    "segmentConfigurations": [],
    "activeVersions": [
        {
            "changesetId": "string",
            "segmentConfigurations": [],
            "attachedClusters": ["string"],
            "createdTimestamp": "timestamp",
            "versionId": "string"
        }
    ],
    "status": "CREATING|ACTIVE|UPDATING|FAILED|DELETING",
    "description": "string",
    "autoUpdate": true|false,
    "readWrite": true|false,
    "environmentId": "string",
    "createdTimestamp": "timestamp",
    "lastModifiedTimestamp": "timestamp",
    "statusReason": "string"
}
```

---

### 4.4 `list-kx-dataviews`

Returns a list of all KX dataviews for a specific database. **Paginated operation.**

**Synopsis:**
```bash
aws finspace list-kx-dataviews \
    --environment-id <value> \
    --database-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--database-name` | **Yes** | string | -- | Database name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Maximum results per page |

**Output Schema:**
```json
{
    "kxDataviews": [
        {
            "environmentId": "string",
            "databaseName": "string",
            "dataviewName": "string",
            "azMode": "SINGLE|MULTI",
            "availabilityZoneId": "string",
            "changesetId": "string",
            "segmentConfigurations": [],
            "activeVersions": [],
            "status": "string",
            "description": "string",
            "autoUpdate": true|false,
            "readWrite": true|false,
            "createdTimestamp": "timestamp",
            "lastModifiedTimestamp": "timestamp",
            "statusReason": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.5 `update-kx-dataview`

Updates the configuration of a KX dataview. Can update the changeset, segment configurations, and other properties.

**Synopsis:**
```bash
aws finspace update-kx-dataview \
    --environment-id <value> \
    --database-name <value> \
    --dataview-name <value> \
    --client-token <value> \
    [--description <value>] \
    [--changeset-id <value>] \
    [--segment-configurations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--database-name` | **Yes** | string | -- | Database name |
| `--dataview-name` | **Yes** | string | -- | Dataview name |
| `--client-token` | **Yes** | string | -- | Idempotency token |
| `--description` | No | string | -- | New description |
| `--changeset-id` | No | string | -- | New changeset ID |
| `--segment-configurations` | No | list | -- | New segment configurations |

**Output Schema:** Same as `get-kx-dataview` output.
