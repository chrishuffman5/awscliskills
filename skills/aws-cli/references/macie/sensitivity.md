# Sensitivity

### 10.1 `get-reveal-configuration`

Retrieves the configuration settings for retrieving occurrences of sensitive data reported by findings.

**Synopsis:**
```bash
aws macie2 get-reveal-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "configuration": {
        "kmsKeyId": "string",
        "status": "ENABLED|DISABLED"
    },
    "retrievalConfiguration": {
        "externalId": "string",
        "retrievalMode": "CALLER_CREDENTIALS|ASSUME_ROLE",
        "roleName": "string"
    }
}
```

---

### 10.2 `update-reveal-configuration`

Updates the reveal configuration for retrieving sensitive data occurrences.

**Synopsis:**
```bash
aws macie2 update-reveal-configuration \
    --configuration <value> \
    [--retrieval-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration` | **Yes** | structure | -- | Reveal configuration |
| `--retrieval-configuration` | No | structure | None | Retrieval configuration |

**Configuration Structure:**
```json
{
    "kmsKeyId": "string",
    "status": "ENABLED|DISABLED"
}
```

**Output Schema:**
```json
{
    "configuration": {
        "kmsKeyId": "string",
        "status": "ENABLED|DISABLED"
    },
    "retrievalConfiguration": {
        "externalId": "string",
        "retrievalMode": "CALLER_CREDENTIALS|ASSUME_ROLE",
        "roleName": "string"
    }
}
```

---

### 10.3 `get-sensitive-data-occurrences`

Retrieves occurrences of sensitive data reported by a finding.

**Synopsis:**
```bash
aws macie2 get-sensitive-data-occurrences \
    --finding-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-id` | **Yes** | string | -- | Finding ID |

**Output Schema:**
```json
{
    "error": "string",
    "sensitiveDataOccurrences": {
        "string": [
            {
                "value": "string"
            }
        ]
    },
    "status": "SUCCESS|ERROR"
}
```

---

### 10.4 `get-sensitive-data-occurrences-availability`

Checks whether occurrences of sensitive data can be retrieved for a finding.

**Synopsis:**
```bash
aws macie2 get-sensitive-data-occurrences-availability \
    --finding-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-id` | **Yes** | string | -- | Finding ID |

**Output Schema:**
```json
{
    "code": "AVAILABLE|UNAVAILABLE|ACCOUNT_NOT_IN_ORGANIZATION|INVALID_CLASSIFICATION_RESULT|OBJECT_UNAVAILABLE|OBJECT_OVERSIZE|UNSUPPORTED_OBJECT_TYPE|UNSUPPORTED_FINDING_TYPE|INVALID_RESULT_SIGNATURE|MEMBER_ROLE_TOO_PERMISSIVE|MISSING_GET_MEMBER_PERMISSION|RESULT_NOT_SIGNED",
    "reasons": ["string"]
}
```

---

### 10.5 `get-sensitivity-inspection-template`

Retrieves the sensitivity inspection template used for automated discovery.

**Synopsis:**
```bash
aws macie2 get-sensitivity-inspection-template \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Template ID |

**Output Schema:**
```json
{
    "description": "string",
    "excludes": {
        "managedDataIdentifierIds": ["string"]
    },
    "includes": {
        "allowListIds": ["string"],
        "customDataIdentifierIds": ["string"],
        "managedDataIdentifierIds": ["string"]
    },
    "name": "string",
    "sensitivityInspectionTemplateId": "string"
}
```

---

### 10.6 `list-sensitivity-inspection-templates`

Lists the sensitivity inspection templates. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-sensitivity-inspection-templates \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "sensitivityInspectionTemplates": [
        {
            "id": "string",
            "name": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 10.7 `update-sensitivity-inspection-template`

Updates the sensitivity inspection template settings.

**Synopsis:**
```bash
aws macie2 update-sensitivity-inspection-template \
    --id <value> \
    [--description <value>] \
    [--excludes <value>] \
    [--includes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Template ID |
| `--description` | No | string | None | Updated description |
| `--excludes` | No | structure | None | Data identifiers to exclude |
| `--includes` | No | structure | None | Data identifiers to include |

**Output:** None (HTTP 200 on success)
