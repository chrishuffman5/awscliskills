# Proxy Sessions

Commands from the `aws chime-sdk-voice` service.

### 15.1 `create-proxy-session`

Creates a proxy session for anonymous calling between two participants.

**Synopsis:**
```bash
aws chime-sdk-voice create-proxy-session \
    --voice-connector-id <value> \
    --participant-phone-numbers <value> \
    --capabilities <value> \
    [--name <value>] \
    [--expiry-minutes <value>] \
    [--number-selection-behavior <value>] \
    [--geo-match-level <value>] \
    [--geo-match-params <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--participant-phone-numbers` | **Yes** | list | -- | Participant phone numbers (exactly 2, E.164) |
| `--capabilities` | **Yes** | list | -- | `Voice` and/or `SMS` |
| `--name` | No | string | None | Session name (max 128 chars) |
| `--expiry-minutes` | No | integer | None | Session expiry in minutes (min 1) |
| `--number-selection-behavior` | No | string | None | `PreferSticky` or `AvoidSticky` |
| `--geo-match-level` | No | string | None | `Country` or `AreaCode` |
| `--geo-match-params` | No | structure | None | Geo-match country and area code |

**GeoMatchParams:**
```json
{
    "Country": "string (ISO 3166-1 alpha-2)",
    "AreaCode": "string (3 digits)"
}
```

**Output Schema:**
```json
{
    "ProxySession": {
        "VoiceConnectorId": "string",
        "ProxySessionId": "string",
        "Name": "string",
        "Status": "Open|InProgress|Closed",
        "ExpiryMinutes": "integer",
        "Capabilities": ["Voice", "SMS"],
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp",
        "EndedTimestamp": "timestamp",
        "Participants": [
            {
                "PhoneNumber": "string",
                "ProxyPhoneNumber": "string"
            }
        ],
        "NumberSelectionBehavior": "PreferSticky|AvoidSticky",
        "GeoMatchLevel": "Country|AreaCode",
        "GeoMatchParams": {
            "Country": "string",
            "AreaCode": "string"
        }
    }
}
```

---

### 15.2 `get-proxy-session`

Gets proxy session details.

**Synopsis:**
```bash
aws chime-sdk-voice get-proxy-session \
    --voice-connector-id <value> \
    --proxy-session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--proxy-session-id` | **Yes** | string | -- | Proxy session ID |

**Output Schema:** Same as `create-proxy-session` ProxySession object.

---

### 15.3 `list-proxy-sessions`

Lists proxy sessions for a voice connector. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-voice list-proxy-sessions \
    --voice-connector-id <value> \
    [--status <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--status` | No | string | None | `Open`, `InProgress`, or `Closed` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-99) |

**Output Schema:**
```json
{
    "ProxySessions": [{ "...ProxySession..." }],
    "NextToken": "string"
}
```

---

### 15.4 `update-proxy-session`

Updates a proxy session's capabilities and expiry.

**Synopsis:**
```bash
aws chime-sdk-voice update-proxy-session \
    --voice-connector-id <value> \
    --proxy-session-id <value> \
    --capabilities <value> \
    [--expiry-minutes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--proxy-session-id` | **Yes** | string | -- | Proxy session ID |
| `--capabilities` | **Yes** | list | -- | `Voice` and/or `SMS` |
| `--expiry-minutes` | No | integer | None | Updated expiry in minutes |

**Output Schema:** Same as `create-proxy-session` ProxySession object.

---

### 15.5 `delete-proxy-session`

Deletes a proxy session.

**Synopsis:**
```bash
aws chime-sdk-voice delete-proxy-session \
    --voice-connector-id <value> \
    --proxy-session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--proxy-session-id` | **Yes** | string | -- | Proxy session ID |

**Output:** None
