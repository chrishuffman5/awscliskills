# Threat Intel Sets

### 5.1 `create-threat-intel-set`

Creates a new ThreatIntelSet, which consists of known malicious IP addresses used by GuardDuty to generate findings.

**Synopsis:**
```bash
aws guardduty create-threat-intel-set \
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
| `--name` | **Yes** | string | -- | User-friendly name for the threat intel set (1-300 chars) |
| `--format` | **Yes** | string | -- | Format of the file: `TXT`, `STIX`, `OTX_CSV`, `ALIEN_VAULT`, `PROOF_POINT`, `FIRE_EYE` |
| `--location` | **Yes** | string | -- | S3 URI of the file containing the threat intel set (1-300 chars) |
| `--activate` / `--no-activate` | **Yes** | boolean | -- | Whether to activate the threat intel set |
| `--client-token` | No | string | None | Idempotency token (0-64 chars) |
| `--tags` | No | map | None | Tags to add (max 200) |

**Output Schema:**
```json
{
    "ThreatIntelSetId": "string"
}
```

---

### 5.2 `delete-threat-intel-set`

Deletes the ThreatIntelSet specified by the ThreatIntelSet ID.

**Synopsis:**
```bash
aws guardduty delete-threat-intel-set \
    --detector-id <value> \
    --threat-intel-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--threat-intel-set-id` | **Yes** | string | -- | The threat intel set ID to delete |

**Output:** None (HTTP 200 on success)

---

### 5.3 `get-threat-intel-set`

Retrieves the ThreatIntelSet specified by the ThreatIntelSet ID.

**Synopsis:**
```bash
aws guardduty get-threat-intel-set \
    --detector-id <value> \
    --threat-intel-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--threat-intel-set-id` | **Yes** | string | -- | The threat intel set ID to retrieve |

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

### 5.4 `list-threat-intel-sets`

Lists the ThreatIntelSets of the GuardDuty service specified by the detector ID. **Paginated operation.**

**Synopsis:**
```bash
aws guardduty list-threat-intel-sets \
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
    "ThreatIntelSetIds": ["string"],
    "NextToken": "string"
}
```

---

### 5.5 `update-threat-intel-set`

Updates the ThreatIntelSet specified by the ThreatIntelSet ID.

**Synopsis:**
```bash
aws guardduty update-threat-intel-set \
    --detector-id <value> \
    --threat-intel-set-id <value> \
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
| `--threat-intel-set-id` | **Yes** | string | -- | The threat intel set ID to update |
| `--name` | No | string | None | New name for the threat intel set |
| `--location` | No | string | None | New S3 URI for the threat intel set file |
| `--activate` / `--no-activate` | No | boolean | None | Whether to activate/deactivate the threat intel set |

**Output:** None (HTTP 200 on success)
