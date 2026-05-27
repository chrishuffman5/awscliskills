# Player Sessions

### 5.1 `create-player-session`

Reserves a slot in a game session for a single player.

**Synopsis:**
```bash
aws gamelift create-player-session \
    --game-session-id <value> \
    --player-id <value> \
    [--player-data <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-session-id` | **Yes** | string | -- | Game session ID |
| `--player-id` | **Yes** | string | -- | Unique player identifier (1-1024 chars) |
| `--player-data` | No | string | None | Developer-defined player data (1-2048 chars) |

**Output Schema:**
```json
{
    "PlayerSession": {
        "PlayerSessionId": "string",
        "PlayerId": "string",
        "GameSessionId": "string",
        "FleetId": "string",
        "FleetArn": "string",
        "CreationTime": "timestamp",
        "TerminationTime": "timestamp",
        "Status": "RESERVED|ACTIVE|COMPLETED|TIMEDOUT",
        "IpAddress": "string",
        "DnsName": "string",
        "Port": "integer",
        "PlayerData": "string"
    }
}
```

---

### 5.2 `create-player-sessions`

Reserves slots in a game session for multiple players in a single call.

**Synopsis:**
```bash
aws gamelift create-player-sessions \
    --game-session-id <value> \
    --player-ids <value> \
    [--player-data-map <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-session-id` | **Yes** | string | -- | Game session ID |
| `--player-ids` | **Yes** | list(string) | -- | List of unique player IDs (1-25 players) |
| `--player-data-map` | No | map | None | Map of player ID to player data. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "PlayerSessions": [
        {
            "PlayerSessionId": "string",
            "PlayerId": "string",
            "GameSessionId": "string",
            "FleetId": "string",
            "FleetArn": "string",
            "CreationTime": "timestamp",
            "Status": "RESERVED|ACTIVE|COMPLETED|TIMEDOUT",
            "IpAddress": "string",
            "DnsName": "string",
            "Port": "integer",
            "PlayerData": "string"
        }
    ]
}
```

---

### 5.3 `describe-player-sessions`

Retrieves player session properties. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-player-sessions \
    [--game-session-id <value>] \
    [--player-id <value>] \
    [--player-session-id <value>] \
    [--player-session-status-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--game-session-id` | No | string | None | Filter by game session |
| `--player-id` | No | string | None | Filter by player |
| `--player-session-id` | No | string | None | Specific player session |
| `--player-session-status-filter` | No | string | None | `RESERVED`, `ACTIVE`, `COMPLETED`, `TIMEDOUT` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PlayerSessions": [
        {
            "PlayerSessionId": "string",
            "PlayerId": "string",
            "GameSessionId": "string",
            "FleetId": "string",
            "FleetArn": "string",
            "CreationTime": "timestamp",
            "TerminationTime": "timestamp",
            "Status": "RESERVED|ACTIVE|COMPLETED|TIMEDOUT",
            "IpAddress": "string",
            "DnsName": "string",
            "Port": "integer",
            "PlayerData": "string"
        }
    ],
    "NextToken": "string"
}
```
