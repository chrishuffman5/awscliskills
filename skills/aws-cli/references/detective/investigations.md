# Investigations

### 3.1 `start-investigation`

Creates and starts a new investigation for the specified entity.

**Synopsis:**
```bash
aws detective start-investigation \
    --graph-arn <value> \
    --entity-arn <value> \
    --scope-start-time <value> \
    --scope-end-time <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--entity-arn` | **Yes** | string | -- | ARN of the entity to investigate (IAM user/role, IP address, etc.) |
| `--scope-start-time` | **Yes** | timestamp | -- | Start time of the investigation scope (ISO 8601) |
| `--scope-end-time` | **Yes** | timestamp | -- | End time of the investigation scope (ISO 8601) |

**Output Schema:**
```json
{
    "InvestigationId": "string"
}
```

---

### 3.2 `get-investigation`

Returns the investigation results for a specified investigation.

**Synopsis:**
```bash
aws detective get-investigation \
    --graph-arn <value> \
    --investigation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--investigation-id` | **Yes** | string | -- | Investigation ID |

**Output Schema:**
```json
{
    "GraphArn": "string",
    "InvestigationId": "string",
    "EntityArn": "string",
    "EntityType": "IAM_ROLE|IAM_USER",
    "CreatedTime": "timestamp",
    "ScopeStartTime": "timestamp",
    "ScopeEndTime": "timestamp",
    "Status": "RUNNING|FAILED|SUCCESSFUL",
    "Severity": "INFORMATIONAL|LOW|MEDIUM|HIGH|CRITICAL",
    "State": "ACTIVE|ARCHIVED"
}
```

---

### 3.3 `list-investigations`

Lists all investigations in a behavior graph. **Paginated operation.**

**Synopsis:**
```bash
aws detective list-investigations \
    --graph-arn <value> \
    [--filter-criteria <value>] \
    [--sort-criteria <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--filter-criteria` | No | structure | None | Filter criteria for investigations |
| `--sort-criteria` | No | structure | None | Sort criteria |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Criteria Structure:**
```json
{
    "Severity": {
        "Value": "string"
    },
    "Status": {
        "Value": "string"
    },
    "State": {
        "Value": "string"
    },
    "EntityArn": {
        "Value": "string"
    },
    "CreatedTime": {
        "StartInclusive": "timestamp",
        "EndInclusive": "timestamp"
    }
}
```

**Sort Criteria Structure:**
```json
{
    "Field": "SEVERITY|STATUS|CREATED_TIME",
    "SortOrder": "ASC|DESC"
}
```

**Output Schema:**
```json
{
    "InvestigationDetails": [
        {
            "InvestigationId": "string",
            "Severity": "INFORMATIONAL|LOW|MEDIUM|HIGH|CRITICAL",
            "Status": "RUNNING|FAILED|SUCCESSFUL",
            "State": "ACTIVE|ARCHIVED",
            "CreatedTime": "timestamp",
            "EntityArn": "string",
            "EntityType": "IAM_ROLE|IAM_USER"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `update-investigation-state`

Updates the state of an investigation (active or archived).

**Synopsis:**
```bash
aws detective update-investigation-state \
    --graph-arn <value> \
    --investigation-id <value> \
    --state <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--investigation-id` | **Yes** | string | -- | Investigation ID |
| `--state` | **Yes** | string | -- | New state: `ACTIVE` or `ARCHIVED` |

**Output:** None (HTTP 200 on success)

---

### 3.5 `list-indicators`

Lists indicators of compromise associated with an investigation. **Paginated operation.**

**Synopsis:**
```bash
aws detective list-indicators \
    --graph-arn <value> \
    --investigation-id <value> \
    [--indicator-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--investigation-id` | **Yes** | string | -- | Investigation ID |
| `--indicator-type` | No | string | None | Filter by indicator type: `TTP_OBSERVED`, `IMPOSSIBLE_TRAVEL`, `FLAGGED_IP_ADDRESS`, `NEW_GEOLOCATION`, `NEW_ASO`, `NEW_USER_AGENT`, `RELATED_FINDING`, `RELATED_FINDING_GROUP` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GraphArn": "string",
    "InvestigationId": "string",
    "Indicators": [
        {
            "IndicatorType": "TTP_OBSERVED|IMPOSSIBLE_TRAVEL|FLAGGED_IP_ADDRESS|NEW_GEOLOCATION|NEW_ASO|NEW_USER_AGENT|RELATED_FINDING|RELATED_FINDING_GROUP",
            "IndicatorDetail": {
                "TTPsObservedDetail": {
                    "Tactic": "string",
                    "Technique": "string",
                    "Procedure": "string",
                    "IpAddress": "string",
                    "APIName": "string",
                    "APISuccessCount": "long",
                    "APIFailureCount": "long"
                },
                "ImpossibleTravelDetail": {
                    "StartingIpAddress": "string",
                    "EndingIpAddress": "string",
                    "StartingLocation": "string",
                    "EndingLocation": "string",
                    "HourlyTimeDelta": "integer"
                },
                "FlaggedIpAddressDetail": {
                    "IpAddress": "string",
                    "Reason": "AWS_THREAT_INTELLIGENCE"
                },
                "NewGeolocationDetail": {
                    "Location": "string",
                    "IpAddress": "string",
                    "IsNewForEntireAccount": "boolean"
                },
                "NewAsoDetail": {
                    "Aso": "string",
                    "IsNewForEntireAccount": "boolean"
                },
                "NewUserAgentDetail": {
                    "UserAgent": "string",
                    "IsNewForEntireAccount": "boolean"
                },
                "RelatedFindingDetail": {
                    "Arn": "string",
                    "Type": "string",
                    "IpAddress": "string"
                },
                "RelatedFindingGroupDetail": {
                    "Id": "string"
                }
            }
        }
    ],
    "NextToken": "string"
}
```
