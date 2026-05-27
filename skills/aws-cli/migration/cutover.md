# Cutover

### 4.1 `start-test`

Launches test instances for the specified source servers. Creates a launch job.

**Synopsis:**
```bash
aws mgn start-test \
    --source-server-ids <value> \
    [--account-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-ids` | **Yes** | list(string) | -- | Source server IDs (1-200). Format: `s-[0-9a-zA-Z]{17}` |
| `--account-id` | No | string | None | Account ID |
| `--tags` | No | map | None | Tags for the test instances |

**Output Schema:**
```json
{
    "job": {
        "jobID": "string",
        "arn": "string",
        "type": "LAUNCH|TERMINATE",
        "initiatedBy": "START_TEST|START_CUTOVER|DIAGNOSTIC|TERMINATE",
        "status": "PENDING|STARTED|COMPLETED",
        "creationDateTime": "string",
        "endDateTime": "string",
        "participatingServers": [
            {
                "sourceServerID": "string",
                "launchStatus": "PENDING|IN_PROGRESS|LAUNCHED|FAILED|TERMINATED",
                "launchedEc2InstanceID": "string",
                "postLaunchActionsStatus": {}
            }
        ],
        "tags": {"key": "value"}
    }
}
```

---

### 4.2 `start-cutover`

Launches cutover instances for the specified source servers. This is the production migration.

**Synopsis:**
```bash
aws mgn start-cutover \
    --source-server-ids <value> \
    [--account-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-ids` | **Yes** | list(string) | -- | Source server IDs (1-200) |
| `--account-id` | No | string | None | Account ID |
| `--tags` | No | map | None | Tags for the cutover instances |

**Output Schema:** Same as start-test.

---

### 4.3 `finalize-cutover`

Finalizes the cutover for a source server. This confirms the migration is complete and stops replication.

**Synopsis:**
```bash
aws mgn finalize-cutover \
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

**Output Schema:** Single source server item (same as describe-source-servers output).

---

### 4.4 `terminate-target-instances`

Terminates the target EC2 instances that were launched for test or cutover.

**Synopsis:**
```bash
aws mgn terminate-target-instances \
    --source-server-ids <value> \
    [--account-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-ids` | **Yes** | list(string) | -- | Source server IDs (1-200) |
| `--account-id` | No | string | None | Account ID |
| `--tags` | No | map | None | Tags |

**Output Schema:** Same as start-test (job object).
