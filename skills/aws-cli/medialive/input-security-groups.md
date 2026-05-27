# Input Security Groups

### 3.1 `create-input-security-group`

Creates an input security group with IP whitelist rules to control which IPs can push content to inputs.

**Synopsis:**
```bash
aws medialive create-input-security-group \
    [--whitelist-rules <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--whitelist-rules` | No | list | None | IPv4 CIDR whitelist rules |
| `--tags` | No | map | None | Key-value tag pairs |

**WhitelistRules:**
```json
[
    {"Cidr": "10.0.0.0/8"},
    {"Cidr": "192.168.1.0/24"}
]
```

**Output Schema:**
```json
{
    "SecurityGroup": {
        "Arn": "string",
        "Id": "string",
        "Inputs": ["string"],
        "Channels": ["string"],
        "State": "IDLE|IN_USE|UPDATING|DELETED",
        "WhitelistRules": [{"Cidr": "string"}],
        "Tags": {}
    }
}
```

---

### 3.2 `describe-input-security-group`

Describes an input security group.

**Synopsis:**
```bash
aws medialive describe-input-security-group \
    --input-security-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-security-group-id` | **Yes** | string | -- | Security group ID |

**Output Schema:** Same as `create-input-security-group` output.

---

### 3.3 `update-input-security-group`

Updates the whitelist rules or tags for an input security group.

**Synopsis:**
```bash
aws medialive update-input-security-group \
    --input-security-group-id <value> \
    [--whitelist-rules <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-security-group-id` | **Yes** | string | -- | Security group ID to update |
| `--whitelist-rules` | No | list | None | Updated whitelist rules |
| `--tags` | No | map | None | Updated tags |

**Output Schema:**
```json
{
    "SecurityGroup": {
        "Arn": "string",
        "Id": "string",
        "State": "UPDATING",
        "WhitelistRules": [{"Cidr": "string"}]
    }
}
```

---

### 3.4 `delete-input-security-group`

Deletes an input security group. Must not be in use by any inputs.

**Synopsis:**
```bash
aws medialive delete-input-security-group \
    --input-security-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-security-group-id` | **Yes** | string | -- | Security group ID to delete |

**Output:** None

---

### 3.5 `list-input-security-groups`

Lists input security groups. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-input-security-groups \
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
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "InputSecurityGroups": [
        {
            "Arn": "string",
            "Id": "string",
            "Inputs": ["string"],
            "State": "string",
            "WhitelistRules": [{"Cidr": "string"}],
            "Tags": {}
        }
    ]
}
```
