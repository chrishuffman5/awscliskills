# Signal Maps

### 11.1 `create-signal-map`

Creates a signal map by discovering resources from a top-level entry point (e.g., a channel ARN).

**Synopsis:**
```bash
aws medialive create-signal-map \
    --discovery-entry-point-arn <value> \
    --name <value> \
    [--cloud-watch-alarm-template-group-identifiers <value>] \
    [--description <value>] \
    [--event-bridge-rule-template-group-identifiers <value>] \
    [--tags <value>] \
    [--request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--discovery-entry-point-arn` | **Yes** | string | -- | ARN of the resource to discover from |
| `--name` | **Yes** | string | -- | Signal map name (unique per region) |
| `--cloud-watch-alarm-template-group-identifiers` | No | list | None | Alarm template group IDs |
| `--description` | No | string | None | Description |
| `--event-bridge-rule-template-group-identifiers` | No | list | None | Rule template group IDs |
| `--tags` | No | map | None | Key-value tag pairs |
| `--request-id` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "DiscoveryEntryPointArn": "string",
    "Status": "CREATE_IN_PROGRESS|CREATE_COMPLETE|CREATE_FAILED|UPDATE_IN_PROGRESS|UPDATE_COMPLETE|UPDATE_REVERTED|UPDATE_FAILED|READY|NOT_READY",
    "ErrorMessage": "string",
    "CloudWatchAlarmTemplateGroupIds": ["string"],
    "EventBridgeRuleTemplateGroupIds": ["string"],
    "MediaResourceMap": {},
    "FailedMediaResourceMap": {},
    "MonitorDeployment": {},
    "LastDiscoveredAt": "timestamp",
    "LastSuccessfulMonitorDeployment": {},
    "MonitorChangesPendingDeployment": "boolean",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "Tags": {}
}
```

---

### 11.2 `get-signal-map`

Gets a signal map by ID.

**Synopsis:**
```bash
aws medialive get-signal-map \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Signal map ID |

**Output Schema:** Same as `create-signal-map` output.

---

### 11.3 `start-update-signal-map`

Initiates an update to a signal map's discovery, re-scanning resources from the entry point.

**Synopsis:**
```bash
aws medialive start-update-signal-map \
    --identifier <value> \
    [--cloud-watch-alarm-template-group-identifiers <value>] \
    [--description <value>] \
    [--discovery-entry-point-arn <value>] \
    [--event-bridge-rule-template-group-identifiers <value>] \
    [--force-rediscovery | --no-force-rediscovery] \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Signal map ID |
| `--cloud-watch-alarm-template-group-identifiers` | No | list | None | Updated alarm groups |
| `--description` | No | string | None | Updated description |
| `--discovery-entry-point-arn` | No | string | None | Updated entry point |
| `--event-bridge-rule-template-group-identifiers` | No | list | None | Updated rule groups |
| `--force-rediscovery` | No | boolean | false | Force full rediscovery |
| `--name` | No | string | None | Updated name |

**Output Schema:** Same as `create-signal-map` output.

---

### 11.4 `delete-signal-map`

Deletes a signal map.

**Synopsis:**
```bash
aws medialive delete-signal-map \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Signal map ID to delete |

**Output:** None

---

### 11.5 `list-signal-maps`

Lists signal maps. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-signal-maps \
    [--cloud-watch-alarm-template-group-identifier <value>] \
    [--event-bridge-rule-template-group-identifier <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cloud-watch-alarm-template-group-identifier` | No | string | None | Filter by alarm template group |
| `--event-bridge-rule-template-group-identifier` | No | string | None | Filter by rule template group |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "SignalMaps": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "Status": "string",
            "CreatedAt": "timestamp",
            "ModifiedAt": "timestamp",
            "MonitorDeploymentStatus": "string",
            "Tags": {}
        }
    ]
}
```

---

### 11.6 `start-monitor-deployment`

Deploys CloudWatch alarms and EventBridge rules for a signal map.

**Synopsis:**
```bash
aws medialive start-monitor-deployment \
    --identifier <value> \
    [--dry-run | --no-dry-run] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Signal map ID |
| `--dry-run` | No | boolean | false | Validate without deploying |

**Output Schema:** Same as `create-signal-map` output.

---

### 11.7 `start-delete-monitor-deployment`

Removes deployed monitoring (alarms and rules) from a signal map.

**Synopsis:**
```bash
aws medialive start-delete-monitor-deployment \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Signal map ID |

**Output Schema:** Same as `create-signal-map` output.
