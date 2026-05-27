# Trusts

### 3.1 `create-trust`

Creates a trust relationship between a Managed Microsoft AD directory and an external domain.

**Synopsis:**
```bash
aws ds create-trust \
    --directory-id <value> \
    --remote-domain-name <value> \
    --trust-password <value> \
    --trust-direction <value> \
    [--trust-type <value>] \
    [--conditional-forwarder-ip-addrs <value>] \
    [--conditional-forwarder-ipv6-addrs <value>] \
    [--selective-auth <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID (pattern: `d-[0-9a-f]{10}`) |
| `--remote-domain-name` | **Yes** | string | -- | FQDN of the external domain |
| `--trust-password` | **Yes** | string | -- | Trust password (1-128 chars) |
| `--trust-direction` | **Yes** | string | -- | `One-Way: Outgoing`, `One-Way: Incoming`, or `Two-Way` |
| `--trust-type` | No | string | `Forest` | `Forest` or `External` |
| `--conditional-forwarder-ip-addrs` | No | list(string) | None | IPv4 addresses of remote DNS servers |
| `--conditional-forwarder-ipv6-addrs` | No | list(string) | None | IPv6 addresses of remote DNS servers |
| `--selective-auth` | No | string | None | `Enabled` or `Disabled` |

**Output Schema:**
```json
{
    "TrustId": "string"
}
```

---

### 3.2 `delete-trust`

Deletes an existing trust relationship.

**Synopsis:**
```bash
aws ds delete-trust \
    --trust-id <value> \
    [--delete-associated-conditional-forwarder | --no-delete-associated-conditional-forwarder] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-id` | **Yes** | string | -- | Trust ID (pattern: `t-[0-9a-f]{10}`) |
| `--delete-associated-conditional-forwarder` | No | boolean | false | Also delete the associated conditional forwarder |

**Output Schema:**
```json
{
    "TrustId": "string"
}
```

---

### 3.3 `describe-trusts`

Describes trust relationships for a directory. **Paginated operation.**

**Synopsis:**
```bash
aws ds describe-trusts \
    [--directory-id <value>] \
    [--trust-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | No | string | None | Filter by directory ID |
| `--trust-ids` | No | list(string) | None | Filter by trust IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Trusts": [
        {
            "DirectoryId": "string",
            "TrustId": "string",
            "RemoteDomainName": "string",
            "TrustType": "Forest|External",
            "TrustDirection": "One-Way: Outgoing|One-Way: Incoming|Two-Way",
            "TrustState": "Creating|Created|Verifying|VerifyFailed|Verified|Updating|UpdateFailed|Updated|Deleting|Deleted|Failed",
            "CreatedDateTime": "timestamp",
            "LastUpdatedDateTime": "timestamp",
            "StateLastUpdatedDateTime": "timestamp",
            "TrustStateReason": "string",
            "SelectiveAuth": "Enabled|Disabled"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `update-trust`

Updates a trust relationship.

**Synopsis:**
```bash
aws ds update-trust \
    --trust-id <value> \
    [--selective-auth <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-id` | **Yes** | string | -- | Trust ID |
| `--selective-auth` | No | string | None | `Enabled` or `Disabled` |

**Output Schema:**
```json
{
    "RequestId": "string",
    "TrustId": "string"
}
```

---

### 3.5 `verify-trust`

Verifies a trust relationship by sending a verification request to the remote domain.

**Synopsis:**
```bash
aws ds verify-trust \
    --trust-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-id` | **Yes** | string | -- | Trust ID to verify |

**Output Schema:**
```json
{
    "TrustId": "string"
}
```
