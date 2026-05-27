# Handshakes

### 5.1 `accept-handshake`

Accepts a handshake request (such as an invitation to join an organization).

**Synopsis:**
```bash
aws organizations accept-handshake \
    --handshake-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--handshake-id` | **Yes** | string | -- | ID of the handshake to accept (e.g., `h-abc12345`) |

**Output Schema:**
```json
{
    "Handshake": {
        "Id": "string",
        "Arn": "string",
        "Parties": [
            {
                "Id": "string",
                "Type": "ACCOUNT|ORGANIZATION|EMAIL"
            }
        ],
        "State": "REQUESTED|OPEN|CANCELED|ACCEPTED|DECLINED|EXPIRED",
        "RequestedTimestamp": "timestamp",
        "ExpirationTimestamp": "timestamp",
        "Action": "INVITE|ENABLE_ALL_FEATURES|APPROVE_ALL_FEATURES|ADD_ORGANIZATIONS_SERVICE_LINKED_ROLE",
        "Resources": [
            {
                "Value": "string",
                "Type": "ACCOUNT|ORGANIZATION|ORGANIZATION_FEATURE_SET|EMAIL|MASTER_EMAIL|MASTER_NAME|NOTES|PARENT_HANDSHAKE",
                "Resources": []
            }
        ]
    }
}
```

---

### 5.2 `cancel-handshake`

Cancels a handshake that was previously sent. Only the sender can cancel a handshake.

**Synopsis:**
```bash
aws organizations cancel-handshake \
    --handshake-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--handshake-id` | **Yes** | string | -- | ID of the handshake to cancel |

**Output Schema:**
```json
{
    "Handshake": {
        "Id": "string",
        "Arn": "string",
        "Parties": [],
        "State": "CANCELED",
        "RequestedTimestamp": "timestamp",
        "ExpirationTimestamp": "timestamp",
        "Action": "string",
        "Resources": []
    }
}
```

---

### 5.3 `decline-handshake`

Declines a handshake request. Only the recipient can decline.

**Synopsis:**
```bash
aws organizations decline-handshake \
    --handshake-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--handshake-id` | **Yes** | string | -- | ID of the handshake to decline |

**Output Schema:**
```json
{
    "Handshake": {
        "Id": "string",
        "Arn": "string",
        "Parties": [],
        "State": "DECLINED",
        "RequestedTimestamp": "timestamp",
        "ExpirationTimestamp": "timestamp",
        "Action": "string",
        "Resources": []
    }
}
```

---

### 5.4 `describe-handshake`

Retrieves information about a handshake.

**Synopsis:**
```bash
aws organizations describe-handshake \
    --handshake-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--handshake-id` | **Yes** | string | -- | ID of the handshake |

**Output Schema:**
```json
{
    "Handshake": {
        "Id": "string",
        "Arn": "string",
        "Parties": [
            {
                "Id": "string",
                "Type": "ACCOUNT|ORGANIZATION|EMAIL"
            }
        ],
        "State": "REQUESTED|OPEN|CANCELED|ACCEPTED|DECLINED|EXPIRED",
        "RequestedTimestamp": "timestamp",
        "ExpirationTimestamp": "timestamp",
        "Action": "INVITE|ENABLE_ALL_FEATURES|APPROVE_ALL_FEATURES|ADD_ORGANIZATIONS_SERVICE_LINKED_ROLE",
        "Resources": []
    }
}
```

---

### 5.5 `list-handshakes-for-account`

Lists handshakes sent to or from the calling account. **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-handshakes-for-account \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | None | Filter by action type or parent handshake ID. Shorthand: `ActionType=string,ParentHandshakeId=string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Handshakes": [
        {
            "Id": "string",
            "Arn": "string",
            "Parties": [],
            "State": "string",
            "RequestedTimestamp": "timestamp",
            "ExpirationTimestamp": "timestamp",
            "Action": "string",
            "Resources": []
        }
    ],
    "NextToken": "string"
}
```

---

### 5.6 `list-handshakes-for-organization`

Lists all handshakes for the organization. Must be called from the management account. **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-handshakes-for-organization \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | None | Filter by action type or parent handshake ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Handshakes": [
        {
            "Id": "string",
            "Arn": "string",
            "Parties": [],
            "State": "string",
            "RequestedTimestamp": "timestamp",
            "ExpirationTimestamp": "timestamp",
            "Action": "string",
            "Resources": []
        }
    ],
    "NextToken": "string"
}
```
