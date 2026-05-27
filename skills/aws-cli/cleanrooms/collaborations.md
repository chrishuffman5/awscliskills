# Collaborations

## 1.1 `create-collaboration`

Creates a new Clean Rooms collaboration.

**Synopsis:**
```bash
aws cleanrooms create-collaboration \
    --name <value> \
    --members <value> \
    --creator-member-abilities <value> \
    --creator-display-name <value> \
    --query-log-status <value> \
    [--description <value>] \
    [--data-encryption-metadata <value>] \
    [--creator-payment-configuration <value>] \
    [--analytics-engine <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Collaboration name (1-100 chars) |
| `--members` | **Yes** | list | -- | List of member specifications |
| `--creator-member-abilities` | **Yes** | list(string) | -- | Creator abilities: `CAN_QUERY`, `CAN_RECEIVE_RESULTS` |
| `--creator-display-name` | **Yes** | string | -- | Display name for the creator |
| `--query-log-status` | **Yes** | string | -- | Query log status: `ENABLED` or `DISABLED` |
| `--description` | No | string | None | Description (max 255 chars) |
| `--data-encryption-metadata` | No | structure | None | Data encryption settings |
| `--creator-payment-configuration` | No | structure | None | Payment configuration for the creator |
| `--analytics-engine` | No | string | None | Analytics engine: `SPARK` or `CLEAN_ROOMS_SQL` |
| `--tags` | No | map | None | Key-value tags |

**Members Structure:**
```json
[
    {
        "AccountId": "123456789012",
        "MemberAbilities": ["CAN_QUERY", "CAN_RECEIVE_RESULTS"],
        "DisplayName": "Partner Org",
        "PaymentConfiguration": {
            "QueryCompute": {
                "IsResponsible": true
            }
        }
    }
]
```

**Output Schema:**
```json
{
    "collaboration": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "creatorAccountId": "string",
        "creatorDisplayName": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "memberStatus": "INVITED|ACTIVE|LEFT|REMOVED",
        "membershipId": "string",
        "membershipArn": "string",
        "dataEncryptionMetadata": {},
        "queryLogStatus": "ENABLED|DISABLED",
        "analyticsEngine": "SPARK|CLEAN_ROOMS_SQL"
    }
}
```

---

## 1.2 `delete-collaboration`

Deletes a collaboration. Only the creator can delete.

**Synopsis:**
```bash
aws cleanrooms delete-collaboration \
    --collaboration-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID or ARN |

**Output Schema:**

None (HTTP 204 on success).

---

## 1.3 `get-collaboration`

Returns details for a collaboration.

**Synopsis:**
```bash
aws cleanrooms get-collaboration \
    --collaboration-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID or ARN |

**Output Schema:**
```json
{
    "collaboration": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "creatorAccountId": "string",
        "creatorDisplayName": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "memberStatus": "INVITED|ACTIVE|LEFT|REMOVED",
        "membershipId": "string",
        "membershipArn": "string",
        "dataEncryptionMetadata": {
            "allowCleartext": "boolean",
            "allowDuplicates": "boolean",
            "allowJoinsOnColumnsWithDifferentNames": "boolean",
            "preserveNulls": "boolean"
        },
        "queryLogStatus": "ENABLED|DISABLED",
        "analyticsEngine": "string"
    }
}
```

---

## 1.4 `list-collaborations`

Lists collaborations the account is a part of. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-collaborations \
    [--member-status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--member-status` | No | string | None | Filter: `ACTIVE`, `INVITED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "collaborationList": [
        {
            "id": "string",
            "arn": "string",
            "name": "string",
            "creatorAccountId": "string",
            "creatorDisplayName": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "memberStatus": "string",
            "membershipId": "string",
            "membershipArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 1.5 `update-collaboration`

Updates a collaboration's name or description.

**Synopsis:**
```bash
aws cleanrooms update-collaboration \
    --collaboration-identifier <value> \
    [--name <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID or ARN |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "collaboration": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "creatorAccountId": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

## 1.6 `create-collaboration-change-request`

Creates a change request for a collaboration.

**Synopsis:**
```bash
aws cleanrooms create-collaboration-change-request \
    --collaboration-identifier <value> \
    --changes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID or ARN |
| `--changes` | **Yes** | list | -- | List of proposed changes |

**Output Schema:**
```json
{
    "collaborationChangeRequest": {
        "identifier": "string",
        "collaborationIdentifier": "string",
        "status": "string",
        "changes": [],
        "creatorAccountId": "string",
        "createTime": "timestamp"
    }
}
```

---

## 1.7 `get-collaboration-change-request`

Gets details of a change request.

**Synopsis:**
```bash
aws cleanrooms get-collaboration-change-request \
    --collaboration-identifier <value> \
    --change-request-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID or ARN |
| `--change-request-identifier` | **Yes** | string | -- | Change request ID |

**Output Schema:**
```json
{
    "collaborationChangeRequest": {
        "identifier": "string",
        "collaborationIdentifier": "string",
        "status": "string",
        "changes": [],
        "creatorAccountId": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

## 1.8 `list-collaboration-change-requests`

Lists change requests for a collaboration. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-collaboration-change-requests \
    --collaboration-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID or ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "collaborationChangeRequestSummaries": [
        {
            "identifier": "string",
            "collaborationIdentifier": "string",
            "status": "string",
            "creatorAccountId": "string",
            "createTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 1.9 `update-collaboration-change-request`

Updates a change request (approve or reject).

**Synopsis:**
```bash
aws cleanrooms update-collaboration-change-request \
    --collaboration-identifier <value> \
    --change-request-identifier <value> \
    --changes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID or ARN |
| `--change-request-identifier` | **Yes** | string | -- | Change request ID |
| `--changes` | **Yes** | list | -- | Updated change decisions |

**Output Schema:**
```json
{
    "collaborationChangeRequest": {
        "identifier": "string",
        "collaborationIdentifier": "string",
        "status": "string",
        "changes": [],
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```
