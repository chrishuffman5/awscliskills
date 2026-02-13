# Recovery Instances

### 2.1 `describe-recovery-instances`

Lists all recovery instances or those that match the given filters. **Paginated operation.**

**Synopsis:**
```bash
aws drs describe-recovery-instances \
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
| `--filters` | **Yes** | structure | -- | Filters for recovery instances |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Filters Structure:**
```json
{
    "recoveryInstanceIDs": ["string"],
    "sourceServerIDs": ["string"]
}
```

**Output Schema:**
```json
{
    "items": [
        {
            "ec2InstanceID": "string",
            "ec2InstanceState": "PENDING|RUNNING|STOPPING|STOPPED|SHUTTING_DOWN|TERMINATED|NOT_FOUND",
            "recoveryInstanceID": "string",
            "sourceServerID": "string",
            "arn": "string",
            "isDrill": "boolean",
            "jobID": "string",
            "pointInTimeSnapshotDateTime": "string",
            "recoveryInstanceProperties": {
                "lastUpdatedDateTime": "string",
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
                        "internalDeviceName": "string",
                        "bytes": "long",
                        "ebsVolumeID": "string"
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
                }
            },
            "dataReplicationInfo": {
                "dataReplicationState": "string",
                "dataReplicationInitiation": {},
                "dataReplicationError": {},
                "etaDateTime": "string",
                "replicatedDisks": [],
                "lagDuration": "string",
                "stagingAvailabilityZone": "string"
            },
            "failback": {
                "failbackClientID": "string",
                "failbackClientLastSeenByServiceDateTime": "string",
                "failbackInitiationTime": "string",
                "state": "FAILBACK_NOT_STARTED|FAILBACK_IN_PROGRESS|FAILBACK_READY_FOR_LAUNCH|FAILBACK_COMPLETED|FAILBACK_ERROR|FAILBACK_NOT_READY_FOR_LAUNCH|FAILBACK_LAUNCH_STATE_NOT_AVAILABLE",
                "agentLastSeenByServiceDateTime": "string",
                "failbackJobID": "string",
                "failbackLaunchType": "RECOVERY|DRILL",
                "failbackToOriginalServer": "boolean",
                "elapsedReplicationDuration": "string"
            },
            "tags": {
                "string": "string"
            },
            "originAvailabilityZone": "string",
            "originEnvironment": "ON_PREMISES|AWS",
            "agentVersion": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.2 `delete-recovery-instance`

Deletes a single recovery instance by ID. Must be disconnected and terminated first.

**Synopsis:**
```bash
aws drs delete-recovery-instance \
    --recovery-instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-instance-id` | **Yes** | string | -- | Recovery instance ID |

**Output Schema:**
```json
{}
```

---

### 2.3 `disconnect-recovery-instance`

Disconnect a recovery instance from DRS. This stops the failback replication of the recovery instance.

**Synopsis:**
```bash
aws drs disconnect-recovery-instance \
    --recovery-instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-instance-id` | **Yes** | string | -- | Recovery instance ID |

**Output Schema:**
```json
{}
```

---

### 2.4 `terminate-recovery-instances`

Initiates a Job for terminating the EC2 resources associated with the specified recovery instances.

**Synopsis:**
```bash
aws drs terminate-recovery-instances \
    --recovery-instance-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-instance-ids` | **Yes** | list(string) | -- | One or more recovery instance IDs |

**Output Schema:**
```json
{
    "job": {
        "jobID": "string",
        "arn": "string",
        "type": "LAUNCH|TERMINATE|CREATE_CONVERTED_SNAPSHOT",
        "initiatedBy": "START_RECOVERY|START_DRILL|FAILBACK|DIAGNOSTIC|TERMINATE_RECOVERY_INSTANCES|TARGET_ACCOUNT|CREATE_NETWORK_RECOVERY|UPDATE_NETWORK_RECOVERY|ASSOCIATE_NETWORK_RECOVERY",
        "creationDateTime": "string",
        "endDateTime": "string",
        "status": "PENDING|STARTED|COMPLETED",
        "participatingServers": [
            {
                "sourceServerID": "string",
                "recoveryInstanceID": "string",
                "launchStatus": "PENDING|IN_PROGRESS|LAUNCHED|FAILED|TERMINATED"
            }
        ],
        "tags": {},
        "participatingResources": []
    }
}
```

---

### 2.5 `describe-recovery-snapshots`

Lists all recovery snapshots for the specified source server. **Paginated operation.**

**Synopsis:**
```bash
aws drs describe-recovery-snapshots \
    --source-server-id <value> \
    [--filters <value>] \
    [--order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |
| `--filters` | No | structure | None | Filters. Structure: `fromDateTime=string,toDateTime=string` |
| `--order` | No | string | None | Sort order: `ASC` or `DESC` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "items": [
        {
            "snapshotID": "string",
            "sourceServerID": "string",
            "expectedTimestamp": "string",
            "timestamp": "string",
            "ebsSnapshots": ["string"]
        }
    ],
    "nextToken": "string"
}
```
