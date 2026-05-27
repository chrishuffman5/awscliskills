# Events

### 2.1 `list-health-events`

Lists all health events for a monitor. **Paginated operation.**

**Synopsis:**
```bash
aws internetmonitor list-health-events \
    --monitor-name <value> \
    [--start-time <value>] \
    [--end-time <value>] \
    [--event-status <value>] \
    [--linked-account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name (1-255 chars) |
| `--start-time` | No | timestamp | -- | Start time for filtering events |
| `--end-time` | No | timestamp | -- | End time for filtering events |
| `--event-status` | No | string | -- | `ACTIVE` or `RESOLVED` |
| `--linked-account-id` | No | string | -- | Cross-account ID (12 digits) |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "HealthEvents": [
        {
            "EventArn": "string",
            "EventId": "string",
            "StartedAt": "timestamp",
            "EndedAt": "timestamp",
            "CreatedAt": "timestamp",
            "LastUpdatedAt": "timestamp",
            "ImpactedLocations": [
                {
                    "ASName": "string",
                    "ASNumber": "long",
                    "Country": "string",
                    "Subdivision": "string",
                    "Metro": "string",
                    "City": "string",
                    "Latitude": "double",
                    "Longitude": "double",
                    "CountryCode": "string",
                    "SubdivisionCode": "string",
                    "ServiceLocation": "string",
                    "Status": "ACTIVE|RESOLVED",
                    "CausedBy": {
                        "Networks": [
                            { "ASName": "string", "ASNumber": "long" }
                        ],
                        "AsPath": [
                            { "ASName": "string", "ASNumber": "long" }
                        ],
                        "NetworkEventType": "AWS|Internet"
                    },
                    "InternetHealth": {
                        "Availability": {
                            "ExperienceScore": "double",
                            "PercentOfTotalTrafficImpacted": "double",
                            "PercentOfClientLocationImpacted": "double"
                        },
                        "Performance": {
                            "ExperienceScore": "double",
                            "PercentOfTotalTrafficImpacted": "double",
                            "PercentOfClientLocationImpacted": "double",
                            "RoundTripTime": {
                                "P50": "double",
                                "P90": "double",
                                "P95": "double"
                            }
                        }
                    },
                    "Ipv4Prefixes": ["string"]
                }
            ],
            "Status": "ACTIVE|RESOLVED",
            "PercentOfTotalTrafficImpacted": "double",
            "ImpactType": "AVAILABILITY|PERFORMANCE|LOCAL_AVAILABILITY|LOCAL_PERFORMANCE",
            "HealthScoreThreshold": "double"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.2 `get-health-event`

Gets information about a specific health event.

**Synopsis:**
```bash
aws internetmonitor get-health-event \
    --monitor-name <value> \
    --event-id <value> \
    [--linked-account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name |
| `--event-id` | **Yes** | string | -- | Health event ID (URL-encoded, pattern: `[a-zA-Z0-9/_.-]+`) |
| `--linked-account-id` | No | string | -- | Cross-account ID (12 digits) |

**Output Schema:**
```json
{
    "EventArn": "string",
    "EventId": "string",
    "StartedAt": "timestamp",
    "EndedAt": "timestamp",
    "CreatedAt": "timestamp",
    "LastUpdatedAt": "timestamp",
    "ImpactedLocations": [
        {
            "ASName": "string",
            "ASNumber": "long",
            "Country": "string",
            "Subdivision": "string",
            "Metro": "string",
            "City": "string",
            "Latitude": "double",
            "Longitude": "double",
            "CountryCode": "string",
            "SubdivisionCode": "string",
            "ServiceLocation": "string",
            "Status": "ACTIVE|RESOLVED",
            "CausedBy": {
                "Networks": [],
                "AsPath": [],
                "NetworkEventType": "AWS|Internet"
            },
            "InternetHealth": {
                "Availability": {},
                "Performance": {}
            },
            "Ipv4Prefixes": ["string"]
        }
    ],
    "Status": "ACTIVE|RESOLVED",
    "PercentOfTotalTrafficImpacted": "double",
    "ImpactType": "AVAILABILITY|PERFORMANCE|LOCAL_AVAILABILITY|LOCAL_PERFORMANCE",
    "HealthScoreThreshold": "double"
}
```

---

### 2.3 `list-internet-events`

Lists internet events that cause performance or availability issues for global AWS client locations. **Paginated operation.**

**Synopsis:**
```bash
aws internetmonitor list-internet-events \
    [--start-time <value>] \
    [--end-time <value>] \
    [--event-status <value>] \
    [--event-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-time` | No | timestamp | -- | Start time for filtering |
| `--end-time` | No | timestamp | -- | End time for filtering |
| `--event-status` | No | string | -- | `ACTIVE` or `RESOLVED` |
| `--event-type` | No | string | -- | `AVAILABILITY` or `PERFORMANCE` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "InternetEvents": [
        {
            "EventId": "string",
            "EventArn": "string",
            "StartedAt": "timestamp",
            "EndedAt": "timestamp",
            "ClientLocation": {
                "ASName": "string",
                "ASNumber": "long",
                "Country": "string",
                "Subdivision": "string",
                "Metro": "string",
                "City": "string",
                "Latitude": "double",
                "Longitude": "double"
            },
            "EventType": "AVAILABILITY|PERFORMANCE",
            "EventStatus": "ACTIVE|RESOLVED"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `get-internet-event`

Gets information about a specific internet event.

**Synopsis:**
```bash
aws internetmonitor get-internet-event \
    --event-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-id` | **Yes** | string | -- | Internet event ID |

**Output Schema:**
```json
{
    "EventId": "string",
    "EventArn": "string",
    "StartedAt": "timestamp",
    "EndedAt": "timestamp",
    "ClientLocation": {
        "ASName": "string",
        "ASNumber": "long",
        "Country": "string",
        "Subdivision": "string",
        "Metro": "string",
        "City": "string",
        "Latitude": "double",
        "Longitude": "double"
    },
    "EventType": "AVAILABILITY|PERFORMANCE",
    "EventStatus": "ACTIVE|RESOLVED"
}
```
