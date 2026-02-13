# IP Sets

### 3.1 `create-ip-set`

Creates an IP set. An IP set provides a collection of IP addresses and IP address ranges that you can reference in rules.

**Synopsis:**
```bash
aws wafv2 create-ip-set \
    --name <value> \
    --scope <value> \
    --ip-address-version <value> \
    --addresses <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the IP set |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--ip-address-version` | **Yes** | string | -- | IP version: `IPV4` or `IPV6` |
| `--addresses` | **Yes** | list(string) | -- | IP addresses in CIDR notation (e.g., `192.0.2.0/24`, `2001:db8::/32`) |
| `--description` | No | string | -- | Description |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Summary": {
        "Name": "string",
        "Id": "string",
        "Description": "string",
        "LockToken": "string",
        "ARN": "string"
    }
}
```

---

### 3.2 `delete-ip-set`

Deletes an IP set. Must not be referenced by any rule.

**Synopsis:**
```bash
aws wafv2 delete-ip-set \
    --name <value> \
    --scope <value> \
    --id <value> \
    --lock-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the IP set |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID of the IP set |
| `--lock-token` | **Yes** | string | -- | Lock token from get operation |

**Output:** None on success.

---

### 3.3 `get-ip-set`

Retrieves an IP set with full details.

**Synopsis:**
```bash
aws wafv2 get-ip-set \
    --name <value> \
    --scope <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the IP set |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID of the IP set |

**Output Schema:**
```json
{
    "IPSet": {
        "Name": "string",
        "Id": "string",
        "ARN": "string",
        "Description": "string",
        "IPAddressVersion": "IPV4|IPV6",
        "Addresses": ["string"]
    },
    "LockToken": "string"
}
```

---

### 3.4 `list-ip-sets`

Returns a list of IP sets. **Paginated operation.**

**Synopsis:**
```bash
aws wafv2 list-ip-sets \
    --scope <value> \
    [--next-marker <value>] \
    [--limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--next-marker` | No | string | None | Pagination token |
| `--limit` | No | integer | None | Maximum results (1-100) |

**Output Schema:**
```json
{
    "NextMarker": "string",
    "IPSets": [
        {
            "Name": "string",
            "Id": "string",
            "Description": "string",
            "LockToken": "string",
            "ARN": "string"
        }
    ]
}
```

---

### 3.5 `update-ip-set`

Updates an IP set. Replaces the entire set of addresses. Requires the current lock token.

**Synopsis:**
```bash
aws wafv2 update-ip-set \
    --name <value> \
    --scope <value> \
    --id <value> \
    --lock-token <value> \
    --addresses <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the IP set |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID of the IP set |
| `--lock-token` | **Yes** | string | -- | Lock token from get operation |
| `--addresses` | **Yes** | list(string) | -- | New addresses in CIDR notation (replaces all existing) |
| `--description` | No | string | -- | New description |

**Output Schema:**
```json
{
    "NextLockToken": "string"
}
```
