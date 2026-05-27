# Service Updates

### 9.1 `describe-service-updates`

Returns details of the service updates. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-service-updates \
    [--service-update-name <value>] \
    [--service-update-status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-update-name` | No | string | -- | Specific service update name |
| `--service-update-status` | No | list(string) | -- | Filter by status: `available`, `cancelled`, `expired` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ServiceUpdates": [
        {
            "ServiceUpdateName": "string",
            "ServiceUpdateReleaseDate": "timestamp",
            "ServiceUpdateEndDate": "timestamp",
            "ServiceUpdateSeverity": "critical|important|medium|low",
            "ServiceUpdateRecommendedApplyByDate": "timestamp",
            "ServiceUpdateStatus": "available|cancelled|expired",
            "ServiceUpdateDescription": "string",
            "ServiceUpdateType": "security-update",
            "Engine": "string",
            "EngineVersion": "string",
            "AutoUpdateAfterRecommendedApplyByDate": "boolean",
            "EstimatedUpdateTime": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.2 `describe-update-actions`

Returns details of the update actions for clusters or replication groups. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-update-actions \
    [--service-update-name <value>] \
    [--replication-group-ids <value>] \
    [--cache-cluster-ids <value>] \
    [--engine <value>] \
    [--service-update-status <value>] \
    [--service-update-time-range <value>] \
    [--update-action-status <value>] \
    [--show-node-level-update-status | --no-show-node-level-update-status] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-update-name` | No | string | -- | Filter by service update name |
| `--replication-group-ids` | No | list(string) | -- | Filter by replication group IDs |
| `--cache-cluster-ids` | No | list(string) | -- | Filter by cache cluster IDs |
| `--engine` | No | string | -- | Filter by engine |
| `--service-update-status` | No | list(string) | -- | Filter by update status |
| `--service-update-time-range` | No | structure | -- | Filter by time range. Shorthand: `StartTime=timestamp,EndTime=timestamp` |
| `--update-action-status` | No | list(string) | -- | Filter: `not-applied`, `waiting-to-start`, `in-progress`, `stopping`, `stopped`, `complete`, `scheduling`, `scheduled`, `not-applicable` |
| `--show-node-level-update-status` | No | boolean | false | Show per-node update status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "UpdateActions": [
        {
            "ReplicationGroupId": "string",
            "CacheClusterId": "string",
            "ServiceUpdateName": "string",
            "ServiceUpdateReleaseDate": "timestamp",
            "ServiceUpdateSeverity": "critical|important|medium|low",
            "ServiceUpdateStatus": "available|cancelled|expired",
            "ServiceUpdateRecommendedApplyByDate": "timestamp",
            "ServiceUpdateType": "security-update",
            "UpdateActionAvailableDate": "timestamp",
            "UpdateActionStatus": "not-applied|waiting-to-start|in-progress|stopping|stopped|complete|scheduling|scheduled|not-applicable",
            "NodesUpdated": "string",
            "UpdateActionStatusModifiedDate": "timestamp",
            "SlaMet": "yes|no|n/a",
            "NodeGroupUpdateStatus": [
                {
                    "NodeGroupId": "string",
                    "NodeGroupMemberUpdateStatus": [
                        {
                            "CacheClusterId": "string",
                            "CacheNodeId": "string",
                            "NodeUpdateStatus": "not-applied|waiting-to-start|in-progress|stopping|stopped|complete",
                            "NodeDeletionDate": "timestamp",
                            "NodeUpdateStartDate": "timestamp",
                            "NodeUpdateEndDate": "timestamp",
                            "NodeUpdateInitiatedBy": "system|customer",
                            "NodeUpdateInitiatedDate": "timestamp",
                            "NodeUpdateStatusModifiedDate": "timestamp"
                        }
                    ]
                }
            ],
            "CacheNodeUpdateStatus": [],
            "EstimatedUpdateTime": "string",
            "Engine": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.3 `batch-apply-update-action`

Applies a service update to one or more replication groups or cache clusters.

**Synopsis:**
```bash
aws elasticache batch-apply-update-action \
    --service-update-name <value> \
    [--replication-group-ids <value>] \
    [--cache-cluster-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-update-name` | **Yes** | string | -- | Name of the service update to apply |
| `--replication-group-ids` | No | list(string) | -- | Replication group IDs to apply update to |
| `--cache-cluster-ids` | No | list(string) | -- | Cache cluster IDs to apply update to |

**Output Schema:**
```json
{
    "ProcessedUpdateActions": [
        {
            "ReplicationGroupId": "string",
            "CacheClusterId": "string",
            "ServiceUpdateName": "string",
            "UpdateActionStatus": "not-applied|waiting-to-start|in-progress|stopping|stopped|complete|scheduling|scheduled|not-applicable"
        }
    ],
    "UnprocessedUpdateActions": [
        {
            "ReplicationGroupId": "string",
            "CacheClusterId": "string",
            "ServiceUpdateName": "string",
            "ErrorType": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 9.4 `batch-stop-update-action`

Stops a service update that is in progress on one or more replication groups or cache clusters.

**Synopsis:**
```bash
aws elasticache batch-stop-update-action \
    --service-update-name <value> \
    [--replication-group-ids <value>] \
    [--cache-cluster-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-update-name` | **Yes** | string | -- | Name of the service update to stop |
| `--replication-group-ids` | No | list(string) | -- | Replication group IDs |
| `--cache-cluster-ids` | No | list(string) | -- | Cache cluster IDs |

**Output Schema:** Same as `batch-apply-update-action` output.
