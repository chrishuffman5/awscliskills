# Matchmaking

### 6.1 `create-matchmaking-configuration`

Creates a FlexMatch matchmaking configuration.

**Synopsis:**
```bash
aws gamelift create-matchmaking-configuration \
    --name <value> \
    --request-timeout-seconds <value> \
    --acceptance-required | --no-acceptance-required \
    --rule-set-name <value> \
    [--description <value>] \
    [--game-session-queue-arns <value>] \
    [--acceptance-timeout-seconds <value>] \
    [--notification-target <value>] \
    [--additional-player-count <value>] \
    [--custom-event-data <value>] \
    [--game-properties <value>] \
    [--game-session-data <value>] \
    [--backfill-mode <value>] \
    [--flex-match-mode <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Unique identifier (max 128 chars, pattern: `[a-zA-Z0-9-\.]*`) |
| `--request-timeout-seconds` | **Yes** | integer | -- | Max time for matchmaking (1-43200 seconds) |
| `--acceptance-required` | **Yes** | boolean | -- | Whether players must accept matches |
| `--rule-set-name` | **Yes** | string | -- | Rule set name or ARN (1-256 chars) |
| `--description` | No | string | None | Description (1-1024 chars) |
| `--game-session-queue-arns` | No | list(string) | None | Queue ARNs for game placement |
| `--acceptance-timeout-seconds` | No | integer | None | Time to wait for acceptance (1-600 seconds) |
| `--notification-target` | No | string | None | SNS topic ARN for notifications |
| `--additional-player-count` | No | integer | None | Extra player slots to keep open |
| `--custom-event-data` | No | string | None | Custom data for events (max 256 chars) |
| `--game-properties` | No | list | None | Properties for game sessions (max 16) |
| `--game-session-data` | No | string | None | Game session data (1-4096 chars) |
| `--backfill-mode` | No | string | None | `AUTOMATIC` or `MANUAL` |
| `--flex-match-mode` | No | string | None | `STANDALONE` or `WITH_QUEUE` |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "Configuration": {
        "Name": "string",
        "ConfigurationArn": "string",
        "Description": "string",
        "GameSessionQueueArns": ["string"],
        "RequestTimeoutSeconds": "integer",
        "AcceptanceTimeoutSeconds": "integer",
        "AcceptanceRequired": "boolean",
        "RuleSetName": "string",
        "RuleSetArn": "string",
        "NotificationTarget": "string",
        "AdditionalPlayerCount": "integer",
        "CustomEventData": "string",
        "CreationTime": "timestamp",
        "GameProperties": [],
        "GameSessionData": "string",
        "BackfillMode": "AUTOMATIC|MANUAL",
        "FlexMatchMode": "STANDALONE|WITH_QUEUE"
    }
}
```

---

### 6.2 `delete-matchmaking-configuration`

Permanently deletes a matchmaking configuration.

**Synopsis:**
```bash
aws gamelift delete-matchmaking-configuration \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Configuration name or ARN |

**Output Schema:**
```json
None
```

---

### 6.3 `describe-matchmaking-configurations`

Retrieves matchmaking configurations. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-matchmaking-configurations \
    [--names <value>] \
    [--rule-set-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | No | list(string) | None | Configuration names (max 10) |
| `--rule-set-name` | No | string | None | Filter by rule set |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Configurations": [
        {
            "Name": "string",
            "ConfigurationArn": "string",
            "Description": "string",
            "RuleSetName": "string",
            "RequestTimeoutSeconds": "integer",
            "AcceptanceRequired": "boolean",
            "FlexMatchMode": "string",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `update-matchmaking-configuration`

Updates a matchmaking configuration.

**Synopsis:**
```bash
aws gamelift update-matchmaking-configuration \
    --name <value> \
    [--description <value>] \
    [--game-session-queue-arns <value>] \
    [--request-timeout-seconds <value>] \
    [--acceptance-timeout-seconds <value>] \
    [--acceptance-required | --no-acceptance-required] \
    [--rule-set-name <value>] \
    [--notification-target <value>] \
    [--additional-player-count <value>] \
    [--custom-event-data <value>] \
    [--game-properties <value>] \
    [--game-session-data <value>] \
    [--backfill-mode <value>] \
    [--flex-match-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Configuration name or ARN |
| `--description` | No | string | None | New description |
| `--game-session-queue-arns` | No | list(string) | None | New queue ARNs |
| `--request-timeout-seconds` | No | integer | None | New timeout |
| `--acceptance-timeout-seconds` | No | integer | None | New acceptance timeout |
| `--acceptance-required` | No | boolean | None | Whether acceptance is required |
| `--rule-set-name` | No | string | None | New rule set |
| `--notification-target` | No | string | None | New SNS topic |
| `--additional-player-count` | No | integer | None | Additional player slots |
| `--custom-event-data` | No | string | None | Custom event data |
| `--game-properties` | No | list | None | Game properties |
| `--game-session-data` | No | string | None | Game session data |
| `--backfill-mode` | No | string | None | `AUTOMATIC` or `MANUAL` |
| `--flex-match-mode` | No | string | None | `STANDALONE` or `WITH_QUEUE` |

**Output Schema:**
```json
{
    "Configuration": {
        "Name": "string",
        "ConfigurationArn": "string",
        "Description": "string",
        "RuleSetName": "string",
        "RequestTimeoutSeconds": "integer",
        "AcceptanceRequired": "boolean",
        "FlexMatchMode": "string"
    }
}
```

---

### 6.5 `create-matchmaking-rule-set`

Creates a FlexMatch rule set that defines match criteria.

**Synopsis:**
```bash
aws gamelift create-matchmaking-rule-set \
    --name <value> \
    --rule-set-body <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Rule set name (1-128 chars, pattern: `[a-zA-Z0-9-\.]*`) |
| `--rule-set-body` | **Yes** | string | -- | JSON string with rule set definition (1-65535 chars) |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "RuleSet": {
        "RuleSetName": "string",
        "RuleSetArn": "string",
        "RuleSetBody": "string",
        "CreationTime": "timestamp"
    }
}
```

---

### 6.6 `delete-matchmaking-rule-set`

Deletes a matchmaking rule set (must not be referenced by any active configuration).

**Synopsis:**
```bash
aws gamelift delete-matchmaking-rule-set \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Rule set name or ARN |

**Output Schema:**
```json
None
```

---

### 6.7 `describe-matchmaking-rule-sets`

Retrieves matchmaking rule sets. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-matchmaking-rule-sets \
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
| `--names` | No | list(string) | None | Rule set names (max 10) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RuleSets": [
        {
            "RuleSetName": "string",
            "RuleSetArn": "string",
            "RuleSetBody": "string",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.8 `validate-matchmaking-rule-set`

Validates the syntax of a matchmaking rule set definition.

**Synopsis:**
```bash
aws gamelift validate-matchmaking-rule-set \
    --rule-set-body <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-set-body` | **Yes** | string | -- | JSON rule set definition to validate |

**Output Schema:**
```json
{
    "Valid": "boolean"
}
```

---

### 6.9 `start-matchmaking`

Submits a matchmaking request using a FlexMatch configuration.

**Synopsis:**
```bash
aws gamelift start-matchmaking \
    [--ticket-id <value>] \
    --configuration-name <value> \
    --players <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ticket-id` | No | string | None | Unique ticket identifier (max 128 chars) |
| `--configuration-name` | **Yes** | string | -- | Matchmaking configuration name or ARN |
| `--players` | **Yes** | list | -- | Players to match. JSON: `[{PlayerId,PlayerAttributes,Team,LatencyInMs}]` |

**Player Structure:**
```json
{
    "PlayerId": "string",
    "PlayerAttributes": {
        "string": {"S": "string", "N": "double", "SL": ["string"], "SDM": {"string": "double"}}
    },
    "Team": "string",
    "LatencyInMs": {"string": "integer"}
}
```

**Output Schema:**
```json
{
    "MatchmakingTicket": {
        "TicketId": "string",
        "ConfigurationName": "string",
        "ConfigurationArn": "string",
        "Status": "QUEUED|SEARCHING|REQUIRES_ACCEPTANCE|PLACING|COMPLETED|CANCELLED|TIMED_OUT|FAILED",
        "StatusReason": "string",
        "StatusMessage": "string",
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "Players": [],
        "GameSessionConnectionInfo": {
            "GameSessionArn": "string",
            "IpAddress": "string",
            "DnsName": "string",
            "Port": "integer",
            "MatchedPlayerSessions": [
                {"PlayerId": "string", "PlayerSessionId": "string"}
            ]
        },
        "EstimatedWaitTime": "integer"
    }
}
```

---

### 6.10 `stop-matchmaking`

Cancels a matchmaking ticket.

**Synopsis:**
```bash
aws gamelift stop-matchmaking \
    --ticket-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ticket-id` | **Yes** | string | -- | Matchmaking ticket ID |

**Output Schema:**
```json
None
```

---

### 6.11 `start-match-backfill`

Finds new players for existing game sessions via matchmaking.

**Synopsis:**
```bash
aws gamelift start-match-backfill \
    [--ticket-id <value>] \
    --configuration-name <value> \
    [--game-session-arn <value>] \
    --players <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ticket-id` | No | string | None | Unique ticket ID |
| `--configuration-name` | **Yes** | string | -- | Matchmaking configuration name or ARN |
| `--game-session-arn` | No | string | None | Game session ARN to backfill |
| `--players` | **Yes** | list | -- | Current players in the session (JSON) |

**Output Schema:**
```json
{
    "MatchmakingTicket": {
        "TicketId": "string",
        "ConfigurationName": "string",
        "Status": "string",
        "Players": []
    }
}
```

---

### 6.12 `describe-matchmaking`

Retrieves details for one or more matchmaking tickets.

**Synopsis:**
```bash
aws gamelift describe-matchmaking \
    --ticket-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ticket-ids` | **Yes** | list(string) | -- | Matchmaking ticket IDs (max 10) |

**Output Schema:**
```json
{
    "TicketList": [
        {
            "TicketId": "string",
            "ConfigurationName": "string",
            "ConfigurationArn": "string",
            "Status": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "Players": [],
            "GameSessionConnectionInfo": {},
            "EstimatedWaitTime": "integer"
        }
    ]
}
```

---

### 6.13 `accept-match`

Accepts or rejects a proposed FlexMatch match (when acceptance is required).

**Synopsis:**
```bash
aws gamelift accept-match \
    --ticket-id <value> \
    --player-ids <value> \
    --acceptance-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ticket-id` | **Yes** | string | -- | Matchmaking ticket ID |
| `--player-ids` | **Yes** | list(string) | -- | Player IDs accepting/rejecting |
| `--acceptance-type` | **Yes** | string | -- | `ACCEPT` or `REJECT` |

**Output Schema:**
```json
None
```
