# OpsItems

### 9.1 `create-ops-item`

Creates an OpsItem, which is an operational issue or event that needs investigation and resolution.

**Synopsis:**
```bash
aws ssm create-ops-item \
    --description <value> \
    --source <value> \
    --title <value> \
    [--ops-item-type <value>] \
    [--operational-data <value>] \
    [--notifications <value>] \
    [--priority <value>] \
    [--related-ops-items <value>] \
    [--tags <value>] \
    [--category <value>] \
    [--severity <value>] \
    [--actual-start-time <value>] \
    [--actual-end-time <value>] \
    [--planned-start-time <value>] \
    [--planned-end-time <value>] \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--description` | **Yes** | string | -- | Description of the OpsItem (max 1024 chars) |
| `--source` | **Yes** | string | -- | Source of the OpsItem (e.g. `EC2`, custom app name) |
| `--title` | **Yes** | string | -- | Title of the OpsItem (max 1024 chars) |
| `--ops-item-type` | No | string | None | OpsItem type path (e.g. `/aws/issue`) |
| `--operational-data` | No | map | None | Key-value operational data |
| `--notifications` | No | list | None | SNS topic ARNs for notifications |
| `--priority` | No | integer | None | Priority (1-5, 1 = highest) |
| `--related-ops-items` | No | list | None | Related OpsItem IDs |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--category` | No | string | None | Category |
| `--severity` | No | string | None | Severity (1-4, 1 = highest) |
| `--actual-start-time` | No | timestamp | None | Actual start time |
| `--actual-end-time` | No | timestamp | None | Actual end time |
| `--planned-start-time` | No | timestamp | None | Planned start time |
| `--planned-end-time` | No | timestamp | None | Planned end time |

**Output Schema:**
```json
{
    "OpsItemId": "string",
    "OpsItemArn": "string"
}
```

---

### 9.2 `delete-ops-item`

Deletes an OpsItem.

**Synopsis:**
```bash
aws ssm delete-ops-item \
    --ops-item-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ops-item-id` | **Yes** | string | -- | OpsItem ID to delete |

**Output Schema:**
```json
{}
```

---

### 9.3 `get-ops-item`

Gets details about a specific OpsItem.

**Synopsis:**
```bash
aws ssm get-ops-item \
    --ops-item-id <value> \
    [--ops-item-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ops-item-id` | **Yes** | string | -- | OpsItem ID |

**Output Schema:**
```json
{
    "OpsItem": {
        "CreatedBy": "string",
        "OpsItemType": "string",
        "CreatedTime": "timestamp",
        "Description": "string",
        "LastModifiedBy": "string",
        "LastModifiedTime": "timestamp",
        "Notifications": [
            {
                "Arn": "string"
            }
        ],
        "Priority": "integer",
        "RelatedOpsItems": [
            {
                "OpsItemId": "string"
            }
        ],
        "Status": "Open|InProgress|Resolved|Pending|TimedOut|Cancelling|Cancelled|Failed|CompletedWithSuccess|CompletedWithFailure|Scheduled|RunbookInProgress|PendingChangeCalendarOverride|ChangeCalendarOverrideApproved|ChangeCalendarOverrideRejected|PendingApproval|Approved|Rejected|Closed",
        "OpsItemId": "string",
        "Version": "string",
        "Title": "string",
        "Source": "string",
        "OperationalData": {},
        "Category": "string",
        "Severity": "string",
        "ActualStartTime": "timestamp",
        "ActualEndTime": "timestamp",
        "PlannedStartTime": "timestamp",
        "PlannedEndTime": "timestamp",
        "OpsItemArn": "string"
    }
}
```

---

### 9.4 `update-ops-item`

Updates an OpsItem.

**Synopsis:**
```bash
aws ssm update-ops-item \
    --ops-item-id <value> \
    [--description <value>] \
    [--operational-data <value>] \
    [--operational-data-to-delete <value>] \
    [--notifications <value>] \
    [--priority <value>] \
    [--related-ops-items <value>] \
    [--status <value>] \
    [--title <value>] \
    [--category <value>] \
    [--severity <value>] \
    [--actual-start-time <value>] \
    [--actual-end-time <value>] \
    [--planned-start-time <value>] \
    [--planned-end-time <value>] \
    [--ops-item-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ops-item-id` | **Yes** | string | -- | OpsItem ID |
| `--description` | No | string | None | Updated description |
| `--operational-data` | No | map | None | Operational data to add/update |
| `--operational-data-to-delete` | No | list(string) | None | Operational data keys to delete |
| `--notifications` | No | list | None | Updated notifications |
| `--priority` | No | integer | None | Updated priority |
| `--related-ops-items` | No | list | None | Updated related items |
| `--status` | No | string | None | Updated status |
| `--title` | No | string | None | Updated title |
| `--category` | No | string | None | Updated category |
| `--severity` | No | string | None | Updated severity |

**Output Schema:**
```json
{}
```

---

### 9.5 `describe-ops-items`

Lists OpsItems with optional filters. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-ops-items \
    [--ops-item-filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ops-item-filters` | No | list | None | Filters: `Status`, `CreatedBy`, `Source`, `Priority`, `Title`, `OpsItemId`, `CreatedTime`, `LastModifiedTime`, `ActualStartTime`, `ActualEndTime`, `PlannedStartTime`, `PlannedEndTime`, `OperationalData`, `OperationalDataKey`, `OperationalDataValue`, `ResourceId`, `AutomationType`, `Category`, `Severity`, `OpsItemType`, `ChangeRequestByRequesterArn`, `ChangeRequestByRequesterName`, `ChangeRequestByApproverArn`, `ChangeRequestByApproverName`, `ChangeRequestByTemplate`, `ChangeRequestByTargetsResourceGroup`, `InsightByType`, `AccountId` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 50) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OpsItemSummaries": [
        {
            "CreatedBy": "string",
            "CreatedTime": "timestamp",
            "LastModifiedBy": "string",
            "LastModifiedTime": "timestamp",
            "Priority": "integer",
            "Source": "string",
            "Status": "string",
            "OpsItemId": "string",
            "Title": "string",
            "OperationalData": {},
            "Category": "string",
            "Severity": "string",
            "OpsItemType": "string",
            "ActualStartTime": "timestamp",
            "ActualEndTime": "timestamp",
            "PlannedStartTime": "timestamp",
            "PlannedEndTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.6 `list-ops-item-events`

Lists events for a specific OpsItem. **Paginated operation.**

**Synopsis:**
```bash
aws ssm list-ops-item-events \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters: `OpsItemId` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Summaries": [
        {
            "OpsItemId": "string",
            "EventId": "string",
            "Source": "string",
            "DetailType": "string",
            "Detail": "string",
            "CreatedBy": {
                "Arn": "string"
            },
            "CreatedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.7 `create-ops-metadata`

Creates OpsMetadata for an application or resource.

**Synopsis:**
```bash
aws ssm create-ops-metadata \
    --resource-id <value> \
    [--metadata <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | Resource ID (SSM document ARN or application name) |
| `--metadata` | No | map | None | Metadata key-value pairs |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "OpsMetadataArn": "string"
}
```

---

### 9.8 `delete-ops-metadata`

Deletes OpsMetadata.

**Synopsis:**
```bash
aws ssm delete-ops-metadata \
    --ops-metadata-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ops-metadata-arn` | **Yes** | string | -- | OpsMetadata ARN |

**Output Schema:**
```json
{}
```

---

### 9.9 `get-ops-metadata`

Retrieves OpsMetadata.

**Synopsis:**
```bash
aws ssm get-ops-metadata \
    --ops-metadata-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ops-metadata-arn` | **Yes** | string | -- | OpsMetadata ARN |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ResourceId": "string",
    "Metadata": {
        "key": {
            "Value": "string"
        }
    },
    "NextToken": "string"
}
```

---

### 9.10 `list-ops-metadata`

Lists OpsMetadata objects. **Paginated operation.**

**Synopsis:**
```bash
aws ssm list-ops-metadata \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "OpsMetadataList": [
        {
            "ResourceId": "string",
            "OpsMetadataArn": "string",
            "LastModifiedDate": "timestamp",
            "LastModifiedUser": "string",
            "CreationDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.11 `update-ops-metadata`

Updates OpsMetadata key-value pairs.

**Synopsis:**
```bash
aws ssm update-ops-metadata \
    --ops-metadata-arn <value> \
    [--metadata-to-update <value>] \
    [--keys-to-delete <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ops-metadata-arn` | **Yes** | string | -- | OpsMetadata ARN |
| `--metadata-to-update` | No | map | None | Metadata key-value pairs to add or update |
| `--keys-to-delete` | No | list(string) | None | Metadata keys to delete |

**Output Schema:**
```json
{
    "OpsMetadataArn": "string"
}
```
