# Maintenance

### 9.1 `start-domain-maintenance`

Starts a maintenance action on a domain.

**Synopsis:**
```bash
aws opensearch start-domain-maintenance \
    --domain-name <value> \
    --action <value> \
    [--node-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--action` | **Yes** | string | -- | Maintenance action: `REBOOT_NODE`, `RESTART_SEARCH_PROCESS`, `RESTART_DASHBOARD` |
| `--node-id` | No | string | -- | Node ID for node-specific actions |

**Output Schema:**
```json
{
    "MaintenanceId": "string"
}
```

---

### 9.2 `get-domain-maintenance-status`

Returns the status of a maintenance action.

**Synopsis:**
```bash
aws opensearch get-domain-maintenance-status \
    --domain-name <value> \
    --maintenance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--maintenance-id` | **Yes** | string | -- | Maintenance action ID |

**Output Schema:**
```json
{
    "Status": "PENDING|IN_PROGRESS|COMPLETED|FAILED|TIMED_OUT",
    "StatusMessage": "string",
    "NodeId": "string",
    "Action": "REBOOT_NODE|RESTART_SEARCH_PROCESS|RESTART_DASHBOARD",
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp"
}
```

---

### 9.3 `list-domain-maintenances`

Lists maintenance actions for a domain. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch list-domain-maintenances \
    --domain-name <value> \
    [--action <value>] \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--action` | No | string | None | Filter by action type |
| `--status` | No | string | None | Filter by status |

**Output Schema:**
```json
{
    "DomainMaintenances": [
        {
            "MaintenanceId": "string",
            "DomainName": "string",
            "Action": "string",
            "NodeId": "string",
            "Status": "string",
            "StatusMessage": "string",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.4 `describe-dry-run-progress`

Returns progress information for a dry-run domain configuration change.

**Synopsis:**
```bash
aws opensearch describe-dry-run-progress \
    --domain-name <value> \
    [--dry-run-id <value>] \
    [--load-dry-run-config | --no-load-dry-run-config] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--dry-run-id` | No | string | -- | Specific dry-run ID |
| `--load-dry-run-config` | No | boolean | false | Include full config in response |

**Output Schema:**
```json
{
    "DryRunProgressStatus": {
        "DryRunId": "string",
        "DryRunStatus": "string",
        "CreationDate": "string",
        "UpdateDate": "string",
        "ValidationFailures": []
    },
    "DryRunConfig": {},
    "DryRunResults": {
        "DeploymentType": "string",
        "Message": "string"
    }
}
```

---

### 9.5 `add-tags`

Adds tags to an OpenSearch Service domain.

**Synopsis:**
```bash
aws opensearch add-tags \
    --arn <value> \
    --tag-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the domain |
| `--tag-list` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Output:** None

---

### 9.6 `remove-tags`

Removes tags from an OpenSearch Service domain.

**Synopsis:**
```bash
aws opensearch remove-tags \
    --arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the domain |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 9.7 `list-tags`

Lists tags for an OpenSearch Service domain.

**Synopsis:**
```bash
aws opensearch list-tags \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the domain |

**Output Schema:**
```json
{
    "TagList": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
