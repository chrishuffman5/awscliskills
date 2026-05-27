# IP Sets

### 4.1 `create-ip-set`

Creates a new IPSet, which is a list of trusted IP addresses from which secure communication is allowed with AWS infrastructure and applications.

**Synopsis:**
```bash
aws guardduty create-ip-set \
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
| `--name` | **Yes** | string | -- | User-friendly name for the IP set (1-300 chars) |
| `--format` | **Yes** | string | -- | Format of the file: `TXT`, `STIX`, `OTX_CSV`, `ALIEN_VAULT`, `PROOF_POINT`, `FIRE_EYE` |
| `--location` | **Yes** | string | -- | S3 URI of the file containing the IP set (1-300 chars) |
| `--activate` / `--no-activate` | **Yes** | boolean | -- | Whether to activate the IP set |
| `--client-token` | No | string | None | Idempotency token (0-64 chars) |
| `--tags` | No | map | None | Tags to add (max 200) |

**Output Schema:**
```json
{
    "IpSetId": "string"
}
```

---

### 4.2 `delete-ip-set`

Deletes the IPSet specified by the IPSet ID.

**Synopsis:**
```bash
aws guardduty delete-ip-set \
    --detector-id <value> \
    --ip-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--ip-set-id` | **Yes** | string | -- | The IP set ID to delete |

**Output:** None (HTTP 200 on success)

---

### 4.3 `get-ip-set`

Retrieves the IPSet specified by the IPSet ID.

**Synopsis:**
```bash
aws guardduty get-ip-set \
    --detector-id <value> \
    --ip-set-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--ip-set-id` | **Yes** | string | -- | The IP set ID to retrieve |

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

### 4.4 `list-ip-sets`

Lists the IPSets of the GuardDuty service specified by the detector ID. **Paginated operation.**

**Synopsis:**
```bash
aws guardduty list-ip-sets \
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
    "IpSetIds": ["string"],
    "NextToken": "string"
}
```

---

### 4.5 `update-ip-set`

Updates the IPSet specified by the IPSet ID.

**Synopsis:**
```bash
aws guardduty update-ip-set \
    --detector-id <value> \
    --ip-set-id <value> \
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
| `--ip-set-id` | **Yes** | string | -- | The IP set ID to update |
| `--name` | No | string | None | New name for the IP set |
| `--location` | No | string | None | New S3 URI for the IP set file |
| `--activate` / `--no-activate` | No | boolean | None | Whether to activate/deactivate the IP set |

**Output:** None (HTTP 200 on success)
