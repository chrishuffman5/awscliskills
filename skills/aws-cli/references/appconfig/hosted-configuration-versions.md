# Hosted Configuration Versions

### 6.1 `create-hosted-configuration-version`

Creates a new configuration version in the AppConfig hosted configuration store.

**Synopsis:**
```bash
aws appconfig create-hosted-configuration-version \
    --application-id <value> \
    --configuration-profile-id <value> \
    --content <value> \
    --content-type <value> \
    [--description <value>] \
    [--latest-version-number <value>] \
    [--version-label <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>] \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--configuration-profile-id` | **Yes** | string | -- | Configuration profile ID |
| `--content` | **Yes** | blob | -- | Configuration data (JSON, TOML, protocol buffers, etc.) |
| `--content-type` | **Yes** | string | -- | MIME type of content (1-255 chars), e.g., `application/json` |
| `outfile` | **Yes** | string | -- | Filename to save output content |
| `--description` | No | string | None | Description (0-1024 chars) |
| `--latest-version-number` | No | integer | None | Latest version number for optimistic locking |
| `--version-label` | No | string | None | User-defined version label (1-64 chars, must contain non-numeric chars) |

**Output Schema:**
```json
{
    "ApplicationId": "string",
    "ConfigurationProfileId": "string",
    "VersionNumber": "integer",
    "Description": "string",
    "Content": "blob",
    "ContentType": "string",
    "VersionLabel": "string",
    "KmsKeyArn": "string"
}
```

---

### 6.2 `get-hosted-configuration-version`

Retrieves a hosted configuration version.

**Synopsis:**
```bash
aws appconfig get-hosted-configuration-version \
    --application-id <value> \
    --configuration-profile-id <value> \
    --version-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>] \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--configuration-profile-id` | **Yes** | string | -- | Configuration profile ID |
| `--version-number` | **Yes** | integer | -- | Version number to retrieve |
| `outfile` | **Yes** | string | -- | Filename to save output content |

**Output Schema:**
```json
{
    "ApplicationId": "string",
    "ConfigurationProfileId": "string",
    "VersionNumber": "integer",
    "Description": "string",
    "Content": "blob",
    "ContentType": "string",
    "VersionLabel": "string",
    "KmsKeyArn": "string"
}
```

---

### 6.3 `list-hosted-configuration-versions`

Lists hosted configuration versions. **Paginated operation.**

**Synopsis:**
```bash
aws appconfig list-hosted-configuration-versions \
    --application-id <value> \
    --configuration-profile-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--version-label <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--configuration-profile-id` | **Yes** | string | -- | Configuration profile ID |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |
| `--version-label` | No | string | None | Filter by version label |

**Output Schema:**
```json
{
    "Items": [
        {
            "ApplicationId": "string",
            "ConfigurationProfileId": "string",
            "VersionNumber": "integer",
            "Description": "string",
            "ContentType": "string",
            "VersionLabel": "string",
            "KmsKeyArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `delete-hosted-configuration-version`

Deletes a specific version of a hosted configuration.

**Synopsis:**
```bash
aws appconfig delete-hosted-configuration-version \
    --application-id <value> \
    --configuration-profile-id <value> \
    --version-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--configuration-profile-id` | **Yes** | string | -- | Configuration profile ID |
| `--version-number` | **Yes** | integer | -- | Version number to delete |

**Output:** None
