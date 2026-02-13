# Source Servers

### 1.1 `describe-source-servers`

Lists all source servers or filters them based on criteria. **Paginated operation.**

**Synopsis:**
```bash
aws drs describe-source-servers \
    --filters <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | **Yes** | structure | -- | Filters for source servers |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items to return |

**Filters Structure:**
```json
{
    "sourceServerIDs": ["string"],
    "hardwareId": "string",
    "stagingAccountIDs": ["string"]
}
```

**Output Schema:**
```json
{
    "items": [
        {
            "sourceServerID": "string",
            "arn": "string",
            "recoveryInstanceId": "string",
            "lastLaunchResult": "NOT_STARTED|PENDING|SUCCEEDED|FAILED",
            "dataReplicationInfo": {
                "dataReplicationState": "STOPPED|INITIATING|INITIAL_SYNC|BACKLOG|CREATING_SNAPSHOT|CONTINUOUS|PAUSED|RESCAN|STALLED|DISCONNECTED",
                "dataReplicationInitiation": {
                    "startDateTime": "string",
                    "nextAttemptDateTime": "string",
                    "steps": [
                        {
                            "name": "string",
                            "status": "NOT_STARTED|IN_PROGRESS|SUCCEEDED|FAILED|SKIPPED"
                        }
                    ]
                },
                "etaDateTime": "string",
                "replicatedDisks": [
                    {
                        "deviceName": "string",
                        "totalStorageBytes": "long",
                        "replicatedStorageBytes": "long",
                        "rescannedStorageBytes": "long",
                        "backloggedStorageBytes": "long"
                    }
                ],
                "lagDuration": "string",
                "dataReplicationError": {
                    "error": "string",
                    "rawError": "string"
                },
                "stagingAvailabilityZone": "string"
            },
            "lifeCycle": {
                "addedToServiceDateTime": "string",
                "firstByteDateTime": "string",
                "elapsedReplicationDuration": "string",
                "lastSeenByServiceDateTime": "string",
                "lastLaunch": {
                    "initiated": {
                        "apiCallDateTime": "string",
                        "jobID": "string",
                        "type": "RECOVERY|DRILL"
                    },
                    "status": "PENDING|IN_PROGRESS|LAUNCHED|FAILED|TERMINATED"
                }
            },
            "sourceProperties": {
                "lastUpdatedDateTime": "string",
                "recommendedInstanceType": "string",
                "identificationHints": {
                    "fqdn": "string",
                    "hostname": "string",
                    "vmWareUuid": "string",
                    "awsInstanceID": "string"
                },
                "networkInterfaces": [
                    {
                        "macAddress": "string",
                        "ips": ["string"],
                        "isPrimary": "boolean"
                    }
                ],
                "disks": [
                    {
                        "deviceName": "string",
                        "bytes": "long"
                    }
                ],
                "cpus": [
                    {
                        "cores": "long",
                        "modelName": "string"
                    }
                ],
                "ramBytes": "long",
                "os": {
                    "fullString": "string"
                },
                "supportsNitroInstances": "boolean"
            },
            "stagingArea": {
                "status": "EXTENDED|EXTENSION_ERROR|NOT_EXTENDED",
                "stagingAccountID": "string",
                "stagingSourceServerArn": "string",
                "errorMessage": "string"
            },
            "tags": {
                "string": "string"
            },
            "replicationDirection": "FAILOVER|FAILBACK",
            "reversedDirectionSourceServerArn": "string",
            "sourceCloudProperties": {
                "originAccountID": "string",
                "originRegion": "string",
                "originAvailabilityZone": "string"
            },
            "agentVersion": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.2 `delete-source-server`

Deletes a single source server by ID. The source server must be disconnected first.

**Synopsis:**
```bash
aws drs delete-source-server \
    --source-server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID to delete |

**Output Schema:**
```json
{}
```

---

### 1.3 `disconnect-source-server`

Disconnects a specific source server from DRS. This stops replication for the source server and the data replication agent running on it.

**Synopsis:**
```bash
aws drs disconnect-source-server \
    --source-server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID to disconnect |

**Output Schema:**
```json
{
    "sourceServerID": "string",
    "arn": "string",
    "recoveryInstanceId": "string",
    "lastLaunchResult": "NOT_STARTED|PENDING|SUCCEEDED|FAILED",
    "dataReplicationInfo": {},
    "lifeCycle": {},
    "sourceProperties": {},
    "stagingArea": {},
    "tags": {},
    "replicationDirection": "FAILOVER|FAILBACK",
    "reversedDirectionSourceServerArn": "string",
    "sourceCloudProperties": {},
    "agentVersion": "string"
}
```

---

### 1.4 `create-extended-source-server`

Create an extended source server in the target account.

**Synopsis:**
```bash
aws drs create-extended-source-server \
    --source-server-arn <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-arn` | **Yes** | string | -- | ARN of the source server in the staging account |
| `--tags` | No | map | None | Tags for the extended source server |

**Output Schema:**
```json
{
    "sourceServer": {
        "sourceServerID": "string",
        "arn": "string",
        "recoveryInstanceId": "string",
        "lastLaunchResult": "string",
        "dataReplicationInfo": {},
        "lifeCycle": {},
        "sourceProperties": {},
        "stagingArea": {},
        "tags": {},
        "replicationDirection": "FAILOVER|FAILBACK",
        "reversedDirectionSourceServerArn": "string",
        "sourceCloudProperties": {},
        "agentVersion": "string"
    }
}
```

---

### 1.5 `list-extensible-source-servers`

Returns a list of source servers on a staging account that are extensible. **Paginated operation.**

**Synopsis:**
```bash
aws drs list-extensible-source-servers \
    --staging-account-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--staging-account-id` | **Yes** | string | -- | Staging account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "items": [
        {
            "sourceServerID": "string",
            "arn": "string",
            "recoveryInstanceId": "string",
            "lastLaunchResult": "string",
            "dataReplicationInfo": {},
            "lifeCycle": {},
            "sourceProperties": {},
            "stagingArea": {},
            "tags": {},
            "replicationDirection": "string",
            "reversedDirectionSourceServerArn": "string",
            "sourceCloudProperties": {},
            "agentVersion": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.6 `start-replication`

Starts replication for a stopped source server. This action requires the source server to have the DRS agent installed.

**Synopsis:**
```bash
aws drs start-replication \
    --source-server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |

**Output Schema:**
```json
{
    "sourceServer": {
        "sourceServerID": "string",
        "arn": "string",
        "recoveryInstanceId": "string",
        "lastLaunchResult": "string",
        "dataReplicationInfo": {},
        "lifeCycle": {},
        "sourceProperties": {},
        "stagingArea": {},
        "tags": {},
        "replicationDirection": "FAILOVER|FAILBACK",
        "reversedDirectionSourceServerArn": "string",
        "sourceCloudProperties": {},
        "agentVersion": "string"
    }
}
```

---

### 1.7 `stop-replication`

Stops replication for a source server. This action stops any ongoing replication and causes the source server to no longer be protected.

**Synopsis:**
```bash
aws drs stop-replication \
    --source-server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |

**Output Schema:**
```json
{
    "sourceServer": {
        "sourceServerID": "string",
        "arn": "string",
        "recoveryInstanceId": "string",
        "lastLaunchResult": "string",
        "dataReplicationInfo": {},
        "lifeCycle": {},
        "sourceProperties": {},
        "stagingArea": {},
        "tags": {},
        "replicationDirection": "FAILOVER|FAILBACK",
        "reversedDirectionSourceServerArn": "string",
        "sourceCloudProperties": {},
        "agentVersion": "string"
    }
}
```
