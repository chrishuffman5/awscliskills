# Organization

### 1.1 `create-organization`

Creates an AWS Organization. The account making the call becomes the management account.

**Synopsis:**
```bash
aws organizations create-organization \
    [--feature-set <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--feature-set` | No | string | `ALL` | Feature set: `ALL` or `CONSOLIDATED_BILLING` |

**Output Schema:**
```json
{
    "Organization": {
        "Id": "string",
        "Arn": "string",
        "FeatureSet": "ALL|CONSOLIDATED_BILLING",
        "MasterAccountArn": "string",
        "MasterAccountId": "string",
        "MasterAccountEmail": "string",
        "AvailablePolicyTypes": [
            {
                "Type": "SERVICE_CONTROL_POLICY|TAG_POLICY|BACKUP_POLICY|AISERVICES_OPT_OUT_POLICY",
                "Status": "ENABLED|PENDING_ENABLE|PENDING_DISABLE"
            }
        ]
    }
}
```

---

### 1.2 `delete-organization`

Deletes the organization. You can only delete an organization after you remove all member accounts.

**Synopsis:**
```bash
aws organizations delete-organization \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| _(none)_ | -- | -- | -- | No parameters beyond global options |

**Output Schema:**
```json
{}
```

---

### 1.3 `describe-organization`

Retrieves information about the organization that the calling account belongs to.

**Synopsis:**
```bash
aws organizations describe-organization \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| _(none)_ | -- | -- | -- | No parameters beyond global options |

**Output Schema:**
```json
{
    "Organization": {
        "Id": "string",
        "Arn": "string",
        "FeatureSet": "ALL|CONSOLIDATED_BILLING",
        "MasterAccountArn": "string",
        "MasterAccountId": "string",
        "MasterAccountEmail": "string",
        "AvailablePolicyTypes": [
            {
                "Type": "SERVICE_CONTROL_POLICY|TAG_POLICY|BACKUP_POLICY|AISERVICES_OPT_OUT_POLICY",
                "Status": "ENABLED|PENDING_ENABLE|PENDING_DISABLE"
            }
        ]
    }
}
```

---

### 1.4 `list-roots`

Lists the roots that are defined in the organization. **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-roots \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Roots": [
        {
            "Id": "string",
            "Arn": "string",
            "Name": "string",
            "PolicyTypes": [
                {
                    "Type": "SERVICE_CONTROL_POLICY|TAG_POLICY|BACKUP_POLICY|AISERVICES_OPT_OUT_POLICY",
                    "Status": "ENABLED|PENDING_ENABLE|PENDING_DISABLE"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `enable-all-features`

Enables all features in the organization. Requires all member accounts to accept the change via handshake.

**Synopsis:**
```bash
aws organizations enable-all-features \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| _(none)_ | -- | -- | -- | No parameters beyond global options |

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

### 1.6 `leave-organization`

Removes a member account from its organization. Can only be called by a member account (not the management account). The account becomes a standalone account.

**Synopsis:**
```bash
aws organizations leave-organization \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| _(none)_ | -- | -- | -- | No parameters beyond global options |

**Output Schema:**
```json
{}
```
