# Memberships

## 2.1 `create-membership`

Joins a collaboration by creating a membership.

**Synopsis:**
```bash
aws cleanrooms create-membership \
    --collaboration-identifier <value> \
    --query-log-status <value> \
    [--default-result-configuration <value>] \
    [--payment-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID or ARN to join |
| `--query-log-status` | **Yes** | string | -- | Query log status: `ENABLED` or `DISABLED` |
| `--default-result-configuration` | No | structure | None | Default result output configuration (S3 bucket, format) |
| `--payment-configuration` | No | structure | None | Payment responsibility settings |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "membership": {
        "id": "string",
        "arn": "string",
        "collaborationArn": "string",
        "collaborationId": "string",
        "collaborationCreatorAccountId": "string",
        "collaborationCreatorDisplayName": "string",
        "collaborationName": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "status": "ACTIVE|REMOVED|COLLABORATION_DELETED",
        "memberAbilities": ["string"],
        "queryLogStatus": "ENABLED|DISABLED",
        "defaultResultConfiguration": {},
        "paymentConfiguration": {}
    }
}
```

---

## 2.2 `delete-membership`

Leaves a collaboration by deleting membership.

**Synopsis:**
```bash
aws cleanrooms delete-membership \
    --membership-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID or ARN |

**Output Schema:**

None (HTTP 204 on success).

---

## 2.3 `get-membership`

Returns details for a membership.

**Synopsis:**
```bash
aws cleanrooms get-membership \
    --membership-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID or ARN |

**Output Schema:**
```json
{
    "membership": {
        "id": "string",
        "arn": "string",
        "collaborationArn": "string",
        "collaborationId": "string",
        "collaborationCreatorAccountId": "string",
        "collaborationCreatorDisplayName": "string",
        "collaborationName": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "status": "ACTIVE|REMOVED|COLLABORATION_DELETED",
        "memberAbilities": ["string"],
        "queryLogStatus": "string",
        "defaultResultConfiguration": {
            "outputConfiguration": {
                "s3": {
                    "resultFormat": "CSV|PARQUET",
                    "bucket": "string",
                    "keyPrefix": "string"
                }
            },
            "roleArn": "string"
        },
        "paymentConfiguration": {
            "queryCompute": {
                "isResponsible": "boolean"
            }
        }
    }
}
```

---

## 2.4 `list-memberships`

Lists all memberships for the account. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-memberships \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | None | Filter: `ACTIVE`, `REMOVED`, `COLLABORATION_DELETED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "membershipSummaries": [
        {
            "id": "string",
            "arn": "string",
            "collaborationArn": "string",
            "collaborationId": "string",
            "collaborationCreatorAccountId": "string",
            "collaborationCreatorDisplayName": "string",
            "collaborationName": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "status": "string",
            "memberAbilities": ["string"]
        }
    ],
    "nextToken": "string"
}
```

---

## 2.5 `update-membership`

Updates membership settings (query log status, default result configuration).

**Synopsis:**
```bash
aws cleanrooms update-membership \
    --membership-identifier <value> \
    [--query-log-status <value>] \
    [--default-result-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID or ARN |
| `--query-log-status` | No | string | None | `ENABLED` or `DISABLED` |
| `--default-result-configuration` | No | structure | None | Updated result output configuration |

**Output Schema:**
```json
{
    "membership": {
        "id": "string",
        "arn": "string",
        "status": "string",
        "queryLogStatus": "string",
        "defaultResultConfiguration": {},
        "updateTime": "timestamp"
    }
}
```

---

## 2.6 `delete-member`

Removes a member from a collaboration. Only the creator can remove members.

**Synopsis:**
```bash
aws cleanrooms delete-member \
    --collaboration-identifier <value> \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID or ARN |
| `--account-id` | **Yes** | string | -- | AWS account ID of the member to remove |

**Output Schema:**

None (HTTP 204 on success).

---

## 2.7 `list-members`

Lists all members in a collaboration. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-members \
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
    "memberSummaries": [
        {
            "accountId": "string",
            "status": "INVITED|ACTIVE|LEFT|REMOVED",
            "displayName": "string",
            "abilities": ["string"],
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "membershipId": "string",
            "membershipArn": "string",
            "paymentConfiguration": {}
        }
    ],
    "nextToken": "string"
}
```
