# App Monitors

### 1.1 `create-app-monitor`

Creates an app monitor for collecting real-user monitoring telemetry from a web, Android, or iOS application.

**Synopsis:**
```bash
aws rum create-app-monitor \
    --name <value> \
    [--domain <value>] \
    [--domain-list <value>] \
    [--app-monitor-configuration <value>] \
    [--cw-log-enabled | --no-cw-log-enabled] \
    [--custom-events <value>] \
    [--deobfuscation-configuration <value>] \
    [--platform <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | App monitor name (1-255 chars) |
| `--domain` | No | string | None | Top-level domain (1-253 chars). Either `--domain` or `--domain-list` should be provided |
| `--domain-list` | No | list | None | List of domains (1-5) |
| `--app-monitor-configuration` | No | structure | None | Monitoring configuration |
| `--cw-log-enabled` | No | boolean | false | Send data to CloudWatch Logs |
| `--custom-events` | No | structure | None | Custom events configuration |
| `--deobfuscation-configuration` | No | structure | None | Source map configuration for stack traces |
| `--platform` | No | string | Web | `Web`, `Android`, or `iOS` |
| `--tags` | No | map | None | Tags (max 50) |

**AppMonitorConfiguration structure:**
```json
{
    "IdentityPoolId": "string",
    "ExcludedPages": ["string"],
    "IncludedPages": ["string"],
    "FavoritePages": ["string"],
    "SessionSampleRate": 0.1,
    "GuestRoleArn": "string",
    "AllowCookies": true,
    "Telemetries": ["errors", "performance", "http"],
    "EnableXRay": false
}
```

**CustomEvents structure:**
```json
{
    "Status": "ENABLED|DISABLED"
}
```

**DeobfuscationConfiguration structure:**
```json
{
    "JavaScriptSourceMaps": {
        "Status": "ENABLED|DISABLED",
        "S3Uri": "s3://bucket/prefix/"
    }
}
```

**Output Schema:**
```json
{
    "Id": "string"
}
```

---

### 1.2 `get-app-monitor`

Retrieves complete app monitor details.

**Synopsis:**
```bash
aws rum get-app-monitor \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | App monitor name (1-255 chars) |

**Output Schema:**
```json
{
    "AppMonitor": {
        "Name": "string",
        "Domain": "string",
        "DomainList": ["string"],
        "Id": "string",
        "Created": "string",
        "LastModified": "string",
        "Tags": {},
        "State": "CREATED|DELETING|ACTIVE",
        "AppMonitorConfiguration": {
            "IdentityPoolId": "string",
            "ExcludedPages": [],
            "IncludedPages": [],
            "FavoritePages": [],
            "SessionSampleRate": "double",
            "GuestRoleArn": "string",
            "AllowCookies": "boolean",
            "Telemetries": ["errors|performance|http"],
            "EnableXRay": "boolean"
        },
        "DataStorage": {
            "CwLog": {
                "CwLogEnabled": "boolean",
                "CwLogGroup": "string"
            }
        },
        "CustomEvents": {
            "Status": "ENABLED|DISABLED"
        },
        "DeobfuscationConfiguration": {
            "JavaScriptSourceMaps": {
                "Status": "ENABLED|DISABLED",
                "S3Uri": "string"
            }
        },
        "Platform": "Web|Android|iOS"
    }
}
```

---

### 1.3 `list-app-monitors`

Lists all app monitors. **Paginated operation.**

**Synopsis:**
```bash
aws rum list-app-monitors \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |

**Output Schema:**
```json
{
    "NextToken": "string",
    "AppMonitorSummaries": [
        {
            "Name": "string",
            "Id": "string",
            "Created": "string",
            "LastModified": "string",
            "State": "CREATED|DELETING|ACTIVE",
            "Platform": "Web|Android|iOS"
        }
    ]
}
```

---

### 1.4 `update-app-monitor`

Updates an existing app monitor configuration.

**Synopsis:**
```bash
aws rum update-app-monitor \
    --name <value> \
    [--domain <value>] \
    [--domain-list <value>] \
    [--app-monitor-configuration <value>] \
    [--cw-log-enabled | --no-cw-log-enabled] \
    [--custom-events <value>] \
    [--deobfuscation-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | App monitor name (1-255 chars) |
| `--domain` | No | string | None | Updated domain (1-253 chars) |
| `--domain-list` | No | list | None | Updated domain list (1-5) |
| `--app-monitor-configuration` | No | structure | None | Updated monitoring configuration |
| `--cw-log-enabled` | No | boolean | None | Updated CloudWatch Logs setting |
| `--custom-events` | No | structure | None | Updated custom events configuration |
| `--deobfuscation-configuration` | No | structure | None | Updated source map configuration |

**Output:** None

---

### 1.5 `delete-app-monitor`

Deletes an app monitor.

**Synopsis:**
```bash
aws rum delete-app-monitor \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | App monitor name (1-255 chars) |

**Output:** None

---

### 1.6 `get-app-monitor-data`

Retrieves collected monitoring data from an app monitor. **Paginated operation.**

**Synopsis:**
```bash
aws rum get-app-monitor-data \
    --name <value> \
    --time-range <value> \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | App monitor name (1-255 chars) |
| `--time-range` | **Yes** | structure | -- | Time range for data retrieval |
| `--filters` | No | list | None | Query filters |
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |

**TimeRange structure:**
```json
{
    "After": 1700000000,
    "Before": 1700086400
}
```

`After` is required (epoch seconds). `Before` is optional; defaults to current time.

**Filters structure:**
```json
[
    {
        "Name": "Browser|Device|Country|Page|OS|EventType|Invert",
        "Values": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "Events": ["string"],
    "NextToken": "string"
}
```

---

### 1.7 `put-rum-events`

Sends telemetry events to an app monitor. Primarily used by the RUM web client, but can also be called directly.

**Synopsis:**
```bash
aws rum put-rum-events \
    --id <value> \
    --batch-id <value> \
    --app-monitor-details <value> \
    --user-details <value> \
    --rum-events <value> \
    [--alias <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | App monitor ID (UUID format) |
| `--batch-id` | **Yes** | string | -- | Unique batch identifier (UUID format) |
| `--app-monitor-details` | **Yes** | structure | -- | App monitor info |
| `--user-details` | **Yes** | structure | -- | User session info |
| `--rum-events` | **Yes** | list | -- | Telemetry events |
| `--alias` | No | string | None | Alias for resource-based policy (1-255 chars) |

**AppMonitorDetails structure:**
```json
{
    "name": "string",
    "id": "string",
    "version": "string"
}
```

**UserDetails structure:**
```json
{
    "userId": "string",
    "sessionId": "string"
}
```

**RumEvents structure:**
```json
[
    {
        "id": "string",
        "timestamp": "timestamp",
        "type": "string",
        "metadata": "string",
        "details": "string"
    }
]
```

**Output:** None
