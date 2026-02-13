# Game Sessions

### 4.1 `create-game-session`

Creates a new game session on a fleet or via an alias.

**Synopsis:**
```bash
aws gamelift create-game-session \
    [--fleet-id <value>] \
    [--alias-id <value>] \
    --maximum-player-session-count <value> \
    [--name <value>] \
    [--game-properties <value>] \
    [--creator-id <value>] \
    [--game-session-id <value>] \
    [--idempotency-token <value>] \
    [--game-session-data <value>] \
    [--location <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | No | string | None | Fleet ID or ARN (provide either fleet-id or alias-id) |
| `--alias-id` | No | string | None | Alias ID or ARN |
| `--maximum-player-session-count` | **Yes** | integer | -- | Max simultaneous players (min: 0) |
| `--name` | No | string | None | Descriptive label (1-1024 chars) |
| `--game-properties` | No | list | None | Custom properties (max 16). Shorthand: `Key=string,Value=string ...` |
| `--creator-id` | No | string | None | Player/entity identifier (1-1024 chars) |
| `--game-session-id` | No | string | None | **Deprecated**. Use `--idempotency-token` |
| `--idempotency-token` | No | string | None | Unique request identifier (1-48 chars) |
| `--game-session-data` | No | string | None | Custom data string (max 262144 bytes) |
| `--location` | No | string | Home region | Remote location for the session |

**Output Schema:**
```json
{
    "GameSession": {
        "GameSessionId": "string",
        "Name": "string",
        "FleetId": "string",
        "FleetArn": "string",
        "CreationTime": "timestamp",
        "TerminationTime": "timestamp",
        "CurrentPlayerSessionCount": "integer",
        "MaximumPlayerSessionCount": "integer",
        "Status": "ACTIVE|ACTIVATING|TERMINATED|TERMINATING|ERROR",
        "StatusReason": "INTERRUPTED|TRIGGERED_ON_PROCESS_TERMINATE|FORCE_TERMINATED",
        "GameProperties": [
            {"Key": "string", "Value": "string"}
        ],
        "IpAddress": "string",
        "DnsName": "string",
        "Port": "integer",
        "PlayerSessionCreationPolicy": "ACCEPT_ALL|DENY_ALL",
        "CreatorId": "string",
        "GameSessionData": "string",
        "MatchmakerData": "string",
        "Location": "string"
    }
}
```

---

### 4.2 `describe-game-sessions`

Retrieves properties for active game sessions. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-game-sessions \
    [--fleet-id <value>] \
    [--game-session-id <value>] \
    [--alias-id <value>] \
    [--location <value>] \
    [--status-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | No | string | None | Filter by fleet |
| `--game-session-id` | No | string | None | Specific game session ID |
| `--alias-id` | No | string | None | Filter by alias |
| `--location` | No | string | None | Filter by location |
| `--status-filter` | No | string | None | `ACTIVE`, `ACTIVATING`, `TERMINATED`, `TERMINATING`, `ERROR` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GameSessions": [
        {
            "GameSessionId": "string",
            "Name": "string",
            "FleetId": "string",
            "FleetArn": "string",
            "Status": "string",
            "CurrentPlayerSessionCount": "integer",
            "MaximumPlayerSessionCount": "integer",
            "IpAddress": "string",
            "DnsName": "string",
            "Port": "integer",
            "Location": "string",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.3 `describe-game-session-details`

Retrieves game sessions with their protection policy information. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-game-session-details \
    [--fleet-id <value>] \
    [--game-session-id <value>] \
    [--alias-id <value>] \
    [--location <value>] \
    [--status-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | No | string | None | Filter by fleet |
| `--game-session-id` | No | string | None | Specific game session |
| `--alias-id` | No | string | None | Filter by alias |
| `--location` | No | string | None | Filter by location |
| `--status-filter` | No | string | None | Filter by status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GameSessionDetails": [
        {
            "GameSession": {
                "GameSessionId": "string",
                "Name": "string",
                "FleetId": "string",
                "Status": "string",
                "IpAddress": "string",
                "Port": "integer"
            },
            "ProtectionPolicy": "NoProtection|FullProtection"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `search-game-sessions`

Searches for game sessions based on a set of search criteria. **Paginated.**

**Synopsis:**
```bash
aws gamelift search-game-sessions \
    [--fleet-id <value>] \
    [--alias-id <value>] \
    [--location <value>] \
    [--filter-expression <value>] \
    [--sort-expression <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | No | string | None | Fleet ID or ARN |
| `--alias-id` | No | string | None | Alias ID or ARN |
| `--location` | No | string | None | Fleet location |
| `--filter-expression` | No | string | None | Search filter (e.g., `"maximumSessions>=10 AND hasAvailablePlayerSessions=true"`) |
| `--sort-expression` | No | string | None | Sort criteria (e.g., `"creationTimeMillis ASC"`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GameSessions": [
        {
            "GameSessionId": "string",
            "Name": "string",
            "FleetId": "string",
            "Status": "string",
            "CurrentPlayerSessionCount": "integer",
            "MaximumPlayerSessionCount": "integer",
            "IpAddress": "string",
            "Port": "integer",
            "Location": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `update-game-session`

Updates game session properties.

**Synopsis:**
```bash
aws gamelift update-game-session \
    --game-session-id <value> \
    [--maximum-player-session-count <value>] \
    [--name <value>] \
    [--player-session-creation-policy <value>] \
    [--protection-policy <value>] \
    [--game-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-session-id` | **Yes** | string | -- | Game session ID |
| `--maximum-player-session-count` | No | integer | None | New max player count |
| `--name` | No | string | None | New name |
| `--player-session-creation-policy` | No | string | None | `ACCEPT_ALL` or `DENY_ALL` |
| `--protection-policy` | No | string | None | `NoProtection` or `FullProtection` |
| `--game-properties` | No | list | None | Updated game properties |

**Output Schema:**
```json
{
    "GameSession": {
        "GameSessionId": "string",
        "Name": "string",
        "FleetId": "string",
        "Status": "string",
        "MaximumPlayerSessionCount": "integer",
        "PlayerSessionCreationPolicy": "string"
    }
}
```

---

### 4.6 `terminate-game-session`

Terminates an active game session, forcing all players to disconnect.

**Synopsis:**
```bash
aws gamelift terminate-game-session \
    --game-session-id <value> \
    [--termination-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-session-id` | **Yes** | string | -- | Game session ID |
| `--termination-mode` | No | string | None | `TRIGGER_ON_PROCESS_TERMINATE` or `FORCE_TERMINATE` |

**Output Schema:**
```json
{
    "GameSession": {
        "GameSessionId": "string",
        "Status": "string",
        "StatusReason": "string"
    }
}
```

---

### 4.7 `get-game-session-log`

**Deprecated.** Downloads game session logs. Use `get-game-session-log-url` instead.

**Synopsis:**
```bash
aws gamelift get-game-session-log \
    --game-session-id <value> \
    --save-as <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-session-id` | **Yes** | string | -- | Game session ID |
| `--save-as` | **Yes** | string | -- | Local file path to save the log |

**Output Schema:**
```json
None (downloads file to --save-as path)
```

---

### 4.8 `get-game-session-log-url`

Retrieves a presigned S3 URL for downloading game session logs.

**Synopsis:**
```bash
aws gamelift get-game-session-log-url \
    --game-session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-session-id` | **Yes** | string | -- | Game session ID |

**Output Schema:**
```json
{
    "PreSignedUrl": "string"
}
```

---

### 4.9 `describe-game-session-placement`

Retrieves details of a game session placement request.

**Synopsis:**
```bash
aws gamelift describe-game-session-placement \
    --placement-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--placement-id` | **Yes** | string | -- | Placement request ID |

**Output Schema:**
```json
{
    "GameSessionPlacement": {
        "PlacementId": "string",
        "GameSessionQueueName": "string",
        "Status": "PENDING|FULFILLED|CANCELLED|TIMED_OUT|FAILED",
        "GameProperties": [],
        "MaximumPlayerSessionCount": "integer",
        "GameSessionName": "string",
        "GameSessionId": "string",
        "GameSessionArn": "string",
        "GameSessionRegion": "string",
        "PlayerLatencies": [
            {"PlayerId": "string", "RegionIdentifier": "string", "LatencyInMilliseconds": "float"}
        ],
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "IpAddress": "string",
        "DnsName": "string",
        "Port": "integer",
        "PlacedPlayerSessions": [
            {"PlayerId": "string", "PlayerSessionId": "string"}
        ],
        "GameSessionData": "string",
        "MatchmakerData": "string"
    }
}
```

---

### 4.10 `start-game-session-placement`

Places a request in a game session queue to find a fleet and create a game session.

**Synopsis:**
```bash
aws gamelift start-game-session-placement \
    --placement-id <value> \
    --game-session-queue-name <value> \
    --maximum-player-session-count <value> \
    [--game-properties <value>] \
    [--game-session-name <value>] \
    [--player-latencies <value>] \
    [--desired-player-sessions <value>] \
    [--game-session-data <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--placement-id` | **Yes** | string | -- | Unique placement request ID (1-48 chars) |
| `--game-session-queue-name` | **Yes** | string | -- | Queue name or ARN |
| `--maximum-player-session-count` | **Yes** | integer | -- | Max player count |
| `--game-properties` | No | list | None | Game properties (max 16) |
| `--game-session-name` | No | string | None | Game session name |
| `--player-latencies` | No | list | None | Latency data. Shorthand: `PlayerId=string,RegionIdentifier=string,LatencyInMilliseconds=float` |
| `--desired-player-sessions` | No | list | None | Players to reserve slots for. Shorthand: `PlayerId=string,PlayerData=string` |
| `--game-session-data` | No | string | None | Custom data string |

**Output Schema:**
```json
{
    "GameSessionPlacement": {
        "PlacementId": "string",
        "GameSessionQueueName": "string",
        "Status": "PENDING|FULFILLED|CANCELLED|TIMED_OUT|FAILED",
        "MaximumPlayerSessionCount": "integer",
        "StartTime": "timestamp"
    }
}
```

---

### 4.11 `stop-game-session-placement`

Cancels a game session placement request.

**Synopsis:**
```bash
aws gamelift stop-game-session-placement \
    --placement-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--placement-id` | **Yes** | string | -- | Placement request ID to cancel |

**Output Schema:**
```json
{
    "GameSessionPlacement": {
        "PlacementId": "string",
        "Status": "CANCELLED"
    }
}
```

---

### 4.12 `create-game-session-queue`

Creates a game session placement queue for multi-fleet game session placement.

**Synopsis:**
```bash
aws gamelift create-game-session-queue \
    --name <value> \
    [--timeout-in-seconds <value>] \
    [--player-latency-policies <value>] \
    [--destinations <value>] \
    [--filter-configuration <value>] \
    [--priority-configuration <value>] \
    [--custom-event-data <value>] \
    [--notification-target <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Queue name (1-128 chars) |
| `--timeout-in-seconds` | No | integer | None | Placement timeout in seconds |
| `--player-latency-policies` | No | list | None | Latency policies. Shorthand: `MaximumIndividualPlayerLatencyMilliseconds=int,PolicyDurationSeconds=int` |
| `--destinations` | No | list | None | Fleet/alias destinations. Shorthand: `DestinationArn=string` |
| `--filter-configuration` | No | structure | None | Location filters. Shorthand: `AllowedLocations=string,string` |
| `--priority-configuration` | No | structure | None | Priority settings (JSON) |
| `--custom-event-data` | No | string | None | Custom data for events (max 256 chars) |
| `--notification-target` | No | string | None | SNS topic ARN |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "GameSessionQueue": {
        "Name": "string",
        "GameSessionQueueArn": "string",
        "TimeoutInSeconds": "integer",
        "PlayerLatencyPolicies": [],
        "Destinations": [
            {"DestinationArn": "string"}
        ],
        "FilterConfiguration": {
            "AllowedLocations": ["string"]
        },
        "PriorityConfiguration": {
            "PriorityOrder": ["string"],
            "LocationOrder": ["string"]
        },
        "CustomEventData": "string",
        "NotificationTarget": "string"
    }
}
```

---

### 4.13 `delete-game-session-queue`

Deletes a game session queue.

**Synopsis:**
```bash
aws gamelift delete-game-session-queue \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Queue name or ARN |

**Output Schema:**
```json
None
```

---

### 4.14 `describe-game-session-queues`

Retrieves properties for game session queues. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-game-session-queues \
    [--names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | No | list(string) | None | Queue names or ARNs (omit for all) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GameSessionQueues": [
        {
            "Name": "string",
            "GameSessionQueueArn": "string",
            "TimeoutInSeconds": "integer",
            "PlayerLatencyPolicies": [],
            "Destinations": [],
            "FilterConfiguration": {},
            "PriorityConfiguration": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 4.15 `update-game-session-queue`

Updates properties for a game session queue.

**Synopsis:**
```bash
aws gamelift update-game-session-queue \
    --name <value> \
    [--timeout-in-seconds <value>] \
    [--player-latency-policies <value>] \
    [--destinations <value>] \
    [--filter-configuration <value>] \
    [--priority-configuration <value>] \
    [--custom-event-data <value>] \
    [--notification-target <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Queue name or ARN |
| `--timeout-in-seconds` | No | integer | None | New timeout |
| `--player-latency-policies` | No | list | None | New latency policies |
| `--destinations` | No | list | None | New destinations |
| `--filter-configuration` | No | structure | None | New filter config |
| `--priority-configuration` | No | structure | None | New priority config |
| `--custom-event-data` | No | string | None | New custom event data |
| `--notification-target` | No | string | None | New SNS topic ARN |

**Output Schema:**
```json
{
    "GameSessionQueue": {
        "Name": "string",
        "GameSessionQueueArn": "string",
        "TimeoutInSeconds": "integer",
        "PlayerLatencyPolicies": [],
        "Destinations": [],
        "FilterConfiguration": {},
        "PriorityConfiguration": {}
    }
}
```
