# Disks

### 3.1 `create-disk`

Creates a block storage disk.

**Synopsis:**
```bash
aws lightsail create-disk \
    --disk-name <value> \
    --availability-zone <value> \
    --size-in-gb <value> \
    [--tags <value>] \
    [--add-ons <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--disk-name` | **Yes** | string | -- | Name for the disk |
| `--availability-zone` | **Yes** | string | -- | Availability zone (e.g., `us-east-1a`) |
| `--size-in-gb` | **Yes** | integer | -- | Size in GB (8 to 32768) |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |
| `--add-ons` | No | list | None | Add-on configurations (e.g., auto snapshots) |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Disk",
            "operationType": "CreateDisk",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 3.2 `create-disk-from-snapshot`

Creates a disk from a disk or instance snapshot.

**Synopsis:**
```bash
aws lightsail create-disk-from-snapshot \
    --disk-name <value> \
    --availability-zone <value> \
    --size-in-gb <value> \
    [--disk-snapshot-name <value>] \
    [--tags <value>] \
    [--add-ons <value>] \
    [--source-disk-name <value>] \
    [--restore-date <value>] \
    [--use-latest-restorable-auto-snapshot | --no-use-latest-restorable-auto-snapshot] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--disk-name` | **Yes** | string | -- | Name for the new disk |
| `--availability-zone` | **Yes** | string | -- | Availability zone |
| `--size-in-gb` | **Yes** | integer | -- | Size in GB |
| `--disk-snapshot-name` | No | string | None | Snapshot to create from |
| `--tags` | No | list | None | Tags |
| `--add-ons` | No | list | None | Add-on configurations |
| `--source-disk-name` | No | string | None | Source disk for auto snapshot restore |
| `--restore-date` | No | string | None | Auto snapshot date (YYYY-MM-DD) |
| `--use-latest-restorable-auto-snapshot` | No | boolean | false | Use latest auto snapshot |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Disk",
            "operationType": "CreateDiskFromSnapshot",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 3.3 `create-disk-snapshot`

Creates a snapshot of a block storage disk.

**Synopsis:**
```bash
aws lightsail create-disk-snapshot \
    --disk-snapshot-name <value> \
    [--disk-name <value>] \
    [--instance-name <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--disk-snapshot-name` | **Yes** | string | -- | Name for the snapshot |
| `--disk-name` | No | string | None | Name of the disk (required if not using `--instance-name`) |
| `--instance-name` | No | string | None | Instance name (creates snapshot of system disk) |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "DiskSnapshot",
            "operationType": "CreateDiskSnapshot",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 3.4 `delete-disk`

Deletes a block storage disk. The disk must be detached first.

**Synopsis:**
```bash
aws lightsail delete-disk \
    --disk-name <value> \
    [--force-delete-add-ons | --no-force-delete-add-ons] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--disk-name` | **Yes** | string | -- | Name of the disk to delete |
| `--force-delete-add-ons` | No | boolean | false | Force delete add-ons |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Disk",
            "operationType": "DeleteDisk",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 3.5 `delete-disk-snapshot`

Deletes a disk snapshot.

**Synopsis:**
```bash
aws lightsail delete-disk-snapshot \
    --disk-snapshot-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--disk-snapshot-name` | **Yes** | string | -- | Name of the disk snapshot to delete |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "DiskSnapshot",
            "operationType": "DeleteDiskSnapshot",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 3.6 `attach-disk`

Attaches a block storage disk to an instance.

**Synopsis:**
```bash
aws lightsail attach-disk \
    --disk-name <value> \
    --instance-name <value> \
    --disk-path <value> \
    [--auto-mounting | --no-auto-mounting] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--disk-name` | **Yes** | string | -- | Name of the disk to attach |
| `--instance-name` | **Yes** | string | -- | Name of the target instance |
| `--disk-path` | **Yes** | string | -- | Disk path (e.g., `/dev/xvdf`) |
| `--auto-mounting` | No | boolean | None | Enable auto mounting |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Disk",
            "operationType": "AttachDisk",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 3.7 `detach-disk`

Detaches a block storage disk from an instance.

**Synopsis:**
```bash
aws lightsail detach-disk \
    --disk-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--disk-name` | **Yes** | string | -- | Name of the disk to detach |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Disk",
            "operationType": "DetachDisk",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 3.8 `get-disk`

Returns information about a specific block storage disk.

**Synopsis:**
```bash
aws lightsail get-disk \
    --disk-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--disk-name` | **Yes** | string | -- | Name of the disk |

**Output Schema:**
```json
{
    "disk": {
        "name": "string",
        "arn": "string",
        "supportCode": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "Disk",
        "tags": [
            {
                "key": "string",
                "value": "string"
            }
        ],
        "addOns": [],
        "sizeInGb": "integer",
        "isSystemDisk": true|false,
        "iops": "integer",
        "path": "string",
        "state": "pending|error|available|in-use|unknown",
        "attachedTo": "string",
        "isAttached": true|false,
        "attachmentState": "string",
        "gbInUse": "integer",
        "autoMountStatus": "Failed|Pending|Mounted|NotMounted"
    }
}
```

---

### 3.9 `get-disks`

Returns information about all block storage disks. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-disks \
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
    "disks": [
        {
            "name": "string",
            "arn": "string",
            "sizeInGb": "integer",
            "state": "pending|error|available|in-use|unknown",
            "attachedTo": "string",
            "isAttached": true|false
        }
    ],
    "nextPageToken": "string"
}
```

---

### 3.10 `get-disk-snapshot`

Returns information about a specific disk snapshot.

**Synopsis:**
```bash
aws lightsail get-disk-snapshot \
    --disk-snapshot-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--disk-snapshot-name` | **Yes** | string | -- | Name of the disk snapshot |

**Output Schema:**
```json
{
    "diskSnapshot": {
        "name": "string",
        "arn": "string",
        "supportCode": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "DiskSnapshot",
        "tags": [],
        "sizeInGb": "integer",
        "state": "pending|completed|error",
        "progress": "string",
        "fromDiskName": "string",
        "fromDiskArn": "string",
        "fromInstanceName": "string",
        "fromInstanceArn": "string",
        "isFromAutoSnapshot": true|false
    }
}
```

---

### 3.11 `get-disk-snapshots`

Returns all disk snapshots. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-disk-snapshots \
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
    "diskSnapshots": [
        {
            "name": "string",
            "arn": "string",
            "sizeInGb": "integer",
            "state": "pending|completed|error",
            "fromDiskName": "string",
            "createdAt": "timestamp"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 3.12 `get-auto-snapshots`

Returns auto snapshot information for a resource.

**Synopsis:**
```bash
aws lightsail get-auto-snapshots \
    --resource-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | Name of the resource (instance or disk) |

**Output Schema:**
```json
{
    "resourceName": "string",
    "resourceType": "Instance|Disk",
    "autoSnapshots": [
        {
            "date": "string",
            "createdAt": "timestamp",
            "status": "Success|Failed|InProgress",
            "fromAttachedDisks": [
                {
                    "path": "string",
                    "sizeInGb": "integer"
                }
            ]
        }
    ]
}
```

---

### 3.13 `delete-auto-snapshot`

Deletes an automatic snapshot for a resource.

**Synopsis:**
```bash
aws lightsail delete-auto-snapshot \
    --resource-name <value> \
    --date <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | Name of the resource |
| `--date` | **Yes** | string | -- | Date of the auto snapshot (YYYY-MM-DD) |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Instance|Disk",
            "operationType": "DeleteAutoSnapshot",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 3.14 `enable-add-on`

Enables an add-on (e.g., auto snapshots) for a resource.

**Synopsis:**
```bash
aws lightsail enable-add-on \
    --resource-name <value> \
    --add-on-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | Name of the resource |
| `--add-on-request` | **Yes** | structure | -- | Add-on configuration. Shorthand: `addOnType=AutoSnapshot,autoSnapshotAddOnRequest={snapshotTimeOfDay=string}` |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Instance|Disk",
            "operationType": "EnableAddOn",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 3.15 `disable-add-on`

Disables an add-on for a resource.

**Synopsis:**
```bash
aws lightsail disable-add-on \
    --add-on-type <value> \
    --resource-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--add-on-type` | **Yes** | string | -- | Add-on type: `AutoSnapshot`, `StopInstanceOnIdle` |
| `--resource-name` | **Yes** | string | -- | Name of the resource |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Instance|Disk",
            "operationType": "DisableAddOn",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```
