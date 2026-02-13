# Instance Snapshots

### 2.1 `create-instance-snapshot`

Creates a snapshot of a specific Lightsail instance.

**Synopsis:**
```bash
aws lightsail create-instance-snapshot \
    --instance-snapshot-name <value> \
    --instance-name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-snapshot-name` | **Yes** | string | -- | Name for the snapshot |
| `--instance-name` | **Yes** | string | -- | Name of the source instance |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "InstanceSnapshot",
            "operationType": "CreateInstanceSnapshot",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 2.2 `delete-instance-snapshot`

Deletes a specific instance snapshot.

**Synopsis:**
```bash
aws lightsail delete-instance-snapshot \
    --instance-snapshot-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-snapshot-name` | **Yes** | string | -- | Name of the snapshot to delete |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "InstanceSnapshot",
            "operationType": "DeleteInstanceSnapshot",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 2.3 `get-instance-snapshot`

Returns information about a specific instance snapshot.

**Synopsis:**
```bash
aws lightsail get-instance-snapshot \
    --instance-snapshot-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-snapshot-name` | **Yes** | string | -- | Name of the snapshot |

**Output Schema:**
```json
{
    "instanceSnapshot": {
        "name": "string",
        "arn": "string",
        "supportCode": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "InstanceSnapshot",
        "tags": [
            {
                "key": "string",
                "value": "string"
            }
        ],
        "state": "pending|error|available",
        "progress": "string",
        "fromAttachedDisks": [
            {
                "name": "string",
                "arn": "string",
                "sizeInGb": "integer",
                "isSystemDisk": true|false,
                "path": "string"
            }
        ],
        "fromInstanceName": "string",
        "fromInstanceArn": "string",
        "fromBlueprintId": "string",
        "fromBundleId": "string",
        "isFromAutoSnapshot": true|false,
        "sizeInGb": "integer"
    }
}
```

---

### 2.4 `get-instance-snapshots`

Returns all instance snapshots. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-instance-snapshots \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token from previous response |

**Output Schema:**
```json
{
    "instanceSnapshots": [
        {
            "name": "string",
            "arn": "string",
            "state": "pending|error|available",
            "fromInstanceName": "string",
            "fromBlueprintId": "string",
            "fromBundleId": "string",
            "sizeInGb": "integer",
            "createdAt": "timestamp"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 2.5 `export-snapshot`

Exports a Lightsail instance or disk snapshot to Amazon EC2.

**Synopsis:**
```bash
aws lightsail export-snapshot \
    --source-snapshot-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-snapshot-name` | **Yes** | string | -- | Name of the snapshot to export |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "InstanceSnapshot|DiskSnapshot",
            "operationType": "ExportSnapshot",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 2.6 `get-export-snapshot-records`

Returns export snapshot records. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-export-snapshot-records \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "exportSnapshotRecords": [
        {
            "name": "string",
            "arn": "string",
            "createdAt": "timestamp",
            "location": {
                "availabilityZone": "string",
                "regionName": "string"
            },
            "resourceType": "ExportSnapshotRecord",
            "state": "Started|Succeeded|Failed",
            "sourceInfo": {
                "resourceType": "InstanceSnapshot|DiskSnapshot",
                "createdAt": "timestamp",
                "name": "string",
                "arn": "string",
                "fromResourceName": "string",
                "fromResourceArn": "string"
            },
            "destinationInfo": {
                "id": "string",
                "service": "string"
            }
        }
    ],
    "nextPageToken": "string"
}
```

---

### 2.7 `copy-snapshot`

Copies a snapshot from one AWS region to another.

**Synopsis:**
```bash
aws lightsail copy-snapshot \
    --target-snapshot-name <value> \
    --source-region <value> \
    [--source-snapshot-name <value>] \
    [--source-resource-name <value>] \
    [--restore-date <value>] \
    [--use-latest-restorable-auto-snapshot | --no-use-latest-restorable-auto-snapshot] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-snapshot-name` | **Yes** | string | -- | Name for the new snapshot in the target region |
| `--source-region` | **Yes** | string | -- | Source region (e.g., `us-east-1`) |
| `--source-snapshot-name` | No | string | None | Name of the source snapshot |
| `--source-resource-name` | No | string | None | Source resource for auto snapshot copy |
| `--restore-date` | No | string | None | Date of auto snapshot (YYYY-MM-DD) |
| `--use-latest-restorable-auto-snapshot` | No | boolean | false | Use latest auto snapshot |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "InstanceSnapshot|DiskSnapshot",
            "operationType": "CopySnapshot",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 2.8 `create-cloud-formation-stack`

Creates an AWS CloudFormation stack to create EC2 resources from an exported Lightsail snapshot.

**Synopsis:**
```bash
aws lightsail create-cloud-formation-stack \
    --instances <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instances` | **Yes** | list | -- | Instance entry list. Shorthand: `sourceName=string,instanceType=string,portInfoSource=DEFAULT\|INSTANCE\|NONE\|CLOSED,userData=string,availabilityZone=string ...` |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "CloudFormationStackRecord",
            "operationType": "CreateCloudFormationStack",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 2.9 `get-cloud-formation-stack-records`

Returns CloudFormation stack records. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-cloud-formation-stack-records \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "cloudFormationStackRecords": [
        {
            "name": "string",
            "arn": "string",
            "createdAt": "timestamp",
            "location": {
                "availabilityZone": "string",
                "regionName": "string"
            },
            "resourceType": "CloudFormationStackRecord",
            "state": "Started|Succeeded|Failed",
            "sourceInfo": [
                {
                    "resourceType": "ExportSnapshotRecord",
                    "name": "string",
                    "arn": "string"
                }
            ],
            "destinationInfo": {
                "id": "string",
                "service": "string"
            }
        }
    ],
    "nextPageToken": "string"
}
```
