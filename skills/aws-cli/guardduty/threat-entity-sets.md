# Threat Entity Sets

### 6.1 `create-threat-entity-set`

Creates a new threat entity set. Threat entity sets contain entities (such as IP addresses, domains, or file hashes) that are considered threats.

**Synopsis:**
```bash
aws guardduty create-threat-entity-set \
    --detector-id <value> \
    --name <value> \
    --format <value> \
    --location <value> \
    --activate | --no-activate \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--name` | **Yes** | string | -- | User-friendly name for the threat entity set (1-300 chars) |
| `--format` | **Yes** | string | -- | Format of the file: `TXT`, `STIX`, `OTX_CSV`, `ALIEN_VAULT`, `PROOF_POINT`, `FIRE_EYE` |
| `--location` | **Yes** | string | -- | S3 URI of the file containing the threat entity set (1-300 chars) |
| `--activate` / `--no-activate` | **Yes** | boolean | -- | Whether to activate the threat entity set |
| `--client-token` | No | string | None | Idempotency token (0-64 chars) |
| `--tags` | No | map | None | Tags to add (max 200) |

**Output Schema:**
```json
{
    "ThreatEntitySetId": "string"
}
```

---

### 6.2 `delete-threat-entity-set`

Deletes the threat entity set specified by the threat entity set ID.

**Synopsis:**
```bash
aws guardduty delete-threat-entity-set \
    --detector-id <value> \
    --threat-entity-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--threat-entity-set-id` | **Yes** | string | -- | The threat entity set ID to delete |

**Output:** None (HTTP 200 on success)

---

### 6.3 `get-threat-entity-set`

Retrieves the threat entity set specified by the threat entity set ID.

**Synopsis:**
```bash
aws guardduty get-threat-entity-set \
    --detector-id <value> \
    --threat-entity-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--threat-entity-set-id` | **Yes** | string | -- | The threat entity set ID to retrieve |

**Output Schema:**
```json
{
    "Name": "string",
    "Format": "TXT|STIX|OTX_CSV|ALIEN_VAULT|PROOF_POINT|FIRE_EYE",
    "Location": "string",
    "Status": "INACTIVE|ACTIVATING|ACTIVE|DEACTIVATING|ERROR|DELETE_PENDING|DELETED",
    "Tags": {
        "string": "string"
    }
}
```

---

### 6.4 `list-threat-entity-sets`

Lists the threat entity sets of the GuardDuty service specified by the detector ID. **Paginated operation.**

**Synopsis:**
```bash
aws guardduty list-threat-entity-sets \
    --detector-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (1-50) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ThreatEntitySetIds": ["string"],
    "NextToken": "string"
}
```

---

### 6.5 `update-threat-entity-set`

Updates the threat entity set specified by the threat entity set ID.

**Synopsis:**
```bash
aws guardduty update-threat-entity-set \
    --detector-id <value> \
    --threat-entity-set-id <value> \
    [--name <value>] \
    [--location <value>] \
    [--activate | --no-activate] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--threat-entity-set-id` | **Yes** | string | -- | The threat entity set ID to update |
| `--name` | No | string | None | New name for the threat entity set |
| `--location` | No | string | None | New S3 URI for the threat entity set file |
| `--activate` / `--no-activate` | No | boolean | None | Whether to activate/deactivate the threat entity set |

**Output:** None (HTTP 200 on success)
