# Serverless Replication

Serverless replications use DMS Serverless, which automatically provisions and scales capacity. Unlike traditional replication tasks, serverless replications do not require a dedicated replication instance.

### 5.1 `create-replication-config`

Creates a configuration that you can later provide to configure and start a DMS Serverless replication.

**Synopsis:**
```bash
aws dms create-replication-config \
    --replication-config-identifier <value> \
    --source-endpoint-arn <value> \
    --target-endpoint-arn <value> \
    --compute-config <value> \
    --replication-type <value> \
    --table-mappings <value> \
    [--replication-settings <value>] \
    [--supplemental-settings <value>] \
    [--resource-identifier <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-config-identifier` | **Yes** | string | -- | Unique identifier for this replication config |
| `--source-endpoint-arn` | **Yes** | string | -- | ARN of the source endpoint |
| `--target-endpoint-arn` | **Yes** | string | -- | ARN of the target endpoint |
| `--compute-config` | **Yes** | structure | -- | Compute configuration (see below) |
| `--replication-type` | **Yes** | string | -- | `full-load`, `cdc`, or `full-load-and-cdc` |
| `--table-mappings` | **Yes** | string | -- | Table mappings JSON |
| `--replication-settings` | No | string | -- | Replication settings JSON |
| `--supplemental-settings` | No | string | -- | Supplemental settings JSON |
| `--resource-identifier` | No | string | -- | Friendly ARN identifier |
| `--tags` | No | list | -- | Tags |

**Compute Config Structure:**
```json
{
    "AvailabilityZone": "string",
    "DnsNameServers": "string",
    "KmsKeyId": "string",
    "MaxCapacityUnits": "integer",
    "MinCapacityUnits": "integer",
    "MultiAZ": "boolean",
    "PreferredMaintenanceWindow": "string",
    "ReplicationSubnetGroupId": "string",
    "VpcSecurityGroupIds": ["string"]
}
```

**Output Schema:**
```json
{
    "ReplicationConfig": {
        "ReplicationConfigIdentifier": "string",
        "ReplicationConfigArn": "string",
        "SourceEndpointArn": "string",
        "TargetEndpointArn": "string",
        "ReplicationType": "string",
        "ComputeConfig": {
            "AvailabilityZone": "string",
            "DnsNameServers": "string",
            "KmsKeyId": "string",
            "MaxCapacityUnits": "integer",
            "MinCapacityUnits": "integer",
            "MultiAZ": "boolean",
            "PreferredMaintenanceWindow": "string",
            "ReplicationSubnetGroupId": "string",
            "VpcSecurityGroupIds": ["string"]
        },
        "ReplicationSettings": "string",
        "SupplementalSettings": "string",
        "TableMappings": "string",
        "ReplicationConfigCreateTime": "timestamp",
        "ReplicationConfigUpdateTime": "timestamp"
    }
}
```

---

### 5.2 `delete-replication-config`

Deletes an DMS Serverless replication configuration.

**Synopsis:**
```bash
aws dms delete-replication-config \
    --replication-config-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-config-arn` | **Yes** | string | -- | ARN of the replication config to delete |

**Output Schema:** Same as `create-replication-config`.

---

### 5.3 `describe-replication-configs`

Returns one or more existing DMS Serverless replication configurations. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-replication-configs \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `replication-config-arn`, `replication-config-id`, `replication-type`, `source-endpoint-arn`, `target-endpoint-arn` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "ReplicationConfigs": [
        {
            "ReplicationConfigIdentifier": "string",
            "ReplicationConfigArn": "string",
            "SourceEndpointArn": "string",
            "TargetEndpointArn": "string",
            "ReplicationType": "string",
            "ComputeConfig": {},
            "ReplicationSettings": "string",
            "SupplementalSettings": "string",
            "TableMappings": "string",
            "ReplicationConfigCreateTime": "timestamp",
            "ReplicationConfigUpdateTime": "timestamp"
        }
    ]
}
```

---

### 5.4 `modify-replication-config`

Modifies an existing DMS Serverless replication configuration.

**Synopsis:**
```bash
aws dms modify-replication-config \
    --replication-config-arn <value> \
    [--replication-config-identifier <value>] \
    [--replication-type <value>] \
    [--table-mappings <value>] \
    [--replication-settings <value>] \
    [--supplemental-settings <value>] \
    [--compute-config <value>] \
    [--source-endpoint-arn <value>] \
    [--target-endpoint-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-config-arn` | **Yes** | string | -- | ARN of the replication config |
| `--replication-config-identifier` | No | string | -- | New config identifier |
| `--replication-type` | No | string | -- | New replication type |
| `--table-mappings` | No | string | -- | New table mappings |
| `--replication-settings` | No | string | -- | New replication settings |
| `--supplemental-settings` | No | string | -- | New supplemental settings |
| `--compute-config` | No | structure | -- | New compute configuration |
| `--source-endpoint-arn` | No | string | -- | New source endpoint |
| `--target-endpoint-arn` | No | string | -- | New target endpoint |

**Output Schema:** Same as `create-replication-config`.

---

### 5.5 `start-replication`

For a given DMS Serverless replication configuration, DMS connects to the source endpoint and collects the metadata to analyze the replication workload. DMS then computes and provisions the required capacity and starts replicating to the target endpoint.

**Synopsis:**
```bash
aws dms start-replication \
    --replication-config-arn <value> \
    --start-replication-type <value> \
    [--cdc-start-time <value>] \
    [--cdc-start-position <value>] \
    [--cdc-stop-position <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-config-arn` | **Yes** | string | -- | ARN of the replication config |
| `--start-replication-type` | **Yes** | string | -- | `start-replication`, `resume-processing`, or `reload-target` |
| `--cdc-start-time` | No | timestamp | -- | CDC start time |
| `--cdc-start-position` | No | string | -- | CDC start position |
| `--cdc-stop-position` | No | string | -- | CDC stop position |

**Output Schema:**
```json
{
    "Replication": {
        "ReplicationConfigIdentifier": "string",
        "ReplicationConfigArn": "string",
        "SourceEndpointArn": "string",
        "TargetEndpointArn": "string",
        "ReplicationType": "string",
        "Status": "string",
        "ProvisionData": {
            "ProvisionState": "string",
            "ProvisionedCapacityUnits": "integer",
            "DateProvisioned": "timestamp",
            "IsNewProvisioningAvailable": "boolean",
            "DateNewProvisioningDataAvailable": "timestamp",
            "ReasonForNewProvisioningData": "string"
        },
        "StopReason": "string",
        "FailureMessages": ["string"],
        "ReplicationStats": {
            "FullLoadProgressPercent": "integer",
            "ElapsedTimeMillis": "long",
            "TablesLoaded": "integer",
            "TablesLoading": "integer",
            "TablesQueued": "integer",
            "TablesErrored": "integer",
            "FreshStartDate": "timestamp",
            "StartDate": "timestamp",
            "StopDate": "timestamp",
            "FullLoadStartDate": "timestamp",
            "FullLoadFinishDate": "timestamp"
        },
        "StartReplicationType": "string",
        "CdcStartTime": "timestamp",
        "CdcStartPosition": "string",
        "CdcStopPosition": "string",
        "RecoveryCheckpoint": "string",
        "ReplicationCreateTime": "timestamp",
        "ReplicationUpdateTime": "timestamp",
        "ReplicationLastStopTime": "timestamp",
        "ReplicationDeprovisionTime": "timestamp"
    }
}
```

---

### 5.6 `stop-replication`

Stops a serverless replication.

**Synopsis:**
```bash
aws dms stop-replication \
    --replication-config-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-config-arn` | **Yes** | string | -- | ARN of the replication config |

**Output Schema:** Same as `start-replication`.

---

### 5.7 `describe-replications`

Returns one or more serverless replications. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-replications \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `replication-config-arn`, `replication-type`, `source-endpoint-arn`, `target-endpoint-arn`, `status` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "Replications": [
        {
            "ReplicationConfigIdentifier": "string",
            "ReplicationConfigArn": "string",
            "SourceEndpointArn": "string",
            "TargetEndpointArn": "string",
            "ReplicationType": "string",
            "Status": "string",
            "ProvisionData": {},
            "StopReason": "string",
            "FailureMessages": ["string"],
            "ReplicationStats": {},
            "StartReplicationType": "string",
            "CdcStartTime": "timestamp",
            "CdcStartPosition": "string",
            "CdcStopPosition": "string",
            "RecoveryCheckpoint": "string",
            "ReplicationCreateTime": "timestamp",
            "ReplicationUpdateTime": "timestamp",
            "ReplicationLastStopTime": "timestamp",
            "ReplicationDeprovisionTime": "timestamp"
        }
    ]
}
```

---

### 5.8 `reload-replication-tables`

Reloads the target database table with the source data for a given serverless replication.

**Synopsis:**
```bash
aws dms reload-replication-tables \
    --replication-config-arn <value> \
    --tables-to-reload <value> \
    [--reload-option <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-config-arn` | **Yes** | string | -- | ARN of the replication config |
| `--tables-to-reload` | **Yes** | list | -- | Tables: `SchemaName=string,TableName=string ...` |
| `--reload-option` | No | string | `data-reload` | `data-reload` or `validate-only` |

**Output Schema:**
```json
{
    "ReplicationConfigArn": "string"
}
```

---

### 5.9 `describe-replication-table-statistics`

Returns table and schema-level statistics for one or more serverless replications. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-replication-table-statistics \
    --replication-config-arn <value> \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-config-arn` | **Yes** | string | -- | ARN of the replication config |
| `--filters` | No | list | -- | Filters: `schema-name`, `table-name`, `table-state` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "ReplicationConfigArn": "string",
    "Marker": "string",
    "ReplicationTableStatistics": [
        {
            "SchemaName": "string",
            "TableName": "string",
            "Inserts": "long",
            "Deletes": "long",
            "Updates": "long",
            "Ddls": "long",
            "AppliedInserts": "long",
            "AppliedDeletes": "long",
            "AppliedUpdates": "long",
            "AppliedDdls": "long",
            "FullLoadRows": "long",
            "FullLoadCondtnlChkFailedRows": "long",
            "FullLoadErrorRows": "long",
            "FullLoadStartTime": "timestamp",
            "FullLoadEndTime": "timestamp",
            "FullLoadReloaded": "boolean",
            "LastUpdateTime": "timestamp",
            "TableState": "string",
            "ValidationPendingRecords": "long",
            "ValidationFailedRecords": "long",
            "ValidationSuspendedRecords": "long",
            "ValidationState": "string",
            "ValidationStateDetails": "string"
        }
    ]
}
```
