# Recovery Operations

### 5.1 `start-recovery`

Launches recovery instances for the specified source servers. For each source server, a recovery instance is launched using the most recent recovery snapshot.

**Synopsis:**
```bash
aws drs start-recovery \
    --source-servers <value> \
    [--is-drill | --no-is-drill] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-servers` | **Yes** | list | -- | Source servers to recover. Shorthand: `sourceServerID=string,recoverySnapshotID=string ...` |
| `--is-drill` | No | boolean | false | Whether this is a drill (non-destructive test) |
| `--tags` | No | map | None | Tags for the recovery job |

**Output Schema:**
```json
{
    "job": {
        "jobID": "string",
        "arn": "string",
        "type": "LAUNCH",
        "initiatedBy": "START_RECOVERY|START_DRILL",
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

### 5.2 `start-failback-launch`

Initiates a failback launch for the specified recovery instances.

**Synopsis:**
```bash
aws drs start-failback-launch \
    --recovery-instance-ids <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-instance-ids` | **Yes** | list(string) | -- | Recovery instance IDs to fail back |
| `--tags` | No | map | None | Tags for the failback job |

**Output Schema:**
```json
{
    "job": {
        "jobID": "string",
        "arn": "string",
        "type": "LAUNCH",
        "initiatedBy": "FAILBACK",
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
        "tags": {}
    }
}
```

---

### 5.3 `stop-failback`

Stops the failback process for the specified recovery instance.

**Synopsis:**
```bash
aws drs stop-failback \
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

### 5.4 `reverse-replication`

Start replication to the original source (reverse direction) of the recovery instance. Used after failback to protect the source from the recovery region.

**Synopsis:**
```bash
aws drs reverse-replication \
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
{
    "reversedDirectionSourceServerArn": "string"
}
```

---

### 5.5 `get-failback-replication-configuration`

Lists all failback replication configurations for the specified recovery instance.

**Synopsis:**
```bash
aws drs get-failback-replication-configuration \
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
{
    "recoveryInstanceID": "string",
    "name": "string",
    "bandwidthThrottling": "long",
    "usePrivateIP": "boolean"
}
```

---

### 5.6 `update-failback-replication-configuration`

Allows you to update the failback replication configuration of a recovery instance.

**Synopsis:**
```bash
aws drs update-failback-replication-configuration \
    --recovery-instance-id <value> \
    [--name <value>] \
    [--bandwidth-throttling <value>] \
    [--use-private-ip | --no-use-private-ip] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recovery-instance-id` | **Yes** | string | -- | Recovery instance ID |
| `--name` | No | string | None | Configuration name |
| `--bandwidth-throttling` | No | long | None | Bandwidth throttling in Mbps |
| `--use-private-ip` | No | boolean | None | Use private IP for replication |

**Output Schema:**
```json
{}
```

---

### 5.7 `initialize-service`

Initializes the Elastic Disaster Recovery service in the account. Must be called before using any other DRS operations.

**Synopsis:**
```bash
aws drs initialize-service \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No additional parameters required.

**Output Schema:**
```json
{}
```
