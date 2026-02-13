# Change Sets

### 2.1 `start-change-set`

Creates and starts a new change set for entity updates. Entities targeted by a change set are locked until the change set completes, is cancelled, or fails.

**Synopsis:**
```bash
aws marketplace-catalog start-change-set \
    --catalog <value> \
    --change-set <value> \
    [--change-set-name <value>] \
    [--client-request-token <value>] \
    [--change-set-tags <value>] \
    [--intent <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog` | **Yes** | string | -- | Fixed value: `AWSMarketplace` |
| `--change-set` | **Yes** | list | -- | Array of change objects (1-20 items) |
| `--change-set-name` | No | string | None | Name for the change set (1-100 chars, used for filtering) |
| `--client-request-token` | No | string | None | Unique token for idempotency (1-64 chars) |
| `--change-set-tags` | No | list | None | Tags for the change set (1-200 key-value pairs) |
| `--intent` | No | string | `APPLY` | Request intent: `VALIDATE` (dry run) or `APPLY` (execute) |

**Change Object Structure:**
```json
[
    {
        "ChangeType": "string",
        "Entity": {
            "Type": "string",
            "Identifier": "string"
        },
        "EntityTags": [
            {
                "Key": "string",
                "Value": "string"
            }
        ],
        "Details": "string",
        "DetailsDocument": {},
        "ChangeName": "string"
    }
]
```

| Field | Required | Description |
|-------|----------|-------------|
| `ChangeType` | **Yes** | Change type (e.g., `UpdateInformation`, `AddDeliveryOptions`) |
| `Entity.Type` | **Yes** | Entity type with version (e.g., `AmiProduct@1.0`) |
| `Entity.Identifier` | No | Entity ID (omit for creation) |
| `EntityTags` | No | Tags to apply to the entity (1-200) |
| `Details` | No | JSON string with change details (max 16384 chars) |
| `DetailsDocument` | No | Native JSON alternative to `Details` |
| `ChangeName` | No | Name for this individual change (1-72 chars) |

**Output Schema:**
```json
{
    "ChangeSetId": "string",
    "ChangeSetArn": "string"
}
```

---

### 2.2 `cancel-change-set`

Cancels an open change request. Must be sent before the status changes to `APPLYING`.

**Synopsis:**
```bash
aws marketplace-catalog cancel-change-set \
    --catalog <value> \
    --change-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog` | **Yes** | string | -- | Fixed value: `AWSMarketplace` |
| `--change-set-id` | **Yes** | string | -- | The unique identifier of the change set to cancel |

**Output Schema:**
```json
{
    "ChangeSetId": "string",
    "ChangeSetArn": "string"
}
```

---

### 2.3 `describe-change-set`

Returns the details and current status of a change set. Change sets are retained for 60 days.

**Synopsis:**
```bash
aws marketplace-catalog describe-change-set \
    --catalog <value> \
    --change-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog` | **Yes** | string | -- | Fixed value: `AWSMarketplace` |
| `--change-set-id` | **Yes** | string | -- | The unique identifier of the change set to describe |

**Output Schema:**
```json
{
    "ChangeSetId": "string",
    "ChangeSetArn": "string",
    "ChangeSetName": "string",
    "Intent": "VALIDATE|APPLY",
    "StartTime": "string",
    "EndTime": "string",
    "Status": "PREPARING|APPLYING|SUCCEEDED|CANCELLED|FAILED",
    "FailureCode": "CLIENT_ERROR|SERVER_FAULT",
    "FailureDescription": "string",
    "ChangeSet": [
        {
            "ChangeType": "string",
            "Entity": {
                "Type": "string",
                "Identifier": "string"
            },
            "Details": "string",
            "DetailsDocument": {},
            "ErrorDetailList": [
                {
                    "ErrorCode": "string",
                    "ErrorMessage": "string"
                }
            ],
            "ChangeName": "string"
        }
    ]
}
```

---

### 2.4 `list-change-sets`

Lists change sets with optional filters. **Paginated operation.** Change sets are retained for 60 days.

**Synopsis:**
```bash
aws marketplace-catalog list-change-sets \
    --catalog <value> \
    [--filter-list <value>] \
    [--sort <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog` | **Yes** | string | -- | Fixed value: `AWSMarketplace` |
| `--filter-list` | No | list | None | Array of filter objects (max 8). Shorthand: `Name=string,ValueList=string,string ...` |
| `--sort` | No | structure | None | Sort criteria. Shorthand: `SortBy=string,SortOrder=ASCENDING\|DESCENDING` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Supported Filters:**
| Filter Name | Description |
|-------------|-------------|
| `ChangeSetName` | Filter by change set name |
| `Status` | Filter by status: `PREPARING`, `APPLYING`, `SUCCEEDED`, `CANCELLED`, `FAILED` |
| `EntityId` | Filter by entity ID |
| `BeforeStartTime` | Change sets started before this time |
| `AfterStartTime` | Change sets started after this time |
| `BeforeEndTime` | Change sets ended before this time |
| `AfterEndTime` | Change sets ended after this time |

**Sort Options:**
- `SortBy`: `StartTime` or `EndTime`
- `SortOrder`: `ASCENDING` or `DESCENDING` (default)

**Output Schema:**
```json
{
    "ChangeSetSummaryList": [
        {
            "ChangeSetId": "string",
            "ChangeSetArn": "string",
            "ChangeSetName": "string",
            "StartTime": "string",
            "EndTime": "string",
            "Status": "PREPARING|APPLYING|SUCCEEDED|CANCELLED|FAILED",
            "EntityIdList": ["string"],
            "FailureCode": "CLIENT_ERROR|SERVER_FAULT"
        }
    ],
    "NextToken": "string"
}
```
