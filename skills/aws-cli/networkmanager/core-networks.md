# Core Networks

### 2.1 `create-core-network`

Creates a core network as part of a global network. A core network is the central component of AWS Cloud WAN.

**Synopsis:**
```bash
aws networkmanager create-core-network \
    --global-network-id <value> \
    [--description <value>] \
    [--tags <value>] \
    [--policy-document <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--description` | No | string | None | Description (max 256 chars) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--policy-document` | No | string | None | Core network policy JSON (max 10MB) |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "CoreNetwork": {
        "GlobalNetworkId": "string",
        "CoreNetworkId": "string",
        "CoreNetworkArn": "string",
        "Description": "string",
        "CreatedAt": "timestamp",
        "State": "CREATING|UPDATING|AVAILABLE|DELETING",
        "Segments": [
            {
                "Name": "string",
                "EdgeLocations": ["string"],
                "SharedSegments": ["string"]
            }
        ],
        "NetworkFunctionGroups": [
            {
                "Name": "string",
                "EdgeLocations": ["string"],
                "Segments": {
                    "SendVia": ["string"],
                    "SendTo": ["string"]
                }
            }
        ],
        "Edges": [
            {
                "EdgeLocation": "string",
                "Asn": "long",
                "InsideCidrBlocks": ["string"]
            }
        ],
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 2.2 `delete-core-network`

Deletes a core network. All attachments must be deleted first.

**Synopsis:**
```bash
aws networkmanager delete-core-network \
    --core-network-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |

**Output Schema:**
```json
{
    "CoreNetwork": {
        "GlobalNetworkId": "string",
        "CoreNetworkId": "string",
        "CoreNetworkArn": "string",
        "Description": "string",
        "CreatedAt": "timestamp",
        "State": "CREATING|UPDATING|AVAILABLE|DELETING",
        "Segments": [],
        "Edges": [],
        "Tags": []
    }
}
```

---

### 2.3 `get-core-network`

Returns information about a core network.

**Synopsis:**
```bash
aws networkmanager get-core-network \
    --core-network-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |

**Output Schema:**
```json
{
    "CoreNetwork": {
        "GlobalNetworkId": "string",
        "CoreNetworkId": "string",
        "CoreNetworkArn": "string",
        "Description": "string",
        "CreatedAt": "timestamp",
        "State": "CREATING|UPDATING|AVAILABLE|DELETING",
        "Segments": [
            {
                "Name": "string",
                "EdgeLocations": ["string"],
                "SharedSegments": ["string"]
            }
        ],
        "NetworkFunctionGroups": [],
        "Edges": [
            {
                "EdgeLocation": "string",
                "Asn": "long",
                "InsideCidrBlocks": ["string"]
            }
        ],
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 2.4 `list-core-networks`

Lists core networks. **Paginated.**

**Synopsis:**
```bash
aws networkmanager list-core-networks \
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
    "CoreNetworks": [
        {
            "CoreNetworkId": "string",
            "CoreNetworkArn": "string",
            "GlobalNetworkId": "string",
            "OwnerAccountId": "string",
            "State": "string",
            "Description": "string",
            "Tags": [{"Key": "string", "Value": "string"}]
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `update-core-network`

Updates the description of a core network.

**Synopsis:**
```bash
aws networkmanager update-core-network \
    --core-network-id <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "CoreNetwork": {
        "CoreNetworkId": "string",
        "CoreNetworkArn": "string",
        "GlobalNetworkId": "string",
        "Description": "string",
        "CreatedAt": "timestamp",
        "State": "string",
        "Segments": [],
        "Edges": [],
        "Tags": []
    }
}
```

---

### 2.6 `put-core-network-policy`

Creates or updates a core network policy. The policy defines segments, attachment policies, and segment actions.

**Synopsis:**
```bash
aws networkmanager put-core-network-policy \
    --core-network-id <value> \
    --policy-document <value> \
    [--description <value>] \
    [--latest-version-id <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--policy-document` | **Yes** | string | -- | Policy document JSON (max 10MB). Use `file://` for file input |
| `--description` | No | string | None | Description for this policy version |
| `--latest-version-id` | No | integer | None | Expected latest version ID (for optimistic locking) |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "CoreNetworkPolicy": {
        "CoreNetworkId": "string",
        "PolicyVersionId": "integer",
        "Alias": "LIVE|LATEST",
        "Description": "string",
        "CreatedAt": "timestamp",
        "ChangeSetState": "PENDING_GENERATION|FAILED_GENERATION|READY_TO_EXECUTE|EXECUTING|EXECUTION_SUCCEEDED|OUT_OF_DATE",
        "PolicyErrors": [
            {
                "ErrorCode": "string",
                "Message": "string",
                "Path": "string"
            }
        ],
        "PolicyDocument": "string"
    }
}
```

---

### 2.7 `get-core-network-policy`

Returns the policy document for a core network.

**Synopsis:**
```bash
aws networkmanager get-core-network-policy \
    --core-network-id <value> \
    [--policy-version-id <value>] \
    [--alias <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--policy-version-id` | No | integer | None | Specific policy version |
| `--alias` | No | string | None | `LIVE` or `LATEST` |

**Output Schema:**
```json
{
    "CoreNetworkPolicy": {
        "CoreNetworkId": "string",
        "PolicyVersionId": "integer",
        "Alias": "LIVE|LATEST",
        "Description": "string",
        "CreatedAt": "timestamp",
        "ChangeSetState": "string",
        "PolicyErrors": [],
        "PolicyDocument": "string"
    }
}
```

---

### 2.8 `get-core-network-change-set`

Returns a change set between the LIVE and LATEST policy versions. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-core-network-change-set \
    --core-network-id <value> \
    --policy-version-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--policy-version-id` | **Yes** | integer | -- | Policy version ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CoreNetworkChanges": [
        {
            "Type": "CORE_NETWORK_SEGMENT|CORE_NETWORK_EDGE|ATTACHMENT_MAPPING|ATTACHMENT_ROUTE_PROPAGATION|ATTACHMENT_ROUTE_STATIC|CORE_NETWORK_CONFIGURATION|SEGMENTS_CONFIGURATION|SEGMENT_ACTIONS_CONFIGURATION|ATTACHMENT_POLICIES_CONFIGURATION|NETWORK_FUNCTION_GROUP",
            "Action": "ADD|MODIFY|REMOVE",
            "Identifier": "string",
            "PreviousValues": {},
            "NewValues": {},
            "IdentifierPath": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.9 `get-core-network-change-events`

Returns core network change events. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-core-network-change-events \
    --core-network-id <value> \
    --policy-version-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--policy-version-id` | **Yes** | integer | -- | Policy version ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CoreNetworkChangeEvents": [
        {
            "Type": "string",
            "Action": "string",
            "IdentifierPath": "string",
            "EventTime": "timestamp",
            "Status": "NOT_STARTED|IN_PROGRESS|COMPLETE|FAILED",
            "Values": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 2.10 `execute-core-network-change-set`

Executes a pending change set for a core network policy version.

**Synopsis:**
```bash
aws networkmanager execute-core-network-change-set \
    --core-network-id <value> \
    --policy-version-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--policy-version-id` | **Yes** | integer | -- | Policy version ID to execute |

**Output:** None

---

### 2.11 `list-core-network-policy-versions`

Lists policy versions for a core network. **Paginated.**

**Synopsis:**
```bash
aws networkmanager list-core-network-policy-versions \
    --core-network-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CoreNetworkPolicyVersions": [
        {
            "CoreNetworkId": "string",
            "PolicyVersionId": "integer",
            "Alias": "LIVE|LATEST",
            "Description": "string",
            "CreatedAt": "timestamp",
            "ChangeSetState": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.12 `delete-core-network-policy-version`

Deletes a specific policy version. Cannot delete the currently LIVE version.

**Synopsis:**
```bash
aws networkmanager delete-core-network-policy-version \
    --core-network-id <value> \
    --policy-version-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--policy-version-id` | **Yes** | integer | -- | Policy version ID to delete |

**Output Schema:**
```json
{
    "CoreNetworkPolicy": {
        "CoreNetworkId": "string",
        "PolicyVersionId": "integer",
        "Alias": "string",
        "Description": "string",
        "CreatedAt": "timestamp",
        "ChangeSetState": "string",
        "PolicyDocument": "string"
    }
}
```

---

### 2.13 `restore-core-network-policy-version`

Restores a previous policy version as the LATEST version.

**Synopsis:**
```bash
aws networkmanager restore-core-network-policy-version \
    --core-network-id <value> \
    --policy-version-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--policy-version-id` | **Yes** | integer | -- | Policy version ID to restore |

**Output Schema:**
```json
{
    "CoreNetworkPolicy": {
        "CoreNetworkId": "string",
        "PolicyVersionId": "integer",
        "Alias": "string",
        "Description": "string",
        "CreatedAt": "timestamp",
        "ChangeSetState": "string",
        "PolicyDocument": "string"
    }
}
```
