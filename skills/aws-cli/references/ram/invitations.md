# Invitations

### 2.1 `accept-resource-share-invitation`

Accepts an invitation to join a resource share from another AWS account.

**Synopsis:**
```bash
aws ram accept-resource-share-invitation \
    --resource-share-invitation-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-invitation-arn` | **Yes** | string | -- | ARN of the invitation to accept |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "resourceShareInvitation": {
        "resourceShareInvitationArn": "string",
        "resourceShareName": "string",
        "resourceShareArn": "string",
        "senderAccountId": "string",
        "receiverAccountId": "string",
        "invitationTimestamp": "timestamp",
        "status": "PENDING|ACCEPTED|REJECTED|EXPIRED",
        "resourceShareAssociations": [
            {
                "resourceShareArn": "string",
                "resourceShareName": "string",
                "associatedEntity": "string",
                "associationType": "PRINCIPAL|RESOURCE|SOURCE",
                "status": "ASSOCIATING|ASSOCIATED|FAILED|DISASSOCIATING|DISASSOCIATED|SUSPENDED|SUSPENDING|RESTORING",
                "statusMessage": "string",
                "creationTime": "timestamp",
                "lastUpdatedTime": "timestamp",
                "external": "boolean"
            }
        ],
        "receiverArn": "string"
    },
    "clientToken": "string"
}
```

---

### 2.2 `reject-resource-share-invitation`

Rejects an invitation to join a resource share.

**Synopsis:**
```bash
aws ram reject-resource-share-invitation \
    --resource-share-invitation-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-invitation-arn` | **Yes** | string | -- | ARN of the invitation to reject |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "resourceShareInvitation": {
        "resourceShareInvitationArn": "string",
        "resourceShareName": "string",
        "resourceShareArn": "string",
        "senderAccountId": "string",
        "receiverAccountId": "string",
        "invitationTimestamp": "timestamp",
        "status": "PENDING|ACCEPTED|REJECTED|EXPIRED",
        "resourceShareAssociations": [],
        "receiverArn": "string"
    },
    "clientToken": "string"
}
```

---

### 2.3 `get-resource-share-invitations`

Gets the resource share invitations sent to your account or sent from your account. **Paginated operation.**

**Synopsis:**
```bash
aws ram get-resource-share-invitations \
    [--resource-share-invitation-arns <value>] \
    [--resource-share-arns <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-invitation-arns` | No | list(string) | None | Filter by invitation ARNs |
| `--resource-share-arns` | No | list(string) | None | Filter by resource share ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "resourceShareInvitations": [
        {
            "resourceShareInvitationArn": "string",
            "resourceShareName": "string",
            "resourceShareArn": "string",
            "senderAccountId": "string",
            "receiverAccountId": "string",
            "invitationTimestamp": "timestamp",
            "status": "PENDING|ACCEPTED|REJECTED|EXPIRED",
            "resourceShareAssociations": [],
            "receiverArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.4 `list-pending-invitation-resources`

Lists the resources in a proposed resource share that is pending acceptance. **Paginated operation.**

**Synopsis:**
```bash
aws ram list-pending-invitation-resources \
    --resource-share-invitation-arn <value> \
    [--resource-region-scope <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-invitation-arn` | **Yes** | string | -- | ARN of the pending invitation |
| `--resource-region-scope` | No | string | None | `ALL`, `REGIONAL`, `GLOBAL` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "resources": [
        {
            "arn": "string",
            "type": "string",
            "resourceShareArn": "string",
            "resourceGroupArn": "string",
            "status": "AVAILABLE|ZONAL_RESOURCE_INACCESSIBLE|LIMIT_EXCEEDED|UNAVAILABLE|PENDING",
            "statusMessage": "string",
            "creationTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "resourceRegionScope": "REGIONAL|GLOBAL"
        }
    ],
    "nextToken": "string"
}
```
