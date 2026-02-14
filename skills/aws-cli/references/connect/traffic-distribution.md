# Traffic Distribution

### 18.1 `create-traffic-distribution-group`

Creates a traffic distribution group.

**Synopsis:**
```bash
aws connect create-traffic-distribution-group \
    --name <value> \
    --instance-id <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Group name (1-128 chars) |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--description` | No | string | None | Description (1-250 chars) |
| `--client-token` | No | string | Auto | Idempotency token |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string"
}
```

---

### 18.2 `describe-traffic-distribution-group`

Describes a traffic distribution group.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--traffic-distribution-group-id` | **Yes** | string | -- | TDG ID or ARN |

**Output Schema:**
```json
{
    "TrafficDistributionGroup": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "InstanceArn": "string",
        "Status": "CREATION_IN_PROGRESS|ACTIVE|CREATION_FAILED|PENDING_DELETION|DELETION_FAILED|UPDATE_IN_PROGRESS",
        "IsDefault": "boolean",
        "Tags": { "key": "value" }
    }
}
```

---

### 18.3 `list-traffic-distribution-groups`

Lists traffic distribution groups. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | No | string | None | Filter by instance |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-10) |

---

### 18.4 `delete-traffic-distribution-group`

Deletes a traffic distribution group.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--traffic-distribution-group-id` | **Yes** | string | -- | TDG ID or ARN |

**Output:** None

---

### 18.5 `get-traffic-distribution`

Gets traffic distribution for a TDG.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | TDG ID or ARN |

**Output Schema:**
```json
{
    "TelephonyConfig": {
        "Distributions": [ { "Region": "string", "Percentage": "integer" } ]
    },
    "Id": "string",
    "Arn": "string",
    "SignInConfig": {
        "Distributions": [ { "Region": "string", "Enabled": "boolean" } ]
    },
    "AgentConfig": {
        "Distributions": [ { "Region": "string", "Percentage": "integer" } ]
    }
}
```

---

### 18.6 `update-traffic-distribution`

Updates traffic distribution settings.

**Synopsis:**
```bash
aws connect update-traffic-distribution \
    --id <value> \
    [--telephony-config <value>] \
    [--sign-in-config <value>] \
    [--agent-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | TDG ID or ARN |
| `--telephony-config` | No | structure | None | Telephony distribution |
| `--sign-in-config` | No | structure | None | Sign-in distribution |
| `--agent-config` | No | structure | None | Agent distribution |

**Output:** None

---

### 18.7-18.9 TDG User Commands

`associate-traffic-distribution-group-user`, `list-traffic-distribution-group-users`, `disassociate-traffic-distribution-group-user` manage user associations to traffic distribution groups.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--traffic-distribution-group-id` | **Yes** | string | -- | TDG ID or ARN |
| `--user-id` | **Yes** | string | -- | User ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output:** None (for associate/disassociate)
