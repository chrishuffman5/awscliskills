# Proxy Sessions

CLI namespace: `aws chime-sdk-voice`

### 15.1 `create-proxy-session`

Creates a proxy session for phone number masking on a Voice Connector.

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
    [--geo-match-params <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice Connector ID |
| `--participant-phone-numbers` | **Yes** | list | -- | Exactly 2 phone numbers in E.164 format |
| `--capabilities` | **Yes** | list | -- | `Voice` and/or `SMS` |
| `--name` | No | string | None | Session name (0-30 chars) |
| `--expiry-minutes` | No | integer | None | Session duration in minutes (min 1) |
| `--number-selection-behavior` | No | string | None | `PreferSticky` or `AvoidSticky` |
| `--geo-match-level` | No | string | None | `Country` or `AreaCode` |
| `--geo-match-params` | No | structure | None | Country and area code for proxy number |

**GeoMatchParams structure:**
```json
{
    "Country": "US",
    "AreaCode": "206"
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

### 15.2 `get-proxy-session` / `list-proxy-sessions`

```bash
aws chime-sdk-voice get-proxy-session \
    --voice-connector-id <value> \
    --proxy-session-id <value>

aws chime-sdk-voice list-proxy-sessions \
    --voice-connector-id <value> \
    [--status <value>] \
    [--next-token <value>] \
    [--max-results <value>]
```

**list-proxy-sessions Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice Connector ID |
| `--status` | No | string | None | `Open`, `InProgress`, or `Closed` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

---

### 15.3 `update-proxy-session`

```bash
aws chime-sdk-voice update-proxy-session \
    --voice-connector-id <value> \
    --proxy-session-id <value> \
    --capabilities <value> \
    [--expiry-minutes <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice Connector ID |
| `--proxy-session-id` | **Yes** | string | -- | Proxy session ID |
| `--capabilities` | **Yes** | list | -- | `Voice` and/or `SMS` |
| `--expiry-minutes` | No | integer | None | Updated session duration |

---

### 15.4 `delete-proxy-session`

```bash
aws chime-sdk-voice delete-proxy-session \
    --voice-connector-id <value> \
    --proxy-session-id <value>
```

**Output:** None
