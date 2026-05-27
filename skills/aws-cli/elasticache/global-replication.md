# Global Replication

### 8.1 `create-global-replication-group`

Creates a global replication group spanning multiple AWS regions. Provides cross-region read replicas and disaster recovery.

**Synopsis:**
```bash
aws elasticache create-global-replication-group \
    --global-replication-group-id-suffix <value> \
    --primary-replication-group-id <value> \
    [--global-replication-group-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-replication-group-id-suffix` | **Yes** | string | -- | Suffix for the global group ID (prefixed with `ldgnf-`) |
| `--primary-replication-group-id` | **Yes** | string | -- | ID of the primary replication group |
| `--global-replication-group-description` | No | string | -- | Description |

**Output Schema:**
```json
{
    "GlobalReplicationGroup": {
        "GlobalReplicationGroupId": "string",
        "GlobalReplicationGroupDescription": "string",
        "Status": "creating|available|modifying|deleting|primary-only",
        "CacheNodeType": "string",
        "Engine": "string",
        "EngineVersion": "string",
        "ClusterEnabled": "boolean",
        "GlobalNodeGroups": [
            {
                "GlobalNodeGroupId": "string",
                "Slots": "string"
            }
        ],
        "Members": [
            {
                "ReplicationGroupId": "string",
                "ReplicationGroupRegion": "string",
                "Role": "PRIMARY|SECONDARY",
                "AutomaticFailover": "enabled|disabled|enabling|disabling",
                "Status": "string"
            }
        ],
        "AuthTokenEnabled": "boolean",
        "TransitEncryptionEnabled": "boolean",
        "AtRestEncryptionEnabled": "boolean",
        "ARN": "string"
    }
}
```

---

### 8.2 `delete-global-replication-group`

Deletes a global replication group. All secondary replication groups must be disassociated first.

**Synopsis:**
```bash
aws elasticache delete-global-replication-group \
    --global-replication-group-id <value> \
    --retain-primary-replication-group | --no-retain-primary-replication-group \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-replication-group-id` | **Yes** | string | -- | ID of the global replication group |
| `--retain-primary-replication-group` | **Yes** | boolean | -- | Whether to keep the primary replication group |

**Output Schema:** Same as `create-global-replication-group` output.

---

### 8.3 `describe-global-replication-groups`

Returns information about global replication groups. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-global-replication-groups \
    [--global-replication-group-id <value>] \
    [--show-member-info | --no-show-member-info] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-replication-group-id` | No | string | -- | Specific global group ID |
| `--show-member-info` | No | boolean | false | Include member replication group details |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GlobalReplicationGroups": [
        {
            "GlobalReplicationGroupId": "string",
            "GlobalReplicationGroupDescription": "string",
            "Status": "string",
            "CacheNodeType": "string",
            "Engine": "string",
            "Members": [],
            "ARN": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.4 `modify-global-replication-group`

Modifies a global replication group. Can change node type, engine version, or description.

**Synopsis:**
```bash
aws elasticache modify-global-replication-group \
    --global-replication-group-id <value> \
    --apply-immediately | --no-apply-immediately \
    [--cache-node-type <value>] \
    [--engine-version <value>] \
    [--cache-parameter-group-name <value>] \
    [--global-replication-group-description <value>] \
    [--automatic-failover-enabled | --no-automatic-failover-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-replication-group-id` | **Yes** | string | -- | ID of the global replication group |
| `--apply-immediately` | **Yes** | boolean | -- | Apply changes immediately |
| `--cache-node-type` | No | string | -- | New cache node type |
| `--engine-version` | No | string | -- | New engine version |
| `--cache-parameter-group-name` | No | string | -- | New parameter group name |
| `--global-replication-group-description` | No | string | -- | New description |
| `--automatic-failover-enabled` | No | boolean | -- | Enable/disable automatic failover |

**Output Schema:** Same as `create-global-replication-group` output.

---

### 8.5 `failover-global-replication-group`

Promotes a secondary replication group to primary for a global replication group. Used for disaster recovery.

**Synopsis:**
```bash
aws elasticache failover-global-replication-group \
    --global-replication-group-id <value> \
    --primary-region <value> \
    --primary-replication-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-replication-group-id` | **Yes** | string | -- | ID of the global replication group |
| `--primary-region` | **Yes** | string | -- | Region of the new primary |
| `--primary-replication-group-id` | **Yes** | string | -- | ID of the new primary replication group |

**Output Schema:** Same as `create-global-replication-group` output.

---

### 8.6 `increase-node-groups-in-global-replication-group`

Increases the number of node groups (shards) in a global replication group.

**Synopsis:**
```bash
aws elasticache increase-node-groups-in-global-replication-group \
    --global-replication-group-id <value> \
    --node-group-count <value> \
    --apply-immediately | --no-apply-immediately \
    [--regional-configurations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-replication-group-id` | **Yes** | string | -- | ID of the global replication group |
| `--node-group-count` | **Yes** | integer | -- | New total number of node groups |
| `--apply-immediately` | **Yes** | boolean | -- | Must be true |
| `--regional-configurations` | No | list | -- | Per-region shard configurations |

**Output Schema:** Same as `create-global-replication-group` output.

---

### 8.7 `decrease-node-groups-in-global-replication-group`

Decreases the number of node groups (shards) in a global replication group.

**Synopsis:**
```bash
aws elasticache decrease-node-groups-in-global-replication-group \
    --global-replication-group-id <value> \
    --node-group-count <value> \
    --apply-immediately | --no-apply-immediately \
    [--global-node-groups-to-remove <value>] \
    [--global-node-groups-to-retain <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-replication-group-id` | **Yes** | string | -- | ID of the global replication group |
| `--node-group-count` | **Yes** | integer | -- | New total number of node groups |
| `--apply-immediately` | **Yes** | boolean | -- | Must be true |
| `--global-node-groups-to-remove` | No | list(string) | -- | Global node group IDs to remove |
| `--global-node-groups-to-retain` | No | list(string) | -- | Global node group IDs to retain |

**Output Schema:** Same as `create-global-replication-group` output.

---

### 8.8 `disassociate-global-replication-group`

Removes a secondary replication group from a global replication group. The secondary becomes standalone.

**Synopsis:**
```bash
aws elasticache disassociate-global-replication-group \
    --global-replication-group-id <value> \
    --replication-group-id <value> \
    --replication-group-region <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-replication-group-id` | **Yes** | string | -- | ID of the global replication group |
| `--replication-group-id` | **Yes** | string | -- | ID of the secondary replication group to disassociate |
| `--replication-group-region` | **Yes** | string | -- | Region of the secondary replication group |

**Output Schema:** Same as `create-global-replication-group` output.

---

### 8.9 `rebalance-slots-in-global-replication-group`

Redistributes slots across existing node groups to achieve uniform distribution.

**Synopsis:**
```bash
aws elasticache rebalance-slots-in-global-replication-group \
    --global-replication-group-id <value> \
    --apply-immediately | --no-apply-immediately \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-replication-group-id` | **Yes** | string | -- | ID of the global replication group |
| `--apply-immediately` | **Yes** | boolean | -- | Must be true |

**Output Schema:** Same as `create-global-replication-group` output.
