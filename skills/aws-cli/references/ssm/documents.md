# Documents

### 2.1 `create-document`

Creates an SSM document. Documents define the actions that SSM performs on managed instances.

**Synopsis:**
```bash
aws ssm create-document \
    --content <value> \
    --name <value> \
    [--requires <value>] \
    [--attachments <value>] \
    [--display-name <value>] \
    [--version-name <value>] \
    [--document-type <value>] \
    [--document-format <value>] \
    [--target-type <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--content` | **Yes** | string | -- | Document content (JSON or YAML string, or `file://` path) |
| `--name` | **Yes** | string | -- | Document name (letters, numbers, period, dash, underscore) |
| `--requires` | No | list | None | Documents required by this document |
| `--attachments` | No | list | None | File attachments |
| `--display-name` | No | string | None | Display name for the document |
| `--version-name` | No | string | None | Optional version name |
| `--document-type` | No | string | `Command` | Type: `Command`, `Automation`, `Policy`, `Session`, `Package` |
| `--document-format` | No | string | `JSON` | Format: `JSON`, `YAML`, `TEXT` |
| `--target-type` | No | string | None | Target type (e.g. `/AWS::EC2::Instance`) |
| `--tags` | No | list | None | Tags to apply. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "DocumentDescription": {
        "Sha1": "string",
        "Hash": "string",
        "HashType": "Sha256|Sha1",
        "Name": "string",
        "DisplayName": "string",
        "VersionName": "string",
        "Owner": "string",
        "CreatedDate": "timestamp",
        "Status": "Creating|Active|Updating|Deleting|Failed",
        "StatusInformation": "string",
        "DocumentVersion": "string",
        "Description": "string",
        "Parameters": [
            {
                "Name": "string",
                "Type": "String|StringList",
                "Description": "string",
                "DefaultValue": "string"
            }
        ],
        "PlatformTypes": ["Windows|Linux|MacOS"],
        "DocumentType": "Command|Policy|Automation|Session|Package",
        "SchemaVersion": "string",
        "LatestVersion": "string",
        "DefaultVersion": "string",
        "DocumentFormat": "YAML|JSON|TEXT",
        "TargetType": "string",
        "Tags": [],
        "Requires": []
    }
}
```

---

### 2.2 `delete-document`

Deletes an SSM document and all of its versions.

**Synopsis:**
```bash
aws ssm delete-document \
    --name <value> \
    [--document-version <value>] \
    [--version-name <value>] \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Document name |
| `--document-version` | No | string | None | Specific version to delete |
| `--version-name` | No | string | None | Version name to delete |
| `--force` | No | boolean | false | Force delete even if in use by associations |

**Output Schema:**
```json
{}
```

---

### 2.3 `describe-document`

Describes an SSM document, returning its metadata.

**Synopsis:**
```bash
aws ssm describe-document \
    --name <value> \
    [--document-version <value>] \
    [--version-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Document name |
| `--document-version` | No | string | None | Document version |
| `--version-name` | No | string | None | Version name |

**Output Schema:**
```json
{
    "Document": {
        "Sha1": "string",
        "Hash": "string",
        "HashType": "Sha256|Sha1",
        "Name": "string",
        "DisplayName": "string",
        "VersionName": "string",
        "Owner": "string",
        "CreatedDate": "timestamp",
        "Status": "Creating|Active|Updating|Deleting|Failed",
        "StatusInformation": "string",
        "DocumentVersion": "string",
        "Description": "string",
        "Parameters": [],
        "PlatformTypes": ["Windows|Linux|MacOS"],
        "DocumentType": "string",
        "SchemaVersion": "string",
        "LatestVersion": "string",
        "DefaultVersion": "string",
        "DocumentFormat": "YAML|JSON|TEXT",
        "TargetType": "string",
        "Tags": [],
        "Requires": [],
        "Author": "string",
        "ReviewStatus": "APPROVED|NOT_REVIEWED|PENDING|REJECTED"
    }
}
```

---

### 2.4 `get-document`

Gets the content of an SSM document.

**Synopsis:**
```bash
aws ssm get-document \
    --name <value> \
    [--version-name <value>] \
    [--document-version <value>] \
    [--document-format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Document name |
| `--version-name` | No | string | None | Version name |
| `--document-version` | No | string | None | Document version |
| `--document-format` | No | string | None | Output format: `JSON`, `YAML`, `TEXT` |

**Output Schema:**
```json
{
    "Name": "string",
    "CreatedDate": "timestamp",
    "DisplayName": "string",
    "VersionName": "string",
    "DocumentVersion": "string",
    "Status": "Creating|Active|Updating|Deleting|Failed",
    "StatusInformation": "string",
    "Content": "string",
    "DocumentType": "string",
    "DocumentFormat": "YAML|JSON|TEXT",
    "Requires": [],
    "AttachmentsContent": [],
    "ReviewStatus": "string"
}
```

---

### 2.5 `list-documents`

Lists SSM documents. Supports filtering by owner, name, type, and platform. **Paginated operation.**

**Synopsis:**
```bash
aws ssm list-documents \
    [--document-filter-list <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document-filter-list` | No | list | None | Legacy filters. Keys: `Name`, `Owner`, `PlatformTypes`, `DocumentType` |
| `--filters` | No | list | None | Key-value filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 50) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DocumentIdentifiers": [
        {
            "Name": "string",
            "CreatedDate": "timestamp",
            "DisplayName": "string",
            "Owner": "string",
            "VersionName": "string",
            "PlatformTypes": ["Windows|Linux|MacOS"],
            "DocumentVersion": "string",
            "DocumentType": "string",
            "SchemaVersion": "string",
            "DocumentFormat": "YAML|JSON|TEXT",
            "TargetType": "string",
            "Tags": [],
            "Requires": [],
            "ReviewStatus": "string",
            "Author": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.6 `update-document`

Updates an SSM document, creating a new version.

**Synopsis:**
```bash
aws ssm update-document \
    --content <value> \
    --name <value> \
    [--attachments <value>] \
    [--display-name <value>] \
    [--version-name <value>] \
    [--document-version <value>] \
    [--document-format <value>] \
    [--target-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--content` | **Yes** | string | -- | Updated document content |
| `--name` | **Yes** | string | -- | Document name |
| `--attachments` | No | list | None | File attachments |
| `--display-name` | No | string | None | Display name |
| `--version-name` | No | string | None | Version name |
| `--document-version` | No | string | None | Version to update from (for optimistic locking) |
| `--document-format` | No | string | None | Format: `JSON`, `YAML`, `TEXT` |
| `--target-type` | No | string | None | Target type |

**Output Schema:**
```json
{
    "DocumentDescription": {
        "Name": "string",
        "DocumentVersion": "string",
        "Status": "Creating|Active|Updating|Deleting|Failed",
        "LatestVersion": "string",
        "DefaultVersion": "string"
    }
}
```

---

### 2.7 `update-document-default-version`

Sets the default version of an SSM document.

**Synopsis:**
```bash
aws ssm update-document-default-version \
    --name <value> \
    --document-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Document name |
| `--document-version` | **Yes** | string | -- | Version to set as default |

**Output Schema:**
```json
{
    "Description": {
        "Name": "string",
        "DefaultVersion": "string",
        "DefaultVersionName": "string"
    }
}
```

---

### 2.8 `list-document-versions`

Lists all versions of an SSM document. **Paginated operation.**

**Synopsis:**
```bash
aws ssm list-document-versions \
    --name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Document name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 50) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DocumentVersions": [
        {
            "Name": "string",
            "DisplayName": "string",
            "DocumentVersion": "string",
            "VersionName": "string",
            "CreatedDate": "timestamp",
            "IsDefaultVersion": true,
            "DocumentFormat": "YAML|JSON|TEXT",
            "Status": "Creating|Active|Updating|Deleting|Failed",
            "StatusInformation": "string",
            "ReviewStatus": "string"
        }
    ],
    "NextToken": "string"
}
```
