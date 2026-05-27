# Reusable Delegation Sets

### 7.1 `create-reusable-delegation-set`

Creates a reusable delegation set of four authoritative nameservers. Zones created with this set use the same nameservers.

**Synopsis:**
```bash
aws route53 create-reusable-delegation-set \
    --caller-reference <value> \
    [--hosted-zone-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--caller-reference` | **Yes** | string | -- | Unique string for retry safety (1-128 chars) |
| `--hosted-zone-id` | No | string | None | Copy nameservers from this zone (max 32 chars) |

**Output Schema:**
```json
{
    "DelegationSet": {
        "Id": "string",
        "CallerReference": "string",
        "NameServers": ["string"]
    },
    "Location": "string"
}
```

---

### 7.2 `delete-reusable-delegation-set`

Deletes a reusable delegation set. Cannot delete if any hosted zones use it.

**Synopsis:**
```bash
aws route53 delete-reusable-delegation-set \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Delegation set ID (max 32 chars) |

**Output:** None on success.

---

### 7.3 `get-reusable-delegation-set`

Gets information about a reusable delegation set, including the nameservers.

**Synopsis:**
```bash
aws route53 get-reusable-delegation-set \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Delegation set ID (max 32 chars) |

**Output Schema:**
```json
{
    "DelegationSet": {
        "Id": "string",
        "CallerReference": "string",
        "NameServers": ["string"]
    }
}
```

---

### 7.4 `list-reusable-delegation-sets`

Lists all reusable delegation sets in the account.

**Synopsis:**
```bash
aws route53 list-reusable-delegation-sets \
    [--marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--marker` | No | string | None | Pagination marker (max 64 chars) |
| `--max-items` | No | string | None | Maximum items to return |

**Output Schema:**
```json
{
    "DelegationSets": [
        {
            "Id": "string",
            "CallerReference": "string",
            "NameServers": ["string"]
        }
    ],
    "Marker": "string",
    "IsTruncated": true|false,
    "NextMarker": "string",
    "MaxItems": "string"
}
```

---
