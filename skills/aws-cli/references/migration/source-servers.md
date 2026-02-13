# Source Servers

### 1.1 `describe-source-servers`

Retrieves all source servers or filters by ID. **Paginated.**

**Synopsis:**
```bash
aws mgn describe-source-servers \
    [--filters <value>] \
    [--account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | structure | None | Filter criteria (see below) |
| `--account-id` | No | string | None | AWS account ID (12-digit) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filters Structure:**
```json
{
    "sourceServerIDs": ["string"],
    "isArchived": true|false,
    "replicationTypes": ["AGENT_BASED", "SNAPSHOT_SHIPPING"],
    "lifeCycleStates": ["STOPPED", "NOT_READY", "READY_FOR_TEST", "TESTING", "READY_FOR_CUTOVER", "CUTTING_OVER", "CUTOVER", "DISCONNECTED", "DISCOVERED", "PENDING_INSTALLATION"],
    "applicationIDs": ["string"]
}
```

**Output Schema:**
```json
{
    "items": [
        {
            "sourceServerID": "string",
            "arn": "string",
            "isArchived": true|false,
            "tags": {"key": "value"},
            "replicationType": "AGENT_BASED|SNAPSHOT_SHIPPING",
            "vcenterClientID": "string",
            "applicationID": "string",
            "userProvidedID": "string",
            "fqdnForActionFramework": "string",
            "sourceProperties": {
                "lastUpdatedDateTime": "string",
                "recommendedInstanceType": "string",
                "os": {"fullString": "string"},
                "cpus": [{"cores": "long", "modelName": "string"}],
                "ramBytes": "long",
                "disks": [{"deviceName": "string", "bytes": "long"}],
                "networkInterfaces": [{"macAddress": "string", "ips": ["string"], "isPrimary": true|false}],
                "identificationHints": {"hostname": "string", "fqdn": "string", "vmWareUuid": "string", "awsInstanceID": "string", "vmPath": "string"}
            },
            "dataReplicationInfo": {
                "dataReplicationState": "string",
                "lagDuration": "string",
                "etaDateTime": "string",
                "replicatedDisks": [{"deviceName": "string", "totalStorageBytes": "long", "replicatedStorageBytes": "long"}],
                "lastSnapshotDateTime": "string"
            },
            "lifeCycle": {
                "addedToServiceDateTime": "string",
                "firstByteDateTime": "string",
                "elapsedReplicationDuration": "string",
                "lastSeenByServiceDateTime": "string",
                "state": "string",
                "lastTest": {"initiatedDateTime": "string", "revertedDateTime": "string"},
                "lastCutover": {"initiatedDateTime": "string", "revertedDateTime": "string", "finalizedDateTime": "string"}
            },
            "launchedInstance": {
                "ec2InstanceID": "string",
                "jobID": "string",
                "firstBoot": "WAITING|SUCCEEDED|UNKNOWN|STOPPED"
            },
            "connectorAction": {
                "credentialsSecretArn": "string",
                "connectorArn": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 1.2 `delete-source-server`

Deletes a source server. The source server must be disconnected first.

**Synopsis:**
```bash
aws mgn delete-source-server \
    --source-server-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID (format: `s-[0-9a-zA-Z]{17}`) |
| `--account-id` | No | string | None | Account ID |

**Output:** None

---

### 1.3 `update-source-server`

Updates source server properties.

**Synopsis:**
```bash
aws mgn update-source-server \
    --source-server-id <value> \
    [--account-id <value>] \
    [--connector-action <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |
| `--account-id` | No | string | None | Account ID |
| `--connector-action` | No | structure | None | Connector action. Shorthand: `connectorArn=string,credentialsSecretArn=string` |

**Output Schema:** Same as a single source server item.

---

### 1.4 `update-source-server-replication-type`

Allows you to change between AGENT_BASED and SNAPSHOT_SHIPPING replication types.

**Synopsis:**
```bash
aws mgn update-source-server-replication-type \
    --source-server-id <value> \
    --replication-type <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |
| `--replication-type` | **Yes** | string | -- | `AGENT_BASED` or `SNAPSHOT_SHIPPING` |
| `--account-id` | No | string | None | Account ID |

**Output Schema:** Same as a single source server item.

---

### 1.5 `change-server-life-cycle-state`

Changes the lifecycle state of a source server.

**Synopsis:**
```bash
aws mgn change-server-life-cycle-state \
    --source-server-id <value> \
    --life-cycle <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |
| `--life-cycle` | **Yes** | structure | -- | Lifecycle state change. Shorthand: `state=READY_FOR_TEST\|READY_FOR_CUTOVER\|CUTOVER` |
| `--account-id` | No | string | None | Account ID |

**Output Schema:** Same as a single source server item.

---

### 1.6 `mark-as-archived`

Archives a source server, removing it from the active console view.

**Synopsis:**
```bash
aws mgn mark-as-archived \
    --source-server-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |
| `--account-id` | No | string | None | Account ID |

**Output Schema:** Same as a single source server item.

---

### 1.7 `disconnect-from-service`

Disconnects a source server from the MGN service. Does not stop replication.

**Synopsis:**
```bash
aws mgn disconnect-from-service \
    --source-server-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |
| `--account-id` | No | string | None | Account ID |

**Output Schema:** Same as a single source server item.

---

### 1.8 `describe-vcenter-clients`

Lists vCenter clients. **Paginated.**

**Synopsis:**
```bash
aws mgn describe-vcenter-clients \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "vcenterClientID": "string",
            "arn": "string",
            "hostname": "string",
            "vcenterUUID": "string",
            "datacenterName": "string",
            "lastSeenDatetime": "string",
            "sourceServerTags": {"key": "value"},
            "tags": {"key": "value"}
        }
    ],
    "nextToken": "string"
}
```

---

### 1.9 `delete-vcenter-client`

Deletes a vCenter client.

**Synopsis:**
```bash
aws mgn delete-vcenter-client \
    --vcenter-client-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vcenter-client-id` | **Yes** | string | -- | vCenter client ID |

**Output:** None
