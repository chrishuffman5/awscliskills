# WorkSpaces

### 1.1 `create-workspaces`

Creates one or more WorkSpaces. Supports creating up to 25 WorkSpaces in a single request.

**Synopsis:**
```bash
aws workspaces create-workspaces \
    --workspaces <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspaces` | **Yes** | list | -- | List of WorkSpaces to create (max 25). Each requires DirectoryId, UserName, BundleId |

**WorkSpace Request Structure:**
```json
{
    "DirectoryId": "string",
    "UserName": "string",
    "BundleId": "string",
    "VolumeEncryptionKey": "string",
    "UserVolumeEncryptionEnabled": true|false,
    "RootVolumeEncryptionEnabled": true|false,
    "WorkspaceProperties": {
        "RunningMode": "AUTO_STOP|ALWAYS_ON|MANUAL",
        "RunningModeAutoStopTimeoutInMinutes": "integer",
        "RootVolumeSizeGib": "integer",
        "UserVolumeSizeGib": "integer",
        "ComputeTypeName": "VALUE|STANDARD|PERFORMANCE|POWER|GRAPHICS|POWERPRO|GRAPHICSPRO|GRAPHICS_G4DN|GRAPHICSPRO_G4DN",
        "Protocols": ["string"],
        "OperatingSystemName": "string"
    },
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

**Output Schema:**
```json
{
    "FailedRequests": [
        {
            "WorkspaceRequest": {
                "DirectoryId": "string",
                "UserName": "string",
                "BundleId": "string",
                "VolumeEncryptionKey": "string",
                "UserVolumeEncryptionEnabled": true|false,
                "RootVolumeEncryptionEnabled": true|false,
                "WorkspaceProperties": {},
                "Tags": []
            },
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ],
    "PendingRequests": [
        {
            "WorkspaceId": "string",
            "DirectoryId": "string",
            "UserName": "string",
            "IpAddress": "string",
            "State": "PENDING|AVAILABLE|IMPAIRED|UNHEALTHY|REBOOTING|STARTING|REBUILDING|RESTORING|MAINTENANCE|ADMIN_MAINTENANCE|TERMINATING|TERMINATED|SUSPENDED|UPDATING|STOPPING|STOPPED|ERROR",
            "BundleId": "string",
            "SubnetId": "string",
            "ErrorMessage": "string",
            "ErrorCode": "string",
            "ComputerName": "string",
            "VolumeEncryptionKey": "string",
            "UserVolumeEncryptionEnabled": true|false,
            "RootVolumeEncryptionEnabled": true|false,
            "WorkspaceName": "string",
            "WorkspaceProperties": {
                "RunningMode": "string",
                "RunningModeAutoStopTimeoutInMinutes": "integer",
                "RootVolumeSizeGib": "integer",
                "UserVolumeSizeGib": "integer",
                "ComputeTypeName": "string",
                "Protocols": ["string"],
                "OperatingSystemName": "string"
            },
            "Tags": []
        }
    ]
}
```

---

### 1.2 `terminate-workspaces`

Terminates one or more WorkSpaces. Terminated WorkSpaces cannot be recovered.

**Synopsis:**
```bash
aws workspaces terminate-workspaces \
    --terminate-workspace-requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--terminate-workspace-requests` | **Yes** | list | -- | List of WorkSpaces to terminate. Shorthand: `WorkspaceId=string ...` |

**Output Schema:**
```json
{
    "FailedRequests": [
        {
            "WorkspaceId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 1.3 `reboot-workspaces`

Reboots one or more WorkSpaces. The WorkSpace must be in the AVAILABLE, IMPAIRED, UNHEALTHY, or ERROR state.

**Synopsis:**
```bash
aws workspaces reboot-workspaces \
    --reboot-workspace-requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reboot-workspace-requests` | **Yes** | list | -- | List of WorkSpaces to reboot. Shorthand: `WorkspaceId=string ...` |

**Output Schema:**
```json
{
    "FailedRequests": [
        {
            "WorkspaceId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 1.4 `rebuild-workspaces`

Rebuilds one or more WorkSpaces. Rebuilding recreates the WorkSpace from the last available snapshot. Data on the user volume (D: drive) is preserved.

**Synopsis:**
```bash
aws workspaces rebuild-workspaces \
    --rebuild-workspace-requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rebuild-workspace-requests` | **Yes** | list | -- | List of WorkSpaces to rebuild. Shorthand: `WorkspaceId=string ...` |

**Output Schema:**
```json
{
    "FailedRequests": [
        {
            "WorkspaceId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 1.5 `start-workspaces`

Starts one or more stopped WorkSpaces.

**Synopsis:**
```bash
aws workspaces start-workspaces \
    --start-workspace-requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-workspace-requests` | **Yes** | list | -- | List of WorkSpaces to start. Shorthand: `WorkspaceId=string ...` |

**Output Schema:**
```json
{
    "FailedRequests": [
        {
            "WorkspaceId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 1.6 `stop-workspaces`

Stops one or more running WorkSpaces.

**Synopsis:**
```bash
aws workspaces stop-workspaces \
    --stop-workspace-requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stop-workspace-requests` | **Yes** | list | -- | List of WorkSpaces to stop. Shorthand: `WorkspaceId=string ...` |

**Output Schema:**
```json
{
    "FailedRequests": [
        {
            "WorkspaceId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 1.7 `describe-workspaces`

Describes the specified WorkSpaces or all WorkSpaces. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces describe-workspaces \
    [--workspace-ids <value>] \
    [--directory-id <value>] \
    [--user-name <value>] \
    [--bundle-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-ids` | No | list(string) | None | One or more WorkSpace IDs (max 25) |
| `--directory-id` | No | string | None | Filter by directory ID |
| `--user-name` | No | string | None | Filter by user name (requires --directory-id) |
| `--bundle-id` | No | string | None | Filter by bundle ID |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Workspaces": [
        {
            "WorkspaceId": "string",
            "DirectoryId": "string",
            "UserName": "string",
            "IpAddress": "string",
            "State": "PENDING|AVAILABLE|IMPAIRED|UNHEALTHY|REBOOTING|STARTING|REBUILDING|RESTORING|MAINTENANCE|ADMIN_MAINTENANCE|TERMINATING|TERMINATED|SUSPENDED|UPDATING|STOPPING|STOPPED|ERROR",
            "BundleId": "string",
            "SubnetId": "string",
            "ErrorMessage": "string",
            "ErrorCode": "string",
            "ComputerName": "string",
            "VolumeEncryptionKey": "string",
            "UserVolumeEncryptionEnabled": true|false,
            "RootVolumeEncryptionEnabled": true|false,
            "WorkspaceName": "string",
            "WorkspaceProperties": {
                "RunningMode": "AUTO_STOP|ALWAYS_ON|MANUAL",
                "RunningModeAutoStopTimeoutInMinutes": "integer",
                "RootVolumeSizeGib": "integer",
                "UserVolumeSizeGib": "integer",
                "ComputeTypeName": "string",
                "Protocols": ["string"],
                "OperatingSystemName": "string"
            },
            "ModificationStates": [
                {
                    "Resource": "ROOT_VOLUME|USER_VOLUME|COMPUTE_TYPE",
                    "State": "UPDATE_INITIATED|UPDATE_IN_PROGRESS"
                }
            ],
            "RelatedWorkspaces": [
                {
                    "WorkspaceId": "string",
                    "Region": "string",
                    "State": "string",
                    "Type": "PRIMARY|STANDBY"
                }
            ],
            "DataReplicationSettings": {
                "DataReplication": "NO_REPLICATION|PRIMARY_AS_SOURCE",
                "RecoverySnapshotTime": "timestamp"
            },
            "StandbyWorkspacesProperties": []
        }
    ],
    "NextToken": "string"
}
```

---

### 1.8 `describe-workspaces-connection-status`

Describes the connection status of one or more WorkSpaces. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces describe-workspaces-connection-status \
    [--workspace-ids <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-ids` | No | list(string) | None | One or more WorkSpace IDs (max 25) |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "WorkspacesConnectionStatus": [
        {
            "WorkspaceId": "string",
            "ConnectionState": "CONNECTED|DISCONNECTED|UNKNOWN",
            "ConnectionStateCheckTimestamp": "timestamp",
            "LastKnownUserConnectionTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.9 `modify-workspace-properties`

Modifies the properties of the specified WorkSpace.

**Synopsis:**
```bash
aws workspaces modify-workspace-properties \
    --workspace-id <value> \
    [--workspace-properties <value>] \
    [--data-replication <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The WorkSpace ID |
| `--workspace-properties` | No | structure | None | WorkSpace properties to modify |
| `--data-replication` | No | string | None | Data replication setting: `NO_REPLICATION`, `PRIMARY_AS_SOURCE` |

**WorkSpace Properties Structure:**
```json
{
    "RunningMode": "AUTO_STOP|ALWAYS_ON|MANUAL",
    "RunningModeAutoStopTimeoutInMinutes": "integer",
    "RootVolumeSizeGib": "integer",
    "UserVolumeSizeGib": "integer",
    "ComputeTypeName": "VALUE|STANDARD|PERFORMANCE|POWER|GRAPHICS|POWERPRO|GRAPHICSPRO|GRAPHICS_G4DN|GRAPHICSPRO_G4DN",
    "Protocols": ["string"],
    "OperatingSystemName": "string"
}
```

**Output Schema:**
```json
{}
```

---

### 1.10 `modify-workspace-state`

Sets the state of the specified WorkSpace.

**Synopsis:**
```bash
aws workspaces modify-workspace-state \
    --workspace-id <value> \
    --workspace-state <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The WorkSpace ID |
| `--workspace-state` | **Yes** | string | -- | The WorkSpace state: `AVAILABLE`, `ADMIN_MAINTENANCE` |

**Output Schema:**
```json
{}
```

---

### 1.11 `restore-workspace`

Restores the specified WorkSpace to its last known healthy state. Only available for WorkSpaces with Windows or Amazon Linux operating systems.

**Synopsis:**
```bash
aws workspaces restore-workspace \
    --workspace-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The WorkSpace ID to restore |

**Output Schema:**
```json
{}
```

---

### 1.12 `migrate-workspace`

Migrates a WorkSpace from one bundle to another while retaining data on the user volume.

**Synopsis:**
```bash
aws workspaces migrate-workspace \
    --source-workspace-id <value> \
    --bundle-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-workspace-id` | **Yes** | string | -- | The WorkSpace ID to migrate |
| `--bundle-id` | **Yes** | string | -- | The target bundle ID |

**Output Schema:**
```json
{
    "SourceWorkspaceId": "string",
    "TargetWorkspaceId": "string"
}
```
