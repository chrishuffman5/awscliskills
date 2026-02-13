# Versions

### 3.1 `list-secret-version-ids`

Lists all version IDs for a secret. **Paginated operation.**

**Synopsis:**
```bash
aws secretsmanager list-secret-version-ids \
    --secret-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--include-deprecated | --no-include-deprecated] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |
| `--max-results` | No | integer | None | Number of results per page (1-100) |
| `--next-token` | No | string | None | Pagination token (1-4096 chars) |
| `--include-deprecated` | No | boolean | false | Include versions without staging labels |

**Output Schema:**
```json
{
    "Versions": [
        {
            "VersionId": "string",
            "VersionStages": ["string"],
            "LastAccessedDate": "timestamp",
            "CreatedDate": "timestamp",
            "KmsKeyIds": ["string"]
        }
    ],
    "NextToken": "string",
    "ARN": "string",
    "Name": "string"
}
```

---

### 3.2 `update-secret-version-stage`

Moves a staging label between secret versions. Commonly used to revert to a previous version.

**Synopsis:**
```bash
aws secretsmanager update-secret-version-stage \
    --secret-id <value> \
    --version-stage <value> \
    [--remove-from-version-id <value>] \
    [--move-to-version-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |
| `--version-stage` | **Yes** | string | -- | Staging label to add or move (1-256 chars) |
| `--remove-from-version-id` | No | string | None | Version ID to remove the label from (32-64 chars) |
| `--move-to-version-id` | No | string | None | Version ID to add the label to (32-64 chars). Omit to just remove a label |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string"
}
```

---
